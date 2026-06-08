# ⚡ @nozez-lab/baileys

<p align="center">
  <b>A powerful, production-ready WhatsApp library built on top of Baileys v7</b><br>
  Interactive messages · Albums · Buttons · Lists · Pairing Code · and more
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/@nozez-lab/baileys">
    <img src="https://img.shields.io/npm/v/@nozez-lab/baileys?style=for-the-badge&logo=npm&color=CB3837" />
  </a>
  <a href="https://www.npmjs.com/package/@nozez-lab/baileys">
    <img src="https://img.shields.io/npm/dm/@nozez-lab/baileys?style=for-the-badge&logo=npm&color=orange" />
  </a>
  <a href="https://github.com/nozez-lab/baileys">
    <img src="https://img.shields.io/github/stars/nozez-lab/baileys?style=for-the-badge&logo=github&color=yellow" />
  </a>
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-blue?style=for-the-badge" />
  </a>
  <a href="https://nodejs.org">
    <img src="https://img.shields.io/badge/node-%3E%3D20-339933?logo=node.js&labelColor=green&logoColor=white&style=for-the-badge" />
  </a>
</p>

---

## 📋 Table of Contents

- [✨ What's Different](#-whats-different)
- [🔧 Internal Fixes](#-internal-fixes)
- [📦 Installation](#-installation)
  - [🔌 Import (ESM & CJS)](#-import-esm--cjs)
- [🚀 Quick Start](#-quick-start)
  - [🔐 Auth State](#-auth-state)
- [🗄️ Data Store](#-data-store)
- [🪪 WhatsApp IDs](#-whatsapp-ids)
- [✉️ Sending Messages](#-sending-messages)
  - [📝 Text](#-text)
  - [🔔 Mention](#-mention)
  - [😄 Reaction](#-reaction)
  - [📌 Pin Message](#-pin-message)
  - [➡️ Forward Message](#-forward-message)
  - [👤 Contact](#-contact)
  - [📍 Location](#-location)
  - [📅 Event](#-event)
  - [👥 Group Invite](#-group-invite)
  - [🛍️ Product](#-product)
  - [📊 Poll](#-poll)
- [🖼️ Media Messages](#-media-messages)
  - [🖼️ Image](#-image)
  - [🎥 Video](#-video)
  - [📃 Sticker](#-sticker)
  - [💽 Audio](#-audio)
  - [🗂️ Document](#-document)
  - [🖼️ Album](#-album)
- [👉 Interactive Messages](#-interactive-messages)
  - [📘 Buttons](#-buttons)
  - [📋 List](#-list)
  - [🗄️ Interactive](#-interactive)
- [♻️ Modify Messages](#-modify-messages)
  - [🗑️ Delete](#-delete)
  - [✏️ Edit](#-edit)
- [🧰 Utilities](#-utilities)
  - [🔑 Custom Pairing Code](#-custom-pairing-code)
  - [🖼️ Image Processing](#-image-processing)
  - [📣 Newsletter](#-newsletter)
  - [👥 Group Management](#-group-management)
  - [👤 Profile Management](#-profile-management)
  - [🔏 Privacy](#-privacy)
- [🔗 Fork Base](#-fork-base)
- [📣 Credits](#-credits)

---

## ✨ What's Different

`@nozez-lab/baileys` adalah library WhatsApp yang dikustomisasi untuk kebutuhan bot modern:

- ✅ **Native Interactive Messages** — Buttons, Lists, Native Flows, Carousels, Templates
- ✅ **Album Support** — Kirim gambar/video dalam satu album
- ✅ **Sticker Pack** — Kirim sticker dalam satu paket
- ✅ **Pairing Code** — Koneksi mudah tanpa QR Code
- ✅ **No Obfuscation** — Kode bersih, mudah dibaca dan diaudit
- ✅ **No Auto-Follow** — Tidak ada behavior channel (newsletter) otomatis

---

## 🔧 Internal Fixes

- 🖼️ Perbaikan upload media ke newsletter (bug upstream)
- 🔄 Reimplementasi `makeInMemoryStore` dengan adaptasi minimal ESM untuk Baileys v7
- 📦 FFmpeg dijalankan dengan `spawn` bukan `exec` untuk keamanan proses
- 🗃️ Penambahan `@napi-rs/image` sebagai backend image processing di `getImageProcessingLibrary()`
- 💬 Dukungan quote message di dalam channel (newsletter)
- 🎀 Dukungan custom button icon pada interactive messages

---

## 📦 Installation

**Via `package.json`:**

```json
{
  "dependencies": {
    "@nozez-lab/baileys": "latest"
  }
}
```

**Via terminal:**

```bash
# Dari NPM
npm install @nozez-lab/baileys@latest

# Dari GitHub
npm install github:nozez-lab/baileys
```

### 🔌 Import (ESM & CJS)

```javascript
// ESM
import { makeWASocket } from '@nozez-lab/baileys'

// CJS (Node.js 24+)
const { makeWASocket } = require('@nozez-lab/baileys')
```

---

## 🚀 Quick Start

```javascript
import {
  makeWASocket,
  delay,
  DisconnectReason,
  useMultiFileAuthState
} from '@nozez-lab/baileys'
import { Boom } from '@hapi/boom'
import pino from 'pino'

const PHONE_NUMBER = '628xxxxxxxxxx'
const logger = pino({ level: 'silent' })

async function startBot() {
  const { state, saveCreds } = await useMultiFileAuthState('session')

  const sock = makeWASocket({ logger, auth: state })

  sock.ev.on('creds.update', saveCreds)

  sock.ev.on('connection.update', async (update) => {
    const { connection, lastDisconnect } = update

    if (connection === 'connecting' && !sock.authState.creds.registered) {
      await delay(1500)
      const code = await sock.requestPairingCode(PHONE_NUMBER)
      console.log('🔗 Pairing Code:', code)
    }

    if (connection === 'close') {
      const shouldReconnect =
        new Boom(lastDisconnect?.error)?.output?.statusCode !== DisconnectReason.loggedOut
      if (shouldReconnect) startBot()
    }

    if (connection === 'open') {
      console.log('✅ Connected to WhatsApp')
    }
  })

  sock.ev.on('messages.upsert', async ({ messages }) => {
    for (const msg of messages) {
      if (!msg.message) continue
      console.log('📩 New message:', msg)
    }
  })
}

startBot()
```

### 🔐 Auth State

> [!NOTE]
> Kamu bisa menggunakan `useSingleFileAuthState` atau `useSqliteAuthState` sebagai alternatif dari `useMultiFileAuthState`. `useSingleFileAuthState` sudah memiliki mekanisme cache internal, sehingga tidak perlu membungkus `state.keys` dengan `makeCacheableSignalKeyStore`.

---

## 🗄️ Data Store

> [!CAUTION]
> Sangat disarankan untuk membuat data store sendiri. Menyimpan seluruh riwayat chat di memori dapat menyebabkan penggunaan RAM yang berlebihan.

```javascript
import {
  makeWASocket,
  makeInMemoryStore,
  delay,
  DisconnectReason,
  useMultiFileAuthState
} from '@nozez-lab/baileys'
import pino from 'pino'

const logger = pino({ level: 'silent' })
const STORE_PATH = './store.json'

async function startBot() {
  const { state, saveCreds } = await useMultiFileAuthState('session')
  const sock = makeWASocket({ logger, auth: state })

  const store = makeInMemoryStore({ logger, socket: sock })
  store.bind(sock.ev)

  sock.ev.on('creds.update', saveCreds)
  sock.ev.on('chats.upsert', () => {
    console.log('✉️ Chats:', store.chats.all())
  })

  store.readFromFile(STORE_PATH)
  setInterval(() => store.writeToFile(STORE_PATH), 180_000)
}

startBot()
```

---

## 🪪 WhatsApp IDs

| Tipe | Format |
|------|--------|
| Personal | `628xxxxxxxxx@s.whatsapp.net` |
| LID | `12699999999@lid` |
| Group | `123456789-123345@g.us` |
| Meta AI | `11111111111@bot` |
| Broadcast | `[timestamp]@broadcast` |
| Status | `status@broadcast` |

---

## ✉️ Sending Messages

> [!NOTE]
> Dapatkan `jid` dari `message.key.remoteJid`.

### 📝 Text

```javascript
// Pesan teks biasa
sock.sendMessage(jid, { text: 'Halo! 👋' }, { quoted: message })

// Dengan link preview
sock.sendMessage(jid, {
  text: 'Cek ini! https://github.com/nozez-lab/baileys',
  linkPreview: {
    'matched-text': 'https://github.com/nozez-lab/baileys',
    title: '⚡ @nozez-lab/baileys',
    description: 'WhatsApp bot library by Nozez',
    previewType: 0
  }
})
```

### 🔔 Mention

```javascript
// Mention user tertentu
sock.sendMessage(jid, {
  text: 'Halo @628123456789!',
  mentions: ['628123456789@s.whatsapp.net']
}, { quoted: message })

// Mention semua anggota grup
sock.sendMessage(jid, {
  text: 'Halo @all!',
  mentionAll: true
}, { quoted: message })
```

### 😄 Reaction

```javascript
sock.sendMessage(jid, {
  react: { key: message.key, text: '⚡' }
})
```

### 📌 Pin Message

```javascript
sock.sendMessage(jid, {
  pin: message.key,
  time: 86400, // 86400 (1h), 604800 (7d), 2592000 (30d)
  type: 1      // 2 untuk unpin
})
```

### ➡️ Forward Message

```javascript
sock.sendMessage(jid, {
  forward: message,
  force: true
})
```

### 👤 Contact

```javascript
const vcard = [
  'BEGIN:VCARD',
  'VERSION:3.0',
  'FN:Nozez',
  'ORG:NozezLab;',
  'TEL;type=CELL;type=VOICE;waid=628123456789:+62 812-3456-789',
  'END:VCARD'
].join('\n')

sock.sendMessage(jid, {
  contacts: {
    displayName: 'Nozez',
    contacts: [{ vcard }]
  }
}, { quoted: message })
```

### 📍 Location

```javascript
sock.sendMessage(jid, {
  location: {
    degreesLatitude: -6.2,
    degreesLongitude: 106.8,
    name: 'Jakarta, Indonesia'
  }
}, { quoted: message })
```

### 📅 Event

```javascript
sock.sendMessage(jid, {
  event: {
    name: '🎉 Community Meetup',
    description: 'Kumpul bareng komunitas Nozez!',
    startDate: new Date(Date.now() + 3600000),
    endDate: new Date(Date.now() + 28800000),
    location: {
      name: 'Jakarta',
      degreesLatitude: -6.2,
      degreesLongitude: 106.8
    }
  }
}, { quoted: message })
```

### 👥 Group Invite

```javascript
const inviteCode = groupUrl.split('chat.whatsapp.com/')[1]?.split('?')[0]

sock.sendMessage(jid, {
  groupInvite: {
    inviteCode,
    inviteExpiration: Date.now() + 86400000,
    text: 'Gabung ke grup kita yuk!',
    jid: '1201111111111@g.us',
    subject: 'NozezLab Community'
  }
}, { quoted: message })
```

### 🛍️ Product

```javascript
import { randomUUID } from 'crypto'

sock.sendMessage(jid, {
  image: { url: './product.jpg' },
  body: 'Cek produk ini!',
  footer: '@nozez-lab/baileys',
  product: {
    currencyCode: 'IDR',
    description: 'Produk pilihan terbaik',
    priceAmount1000: 50_000_000,
    productId: randomUUID(),
    productImageCount: 1,
    title: 'Premium Package',
    url: 'https://github.com/nozez-lab/baileys'
  },
  businessOwnerJid: '0@s.whatsapp.net'
})
```

### 📊 Poll

```javascript
sock.sendMessage(jid, {
  poll: {
    name: '🔥 Vote sekarang!',
    values: ['Ya', 'Tidak'],
    selectableCount: 1,
    endDate: new Date(Date.now() + 28800000)
  }
}, { quoted: message })
```

---

## 🖼️ Media Messages

### 🖼️ Image

```javascript
sock.sendMessage(jid, {
  image: { url: './gambar.jpg' },
  caption: 'Gambar keren! ✨'
}, { quoted: message })
```

### 🎥 Video

```javascript
sock.sendMessage(jid, {
  video: { url: './video.mp4' },
  caption: 'Video keren!'
}, { quoted: message })
```

### 📃 Sticker

```javascript
sock.sendMessage(jid, {
  sticker: { url: './sticker.webp' }
}, { quoted: message })
```

### 💽 Audio

```javascript
sock.sendMessage(jid, {
  audio: { url: './audio.mp3' },
  mimetype: 'audio/mp4',
  ptt: true // true = pesan suara, false = file audio
}, { quoted: message })
```

### 🗂️ Document

```javascript
sock.sendMessage(jid, {
  document: { url: './file.pdf' },
  mimetype: 'application/pdf',
  fileName: 'dokumen.pdf',
  caption: 'Ini dokumennya'
}, { quoted: message })
```

### 🖼️ Album

```javascript
sock.sendMessage(jid, {
  album: [
    { image: { url: './foto1.jpg' }, caption: 'Foto 1' },
    { image: { url: './foto2.jpg' }, caption: 'Foto 2' },
    { video: { url: './video.mp4' }, caption: 'Video' }
  ]
}, { quoted: message })
```

---

## 👉 Interactive Messages

### 📘 Buttons

```javascript
sock.sendMessage(jid, {
  image: { url: './banner.jpg' },
  body: 'Pilih menu di bawah ini:',
  footer: '@nozez-lab/baileys',
  buttons: [
    { id: '#menu', text: '📋 Menu Utama' },
    { id: '#info', text: 'ℹ️ Info' },
    { id: '#help', text: '🆘 Bantuan' }
  ]
}, { quoted: message })
```

### 📋 List

```javascript
sock.sendMessage(jid, {
  body: 'Pilih salah satu opsi:',
  footer: '@nozez-lab/baileys',
  button: '📋 Lihat Menu',
  list: [
    {
      title: '🔧 Tools',
      rows: [
        { id: '#ping', title: 'Ping', description: 'Cek koneksi bot' },
        { id: '#info', title: 'Info', description: 'Info bot' }
      ]
    },
    {
      title: '🎮 Fun',
      rows: [
        { id: '#game', title: 'Game', description: 'Main game' }
      ]
    }
  ]
}, { quoted: message })
```

### 🗄️ Interactive

```javascript
sock.sendMessage(jid, {
  body: 'Selamat datang!',
  footer: 'Powered by @nozez-lab/baileys',
  nativeFlowButtons: [
    {
      name: 'quick_reply',
      buttonParamsJson: JSON.stringify({ display_text: '⚡ Mulai', id: '#start' })
    },
    {
      name: 'cta_url',
      buttonParamsJson: JSON.stringify({
        display_text: '🔗 GitHub',
        url: 'https://github.com/nozez-lab/baileys'
      })
    }
  ]
}, { quoted: message })
```

---

## ♻️ Modify Messages

### 🗑️ Delete

```javascript
// Hapus untuk semua
sock.sendMessage(jid, { delete: message.key })
```

### ✏️ Edit

```javascript
sock.sendMessage(jid, {
  edit: message.key,
  text: 'Pesan yang sudah diedit ✏️'
})
```

---

## 🧰 Utilities

### 🔑 Custom Pairing Code

```javascript
const code = await sock.requestPairingCode('628xxxxxxxxxx', 'NOZEZBOT')
console.log('🔑 Pairing Code:', code)
```

### 🖼️ Image Processing

```javascript
import { getImageProcessingLibrary } from '@nozez-lab/baileys'

const lib = await getImageProcessingLibrary()
console.log('Library yang digunakan:', lib)
```

### 📣 Newsletter (Channel)

```javascript
// Buat newsletter
const newsletter = await sock.createNewsLetter({
  name: 'Nozez Updates',
  description: 'Update terbaru dari Nozez',
  picture: fs.readFileSync('./logo.jpg')
})

// Kirim pesan ke newsletter
sock.sendMessage(newsletter.id, { text: '📢 Pengumuman baru!' })
```

### 👥 Group Management

```javascript
// Buat grup
const group = await sock.groupCreate('Nama Grup', ['628xxx@s.whatsapp.net'])

// Tambah anggota
await sock.groupParticipantsUpdate(group.id, ['628xxx@s.whatsapp.net'], 'add')

// Kick anggota
await sock.groupParticipantsUpdate(group.id, ['628xxx@s.whatsapp.net'], 'remove')

// Promosi admin
await sock.groupParticipantsUpdate(group.id, ['628xxx@s.whatsapp.net'], 'promote')
```

### 👤 Profile Management

```javascript
// Update nama
await sock.updateProfileName('Nozez Bot')

// Update status
await sock.updateProfileStatus('Ditenagai oleh @nozez-lab/baileys ⚡')

// Update foto profil
await sock.updateProfilePicture(sock.user.id, { url: './foto.jpg' })
```

### 🔏 Privacy

```javascript
// Atur last seen
await sock.updateLastSeenPrivacy('contacts')

// Atur online
await sock.updateOnlinePrivacy('match_last_seen')

// Atur foto profil
await sock.updateProfilePicturePrivacy('contacts')
```

---

## 🔗 Fork Base

Proyek ini adalah fork dari:

> **[WhiskeySockets/Baileys](https://github.com/WhiskeySockets/Baileys)**

Semua kredit untuk proyek asli tetap diberikan sepenuhnya. Fork ini menambahkan fitur-fitur tambahan yang dibutuhkan untuk pengembangan bot WhatsApp modern.

---

## 📣 Credits

| Kontribusi | Penulis |
|-----------|---------|
| Library Baileys Original | [WhiskeySockets](https://github.com/WhiskeySockets) |
| Fork & Kustomisasi | [Nozez](https://github.com/nozez-lab) |

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/nozez-lab">Nozez</a>
</p>
