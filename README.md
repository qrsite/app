# QRsite - Seamless & Secure File Transfer via QR Codes

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](package.json)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/yourorg/qrsite)

QRsite is a modern web application that revolutionizes file sharing by generating QR codes for seamless and secure file transfers over the internet. Simply upload your files, generate a QR code, and share it with anyone for instant access.

## 🚀 Features

### Core Functionality
- **Instant QR Code Generation**: Upload files and generate QR codes in seconds
- **Secure File Transfer**: End-to-end encryption with AES-256 encryption
- **Multi-File Support**: Upload and share multiple files simultaneously
- **Cross-Platform Compatibility**: Works on any device with a camera and internet connection
- **Temporary Links**: Auto-expiring download links for enhanced security
- **No Registration Required**: Start sharing files immediately without account creation

### Advanced Features
- **Custom Expiration Times**: Set custom expiry periods (1 hour to 7 days)
- **Download Tracking**: Monitor download statistics and access logs
- **Password Protection**: Add optional password protection to sensitive files
- **Bulk Operations**: Generate multiple QR codes for batch file sharing
- **Mobile-First Design**: Optimized for smartphone scanning and sharing
- **Real-time Notifications**: Get notified when files are accessed

## 🛠 Technology Stack

### Frontend
- **Framework**: React 18+ with TypeScript
- **Styling**: Tailwind CSS with custom components
- **State Management**: Zustand for lightweight state management
- **QR Code Generation**: qrcode-generator library with custom styling
- **File Handling**: Web File API with drag-and-drop support
- **PWA Support**: Service workers for offline functionality

### Backend
- **Runtime**: Node.js 18+ with Express.js
- **Database**: PostgreSQL with Prisma ORM
- **File Storage**: AWS S3 with CloudFront CDN
- **Authentication**: JWT tokens with refresh token rotation
- **Encryption**: Node.js Crypto module (AES-256-GCM)
- **API Documentation**: OpenAPI 3.0 with Swagger UI

### Infrastructure
- **Container**: Docker with multi-stage builds
- **Orchestration**: Kubernetes with Helm charts
- **Monitoring**: Prometheus + Grafana stack
- **Logging**: Winston with structured JSON logging
- **CI/CD**: GitHub Actions with automated testing

## 📦 Installation

### Prerequisites
- Node.js 18+ and npm/yarn
- PostgreSQL 13+
- Redis 6+ (for session management)
- AWS S3 bucket (or compatible storage)

### Local Development Setup

```bash
# Clone the repository
git clone https://github.com/yourorg/qrsite.git
cd qrsite

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env

# Configure your environment variables
# Edit .env with your database, AWS, and other service credentials

# Run database migrations
npm run db:migrate

# Seed the database (optional)
npm run db:seed

# Start development servers concurrently
npm run dev
```

### Docker Setup

```bash
# Build and run with Docker Compose
docker-compose up --build

# Or run individual services
docker build -t qrsite .
docker run -p 3000:3000 qrsite
```

## 🔧 Configuration

### Environment Variables

```bash
# Application
NODE_ENV=development
PORT=3000
APP_URL=http://localhost:3000
JWT_SECRET=your-super-secret-jwt-key

# Database
DATABASE_URL=postgresql://username:password@localhost:5432/qrsite
REDIS_URL=redis://localhost:6379

# AWS S3
AWS_ACCESS_KEY_ID=your-access-key
AWS_SECRET_ACCESS_KEY=your-secret-key
AWS_REGION=us-east-1
AWS_S3_BUCKET=qrsite-files

# Security
ENCRYPTION_KEY=your-32-byte-encryption-key
MAX_FILE_SIZE=100MB
MAX_FILES_PER_UPLOAD=10

# Rate Limiting
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100
```

## 🏗 Project Structure

```
qrsite/
├── src/
│   ├── components/          # React components
│   │   ├── common/         # Reusable UI components
│   │   ├── qr/            # QR code related components
│   │   └── upload/        # File upload components
│   ├── pages/              # Next.js pages/routes
│   ├── hooks/              # Custom React hooks
│   ├── utils/              # Utility functions
│   ├── types/              # TypeScript type definitions
│   └── styles/             # Global styles and themes
├── server/
│   ├── controllers/        # Route controllers
│   ├── middleware/         # Express middleware
│   ├── models/            # Database models (Prisma)
│   ├── services/          # Business logic services
│   ├── utils/             # Server utilities
│   └── routes/            # API route definitions
├── tests/                  # Test suites
├── docs/                   # Documentation
├── docker/                 # Docker configurations
└── scripts/               # Build and deployment scripts
```

