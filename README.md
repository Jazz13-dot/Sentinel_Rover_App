# 🛡️ SENTINEL ROVER DEFENSE SYSTEM

A cutting-edge AI-powered laser sentinel rover system with real-time threat detection, automated alert dispatching, and tactical mobile interface.

## 📱 Features:

### Mobile App (Flutter)
- **Real-time Dashboard**: Live monitoring of rover status and threats
- **Interactive Threat Map**: Visual representation of detected drones with severity indicators
- **Instant Alerts**: Push notifications for critical threats
- **System Analytics**: Performance metrics, battery status, and laser availability
- **Tactical UI**: Military-grade dark theme with cybersecurity aesthetics
- **WebSocket Integration**: Real-time bidirectional communication

### Backend API (Node.js)
- **REST API**: Comprehensive endpoints for rover control and threat management
- **WebSocket Server**: Real-time updates via Socket.IO
- **Auto-Alert System**: Automatic dispatch to police, fire, and medical services
- **Threat Tracking**: Complete history and analytics of detected threats
- **Simulation Mode**: Built-in demo mode for testing

## 🚀 Quick Start

### Backend Setup

1. **Navigate to backend directory**
```bash
cd backend
```

2. **Install dependencies**
```bash
npm install
```

3. **Configure environment**
```bash
cp .env.template .env
# Edit .env with your configuration
```

4. **Start the server**
```bash
# Development mode
npm run dev

# Production mode
npm start
```

Server will start on `http://localhost:3000`

### Flutter App Setup

1. **Navigate to project root**
```bash
cd sentinel-rover-app
```

2. **Install dependencies**
```bash
flutter pub get
```

3. **Update backend URL**
Edit `lib/services/websocket_service.dart`:
```dart
socket = IO.io(
  'http://YOUR_BACKEND_IP:3000',  // Update this
  // ...
);
```

4. **Run the app**
```bash
# iOS
flutter run -d ios

# Android
flutter run -d android

# Web (for testing)
flutter run -d chrome
```

## 📡 API Documentation

### REST Endpoints

#### Health Check
```http
GET /api/health
```

#### Rover Status
```http
GET  /api/rover/status
POST /api/rover/status
```

**Example Request:**
```json
{
  "battery": 85,
  "laser_status": "READY",
  "latitude": 13.0827,
  "longitude": 80.2707
}
```

#### Threats
```http
GET  /api/threats
POST /api/threats
POST /api/threats/:id/neutralize
```

**Report Threat:**
```json
{
  "severity": "critical",
  "latitude": 13.0830,
  "longitude": 80.2710,
  "distance": 250.5
}
```

#### Alerts
```http
GET  /api/alerts
POST /api/alerts/dispatch
```

**Dispatch Alert:**
```json
{
  "type": "emergency",
  "location": {
    "latitude": 13.0827,
    "longitude": 80.2707
  },
  "message": "Hostile drone detected"
}
```

### WebSocket Events

#### Client → Server
- `fire_laser`: Command rover to engage laser

#### Server → Client
- `rover_status`: Real-time rover status updates
- `threat_detected`: New threat detected
- `threat_neutralized`: Threat eliminated
- `laser_result`: Result of laser engagement

**Example Usage:**
```javascript
socket.emit('fire_laser', {
  target_id: 'threat-123',
  coordinates: { lat: 13.0830, lng: 80.2710 }
});

socket.on('threat_detected', (threat) => {
  console.log('New threat:', threat);
});
```

## 🎨 UI Screenshots Preview

### Login Screen
- Biometric-style authentication
- Tactical fingerprint scanner animation
- Restricted access warnings

### Dashboard
- Live threat level indicator
- Real-time rover status card
- System performance metrics
- Recent detections feed

### Threat Map
- Interactive grid-based map
- Rover position (center)
- Threat markers with severity colors
- Real-time coordinate tracking

### Settings
- Toggle laser system
- Auto-alert configuration
- Sound alerts
- System preferences

## 🔧 Customization

### Color Scheme
Edit theme in `lib/main.dart`:
```dart
primaryColor: const Color(0xFFFF3366),  // Threat Red
secondary: const Color(0xFF00F5FF),     // Cyber Blue
```

### Fonts
Current fonts:
- **Headers**: Orbitron (tactical/military)
- **Body**: Inter (clean/readable)

To change, edit in `lib/main.dart`:
```dart
GoogleFonts.yourFont(...)
```

### Alert Services
Configure in `backend/server.js`:
```javascript
async function alertPolice(threat) {
  // Add your police API integration
}

async function alertFire(threat) {
  // Add your fire department API
}

async function alertMedical(threat) {
  // Add your medical services API
}
```

## 🔐 Security Considerations

### Production Deployment

1. **Enable Authentication**
   - Implement JWT tokens
   - Add API key validation
   - Secure WebSocket connections

2. **HTTPS/WSS**
   - Use SSL certificates
   - Encrypt all communications
   - Secure environment variables

3. **Rate Limiting**
   - Add express-rate-limit
   - Prevent API abuse
   - Monitor suspicious activity

4. **Database**
   - Replace in-memory storage with MongoDB/PostgreSQL
   - Implement proper data persistence
   - Regular backups

### Legal Compliance

⚠️ **IMPORTANT**: This system involves:
- Laser weapon technology (heavily regulated)
- Emergency service integration (requires authorization)
- Aviation safety concerns (FAA/CAA compliance)
- Privacy and surveillance laws

**Before deployment:**
- Consult with legal experts
- Obtain necessary permits and licenses
- Ensure compliance with local laws
- Implement proper safety protocols

## 📊 System Requirements

### Backend
- Node.js 16+ 
- npm/yarn
- 512MB RAM minimum
- 1GB storage

### Flutter App
- Flutter 3.0+
- Dart 3.0+
- iOS 12+ / Android 6.0+
- 100MB storage

### Rover Hardware (Reference)
- Jetson AGX Orin or equivalent
- High-precision gimbal system
- Laser system (Class 4)
- GPS/IMU module
- 4G/5G modem
- Battery system

## 🧪 Testing

### Backend Tests
```bash
cd backend
npm test  # Add test scripts
```

### Flutter Tests
```bash
flutter test
```

### Integration Testing
1. Start backend server
2. Run Flutter app
3. Verify WebSocket connection
4. Test threat detection flow
5. Check alert dispatching

## 🤝 Contributing

This is a reference implementation. For production use:
1. Implement proper authentication
2. Add comprehensive error handling
3. Create unit and integration tests
4. Add logging and monitoring
5. Implement CI/CD pipeline

## 📝 License

This is a demonstration/educational project. Actual deployment requires:
- Proper licensing for laser technology
- Authorization from emergency services
- Compliance with aviation regulations
- Liability insurance

## ⚠️ Disclaimer

This software is provided for **educational and demonstration purposes only**. The authors are not responsible for:
- Unauthorized use of laser technology
- Improper integration with emergency services
- Violations of aviation safety regulations
- Any damages or injuries resulting from use

Always consult with legal and safety experts before deploying defense systems.

## 📧 Support

For questions about this implementation:
- Review the code documentation
- Check API endpoint examples
- Test with simulation mode first

## 🎯 Roadmap

- [ ] Add user authentication system
- [ ] Implement database persistence
- [ ] Add video streaming from rover
- [ ] Create admin dashboard
- [ ] Add AI model training interface
- [ ] Implement multi-rover support
- [ ] Add historical analytics
- [ ] Create detailed reports/logs

---

**Built with**: Flutter, Node.js, Socket.IO, Express
**Status**: Demo/Educational Implementation
**Version**: 1.0.0
