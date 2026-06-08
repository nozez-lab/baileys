# ðŸŒ± @nozez-lab/baileys

[![Logo](https://files.catbox.moe/c5s9g0.jpg)](https://www.npmjs.com/package/@nozez-lab/baileys)

<p align="center">
   Enhanced Baileys v7 with fixes for newsletter media uploads, plus support for interactive messages, albums, and additional message types.
   <br><br>
   <a href="https://www.npmjs.com/package/@nozez-lab/baileys">
      <img src="https://img.shields.io/npm/v/@nozez-lab/baileys?style=for-the-badge&logo=npm"/>
   </a>
   <a href="https://www.npmjs.com/package/@nozez-lab/baileys">
      <img src="https://img.shields.io/npm/dm/@nozez-lab/baileys?style=for-the-badge&logo=npm"/>
   </a>
   <a href="https://github.com/nozez-lab/baileys">
      <img src="https://img.shields.io/github/stars/nozez-lab/baileys?style=for-the-badge&logo=github"/>
   </a>
   <a href="LICENSE">
      <img src="https://img.shields.io/badge/license-MIT-blue?style=for-the-badge"/>
   </a>
   <a href="https://nodejs.org">
      <img src="https://img.shields.io/badge/node-%3E%3D20-339933?logo=node.js&labelColor=green&logoColor=white&style=for-the-badge"/>
   </a>
   <a href="#">
      <img src="https://img.shields.io/badge/ESM-only?logo=javascript&labelColor=yellow&logoColor=black&style=for-the-badge"/>
   </a>
</p>

â˜• For donation: [Saweria](https://saweria.co/nozez-lab)

### ðŸ“‹ Table of Contents
- [ðŸ“‹ Table of Contents](#-table-of-contents)
- [âœ¨ Highlights](#-highlights)
- [ðŸ› ï¸ Internal Adjustments](#%EF%B8%8F-internal-adjustments)
- [ðŸ“¨ Messages Handling & Compatibility](#-highlights)
- [ðŸ§© Additional Message Options](#-additional-message-options)
- [ðŸ“¥ Installation](#-installation)
   - [ðŸ§© Import (ESM & CJS)](#-import-esm--cjs)
- [ðŸŒ Connect to WhatsApp (Quick Step)](#-connect-to-whatsapp-quick-step)
   - [ðŸ” Auth State](#-auth-state)
- [ðŸ—„ï¸ Implementing Data Store](#%EF%B8%8F-implementing-data-store)
- [ðŸªª WhatsApp IDs Explain](#-whatsapp-ids-explain)
- [âœ‰ï¸ Sending Messages](#%EF%B8%8F-sending-messages)
   - [ðŸ”  Text](#-text)
   - [ðŸ”” Mention](#-mention)
   - [ðŸ˜ Reaction](#-reaction)
   - [ðŸ“Œ Pin Message](#-pin-message)
   - [ðŸ”– Keep Chat](#-keep-chat)
   - [âž¡ï¸ Forward Message](#%EF%B8%8F-forward-message)
   - [ðŸ‘¤ Contact](#-contact)
   - [ðŸ“ Location](#-location)
   - [ðŸ—“ï¸ Event](#%EF%B8%8F-event)
   - [ðŸ‘¥ Group Invite](#-group-invite)
   - [ðŸ›ï¸ Product](#%EF%B8%8F-product)
   - [ðŸ“Š Poll](#-poll)
   - [ðŸ’­ Button Response](#-button-response)
   - [âœ¨ Rich Response](#-rich-response)
   - [ðŸ§¾ Message with Code Block](#-message-with-code-block)
   - [ðŸŒ Message with Inline Entities](#-message-with-inline-entities)
   - [ðŸ“‹ Message with Table](#-message-with-table)
   - [ðŸŽžï¸ Status Mention](#%EF%B8%8F-status-mention)
- [ðŸ“ Sending Media Messages](#-sending-media-messages)
   - [ðŸ–¼ï¸ Image](#%EF%B8%8F-image)
   - [ðŸŽ¥ Video](#-video)
   - [ðŸ“ƒ Sticker](#-sticker)
   - [ðŸ’½ Audio](#-audio)
   - [ðŸ—‚ï¸ Document](#%EF%B8%8F-document)
   - [ðŸ–¼ï¸ Album (Image & Video)](#%EF%B8%8F-album-image--video)
   - [ðŸ“¦ Sticker Pack](#-sticker-pack)
- [ðŸ‘‰ðŸ» Sending Interactive Messages](#-sending-interactive-messages)
   - [ðŸ”˜ Buttons](#-buttons)
   - [ðŸ“‹ List](#-list)
   - [ðŸ—„ï¸ Interactive](#%EF%B8%8F-interactive)
   - [ðŸ«™ Hydrated Template](#-hydrated-template)
- [ðŸ’³ Sending Payment Messages](#-sending-payment-messages)
   - [âž• Invite Payment](#-invite-payment)
   - [ðŸ§¾ Invoice](#-invoice)
   - [ðŸ›ï¸ Order](#%EF%B8%8F-order)
   - [ðŸ’³ Request Payment](#-request-payment)
- [ðŸ‘ï¸ Other Message Options](#%EF%B8%8F-other-message-options)
   - [ðŸ¤– AI Icon](#-ai-icon)
   - [ðŸ•’ Ephemeral](#-ephemeral)
   - [ðŸ“° External Ad Reply](#-external-ad-reply)
   - [ðŸ§‘â€ðŸ§‘â€ðŸ§’ Group Status](#%E2%80%8D%E2%80%8D-group-status)
   - [ðŸ± Lottie Sticker](#-lottie-sticker)
   - [ðŸ§© Raw](#-raw)
   - [ðŸ·ï¸ Secure Meta Service Label](#%EF%B8%8F-secure-meta-service-label)
   - [ðŸ“‘ Spoiler](#-spoiler)
   - [ðŸ‘ï¸ View Once](#%EF%B8%8F-view-once)
   - [ðŸ‘ï¸ View Once V2](#%EF%B8%8F-view-once-v2)
   - [ðŸ‘ï¸ View Once V2 Extension](#%EF%B8%8F-view-once-v2-extension)
- [â™»ï¸ Modify Messages](#%EF%B8%8F-modify-messages)
   - [ðŸ—‘ï¸ Delete Messages](#%EF%B8%8F-delete-messages)
   - [âœï¸ Edit Messages](#%EF%B8%8F-edit-messages)
- [ðŸ§° Additional Contents](#-additional-contents)
   - [ðŸ·ï¸ Find User ID (JID|PN/LID)](#%EF%B8%8F-find-user-id-jidpnlid)
   - [ðŸ”‘ Request Custom Pairing Code](#-request-custom-pairing-code)
   - [ðŸ–¼ï¸ Image Processing](#%EF%B8%8F-image-processing)
   - [ðŸ“£ Newsletter Management](#-newsletter-management)
   - [ðŸ‘¥ Group Management](#-group-management)
   - [ðŸ‘¥ Community Management](#-community-management)
   - [ðŸ‘¤ Profile Management](#-profile-management)
   - [ðŸ›’ Business Management](#-business-management)
   - [ðŸ” Privacy Management](#-privacy-management)
   - [ðŸ“¡ Events](#-events)
- [ðŸš€ Try the Bot](#-try-the-bot)
- [ðŸ“¦ Fork Base](#-fork-base)
- [ðŸ“£ Credits](#-credits)

### âœ¨ Highlights

This fork designed for production use with a focus on clarity and safety:

- ðŸš« No obfuscation. Easy to read and audit.
- ðŸš« No auto-follow channel (newsletter) behavior.

> [!IMPORTANT]
> Hi everyone,
>
> I want to clarify two separate attribution issues regarding packages derived from this fork.
>
> 1. Direct redistribution of my modifications without attribution
>
> The following packages are operated by the same individual under multiple npm accounts:
>
> - [@nuisockets](https://www.npmjs.com/package/@nuisockets/baileys)
> - [@nuiisatoru](https://www.npmjs.com/package/@nuiisatoru/baileys)
> - [@nuiisweetberry](https://www.npmjs.com/package/@nuiisweetberry/baileys)
> - [@nuiisweety](https://www.npmjs.com/package/@nuiisweety/baileys)
>
> These packages redistribute files and modifications originating from this fork while removing contributor credits and modification notes.
>
> 2. Rebranded republishes of this fork
>
> - [@lumina-md](https://www.npmjs.com/package/@lumina-md/baileys)
> - [@sairidev](https://www.npmjs.com/package/@sairidev/baileys-new)
> - [nexora-baileys](https://www.npmjs.com/package/nexora-baileys)
> - [baileys-yorkv2](https://www.npmjs.com/package/baileys-yorkv2)
> - [aetherzxyz](https://www.npmjs.com/package/aetherzxyz)
>
> These packages primarily repackage or republish this fork under different names while failing to preserve proper attribution, credits, or modification notes.
> 
> To be clear, I am **NOT** the original maintainer of Baileys. Full credit and respect belong to:
>
> https://github.com/WhiskeySockets/Baileys
>
> **Forking is completely acceptable. Removing attribution, contributor credits, or modification history is not.**
>
> Please report if necessary.
>
> Thank you. ðŸ¤

> [!NOTE]
> ðŸ“„ This project is maintained with limited scope and is not intended to replace upstream Baileys.
>
> ðŸ˜ž And, really sorry for my bad english.

### ðŸ› ï¸ Internal Adjustments
- ðŸ–¼ï¸ Fixed an issue where media could not be sent to newsletters due to an upstream issue.
- ðŸ“ Reintroduced [`makeInMemoryStore`](#%EF%B8%8F-implementing-data-store) with a minimal ESM adaptation and small adjustments for Baileys v7.
- ðŸ“¦ Switched FFmpeg execution from `exec` to `spawn` for safer process handling.
- ðŸ—ƒï¸ Added [`@napi-rs/image`](https://www.npmjs.com/package/@napi-rs/image) as a supported image processing backend in [`getImageProcessingLibrary()`](#%EF%B8%8F-image-processing), offering a balance between performance and compatibility.

### ðŸ“¨ Messages Handling & Compatibility
- ðŸ“© Expanded messages support for:
   - ðŸ–¼ï¸ [Album Message](#%EF%B8%8F-album-image--video)
   - ðŸ‘¤ [Group Status Message](#%E2%80%8D%E2%80%8D-group-status)
   - ðŸ‘‰ðŸ» [Interactive Message](#-sending-interactive-messages) (buttons, lists, native flows, templates, carousels).
   - ðŸŽžï¸ [Status Mention Message](#%EF%B8%8F-status-mention)
   - ðŸ“¦ [Sticker Pack Message](#-sticker-pack)
   - âœ¨ [Rich Response Message](#-rich-response) **[NEW]**
   - ðŸ§¾ [Message with Code Blocks](#-message-with-code-block) **[NEW]**
   - [ðŸŒ Message with Inline Entities](#-message-with-inline-entities) **[NEW]**
   - ðŸ“‹ [Message with Table](#-message-with-table) **[NEW]**
   - ðŸ’³ [Payment-related Message](#-sending-payment-messages) (payment requests, invites, orders, invoices).
- ðŸ“° Simplified sending messages with ad thumbnail using [`externalAdReply`](#-external-ad-reply), without requiring manual `contextInfo`.
- ðŸ’­ Added support for quoting messages inside channel (newsletter). **[NEW]**
- ðŸŽ€ Added support for [custom button icon](#%EF%B8%8F-interactive). **[NEW]**

### ðŸ§© Additional Message Options
- ðŸ‘ï¸ Added optional boolean flags for message handling:  
   - ðŸ¤– [`ai`](#-ai-icon) - AI icon on message
   - ðŸ“£ [`mentionAll`](#-mention) - Mention all group participants without requiring their JIDs in `mentions` or `mentionedJid` **[NEW]**
   - ðŸ”§ [`ephemeral`](#-ephemeral), [`groupStatus`](#%E2%80%8D%E2%80%8D-group-status), [`isLottie`](#-lottie-sticker), [`spoiler`](#-spoiler), [`viewOnce`](#%EF%B8%8F-view-once), [`viewOnceV2`](#%EF%B8%8F-view-once-v2), [`viewOnceV2Extension`](#%EF%B8%8F-view-once-v2-extension), [`interactiveAsTemplate`](#%EF%B8%8F-interactive) - Message wrappers
   - ðŸ”’ [`secureMetaServiceLabel`](#%EF%B8%8F-secure-meta-service-label) - Secure meta service label on message **[NEW]**
   - ðŸ“„ [`raw`](#-raw) - Build your message manually **(DO NOT USE FOR EXPLOITATION)**

### ðŸ“¥ Installation

- ðŸ“„ Via `package.json`

```json
# NPM
"dependencies": {
   "@nozez-lab/baileys": "latest"
}

# GitHub
"dependencies": {
   "@nozez-lab/baileys": "github:nozez-lab/baileys"
}
```

- âŒ¨ï¸ Via terminal

```bash
# NPM
npm i @nozez-lab/baileys@latest

# GitHub
npm i github:nozez-lab/baileys
```

#### ðŸ§© Import (ESM & CJS)

```javascript
// --- ESM
import { makeWASocket } from '@nozez-lab/baileys'

// --- CJS (tested and working on Node.js 24 âœ…)
const { makeWASocket } = require('@nozez-lab/baileys')
```

### ðŸŒ Connect to WhatsApp (Quick Step)

```javascript
import { makeWASocket, delay, DisconnectReason, useMultiFileAuthState } from '@nozez-lab/baileys'
import { Boom } from '@hapi/boom'
import pino from 'pino'

// --- Connect with pairing code
const myPhoneNumber = '6288888888888'

const logger = pino({ level: 'silent' })

const connectToWhatsApp = async () => {
   const { state, saveCreds } = await useMultiFileAuthState('session')
    
   const sock = makeWASocket({
      logger,
      auth: state
   })

   sock.ev.on('creds.update', saveCreds)

   sock.ev.on('connection.update', (update) => {
      const { connection, lastDisconnect } = update
      if (connection === 'connecting' && !sock.authState.creds.registered) {
         await delay(1500)
         const code = await sock.requestPairingCode(myPhoneNumber)
         console.log('ðŸ”— Pairing code', ':', code)
      }
      else if (connection === 'close') {
         const shouldReconnect = new Boom(connection?.lastDisconnect?.error)?.output?.statusCode !== DisconnectReason.loggedOut
         console.log('âš ï¸ Connection closed because', lastDisconnect.error, ', reconnecting ', shouldReconnect)
         if (shouldReconnect) {
            connectToWhatsApp()
         }
      }
      else if (connection === 'open') {
         console.log('âœ… Successfully connected to WhatsApp')
      }
   })

   sock.ev.on('messages.upsert', async ({ messages }) => {
      for (const message of messages) {
         if (!message.message) continue

         console.log('ðŸ”” Got new message', ':', message)
         await sock.sendMessage(message.key.remoteJid, {
            text: 'ðŸ‘‹ðŸ» Hello world'
         })
      }
   })
}

connectToWhatsApp()
```

#### ðŸ” Auth State

> [!NOTE]
> You can use the experimental `useSingleFileAuthState` and `useSqliteAuthState` as an alternative to `useMultiFileAuthState`. However, `useSingleFileAuthState` already includes an internal caching mechanism, so there is no need to wrap `state.keys` with `makeCacheableSignalKeyStore`.

### ðŸ—„ï¸ Implementing Data Store

> [!CAUTION]
> I highly recommend building your own data store, as keeping an entire chat history in memory can lead to excessive RAM usage.

```javascript
import { makeWASocket, makeInMemoryStore, delay, DisconnectReason, useMultiFileAuthState } from '@nozez-lab/baileys'
import { Boom } from '@hapi/boom'
import pino from 'pino'

const myPhoneNumber = '6288888888888'

// --- Create your store path
const storePath = './store.json'

const logger = pino({ level: 'silent' })

const connectToWhatsApp = async () => {
   const { state, saveCreds } = await useMultiFileAuthState('session')
    
   const sock = makeWASocket({
      logger,
      auth: state
   })

   const store = makeInMemoryStore({
      logger,
      socket: sock
   })

   store.bind(sock.ev)

   sock.ev.on('creds.update', saveCreds)

   sock.ev.on('connection.update', (update) => {
      const { connection, lastDisconnect } = update
      if (connection === 'connecting' && !sock.authState.creds.registered) {
         await delay(1500)
         const code = await sock.requestPairingCode(myPhoneNumber)
         console.log('ðŸ”— Pairing code', ':', code)
      }
      else if (connection === 'close') {
         const shouldReconnect = new Boom(connection?.lastDisconnect?.error)?.output?.statusCode !== DisconnectReason.loggedOut
         console.log('âš ï¸ Connection closed because', lastDisconnect.error, ', reconnecting ', shouldReconnect)
         if (shouldReconnect) {
            connectToWhatsApp()
         }
      }
      else if (connection === 'open') {
         console.log('âœ… Successfully connected to WhatsApp')
      }
   })

   sock.ev.on('chats.upsert', () => {
      console.log('âœ‰ï¸ Got chats', store.chats.all())
   })

   sock.ev.on('contacts.upsert', () => {
      console.log('ðŸ‘¥ Got contacts', Object.values(store.contacts))
   })

   // --- Read store from file
   store.readFromFile(storePath)

   // --- Save store every 3 minutes
   setInterval(() => {
      store.writeToFile(storePath)
   }, 180000)
}

connectToWhatsApp()
```

### ðŸªª WhatsApp IDs Explain

`id` is the WhatsApp ID, called `jid` and `lid` too, of the person or group you're sending the message to.
- It must be in the format `[country code][phone number]@s.whatsapp.net`
   - Example for people: `19999999999@s.whatsapp.net` and `12699999999@lid`.
   - For groups, it must be in the format `123456789-123345@g.us`.
- For Meta AI, it's `11111111111@bot`.
- For broadcast lists, it's `[timestamp of creation]@broadcast`.
- For stories, the ID is `status@broadcast`.

### âœ‰ï¸ Sending Messages

> [!NOTE]
> You can get the `jid` from `message.key.remoteJid` in the first example.

#### ðŸ”  Text

```javascript
// --- Send a regular text message
sock.sendMessage(jid, {
   text: 'ðŸ‘‹ðŸ» Hello'
}, {
   quoted: message
})

// --- Send a text message with a link preview
const urlA = 'https://www.npmjs.com/package/@nozez-lab/baileys'

sock.sendMessage(jid, {
   text: urlA + ' ðŸ‘†ðŸ» Check it out!',
   linkPreview: {
      'matched-text': urlA,
      title: 'ðŸŒ± @nozez-lab/baileys',
      description: 'Underrated Baileys Fork',
      previewType: 0, // --- Use 1 for video playback in the link preview
      jpegThumbnail: fs.readFileSync('./path/to/image.jpg')
   }
})

// --- Send a text message with a large link preview and favicon
import { prepareWAMessageMedia } from '@nozez-lab/baileys'

const urlB = 'https://www.npmjs.com/package/@nozez-lab/baileys#readme'

const { imageMessage: image } = await prepareWAMessageMedia({
   image: {
      url: './path/to/image.jpg'
   }
}, {
   upload: sock.waUploadToServer,
   mediaTypeOverride: 'thumbnail-link'
})

// --- Set the thumbnail display size
image.height = 720
image.width = 480

sock.sendMessage(jid, {
   text: urlB + ' ðŸ‘†ðŸ» Check it out!',
   linkPreview: {
      'matched-text': urlB,
      title: 'ðŸŒ± @nozez-lab/baileys',
      description: 'Underrated Baileys Fork',
      previewType: 0,
      jpegThumbnail: fs.readFileSync('./path/to/image.jpg'),
      highQualityThumbnail: image,
      linkPreviewMetadata: {
         linkMediaDuration: 0, // --- Duration in seconds (for video/audio content)
         socialMediaPostType: 1, // --- Enum: 0 = NONE, 1 = REEL, 2 = LIVE_VIDEO, 3 = LONG_VIDEO, 4 = SINGLE_IMAGE, 5 = CAROUSEL
      } // --- Additional metadata for large link preview
   },
   favicon: {
      url: './path/to/tiny-image.ico'
   }
})
```

#### ðŸ”” Mention

```javascript
// --- Regular mention
sock.sendMessage(jid, {
   text: 'ðŸ‘‹ðŸ» Hello @628123456789',
   mentions: ['628123456789@s.whatsapp.net']
}, {
   quoted: message
})

// --- Mention all
sock.sendMessage(jid, {
   text: 'ðŸ‘‹ðŸ» Hello @all',
   mentionAll: true
}, {
   quoted: message
})
```

#### ðŸ˜ Reaction

```javascript
sock.sendMessage(jid, {
   react: {
      key: message.key,
      text: 'âœ¨'
   }
})
```

#### ðŸ“Œ Pin Message

```javascript
sock.sendMessage(jid, {
   pin: message.key,
   time: 86400, // --- Set the value in seconds: 86400 (1d), 604800 (7d), or 2592000 (30d)
   type: 1 // --- Or 2 to remove
})
```

#### ðŸ”– Keep Chat

> [!NOTE]
> Keep Chat can only be used in chats or groups with disappearing messages enabled.

```javascript
sock.sendMessage(jid, {
   keep: message.key,
   type: 1 // --- Or 2 to remove
})
```

#### âž¡ï¸ Forward Message

```javascript
sock.sendMessage(jid, {
   forward: message,
   force: true // --- Optional
})
```

#### ðŸ‘¤ Contact

```javascript
const vcard = 'BEGIN:VCARD\n'
            + 'VERSION:3.0\n'
            + 'FN:Nozez\n'
            + 'ORG:Waitress;\n'
            + 'TEL;type=CELL;type=VOICE;waid=628123456789:+62 8123 4567 89\n'
            + 'END:VCARD'

sock.sendMessage(jid, {
   contacts: {
      displayName: 'Nozez',
      contacts: [
         { vcard }
      ]
   }
}, {
   quoted: message
})
```

#### ðŸ“ Location

```javascript
sock.sendMessage(jid, {
   location: {
      degreesLatitude: 24.121231,
      degreesLongitude: 55.1121221,
      name: 'ðŸ‘‹ðŸ» I am here'
   }
}, {
   quoted: message
})
```

#### ðŸ—“ï¸ Event

```javascript
sock.sendMessage(jid, {
   event: {
      name: 'ðŸŽ¶ Meet & Mingle Party',
      description: 'Meet & Mingle Party is a fun, casual gathering to connect, chat, and build new relationships within the community.',
      call: 'audio', // --- Or "video", this field is optional
      startDate: new Date(Date.now() + 3600000),
      endDate: new Date(Date.now() + 28800000),
      isCancelled: false, // --- Optional
      isScheduleCall: false, // --- Optional
      extraGuestsAllowed: false, // --- Optional
      location: {
         name: 'Jakarta',
         degreesLatitude: -6.2,
         degreesLongitude: 106.8
      }
   }
}, {
   quoted: message
})
```

#### ðŸ‘¥ Group Invite

```javascript
const inviteCode = groupUrl
   .split('chat.whatsapp.com/')[1]
   ?.split('?')[0]

const groupJid = '1201111111111@g.us'
const groupName = '@nozez-lab/baileys'

sock.sendMessage(jid, {
   groupInvite: {
      inviteCode,
      inviteExpiration: Date.now() + 86400000,
      text: 'ðŸ‘‹ðŸ» Hello, we invite you to join our group.',
      jid: groupJid,
      subject: groupName,
   }
}, {
   quoted: message
})
```

#### ðŸ›ï¸ Product

```javascript
import { randomUUID } from 'crypto'

sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   body: 'ðŸ‘‹ðŸ» Check my product here!',
   footer: '@nozez-lab/baileys',
   product: {
      currencyCode: 'IDR',
      description: 'ðŸ›ï¸ Interesting product!',
      priceAmount1000: 70_000_000,
      productId: randomUUID(),
      productImageCount: 1,
      salePriceAmount1000: 65_000_000,
      signedUrl: 'https://www.npmjs.com/package/@nozez-lab/baileys',
      title: 'ðŸ“¦ Starseed (Premium)',
      url: 'https://www.npmjs.com/package/@nozez-lab/baileys'
   },
   businessOwnerJid: '0@s.whatsapp.net'
})
```

#### ðŸ“Š Poll

```javascript
// --- Regular poll message
sock.sendMessage(jid, {
   poll: {
      name: 'ðŸ”¥ Voting time',
      values: ['Yes', 'No'],
      selectableCount: 1,
      toAnnouncementGroup: false,
      endDate: new Date(Date.now() + 28800000), // --- Optional
      hideVoter: false, // --- Optional
      canAddOption: false // --- Optional
   }
}, {
   quoted: message
})

// --- Quiz (only for newsletter)
sock.sendMessage('1211111111111@newsletter', {
   poll: {
      name: 'ðŸ”¥ Quiz',
      values: ['Yes', 'No'],
      correctAnswer: 'Yes',
      pollType: 1
   }
}, {
   quoted: message
})

// --- Poll result
sock.sendMessage(jid, {
   pollResult: {
      name: 'ðŸ“ Poll Result',
      votes: [{
         name: 'Nice',
         voteCount: 10
      }, {
         name: 'Nah',
         voteCount: 2
      }],
      pollType: 0 // Or 1 for quiz
   }
}, {
   quoted: message
})

// --- Poll update
sock.sendMessage(jid, {
   pollUpdate: {
      metadata: {},
      key: message.key,
      vote: {
         enclv: /* <Buffer> */,
         encPayload: /* <Buffer> */
      }
   }
}, {
   quoted: message
})
```

#### ðŸ’­ Button Response

```javascript
// --- Using buttonsResponseMessage
sock.sendMessage(jid, {
   type: 'plain',
   buttonReply: {
      id: '#Menu',
      displayText: 'âœ¨ Interesting Menu'
   }
}, {
   quoted: message
})

// --- Using interactiveResponseMessage
sock.sendMessage(jid, {
   flowReply: {
      format: 0,
      text: 'ðŸ’­ Response',
      name: 'menu_options',
      paramsJson: JSON.stringify({
         id: '#Menu',
         description: 'âœ¨ Interesting Menu'
      })
   }
}, {
   quoted: message
})

// --- Using listResponseMessage
sock.sendMessage(jid, {
   listReply: {
      title: 'ðŸ“„ See More',
      description: 'âœ¨ Interesting Menu',
      id: '#Menu'
   }
}, {
   quoted: message
})

// --- Using templateButtonReplyMessage
sock.sendMessage(jid, {
   type: 'template',
   buttonReply: {
      id: '#Menu',
      displayText: 'âœ¨ Interesting Menu',
      index: 1
   }
}, {
   quoted: message
})
```

#### âœ¨ Rich Response

> [!NOTE]
> `richResponse[]` is a representation of [`submessages[]`](https://baileys.wiki/docs/api/namespaces/proto/interfaces/IAIRichResponseSubMessage) inside `richResponseMessage`.

> [!TIP]
> You can still use the original [`submessages[]`](https://baileys.wiki/docs/api/namespaces/proto/interfaces/IAIRichResponseSubMessage) field directly.
> The code example below is just an implementation using a helper, not a required structure.

```javascript
sock.sendMessage(jid, {
   disclaimerText: 'RAW submessages structure example',
   richResponse: [{
      text: 'Example Usage',
   }, {
      language: 'javascript',
      code: [{
         highlightType: 0,
         codeContent: 'console.log("Hello, World!")'
      }]
   }, {
      text: 'Pretty simple, right?\n'
   }, {
      text: 'Comparison between Node.js, Bun, and Deno',
   }, {
      title: 'Runtime Comparison',
      table: [{
         isHeading: true,
         items: ['', 'Node.js', 'Bun', 'Deno']
      }, {
         isHeading: false,
         items: ['Engine', 'V8 (C++)', 'JavaScriptCore (C++)', 'V8 (C++)']
      }, {
         isHeading: false,
         items: ['Performance', '4/5', '5/5', '4/5']
      }]
   }, {
      text: 'Does this help clarify the differences?'
   }]
})
```

> [!TIP]
> You can easily add syntax highlighting by importing `tokenizeCode` directly from Baileys.

```javascript
import { tokenizeCode } from '@nozez-lab/baileys'

const language = 'javascript'
const code = 'console.log("Hello, World!")'

sock.sendMessage(jid, {
   disclaimerText: 'Example of tokenizing Code Block',
   richResponse: [{
      text: 'Example Usage',
   }, {
      language,
      code: tokenizeCode(code, language)
   }, {
      text: 'Pretty simple, right?'
   }]
})
```

> ðŸ’¡ Supported Languages: `css`, `html`, `javascript`, `typescript`, `python`, `golang`, `rust`, `c`, `c#`, `c++`, `bash`, `bat`, `powershell`.

#### ðŸ§¾ Message with Code Block

> [!NOTE]
> This feature already includes a built-in tokenizer with `tokenizeCode`.

```javascript
sock.sendMessage(jid, {
   disclaimerText: 'Code Block',
   headerText: '## Example Usage',
   contentText: '---',
   code: 'console.log("Hello, World!")',
   language: 'javascript',
   footerText: 'Pretty simple, right?'
})
```

#### ðŸŒ Message with Inline Entities

```javascript
sock.sendMessage(jid, {
   disclaimerText: 'Inline Entities',
   headerText: '## Check Out!',
   contentText: '---',
   links: [{
      text: '1. Google',
      title: 'Popular Search Engine',
      url: 'https://www.google.com/'
   }, {
      text: '2. YouTube',
      title: 'Popular Streaming Platform',
      url: 'https://www.youtube.com/'
   }, {
      text: '3. Modded Baileys',
      title: 'Underrated Baileys Fork',
      url: 'https://www.npmjs.com/package/@nozez-lab/baileys'
   }],
   footerText: '---'
})
```

#### ðŸ“‹ Message with Table

```javascript
sock.sendMessage(jid, {
   disclaimerText: 'Table',
   headerText: '## Comparison between Node.js, Bun, and Deno',
   contentText: '---',
   title: 'Runtime Comparison',
   table: [
      ['', 'Node.js', 'Bun', 'Deno'],
      ['Engine', 'V8 (C++)', 'JavaScriptCore (C++)', 'V8 (C++)'],
      ['Performance', '4/5', '5/5', '4/5']
   ],
   noHeading: false, // --- Optional
   footerText: 'Does this help clarify the differences?'
})
```

#### ðŸŽžï¸ Status Mention

```javascript
sock.sendMessage([jidA, jidB, jidC], {
   text: 'Hello! ðŸ‘‹ðŸ»'
})
```

### ðŸ“ Sending Media Messages

> [!NOTE]
> For media messages, you can pass a `Buffer` directly, or an object with either `{ stream: Readable }` or `{ url: string }` (local file path or HTTP/HTTPS URL).

#### ðŸ–¼ï¸ Image

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ”¥ Superb'
}, {
   quoted: message
})
```

#### ðŸŽ¥ Video

```javascript
sock.sendMessage(jid, {
   video: {
      url: './path/to/video.mp4'
   },
   gifPlayback: false, // --- Set true if you want to send video as GIF
   ptv: false,  // --- Set true if you want to send video as PTV
   caption: 'ðŸ”¥ Superb'
}, {
   quoted: message
})
```

#### ðŸ“ƒ Sticker

```javascript
sock.sendMessage(jid, {
   sticker: {
      url: './path/to/sticker.webp'
   }
}, {
   quoted: message
})
```

#### ðŸ’½ Audio

```javascript
sock.sendMessage(jid, {
   audio: {
      url: './path/to/audio.mp3'
   },
   ptt: false // --- Set true if you want to send audio as Voice Note
}, {
   quoted: message
})
```

#### ðŸ—‚ï¸ Document

```javascript
sock.sendMessage(jid, {
   document: {
      url: './path/to/document.pdf'
   },
   mimetype: 'application/pdf',
   caption: 'âœ¨ My work!'
}, {
   quoted: message
})
```

#### ðŸ–¼ï¸ Album (Image & Video)

```javascript
sock.sendMessage(jid, {
   album: [{
      image: {
         url: './path/to/image.jpg'
      },
      caption: '1st image'
   }, {
      video: {
         url: './path/to/video.mp4'
      },
      caption: '1st video'
   }, {
      image: {
         url: './path/to/image.jpg'
      },
      caption: '2nd image'
   }, {
      video: {
         url: './path/to/video.mp4'
      },
      caption: '2nd video'
   }]
}, {
   quoted: message
})
```

#### ðŸ“¦ Sticker Pack

> [!IMPORTANT]
> If `sharp` or `@napi-rs/image` is not installed, the `cover` and `stickers` must already be in WebP format.

```javascript
sock.sendMessage(jid, {
   cover: {
      url: './path/to/image.webp'
   },
   stickers: [{
      data: {
         url: './path/to/image.webp'
      }
   }, {
      data: {
         url: './path/to/image.webp'
      }
   }, {
      data: {
         url: './path/to/image.webp'
      }
   }],
   name: 'ðŸ“¦ My Sticker Pack',
   publisher: 'ðŸŒŸ Nozez',
   description: '@nozez-lab/baileys'
}, {
   quoted: message
})
```

### ðŸ‘‰ðŸ» Sending Interactive Messages

#### ðŸ”˜ Buttons

```javascript
// --- Regular buttons message
sock.sendMessage(jid, {
   text: 'ðŸ‘†ðŸ» Buttons!',
   footer: '@nozez-lab/baileys',
   buttons: [{
      text: 'ðŸ‘‹ðŸ» SignUp',
      id: '#SignUp'
   }]
}, {
   quoted: message
})

// --- Buttons with Media & Native Flow
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ‘†ðŸ» Buttons and Native Flow!',
   footer: '@nozez-lab/baileys',
   buttons: [{
      text: 'ðŸ‘‹ðŸ» Rating',
      id: '#Rating'
   }, {
      text: 'ðŸ“‹ Select',
      sections: [{
         title: 'âœ¨ Section 1',
         rows: [{
            header: '',
            title: 'ðŸ’­ Secret Ingredient',
            description: '',
            id: '#SecretIngredient'
         }]
      }, {
         title: 'âœ¨ Section 2',
         highlight_label: 'ðŸ”¥ Popular',
         rows: [{
            header: '',
            title: 'ðŸ·ï¸ Coupon',
            description: '',
            id: '#CouponCode'
         }]
      }]
   }]
}, {
   quoted: message
})
```

#### ðŸ“‹ List

> [!NOTE]
> It only works in private chat (`@s.whatsapp.net`).

```javascript
sock.sendMessage(jid, {
   text: 'ðŸ“‹ List!',
   footer: '@nozez-lab/baileys',
   buttonText: 'ðŸ“‹ Select',
   title: 'ðŸ‘‹ðŸ» Hello',
   sections: [{
      title: 'ðŸš€ Menu 1',
      rows: [{
         title: 'âœ¨ AI',
         description: '',
         rowId: '#AI'
      }]
   }, {
      title: 'ðŸŒ± Menu 2',
      rows: [{
         title: 'ðŸ” Search',
         description: '',
         rowId: '#Search'
      }]
   }]
}, {
   quoted: message
})
```

#### ðŸ—„ï¸ Interactive

```javascript
// --- Native Flow
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ—„ï¸ï¸ Interactive!',
   footer: '@nozez-lab/baileys',
   optionText: 'ðŸ‘‰ðŸ» Select Options', // --- Optional, wrap all native flow into a single list
   optionTitle: 'ðŸ“„ Select Options', // --- Optional
   offerText: 'ðŸ·ï¸ Newest Coupon!', // --- Optional, add an offer into message
   offerCode: '@nozez-lab/baileys', // --- Optional
   offerUrl: 'https://www.npmjs.com/package/@nozez-lab/baileys', // --- Optional
   offerExpiration: Date.now() + 3_600_000, // --- Optional
   nativeFlow: [{
      text: 'ðŸ‘‹ðŸ» Greeting',
      id: '#Greeting',
      icon: 'review' // --- Optional
   }, {
      text: 'ðŸ“ž Call',
      call: '628123456789'
   }, {
      text: 'ðŸ“‹ Copy',
      copy: '@nozez-lab/baileys'
   }, {
      text: 'ðŸŒ Source',
      url: 'https://www.npmjs.com/package/@nozez-lab/baileys',
      useWebview: true // --- Optional
   }, {
      text: 'ðŸ“‹ Select',
      sections: [{
         title: 'âœ¨ Section 1',
         rows: [{
            header: '',
            title: 'ðŸ·ï¸ Coupon',
            description: '',
            id: '#CouponCode'
         }]
      }, {
         title: 'âœ¨ Section 2',
         highlight_label: 'ðŸ”¥ Popular',
         rows: [{
            header: '',
            title: 'ðŸ’­ Secret Ingredient',
            description: '',
            id: '#SecretIngredient'
         }]
      }],
      icon: 'default' // --- Optional
   }],
   interactiveAsTemplate: false, // --- Optional, wrap the interactive message into a template
}, {
   quoted: message
})

// --- Carousel & Native Flow
sock.sendMessage(jid, {
   text: 'ðŸ—‚ï¸ Interactive with Carousel!',
   footer: '@nozez-lab/baileys',
   cards: [{
      image: {
         url: './path/to/image.jpg'
      },
      caption: 'ðŸ–¼ï¸ Image 1',
      footer: 'ðŸ·ï¸ï¸ Pinterest',
      nativeFlow: [{
         text: 'ðŸŒ Source',
         url: 'https://www.npmjs.com/package/@nozez-lab/baileys',
         useWebview: true
      }]
   }, {
      image: {
         url: './path/to/image.jpg'
      },
      caption: 'ðŸ–¼ï¸ Image 2',
      footer: 'ðŸ·ï¸ Pinterest',
      offerText: 'ðŸ·ï¸ New Coupon!',
      offerCode: '@nozez-lab/baileys',
      offerUrl: 'https://www.npmjs.com/package/@nozez-lab/baileys',
      offerExpiration: Date.now() + 3_600_000,
      nativeFlow: [{
         text: 'ðŸŒ Source',
         url: 'https://www.npmjs.com/package/@nozez-lab/baileys'
      }]
   }, {
      image: {
         url: './path/to/image.jpg'
      },
      caption: 'ðŸ–¼ï¸ Image 3',
      footer: 'ðŸ·ï¸ Pinterest',
      optionText: 'ðŸ‘‰ðŸ» Select Options',
      optionTitle: 'ðŸ‘‰ðŸ» Select Options',
      offerText: 'ðŸ·ï¸ New Coupon!',
      offerCode: '@nozez-lab/baileys',
      offerUrl: 'https://www.npmjs.com/package/@nozez-lab/baileys',
      offerExpiration: Date.now() + 3_600_000,
      nativeFlow: [{
         text: 'ðŸ›’ Product',
         id: '#Product',
         icon: 'default'
      }, {
         text: 'ðŸŒ Source',
         url: 'https://www.npmjs.com/package/@nozez-lab/baileys'
      }]
   }]
}, {
   quoted: message
})

// --- Native Flow with Audio in the Footer
sock.sendMessage(jid, {
   text: 'ðŸ”ˆ Music in the footer!',
   audioFooter: {
      url: './path/to/audio.mp3'
   }, // --- Like other media upload methods, buffers and streams are supported
   nativeFlow: [{
      text: 'ðŸ‘ðŸ» Good, next',
      id: '#Next',
      icon: 'review'
   }, {
      text: 'ðŸ‘ŽðŸ» Skip',
      id: '#Skip',
      icon: 'default'
   }]
}, {
   quoted: message
})
```

#### ðŸ«™ Hydrated Template

```javascript
sock.sendMessage(jid, {
   title: 'ðŸ‘‹ðŸ» Hello',
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ«™ Template!',
   footer: '@nozez-lab/baileys',
   templateButtons: [{
      text: 'ðŸ‘‰?? Tap Here',
      id: '#Order'
   }, {
      text: 'ðŸŒ Source',
      url: 'https://www.npmjs.com/package/@nozez-lab/baileys'
   }, {
      text: 'ðŸ“ž Call',
      call: '628123456789'
   }]
}, {
   quoted: message
})
```

### ðŸ’³ Sending Payment Messages

#### âž• Invite Payment

```javascript
sock.sendMessage(jid, {
   paymentInviteServiceType: 3 // 1, 2, or 3
})
```

#### ðŸ§¾ Invoice

> [!NOTE]
> Invoice message are not supported yet.

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   invoiceNote: 'ðŸ·ï¸ Invoice'
})
```

#### ðŸ›ï¸ Order

```javascript
sock.sendMessage(chat, {
   orderText: 'ðŸ›ï¸ Order',
   thumbnail: fs.readFileSync('./path/to/image.jpg') // --- Must in buffer format
}, {
   quoted: message
})
```

#### ðŸ’³ Request Payment

```javascript
sock.sendMessage(jid, {
   text: 'ðŸ’³ Request Payment',
   requestPaymentFrom: '0@s.whatsapp.net'
})
```

### ðŸ‘ï¸ Other Message Options

#### ðŸ¤– AI Icon

> [!NOTE]
> It only works in private chat (`@s.whatsapp.net`).

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ¤– With AI icon!',
   ai: true
}, {
   quoted: message
})
```

#### ðŸ•’ Ephemeral

> [!NOTE]
> Wrap message into `ephemeralMessage`

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ‘ï¸ Ephemeral',
   ephemeral: true
})
```

#### ðŸ“° External Ad Reply

> [!NOTE]
> Add an ad thumbnail to messages (may not be displayed on some WhatsApp versions).

```javascript
sock.sendMessage(jid, {
   text: 'ðŸ“° External Ad Reply',
   externalAdReply: {
      title: 'ðŸ“ Did you know?',
      body: 'â“ I dont know',
      thumbnail: fs.readFileSync('./path/to/image.jpg'), // --- Must in buffer format
      largeThumbnail: false, // --- Or true for bigger thumbnail
      url: 'https://www.npmjs.com/package/@nozez-lab/baileys' // --- Optional, used for WhatsApp internal thumbnail caching and direct URL
   }
}, {
   quoted: message
})
```

#### ðŸ§‘â€ðŸ§‘â€ðŸ§’ Group Status

> [!NOTE]
> It only works in group chat (`@g.us`)

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ‘¥ Group Status!',
   groupStatus: true
})
```

#### ðŸ± Lottie Sticker

> [!NOTE]
> Wrap message into `lottieStickerMessage`

```javascript
sock.sendMessage(jid, {
   sticker: {
      url: './path/to/sticker.webp'
   },
   isLottie: true
})
```

#### ðŸ§© Raw

```javascript
sock.sendMessage(jid, {
   extendedTextMessage: {
      text: 'ðŸ“ƒ Built manually from scratch using the raw WhatsApp proto structure',
      contextInfo: {
         externalAdReply: {
            title: '@nozez-lab/baileys',
            thumbnail: fs.readFileSync('./path/to/image.jpg'),
            sourceApp: 'whatsapp',
            showAdAttribution: true,
            mediaType: 1
         }
      }
   },
   raw: true
}, {
   quoted: message
})
```

#### ðŸ·ï¸ Secure Meta Service Label

```javascript
sock.sendMessage(jid, {
   text: 'ðŸ·ï¸ Just a label!',
   secureMetaServiceLabel: true
})
```

#### ðŸ“‘ Spoiler

> [!NOTE]
> Wrap message into `spoilerMessage`

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'â” Spoiler',
   spoiler: true
})
```

#### ðŸ‘ï¸ View Once

> [!NOTE]
> Wrap message into `viewOnceMessage`

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ‘ï¸ View Once',
   viewOnce: true
})
```

#### ðŸ‘ï¸ View Once V2

> [!NOTE]
> Wrap message into `viewOnceMessageV2`

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ‘ï¸ View Once V2',
   viewOnceV2: true
})
```

#### ðŸ‘ï¸ View Once V2 Extension

> [!NOTE]
> Wrap message into `viewOnceMessageV2Extension`

```javascript
sock.sendMessage(jid, {
   image: {
      url: './path/to/image.jpg'
   },
   caption: 'ðŸ‘ï¸ View Once V2 Extension',
   viewOnceV2Extension: true
})
```

### â™»ï¸ Modify Messages

#### ðŸ—‘ï¸ Delete Messages

```javascript
sock.sendMessage(jid, {
   delete: message.key
})
```

#### âœï¸ Edit Messages

```javascript
// --- Edit plain text
sock.sendMessage(jid, {
   text: 'âœ¨ I mean, nice!',
   edit: message.key
})

// --- Edit media messages caption
sock.sendMessage(jid, {
   caption: 'âœ¨ I mean, here is the image!',
   edit: message.key
})
```

### ðŸ§° Additional Contents

#### ðŸ·ï¸ Find User ID (JID|PN/LID)

> [!NOTE]
> The ID must contain numbers only (no +, (), or -) and must include the country code with WhatsApp ID format.

```javascript
// --- PN (Phone Number)
const phoneNumber = '6281111111111@s.whatsapp.net'

const ids = await sock.findUserId(phoneNumber)

console.log('ðŸ·ï¸ Got user ID', ':', ids)

// --- LID (Local Identifier)
const lid = '43411111111111@lid'

const ids = await sock.findUserId(lid)

console.log('ðŸ·ï¸ Got user ID', ':', ids)

// --- Output
// {
//    phoneNumber: '6281111111111@s.whatsapp.net',
//    lid: '43411111111111@lid'
// }
// --- Output when failed
// {
//    phoneNumber: '6281111111111@s.whatsapp.net',
//    lid: undefined
// }
// --- Same output shape regardless of input type
```

#### ðŸ”‘ Request Custom Pairing Code

> [!NOTE]
> The phone number must contain numbers only (no +, (), or -) and must include the country code.

```javascript
const phoneNumber = '6281111111111'
const customPairingCode = 'STARFALL'

await sock.requestPairingCode(phoneNumber, customPairingCode)

console.log('ðŸ”— Pairing code', ':', customPairingCode)
```

#### ðŸ–¼ï¸ Image Processing

> [!NOTE]
> Automatically use available image processing library: `sharp`, `@napi-rs/image`, or `jimp`

```javascript
import { getImageProcessingLibrary } from '@nozez-lab/baileys'
import { readFile } from 'fs/promises'

const lib = await getImageProcessingLibrary()

const bufferOrFilePath = './path/to/image.jpg'
const width = 512

let output

// --- If sharp installed
if (lib.sharp?.default) {
   const img = lib.sharp.default(bufferOrFilePath)

   output = await img.resize(width)
      .jpeg({ quality: 80 })
      .toBuffer()
}

// --- If @napi-rs/image installed
else if (lib.image?.Transformer) {
   // --- Must in buffer format
   const inputBuffer = Buffer.isBuffer(bufferOrFilePath)
      ? bufferOrFilePath
      : await readFile(bufferOrFilePath)

   const img = new lib.image.Transformer(inputBuffer)

   output = await img.resize(width, undefined, 0)
      .jpeg(50)
}

// --- If jimp installed
else if (lib.jimp?.Jimp) {
   const img = await lib.jimp.Jimp.read(bufferOrFilePath)

   output = await img
      .resize({ w: width, mode: lib.jimp.ResizeStrategy.BILINEAR })
      .getBuffer('image/jpeg', { quality: 50 })
}

// --- Fallback
else {
   throw new Error('No image processing available')
}

console.log('âœ… Process completed!')
console.dir(output, { depth: null })
```

#### ðŸ“£ Newsletter Management

```javascript
// --- Create a new one
sock.newsletterCreate('@nozez-lab/baileys', 'ðŸ“£ Fresh updates weekly')

// --- Get info
const metadata = sock.newsletterMetadata('1231111111111@newsletter')
console.dir(metadata, { depth: null })

// --- Get subscribers count
const subscribers = await sock.newsletterSubscribers('1231111111111@newsletter')
console.dir(subscribers, { depth: null })

// --- Follow and Unfollow
sock.newsletterFollow('1231111111111@newsletter')
sock.newsletterUnfollow('1231111111111@newsletter')

// --- Mute and Unmute
sock.newsletterMute('1231111111111@newsletter')
sock.newsletterUnmute('1231111111111@newsletter')

// --- Demote admin
sock.newsletterDemote('1231111111111@newsletter', '6281111111111@s.whatsapp.net')

// --- Change owner
sock.newsletterChangeOwner('1231111111111@newsletter', '6281111111111@s.whatsapp.net')

// --- Update newsletter
sock.newsletterUpdate('1231111111111@newsletter', { name: '@nozez-lab/baileys' })

// --- Change name
sock.newsletterUpdateName('1231111111111@newsletter', 'ðŸ“¦ @nozez-lab/baileys')

// --- Change description
sock.newsletterUpdateDescription('1231111111111@newsletter', 'ðŸ“£ Fresh updates weekly')

// --- Change photo
sock.newsletterUpdatePicture('1231111111111@newsletter', {
   url: 'path/to/image.jpg'
})

// --- Remove photo
sock.newsletterRemovePicture('1231111111111@newsletter')

// --- React to a message
sock.newsletterReactMessage('1231111111111@newsletter', '100', 'ðŸ’›')

// --- Get admin count
const count = await sock.newsletterAdminCount('1231111111111@newsletter')

// --- Get all subscribed newsletters
const newsletters = await sock.newsletterSubscribed()
console.dir(newsletters, { depth: null })

// --- Fetch newsletter messages
const messages = sock.newsletterFetchMessages('jid', '1231111111111@newsletter', 50, 0, 0)
console.dir(messages, { depth: null })

// --- Delete newsletter
sock.newsletterDelete('1231111111111@newsletter')
```

#### ðŸ‘¥ Group Management

```javascript
// --- Create a new one and add participants using their JIDs
const group = sock.groupCreate('@nozez-lab/baileys', ['628123456789@s.whatsapp.net'])
console.dir(group, { depth: null })

// --- Get info
const metadata = await sock.groupMetadata(jid)
console.dir(metadata, { depth: null })

// --- Get group invite code
const inviteCode = await sock.groupInviteCode(jid)
console.dir(inviteCode, { depth: null })


// --- Revoke invite link
sock.groupRevokeInvite(jid)

// --- Accept group invite
sock.groupAcceptInvite(inviteCode)

// --- Leave group
sock.groupLeave(jid)

// --- Add participants
sock.groupParticipantsUpdate(jid, ['628123456789@s.whatsapp.net'], 'add')

// --- Remove participants
sock.groupParticipantsUpdate(jid, ['628123456789@s.whatsapp.net'], 'remove')

// --- Promote to admin
sock.groupParticipantsUpdate(jid, ['628123456789@s.whatsapp.net'], 'promote')

// --- Demote from admin
sock.groupParticipantsUpdate(jid, ['628123456789@s.whatsapp.net'], 'demote')

// --- Accept join requests
sock.groupRequestParticipantsUpdate(jid, ['628123456789@s.whatsapp.net'], 'approve')

// --- Change name
sock.groupUpdateSubject(jid, 'ðŸ“¦ @nozez-lab/baileys')

// --- Change description
sock.groupUpdateDescription(jid, 'Updated description')

// --- Change photo
sock.updateProfilePicture(jid, {
   url: 'path/to/image.jpg'
})

// --- Remove photo
sock.removeProfilePicture(jid)

// --- Set group as admin only for chatting
sock.groupSettingUpdate(jid, 'announcement')

// --- Set group as open to all for chatting
sock.groupSettingUpdate(jid, 'not_announcement')

// --- Set admin only can edit group info
sock.groupSettingUpdate(jid, 'locked')

// --- Set all participants can edit group info
sock.groupSettingUpdate(jid, 'unlocked')

// --- Set admin only can add participants
sock.groupMemberAddMode(jid, 'admin_add')

// --- Set all participants can add participants
sock.groupMemberAddMode(jid, 'all_member_add')

// --- Enable or disable temporary messages with seconds format
sock.groupToggleEphemeral(jid, 86400)

// --- Disable temporary messages
sock.groupToggleEphemeral(jid, 0)

// --- Enable or disable membership approval mode
sock.groupJoinApprovalMode(jid, 'on')
sock.groupJoinApprovalMode(jid, 'off')

// --- Get all groups metadata
const groups = await sock.groupFetchAllParticipating()
console.dir(groups, { depth: null })

// --- Get pending join requests
const requests = await sock.groupRequestParticipantsList(jid)
console.dir(requests, { depth: null })

// --- Get group info from link
const group = await sock.groupGetInviteInfo('ABC123456789')
console.log('ðŸ‘¥ Got group info from invite code', ':', group)

// --- Update bot member label
sock.updateMemberLabel(jid, '@nozez-lab/baileys')
```

#### ðŸ‘¥ Community Management

```javascript
// --- Create a new one and add description
const community = await sock.communityCreate('@nozez-lab/baileys', 'ðŸ“£ Fresh updates weekly')
console.dir(community, { depth: null })

// --- Create a subgroup for community and add participants using their JIDs
const group = await sock.communityCreateGroup('ðŸ“¢ Announcements', ['628123456789@s.whatsapp.net'], communityJid)

// --- Link an existing group
sock.communityLinkGroup(groupJid, communityJid)

// --- Unlink an existing group
sock.communityUnlinkGroup(groupJid, communityJid)

// --- Get info
const metadata = await sock.communityMetadata(jid)
console.dir(metadata, { depth: null })

// --- Get community invite code
const inviteCode = await sock.communityInviteCode(jid)
console.dir(inviteCode, { depth: null })

// --- Revoke invite link
sock.communityRevokeInvite(jid)

// --- Accept community invite
sock.communityAcceptInvite(inviteCode)

// --- Leave community
sock.communityLeave(jid)

// --- Accept join requests
sock.communityRequestParticipantsUpdate(jid, ['628123456789@s.whatsapp.net'], 'approve')

// --- Change name
sock.communityUpdateSubject(jid, 'ðŸ“¦ @nozez-lab/baileys')

// --- Change description
sock.communityUpdateDescription(jid, 'Updated description')

// --- Set community as admin only for chatting
sock.communitySettingUpdate(jid, 'announcement')

// --- Set community as open to all for chatting
sock.communitySettingUpdate(jid, 'not_announcement')

// --- Set admin only can edit community info
sock.communitySettingUpdate(jid, 'locked')

// --- Set all participants can edit community info
sock.communitySettingUpdate(jid, 'unlocked')

// --- Set admin only can add participants
sock.communityMemberAddMode(jid, 'admin_add')

// --- Set all participants can add participants
sock.communityMemberAddMode(jid, 'all_member_add')

// --- Enable or disable temporary messages with seconds format
sock.communityToggleEphemeral(jid, 86400)

// --- Disable temporary messages
sock.communityToggleEphemeral(jid, 0)

// --- Enable or disable membership approval mode
sock.communityJoinApprovalMode(jid, 'on')
sock.communityJoinApprovalMode(jid, 'off')

// --- Get all communities metadata
const communities = await sock.communityFetchAllParticipating()
console.dir(communities, { depth: null })

// --- Get all community linked groups
const linked = await sock.communityFetchLinkedGroups(jid)
console.dir(linked, { depth: null })

// --- Get pending join requests
const requests = await sock.communityRequestParticipantsList(jid)
console.dir(requests, { depth: null })

// --- Get community info from link
const community = await sock.communityGetInviteInfo('ABC123456789')
console.log('ðŸ‘¥ Got community info from invite code', ':', community)
```

#### ðŸ‘¤ Profile Management

```javascript
// --- Get user profile picture
const url = await sock.profilePictureUrl(jid, 'image')
console.log('ðŸ–¼ï¸ Got user profile url', url)

// --- Update profile picture
sock.updateProfilePicture(jid, buffer)
sock.updateProfilePicture(jid, { url })

// --- Remove profile picture
sock.removeProfilePicture(jid)

// --- Update profile name
sock.updateProfileName('My Name')

// --- Update profile status
sock.updateProfileStatus('Available')

// --- Presence
sock.sendPresenceUpdate('available', jid)
sock.presenceSubscribe(jid)

// --- Read receipts
sock.readMessages([message.key])
sock.sendReceipt(jid, participant, [messageId], 'read')

// --- Block user
sock.updateBlockStatus(jid, 'block')

// --- Unblock user
sock.updateBlockStatus(jid, 'unblock')

// --- Fetch blocklist
const blocked = await sock.fetchBlocklist()
console.dir(blocked, { depth: null })

// --- Modify chats
sock.chatModify({
   archive: true,
   lastMessageOrig: message,
   lastMessage: message
}, jid)

// --- Star messages
sock.star(jid, [{ id: messageId, fromMe: true }], true)

// --- Contact
sock.addOrEditContact(jid, { displayName: 'Starseed' })
sock.removeContact(jid)

// --- Label
sock.addChatLabel(jid, labelId)
sock.removeChatLabel(jid, labelId)
sock.addMessageLabel(jid, messageId, labelId)

// --- App state sync
sock.resyncAppState(['regular', 'critical_block'], true)

// --- Get business profile
const profile = await sock.getBusinessProfile(jid)
console.dir(profile, { depth: null })
```

#### ðŸ›’ Business Management

```javascript
// --- Create a new product
const product = await sock.productCreate({
   name: 'ðŸ§© Starseed (Premium)',
   description: 'Get a full version of Starseed!',
   price: 100000,
   currency: 'IDR',
   originCountryCode: 'ID',
   images: [
      bufferImage,
      {
         url: './path/to/image.jpg'
      }
   ]
})
console.dir(product, { depth: null })

// --- Update product
await sock.productUpdate(productId, {
   name: 'ðŸ§© Starseed (Premium)',
   description: 'Get a full version of Starseed with more features!',
   price: 75000,
   currency: 'IDR',
   images: [
      {
         url: './path/to/image.jpg'
      }
   ]
})

// --- Delete product
sock.productDelete([productId])

// --- Get catalog info
const { products, nextPageCursor } = await sock.getCatalog({
  jid: '628123456789@s.whatsapp.net',
  limit: 10
})

// --- Get collections
const collections = await sock.getCollections('628123456789@s.whatsapp.net', 10)
console.dir(collections, { depth: null })

// --- Get order info
const order = await sock.getOrderDetails(orderId, tokenBase64)
console.dir(order, { depth: null })

// --- Update business profile
await sock.updateBusinessProfile({
   address: 'Jakarta, Indonesia',
   description: 'ðŸ›’ Official Starseed Store',
   websites: ['https://www.npmjs.com/package/@nozez-lab/baileys'],
   email: 'more-more@gmail.com',
   hours: {
      timezone: 'Asia/Jakarta',
      days: [{ day: 'mon', mode: 'open_24h' }]
   }
})

// --- Update cover
sock.updateCoverPhoto({
   url: './path/to/image.jpg'
})

// --- Remove cover
sock.removeCoverPhoto(coverId)

// --- Update quick replies
sock.addOrEditQuickReply({
  shortcut: 'hello',
  message: 'Hello from business account',
})

// --- Remove quick reply
sock.removeQuickReply(timestamp)
```

#### ðŸ” Privacy Management

```javascript
// --- Update last seen privacy
sock.updateLastSeenPrivacy('all')
sock.updateLastSeenPrivacy('contacts')
sock.updateLastSeenPrivacy('contact_blacklist')
sock.updateLastSeenPrivacy('nobody')

// --- Update online privacy
sock.updateOnlinePrivacy('all')
sock.updateOnlinePrivacy('match_last_seen')

// --- Update profile picture privacy
sock.updateProfilePicturePrivacy('contacts')

// --- Update status privacy
sock.updateStatusPrivacy('contacts')

// --- Update read receipts privacy
sock.updateReadReceiptsPrivacy('all')
sock.updateReadReceiptsPrivacy('none')

// --- Update groups add privacy
sock.updateGroupsAddPrivacy('all')
sock.updateGroupsAddPrivacy('contacts')

// --- Update messages privacy
sock.updateMessagesPrivacy('all')
sock.updateMessagesPrivacy('contacts')
sock.updateMessagesPrivacy('nobody')

// --- Update call privacy
sock.updateCallPrivacy('everyone')

// --- Update default disappearing mode
sock.updateDefaultDisappearingMode(86400)

// --- Update link previews privacy
sock.updateDisableLinkPreviewsPrivacy(true)
```

#### ðŸ“¡ Events

```javascript
sock.ev.on('connection.update', (update) => {})
sock.ev.on('creds.update', (update) => {})
sock.ev.on('messaging-history.set', (update) => {})
sock.ev.on('messaging-history.status', (update) => {})
sock.ev.on('chats.upsert', (update) => {})
sock.ev.on('chats.update', (update) => {})
sock.ev.on('chats.delete', (update) => {})
sock.ev.on('chats.lock', (update) => {})
sock.ev.on('lid-mapping.update', (update) => {})
sock.ev.on('presence.update', (update) => {})
sock.ev.on('contacts.upsert', (update) => {})
sock.ev.on('contacts.update', (update) => {})
sock.ev.on('messages.delete', (update) => {})
sock.ev.on('messages.update', (update) => {})
sock.ev.on('messages.media-update', (update) => {})
sock.ev.on('messages.upsert', (update) => {})
sock.ev.on('messages.reaction', (update) => {})
sock.ev.on('message-receipt.update', (update) => {})
sock.ev.on('groups.upsert', (update) => {})
sock.ev.on('groups.update', (update) => {})
sock.ev.on('group-participants.update', (update) => {})
sock.ev.on('group.join-request', (update) => {})
sock.ev.on('group.member-tag.update', (update) => {})
sock.ev.on('blocklist.set', (update) => {})
sock.ev.on('blocklist.update', (update) => {})
sock.ev.on('call', (update) => {})
sock.ev.on('labels.edit', (update) => {})
sock.ev.on('labels.association', (update) => {})
sock.ev.on('newsletter.reaction', (update) => {})
sock.ev.on('newsletter.view', (update) => {})
sock.ev.on('newsletter-participants.update', (update) => {})
sock.ev.on('newsletter-settings.update', (update) => {})
sock.ev.on('settings.update', (update) => {})
```

### ðŸš€ Try the Bot

A fast, lightweight, and modular WhatsApp bot built with [@nozez-lab/baileys](https://www.npmjs.com/package/@nozez-lab/baileys).
Perfect for managing groups, moderating chats, and adding fun with quiz games and handy tools.

ðŸ‘‰ðŸ» [@nozez-lab/starseed](https://github.com/nozez-lab/starseed#readme)

### ðŸ“¦ Fork Base

This fork is based on [Baileys (GitHub)](https://github.com/WhiskeySockets/Baileys)

### ðŸ“£ Credits

This fork uses Protocol Buffer definitions maintained by [WPP Connect](https://github.com/wppconnect-team) via [`wa-proto`](https://github.com/wppconnect-team/wa-proto)

Full credit is attributed to the original maintainers and contributors of Baileys:
- [purpshell](https://github.com/purpshell)
- [jlucaso1](https://github.com/jlucaso1)
- [adiwajshing](https://github.com/adiwajshing)

<!-- Please do not replace my name with yours. It's disrespectful. -->

This fork includes additional enhancements and modifications by [Nozez](https://github.com/nozez-lab)

Special thanks to [itsreimau](https://github.com/itsreimau) for the fix to the `updateBlockStatus` implementation.

> [!CAUTION]
> âš ï¸ **Modification, removal, or misrepresentation of these credits is strictly prohibited. Any redistribution or fork must preserve this section in its original form without exception.**
