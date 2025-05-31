# 🔐 Keyper - Secure Credential Management

> **Dream it, Pixel it** ✨  
> *Made with ❤️ by Pink Pixel*

## 📋 Project Overview

**Keyper** is a modern, secure credential management web service designed to help users safely store and organize their digital credentials. Built with cutting-edge web technologies, Keyper provides a sleek, intuitive interface for managing API keys, passwords, secrets, tokens, and certificates through a hosted web platform.

### 🎯 Purpose
- **Hosted Service**: Free web-based credential management platform
- **Secure Storage**: Safely store various types of credentials with encryption
- **Organization**: Categorize and tag credentials for easy management
- **Accessibility**: Quick search and filtering capabilities
- **User Experience**: Modern, responsive design with dark theme aesthetics
- **No Installation**: Access anywhere through web browser

## 🏗️ Architecture

### **Service Model**
- **Deployment**: Hosted web service on Cloudflare Pages
- **Access**: Web browser only (no downloads or installations)
- **Licensing**: Proprietary software with free service offering
- **Distribution**: Software-as-a-Service (SaaS) model

### **Frontend Architecture**
- **Framework**: React 19.1 with TypeScript 5.8.3
- **Build Tool**: Vite 5.4.19 for fast development and optimized builds
- **Styling**: Tailwind CSS 3.4.11 with custom gradient themes
- **UI Components**: shadcn/ui component library with Radix UI primitives
- **State Management**: React hooks with TanStack Query 5.77.2 for server state
- **Routing**: React Router DOM 7.6.1 for navigation
- **Form Handling**: React Hook Form 7.56.4 with Zod 3.25.34 validation

### **Backend & Database**
- **Backend-as-a-Service**: Supabase 2.49.8
- **Database**: PostgreSQL (via Supabase)
- **Authentication**: Supabase Auth with email/password
- **Real-time**: Supabase real-time subscriptions
- **Security**: Row Level Security (RLS) policies

### **Deployment & Infrastructure**
- **Platform**: Cloudflare Pages
- **Build Tool**: Wrangler 4.17.0 for deployment
- **Configuration**: Complete deployment setup with headers, redirects, and routing
- **Environment**: Environment variable validation and security
- **Verification**: Automated deployment verification tooling

### **Key Components Structure**
```
src/
├── components/
│   ├── ui/                 # shadcn/ui components
│   ├── dashboard/          # Dashboard-specific components
│   ├── AuthForm.tsx        # Authentication form
│   └── CredentialsDashboard.tsx  # Main dashboard
├── pages/
│   ├── Dashboard.tsx       # Main dashboard page
│   ├── Index.tsx          # Landing page
│   └── NotFound.tsx       # 404 page
├── integrations/
│   └── supabase/          # Supabase client and types
├── hooks/                 # Custom React hooks
└── lib/                   # Utility functions
```

## 🗄️ Database Schema

### **Tables**

#### `credentials`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | Primary key |
| `user_id` | UUID | Foreign key to auth.users |
| `title` | String | Credential title |
| `description` | String | Optional description |
| `credential_type` | Enum | Type: api_key, login, secret, token, certificate |
| `priority` | Enum | Priority: low, medium, high, critical |
| `username` | String | Username (for login type) |
| `password` | String | Password (encrypted) |
| `api_key` | String | API key (encrypted) |
| `secret_value` | String | Secret value (encrypted) |
| `url` | String | Associated URL |
| `tags` | String[] | Array of tags |
| `category` | String | Category name |
| `notes` | Text | Additional notes |
| `expires_at` | Timestamp | Expiration date |
| `last_accessed` | Timestamp | Last access time |
| `created_at` | Timestamp | Creation time |
| `updated_at` | Timestamp | Last update time |

#### `categories`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | Primary key |
| `name` | String | Category name |
| `color` | String | Color code |
| `icon` | String | Icon identifier |
| `created_at` | Timestamp | Creation time |

## 🔒 Security Implementation

### **Core Security Features**
- ✅ Row Level Security (RLS) policies for data isolation
- ✅ User-based authentication with Supabase Auth
- ✅ Encrypted credential storage at rest
- ✅ Environment variable validation and protection
- ✅ HTTPS enforcement for all communications
- ✅ Secure session management

### **Security Incident Resolution (May 30, 2025)**
**Issue**: Supabase credentials were accidentally committed to git history  
**Resolution**: ✅ **FULLY RESOLVED**
- ✅ Credentials immediately rotated in Supabase dashboard
- ✅ Git history cleaned using specialized scripts
- ✅ Enhanced .gitignore with comprehensive patterns
- ✅ Environment variable validation strengthened
- ✅ Security checklist and monitoring tools implemented
- ✅ Team notified and repository re-cloned

### **Security Safeguards Implemented**
- **Enhanced .gitignore**: Prevents environment files and sensitive data
- **Environment Validation**: Runtime checks for required variables
- **Security Checklist**: Pre-deployment security verification
- **Monitoring Tools**: Recommendations for gitleaks and git-secrets
- **Documentation**: Comprehensive security best practices guide

