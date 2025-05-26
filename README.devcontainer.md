DaySave.app Development Environment
🚀 Quick Start
Prerequisites

Docker Desktop installed and running
Visual Studio Code with Dev Containers extension
Git configured with your credentials

Getting Started

Clone the repository
bashgit clone https://github.com/andyegli/daysave.app.git
cd daysave.app

Open in Dev Container

Open VS Code
Open the project folder
VS Code will detect the devcontainer configuration
Click "Reopen in Container" or use Command Palette: Dev Containers: Reopen in Container


Environment Setup
bash# Copy environment variables
cp .env.example .env

# Edit .env with your configurations
nano .env

Database Setup
bash# Create database and run migrations
npm run db:create
npm run migrate:dev
npm run seed:dev

Start Development
bash# Start the development server
npm run dev
The application will be available at:

Main App: http://localhost:3000
MailHog (Email testing): http://localhost:8025
Redis Insight: http://localhost:6379



📁 Project Structure
daysave.app/
├── .devcontainer/           # Development container configuration
│   ├── devcontainer.json    # VS Code devcontainer settings
│   ├── docker-compose.yml   # Multi-service development environment
│   └── Dockerfile          # Development container image
├── src/                    # Source code (ESM modules)
│   ├── controllers/        # Request handlers
│   ├── models/            # Sequelize models
│   ├── routes/            # Express routes
│   ├── middleware/        # Custom middleware
│   ├── services/          # Business logic
│   ├── utils/             # Utility functions
│   ├── config/            # Configuration files
│   ├── migrations/        # Database migrations
│   ├── seeders/           # Database seeders
│   └── server.js          # Application entry point
├── views/                 # EJS templates
│   ├── layouts/           # Page layouts
│   ├── partials/          # Reusable components
│   └── pages/             # Page templates
├── public/                # Static assets
│   ├── css/               # Stylesheets
│   ├── js/                # Client-side JavaScript
│   ├── images/            # Images and icons
│   └── partials/          # Client-side partials
├── tests/                 # Test files
│   ├── unit/              # Unit tests
│   ├── integration/       # Integration tests
│   ├── e2e/               # End-to-end tests
│   └── fixtures/          # Test data
├── docs/                  # Documentation
│   ├── md/                # Markdown documentation
│   ├── diagrams/          # PlantUML diagrams
│   │   ├── src/           # .puml source files
│   │   └── out/           # Generated diagrams
│   └── api/               # API documentation
├── ai-service/            # AI processing service
└── logs/                  # Application logs
🛠 Development Tools
Available Scripts

npm run dev - Start development server with hot reload
npm run debug - Start server with debugger attached
npm test - Run unit tests with coverage
npm run test:watch - Run tests in watch mode
npm run test:e2e - Run end-to-end tests
npm run lint - Check code style
npm run format - Format code with Prettier
npm run migrate:dev - Run database migrations
npm run seed:dev - Seed database with test data
npm run plantuml - Generate diagrams from PlantUML files

Database Management
bash# Reset database (drop, create, migrate, seed)
npm run db:reset

# Create new migration
npx sequelize-cli migration:generate --name add-new-feature

# Create new model
npx sequelize-cli model:generate --name User --attributes name:string,email:string

# Create new seeder
npx sequelize-cli seed:generate --name demo-users
VS Code Extensions Included

ESLint & Prettier for code quality
SQL Tools for database management
PlantUML for diagrams
Google Cloud Tools
REST Client for API testing
Error Lens for inline error display
GitLens for Git integration

🔧 Configuration
Environment Variables
Copy .env.example to .env and configure:
Required for basic functionality:

Database connection settings
Session secrets
JWT configuration

Optional for full features:

OAuth provider credentials (Google, Facebook, Microsoft)
Email service configuration (SMTP/SendGrid)
SMS service (Twilio)
Payment providers (Stripe, PayPal)
Google Cloud services
AI service API keys

Google Cloud Setup

Create a Google Cloud Project
Enable required APIs (Storage, Vision, Translate, etc.)
Create a service account
Download service account key to .gcp/service-account.json
Set GOOGLE_CLOUD_PROJECT environment variable

Authentication Providers
Configure OAuth applications:

Google: Google Cloud Console → APIs & Services → Credentials
Facebook: Facebook Developers → My Apps
Microsoft: Azure Portal → App registrations

🧪 Testing
Running Tests
bash# Unit tests
npm test

# Watch mode during development
npm run test:watch

# End-to-end tests
npm run test:e2e

# Coverage report
npm test -- --coverage
Test Structure

Unit tests: src/**/*.test.js
Integration tests: tests/integration/**/*.js
E2E tests: tests/e2e/**/*.spec.js

📊 Monitoring & Logging
Development Logging

Console output with debug levels
File logging to logs/ directory
Request logging with Morgan
Error tracking and stack traces

Performance Monitoring

Request timing middleware
Database query logging
Memory usage tracking
Rate limiting metrics

🐳 Container Services
The development environment includes:

daysave-dev: Main application container
mysql: Database server
redis: Cache and session store
mailhog: Email testing server
ai-service: AI processing backend
nginx: Reverse proxy (optional)

🔐 Security Features
Development Security

Helmet.js security headers
Rate limiting
Input validation and sanitization
XSS protection
SQL injection prevention
CSRF protection
Password hashing with bcrypt
JWT token management

Authentication & Authorization

Multiple auth strategies (local, OAuth, SSO)
Two-factor authentication (TOTP, SMS, email)
Passkey support (WebAuthn)
Role-based access control (RBAC)
Session management
Account lockout protection

📱 Mobile & Accessibility
Mobile Support

Responsive design with Bootstrap
Touch-friendly interfaces
Mobile-specific features
Share-to integration
Location services
Offline caching (Service Worker)

Accessibility

WCAG 2.1 AA compliance
Screen reader compatibility
Keyboard navigation
High contrast themes
Alt text for images
Semantic HTML structure

🚀 Deployment
Google Cloud Platform
bash# Deploy to App Engine
npm run deploy:gcp

# Cloud Build deployment
gcloud builds submit --config cloudbuild.yaml
Environment-specific configs

Development: .env
Production: Cloud environment variables
Staging: Separate configuration files

🤝 Contributing

Follow the established code style (ESLint + Prettier)
Write tests for new features
Update documentation
Use conventional commit messages
Create PlantUML diagrams for architectural changes

📚 Documentation

API documentation: docs/api/
Architecture diagrams: docs/diagrams/
User guides: docs/md/
Code documentation: Generated with JSDoc

🆘 Troubleshooting
Common Issues
Container won't start:

Check Docker Desktop is running
Verify port availability (3000, 3306, 6379)
Review Docker logs

Database connection errors:

Ensure MySQL container is running
Check environment variables
Verify database exists

Authentication not working:

Check OAuth configuration
Verify callback URLs
Review environment variables

AI service unavailable:

Check Python dependencies
Verify AI service container status
Review API endpoints

Getting Help

Check the issues on GitHub
Review documentation in docs/
Use VS Code's integrated terminal for debugging
Check container logs: docker-compose logs service-name