## 🔒 Security Features

### Data Protection
- **End-to-End Encryption**: Files are encrypted before upload using AES-256-GCM
- **Secure Key Management**: Encryption keys are generated per session and never stored
- **HTTPS Enforcement**: All communications secured with TLS 1.3
- **Input Validation**: Comprehensive input sanitization and validation
- **CSRF Protection**: Cross-site request forgery protection enabled

### Access Control
- **Time-Based Expiration**: Automatic link expiration with configurable timeouts
- **Download Limits**: Configurable maximum download attempts
- **IP-Based Rate Limiting**: Prevents abuse with intelligent rate limiting
- **Content-Type Validation**: Strict file type checking and sanitization
- **Virus Scanning**: Integration with ClamAV for malware detection

## 📊 API Endpoints

### File Operations
```
POST   /api/files/upload     # Upload files and generate QR code
GET    /api/files/:id        # Download file by ID
DELETE /api/files/:id        # Delete file (admin only)
GET    /api/files/:id/stats  # Get download statistics
```

### QR Code Management
```
POST   /api/qr/generate      # Generate QR code for files
GET    /api/qr/:code         # Resolve QR code to download links
POST   /api/qr/batch         # Generate multiple QR codes
```

### Analytics
```
GET    /api/analytics/stats  # Get usage statistics
GET    /api/analytics/logs   # Get access logs
```

## 🧪 Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run integration tests
npm run test:integration

# Run e2e tests
npm run test:e2e

# Lint code
npm run lint

# Type checking
npm run type-check
```

## 🚀 Deployment

### Production Build
```bash
# Create optimized production build
npm run build

# Start production server
npm start
```

### Cloud Deployment
The application is containerized and can be deployed to:
- **AWS ECS/EKS**: Using provided CloudFormation templates
- **Google Cloud Run**: Serverless container deployment
- **Azure Container Instances**: Scalable container hosting
- **Kubernetes**: Using provided Helm charts

### Environment-Specific Configurations
- **Development**: Hot reloading, detailed error messages, debug logging
- **Staging**: Production-like environment with additional monitoring
- **Production**: Optimized builds, minimal logging, enhanced security

## 📈 Performance Optimization

- **Code Splitting**: Automatic code splitting with React.lazy()
- **Image Optimization**: WebP conversion with fallbacks
- **Caching Strategy**: Multi-layer caching (CDN, Redis, browser)
- **Bundle Analysis**: Webpack bundle analyzer integration
- **Compression**: Gzip/Brotli compression enabled
- **CDN Integration**: Global content delivery for static assets

## 🔍 Monitoring & Observability

- **Health Checks**: Comprehensive application health monitoring
- **Metrics Collection**: Custom metrics with Prometheus
- **Error Tracking**: Integration with Sentry for error monitoring
- **Performance Monitoring**: APM with detailed transaction tracing
- **Log Aggregation**: Centralized logging with ELK stack
- **Alerting**: Smart alerting based on SLA thresholds

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes with tests
4. Ensure all tests pass (`npm test`)
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

### Code Standards
- **ESLint Configuration**: Strict TypeScript and React rules
- **Prettier Integration**: Automatic code formatting
- **Husky Pre-commit Hooks**: Automated linting and testing
- **Conventional Commits**: Standardized commit message format

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: [https://docs.qrsite.com](https://docs.qrsite.com)
- **Issues**: [GitHub Issues](https://github.com/yourorg/qrsite/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourorg/qrsite/discussions)
- **Email Support**: support@qrsite.com
- **Discord Community**: [Join our Discord](https://discord.gg/qrsite)

## 🙏 Acknowledgments

- [QR Code Generator Library](https://github.com/soldair/node-qrcode)
- [React QR Code Component](https://github.com/zpao/qrcode.react)
- [File Upload Utilities](https://github.com/transloadit/uppy)
- [Encryption Libraries](https://nodejs.org/api/crypto.html)
- All our amazing contributors and the open-source community

## 📋 Roadmap

### Version 2.0 (Coming Soon)
- [ ] Real-time collaboration features
- [ ] Advanced analytics dashboard
- [ ] Mobile app (iOS/Android)
- [ ] API rate limiting enhancements
- [ ] Multi-language support
- [ ] Advanced file preview capabilities

### Version 3.0 (Future)
- [ ] Blockchain-based file verification
- [ ] AI-powered content analysis
- [ ] Advanced user management
- [ ] Enterprise SSO integration
- [ ] Custom branding options
- [ ] Advanced audit logging

---

**Made with ❤️ by the QRsite Team**