# Requirements

## User Roles
| Role | Description |
|------|-------------|
| Guest | Unauthenticated user, limited access |
| Pendonor | Registered blood donor |
| Pasien / Keluarga | Patient or family requesting blood |
| Admin PMI / RS | Hospital or blood bank administrator |

## Features by Role

### Guest
- View public dashboard (news, events, blood stock)
- View donor statistics
- Register / Login

### Pendonor
- Register as donor (health form, blood type, identity verification)
- Receive QR/barcode after registration (PMI integration ready)
- Set availability status (ready / not available)
- Receive urgent notifications when matching blood type is needed
- Accept or ignore donation requests
- View donation history and impact (delivered to patient or not)
- View reminder — how many days until eligible to donate again
- Join community forum, chat with PMI/hospital admin

### Pasien / Keluarga
- Submit urgent blood request
- Track request status in real-time
- Receive notification when donor is confirmed
- View request history

### Admin PMI / RS
- Manage incoming blood requests (process, verify, update status)
- Publish announcements and events → auto-notify all users
- Manage and update blood stock per type
- View reports and charts (donor count, distribution, stock)
- Reply to forum questions and chat with users
- Export reports

## Non-Functional Requirements
- Real-time notifications (FCM)
- Secure authentication (JWT + refresh token)
- Data transparency — blood stock visible to all users
- PMI API integration ready
- Multi-language support (Bahasa Indonesia + English)
- Mobile-first (React Native), web dashboard (Next.js)