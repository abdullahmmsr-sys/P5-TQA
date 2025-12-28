# Event Ticket Management System

A comprehensive event ticketing system with facial recognition for secure entry verification.

## System Architecture

### Components
1. **Flutter Mobile App** - User-facing application for browsing events, purchasing tickets, and face enrollment
2. **Supabase Backend** - Database, authentication, and storage
3. **Face Recognition API** - Python FastAPI service for face detection and verification
4. **Gate Verification App** - Camera-based verification at event entrance

## Features

### User Features
- User authentication (email/password)
- Browse available events
- Purchase event tickets
- Face enrollment before ticket purchase
- View purchased tickets
- QR code generation for backup entry

### Gate/Admin Features
- Real-time face verification using camera
- Manual ticket validation via QR code
- Entry logging and analytics
- Multi-face quality checks (blur, lighting, angle)

## Technology Stack

- **Frontend**: Flutter (iOS & Android)
- **Backend**: Supabase (PostgreSQL, Auth, Storage)
- **Face Recognition**: Python FastAPI + InsightFace
- **Real-time**: Supabase Realtime subscriptions
- **Storage**: Supabase Storage for face templates

## Database Schema

### Tables
1. **users** (managed by Supabase Auth)
2. **events** - Event information
3. **tickets** - User tickets
4. **face_templates** - Encrypted face embeddings
5. **entry_logs** - Gate entry records






## Project Structure

```
event_ticket_app/
├── flutter_app/           # Flutter mobile application
│   ├── lib/
│   │   ├── main.dart
│   │   ├── models/
│   │   ├── screens/
│   │   ├── services/
│   │   └── widgets/
│   └── pubspec.yaml
├── face_recognition_api/  # Python FastAPI service
│   ├── main.py
│   ├── face_utils.py
│   ├── requirements.txt
│   └── models/
├── docs/                  # Documentation
│   ├── database_schema.sql
│   ├── api_documentation.md
│   └── deployment.md
└── README.md
```

## Security Considerations

1. Face templates are stored encrypted
2. API endpoints require authentication
3. Rate limiting on face verification
4. HTTPS only in production
5. Secure storage of face embeddings


