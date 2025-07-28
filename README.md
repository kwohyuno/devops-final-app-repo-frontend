# DevOps Final App - Frontend

A modern React-based frontend application for a social platform with user authentication, board posting, messaging, and user management features. This project is part of a DevOps final project demonstrating containerized deployment with Docker and CI/CD pipelines.

## 🚀 Features

- **User Authentication**: Login and signup functionality with session management
- **Board System**: Create, read, update, and delete posts with real-time sorting
- **Messaging System**: Direct messaging between users
- **User Profile Management**: MyPage functionality for user profile management
- **Responsive Design**: Modern UI built with Material-UI components
- **Docker Containerization**: Multi-stage Docker build for production deployment
- **CI/CD Pipeline**: Automated build and deployment to AWS ECR

## 🛠️ Tech Stack

- **Frontend Framework**: React 18.3.1
- **UI Library**: Material-UI (MUI) v6.1.3
- **Routing**: React Router DOM v6.26.2
- **HTTP Client**: Axios v1.7.7
- **Styling**: Emotion (CSS-in-JS)
- **Containerization**: Docker with Nginx
- **CI/CD**: GitHub Actions
- **Cloud Platform**: AWS ECR

## 📁 Project Structure

```
devops-final-app-repo-frontend/
├── .github/workflows/          # CI/CD pipeline configuration
├── public/                     # Static assets
├── src/
│   ├── pages/                 # Page components
│   │   ├── board/            # Board functionality
│   │   ├── login/            # Authentication
│   │   ├── signup/           # User registration
│   │   ├── message/          # Messaging system
│   │   └── mypage/           # User profile
│   ├── containers/           # Main app container
│   ├── router/               # Routing configuration
│   └── assets/               # Application assets
├── Dockerfile                 # Multi-stage Docker build
├── nginx.conf                 # Nginx configuration
└── package.json              # Dependencies and scripts
```

## 🚀 Getting Started

### Prerequisites

- Node.js 14 or higher
- npm or yarn
- Docker (for containerized deployment)

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/kwohyuno/devops-final-app-repo-frontend.git
   cd devops-final-app-repo-frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm start
   ```

   The application will be available at [http://localhost:3000](http://localhost:3000)

### Available Scripts

- `npm start` - Runs the app in development mode
- `npm test` - Launches the test runner
- `npm run build` - Builds the app for production
- `npm run eject` - Ejects from Create React App (one-way operation)

## 🐳 Docker Deployment

### Build the Docker Image

```bash
docker build -t frontend-app .
```

### Run the Container

```bash
docker run -p 80:80 frontend-app
```

The application will be available at [http://localhost](http://localhost)

## 🔧 Configuration

### Nginx Configuration

The application uses Nginx as a reverse proxy with the following features:

- **Static File Serving**: Serves React build files
- **API Proxying**: Routes `/api/` requests to backend-post service
- **Secondary API**: Routes `/api2/` requests to backend-signup service
- **CORS Support**: Configured for cross-origin requests
- **SPA Routing**: Handles React Router navigation

### Environment Variables

The application connects to backend services through the following endpoints:

- **Primary API**: `http://backend-post:8080/` (via `/api/` proxy)
- **Signup API**: `http://backend-signup:8081/` (via `/api2/` proxy)

## 🔄 CI/CD Pipeline

The project includes a GitHub Actions workflow (`.github/workflows/trigger-nightly.yml`) that:

1. **Triggers on**: Push to main branch
2. **Builds**: Docker image using multi-stage build
3. **Deploys**: To AWS ECR with latest tag
4. **Uses**: AWS credentials from repository secrets

### Required Secrets

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_SESSION_TOKEN`
- `AWS_ECR_URL`

## 📱 Application Features

### Authentication
- User login with session management
- User registration (signup)
- Session storage for user persistence

### Board System
- Create new posts
- View all posts with real-time sorting
- Update existing posts
- Delete posts
- User interaction features

### Messaging
- Direct messaging between users
- Conversation management
- Real-time message handling

### User Management
- User profile pages
- Session management
- Logout functionality

## 🏗️ Architecture

### Frontend Architecture
- **Component-based**: Modular React components
- **Routing**: React Router for navigation
- **State Management**: React hooks for local state
- **API Integration**: Axios for HTTP requests

### Deployment Architecture
- **Multi-stage Docker**: Optimized production builds
- **Nginx Reverse Proxy**: Static file serving and API proxying
- **Microservices**: Separate backend services for different functionalities

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is part of a DevOps final project. Please refer to the course guidelines for usage and distribution.

## 🔗 Related Repositories

- Backend services (backend-post, backend-signup)
- Infrastructure configuration
- CI/CD pipeline configurations

---

**Note**: This is a frontend application designed to work with corresponding backend services. Ensure all backend services are properly configured and running for full functionality.
