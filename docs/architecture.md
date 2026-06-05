# Architecture

## Overview

```text
┌─────────────────┐      ┌─────────────────┐
│   Mobile App    │      │  Web Dashboard  │
│  React Native   │      │     Next.js     │
└────────┬────────┘      └────────┬────────┘
         │                        │
         └──────────┬─────────────┘
                    │
                    ▼
          ┌─────────────────┐
          │    REST API     │
          │ Node.js Express │
          └────────┬────────┘
                   │
      ┌────────────┴────────────┐
      ▼                         ▼
┌─────────────┐          ┌─────────────┐
│ PostgreSQL  │          │    Redis    │
│  Database   │          │ Cache/Queue │
└─────────────┘          └─────────────┘

                   │
                   ▼
          ┌─────────────────┐
          │       FCM       │
          │ Push Notification│
          └─────────────────┘
```

## High Level Architecture

```text
┌────────────────────┐
│      Donor         │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│  Mobile App (RN)   │
└─────────┬──────────┘
          │ HTTPS
          ▼
┌────────────────────┐
│   REST API Server  │
│   Express + TS     │
└──────┬───────┬─────┘
       │       │
       │       │
       ▼       ▼
┌──────────┐ ┌──────────┐
│PostgreSQL│ │  Redis   │
└──────────┘ └──────────┘
       │
       ▼
┌────────────────────┐
│ Firebase Cloud Msg │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Push Notification  │
└────────────────────┘


┌────────────────────┐
│   PMI / Hospital   │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│  Web Dashboard     │
│      Next.js       │
└────────────────────┘
```

## Request Flow

```text
Hospital / Family
       │
       ▼
Create Blood Request
       │
       ▼
Backend Verification
       │
       ▼
Urgent Request Published
       │
       ▼
Matching Donors Found
       │
       ▼
Push Notification Sent
       │
       ▼
Donor Accepts Request
       │
       ▼
Donation Completed
       │
       ▼
Request Closed
```

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Mobile | React Native + TypeScript |
| Web Dashboard | Next.js + TypeScript |
| Backend API | Node.js + Express + TypeScript |
| Database | PostgreSQL |
| Cache / Queue | Redis |
| Authentication | JWT + Refresh Token |
| Push Notification | Firebase Cloud Messaging (FCM) |
| File Storage | Cloudinary |
| Containerization | Docker + Docker Compose |

## Repository Structure

| Repository | Description |
|------------|-------------|
| teman-donor | Main hub — docs, contributing guidelines |
| teman-donor-api | Backend REST API |
| teman-donor-mobile | React Native mobile app |
| teman-donor-web | Next.js web dashboard + landing page |

## API Design
- RESTful API
- Versioned endpoints: `/api/v1/...`
- JWT authentication on protected routes
- Standardized response format:

```json
{
  "success": true,
  "data": {},
  "message": "string",
  "error": null
}
```

## Notification Flow
1. Admin PMI posts urgent blood request
2. Backend queries matching donors (blood type + location)
3. FCM sends push notification to matched donors
4. Donor accepts → status updated → patient notified