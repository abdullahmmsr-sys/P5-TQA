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
- Face enrollment after ticket purchase
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

## Setup Instructions

### Prerequisites
- Flutter SDK (3.0+)
- Python 3.9+
- Supabase account
- macOS/iOS development setup

### Installation

1. **Install Flutter**
```bash
# Install Flutter using homebrew
brew install --cask flutter

# Or download from https://docs.flutter.dev/get-started/install
```

2. **Set up Supabase**
- Create account at https://supabase.com
- Create new project
- Copy your project URL and anon key
- Run the SQL schema (see docs/database_schema.sql)

3. **Install Flutter dependencies**
```bash
cd flutter_app
flutter pub get
```

4. **Configure environment**
- Copy `.env.example` to `.env`
- Add your Supabase credentials

5. **Set up Face Recognition API**
```bash
cd face_recognition_api
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

6. **Run the apps**
```bash
# Terminal 1: Face Recognition API
cd face_recognition_api
python main.py

# Terminal 2: Flutter App
cd flutter_app
flutter run
```

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

## Development Notes

- This project is stored on external SSD at `/Volumes/external/event_ticket_app`
- Face recognition uses InsightFace with buffalo_l model
- Quality checks ensure good face captures (blur, brightness, angle)
- Supports multiple face templates per ticket for better accuracy

## License

MIT License
