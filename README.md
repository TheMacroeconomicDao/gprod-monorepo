# GPROD Monorepo

🏗️ **Unified repository for GPROD Backend and Frontend applications**

## 📁 Project Structure

```
gprod-monorepo/
├── apps/
│   ├── backend/          # NestJS Backend API (Git Submodule)
│   └── frontend/         # React Frontend App (Git Submodule)
├── packages/             # Shared libraries and utilities
│   ├── shared-types/     # TypeScript types shared between apps
│   ├── ui-components/    # Reusable UI components
│   └── utils/           # Common utilities
├── tools/               # Development tools and scripts
├── .github/             # GitHub Actions workflows
├── docker-compose.yml   # Development environment
├── package.json         # Root workspace configuration
└── README.md           # This file
```

## 🚀 Quick Start

### Prerequisites

- **Node.js** >= 18.0.0
- **pnpm** >= 8.0.0
- **Docker** (for local development)
- **kubectl** (for Kubernetes deployment)

### Installation

```bash
# Clone the monorepo
git clone https://github.com/TheMacroeconomicDao/gprod-monorepo.git
cd gprod-monorepo

# Initialize and update submodules
git submodule init
git submodule update

# Install dependencies
pnpm install
```

## 📦 Available Scripts

### Development

```bash
# Start both apps in development mode
pnpm dev

# Start individual apps
pnpm backend:dev     # Start backend only
pnpm frontend:dev    # Start frontend only
```

### Building

```bash
# Build all apps
pnpm build

# Build individual apps
pnpm backend:build   # Build backend only
pnpm frontend:build  # Build frontend only
```

### Docker

```bash
# Start development environment
pnpm docker:up

# Stop development environment
pnpm docker:down

# View logs
pnpm docker:logs
```

### Kubernetes

```bash
# Deploy to Kubernetes
pnpm k8s:deploy
```

## 🔧 Applications

### Backend (`apps/backend/`)

- **Framework**: NestJS
- **Database**: PostgreSQL with Prisma ORM
- **Repository**: [gprod-backend](https://github.com/TheMacroeconomicDao/gprod-backend)
- **Deployment**: Kubernetes on `develop-gprod` namespace
- **API URL**: https://api.dev.gprod.build.infra.gyber.org

### Frontend (`apps/frontend/`)

- **Framework**: React + Vite
- **Architecture**: Feature-Sliced Design (FSD)
- **Repository**: [gyberplan-web-app-frontend](https://gitlab.com/GybernatyTech/gyberplan-web-app-frontend)
- **Deployment**: Static hosting
- **App URL**: https://dev.gprod.build.infra.gyber.org

## 🛠️ Development Workflow

### Working with Submodules

```bash
# Update submodules to latest commits
git submodule update --remote

# Work in a specific submodule
cd apps/backend
git checkout feature-branch
# Make changes, commit, push

# Update parent repo to use new submodule commit
cd ../..
git add apps/backend
git commit -m "update backend submodule"
```

### Adding New Packages

```bash
# Create new shared package
mkdir packages/new-package
cd packages/new-package
pnpm init

# Add to workspace in root package.json
# Workspaces already configured as "packages/*"
```

## 🚀 Deployment

### Backend Deployment

Backend automatically deploys to Kubernetes via GitHub Actions:

1. **Push to `dev` branch** → triggers deployment pipeline
2. **Docker image** built and pushed to GHCR
3. **Kubernetes deployment** via Kustomize
4. **Healthcheck** validates deployment

### Frontend Deployment

Frontend deployment varies by hosting solution.

## 🔐 Environment Variables

Create `.env` files in each application:

- `apps/backend/.env` - Backend environment variables
- `apps/frontend/.env` - Frontend environment variables

## 📋 Contributing

1. **Fork** the repository
2. **Create feature branch**: `git checkout -b feature/amazing-feature`
3. **Work in submodules** as needed
4. **Commit changes**: `git commit -m 'Add amazing feature'`
5. **Push to branch**: `git push origin feature/amazing-feature`
6. **Open Pull Request**

## 🏗️ Architecture

### Git Submodules Strategy

- **Backend**: GitHub repository as submodule
- **Frontend**: GitLab repository as submodule
- **Monorepo**: Unified management and CI/CD

### Workspace Management

- **pnpm workspaces** for dependency management
- **Shared packages** for code reuse
- **Common tooling** across applications

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/TheMacroeconomicDao/gprod-monorepo/issues)
- **Email**: support@gprod.org
- **Documentation**: [Project Wiki](https://github.com/TheMacroeconomicDao/gprod-monorepo/wiki)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Built with ❤️ by The Macroeconomic DAO** 