## 🎨 Design System

### **Color Palette**
- **Primary**: Cyan (#06B6D4)
- **Background**: Dark gradients (Gray 950 → Gray 900 → Cyan 950)
- **Text**: White/Gray scale
- **Accents**: Cyan variants for highlights

### **Typography**
- **Font**: System fonts with Tailwind CSS defaults
- **Hierarchy**: Clear heading structure with proper contrast

### **UI Patterns**
- **Cards**: Glassmorphism effect with backdrop blur
- **Buttons**: Cyan primary with hover states
- **Forms**: Dark theme with cyan accents
- **Icons**: Lucide React 0.511.0 icon library

## 🔧 Key Features

### **Authentication**
- ✅ Email/password authentication
- ✅ Secure session management
- ✅ User registration and login
- ✅ Password visibility toggle

### **Credential Management**
- ✅ Multiple credential types support (API keys, logins, secrets, tokens, certificates)
- ✅ CRUD operations (Create, Read, Update, Delete)
- ✅ Secure storage with encryption
- ✅ Priority levels and categorization
- ✅ Tags for flexible organization
- ✅ Expiration date tracking
- ✅ Last accessed timestamps

### **User Interface**
- ✅ Responsive design for all devices
- ✅ Dark theme with modern aesthetics
- ✅ Search and filtering capabilities
- ✅ Modal-based editing and viewing
- ✅ Grid layout for credential display
- ✅ Loading states and error handling
- ✅ Copy functionality for credentials
- ✅ Password/secret visibility toggles

### **Development & Deployment**
- ✅ TypeScript for type safety
- ✅ ESLint for code quality
- ✅ Automated deployment scripts (PowerShell & Bash)
- ✅ Deployment verification tooling
- ✅ Comprehensive documentation
- ✅ Git cleanup and security scripts

## 📦 Dependencies

### **Core Dependencies**
- `react` (^19.1.0) - UI framework
- `typescript` (^5.8.3) - Type safety
- `vite` (^5.4.19) - Build tool
- `@supabase/supabase-js` (^2.49.8) - Backend client
- `@tanstack/react-query` (^5.77.2) - Server state management

### **UI & Styling**
- `tailwindcss` (^3.4.11) - CSS framework
- `@radix-ui/*` - Accessible UI primitives (various versions)
- `lucide-react` (^0.511.0) - Icon library
- `class-variance-authority` (^0.7.1) - Component variants
- `tailwind-merge` (^3.3.0) - Utility merging
- `tailwindcss-animate` (^1.0.7) - Animations

### **Form & Validation**
- `react-hook-form` (^7.56.4) - Form management
- `@hookform/resolvers` (^5.0.1) - Form validation
- `zod` (^3.25.34) - Schema validation

### **Additional Features**
- `react-router-dom` (^7.6.1) - Routing
- `date-fns` (^4.1.0) - Date utilities
- `sonner` (^2.0.3) - Toast notifications
- `next-themes` (^0.4.6) - Theme management
- `cmdk` (^1.1.1) - Command menu
- `input-otp` (^1.4.2) - OTP input

### **Development Tools**
- `wrangler` (^4.17.0) - Cloudflare deployment
- `eslint` (^9.27.0) - Code linting
- `typescript-eslint` (^8.33.0) - TypeScript linting
- `@vitejs/plugin-react-swc` (^3.10.0) - React plugin

## 🚀 Current Status

**Version**: 0.1.0  
**Status**: ✅ Production Ready  
**Last Analysis**: May 30, 2025 19:21 UTC  
**Security Status**: ✅ Secure (incident resolved)

### **Completed Features**
- ✅ User authentication system
- ✅ Credential CRUD operations
- ✅ Category management
- ✅ Search and filtering
- ✅ Responsive UI design
- ✅ Database integration with RLS
- ✅ Cloudflare Pages deployment
- ✅ Security incident remediation
- ✅ Comprehensive documentation

### **Development Environment**
- **Node.js**: 18+ required
- **Package Manager**: npm (package-lock.json present)
- **Development Server**: Vite dev server on port 8080
- **Build**: Optimized production builds with Vite
- **Deployment**: Automated scripts for Cloudflare Pages

### **Notable Scripts & Tools**
- `npm run dev` - Development server
- `npm run build` - Production build
- `npm run deploy` - Cloudflare Pages deployment
- `verify-deployment.js` - Post-deployment verification
- `cleanup-git-history.*` - Security cleanup tools
- `check-auth-config.js` - Authentication validation

## 📚 Documentation Files
- **README.md**: User-facing documentation and setup guide
- **CONTRIBUTING.md**: Developer contribution guidelines
- **DEPLOYMENT.md**: Deployment instructions and requirements
- **CHANGELOG.md**: Version history and updates
- **security-checklist.md**: Security verification checklist
- **LICENSE**: MIT license terms

---

> **Pink Pixel Development Notes**  
> This project represents a mature MVP with comprehensive features, robust security, and production-ready deployment infrastructure. The resolution of the credential exposure incident has strengthened the overall security posture with enhanced monitoring and prevention measures.
