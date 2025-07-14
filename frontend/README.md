# Klair Frontend - Next.js Application

## 📖 Overview

The Klair frontend is a sophisticated, modern React application built with Next.js 15 that provides an intuitive interface for AI-powered video content analysis. It features real-time progress tracking, conversational AI interactions, and a responsive design optimized for both desktop and mobile experiences.

### 🎯 Key Features

- **🤖 Conversational AI Interface**: Chat with your videos to understand viral potential
- **📹 Advanced Video Upload**: Drag-and-drop, URL import, and real-time progress tracking
- **📊 Real-time Analytics**: Live processing status and usage statistics
- **🎬 Clip Management**: Browse, preview, and export generated clips
- **📱 Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **🔐 Enterprise Auth**: Secure authentication with Clerk integration
- **⚡ Performance Optimized**: Server-side rendering with edge runtime support

---

## 🛠️ Technology Stack

### Core Framework
- **Next.js 15**: App Router with React Server Components
- **React 18**: Latest React features with concurrent rendering
- **TypeScript 5**: Full type safety across the application
- **App Directory**: Modern Next.js routing and layout system

### Styling & UI
- **Tailwind CSS 3.4**: Utility-first CSS framework
- **Radix UI**: Accessible, unstyled UI primitives
- **Framer Motion**: Advanced animations and transitions
- **Custom Components**: shadcn/ui component library
- **Responsive Design**: Mobile-first approach with breakpoints

### State Management & Data
- **React Hooks**: Modern state management with Context API
- **Server Components**: Optimized data fetching with RSC
- **Streaming UI**: Real-time updates with Server-Sent Events
- **Local Storage**: Persistent user preferences and settings

### External Integrations
- **Clerk**: Authentication and user management
- **Vercel Analytics**: Performance monitoring and insights
- **Google Cloud Storage**: Direct file upload integration
- **AI SDK**: Streaming AI responses and interactions

### Development Tools
- **ESLint**: Code linting and quality checks
- **Prettier**: Code formatting and consistency
- **Tailwind IntelliSense**: Enhanced development experience
- **TypeScript**: Static type checking and IntelliSense

---

## 📂 Project Structure

```
frontend/
├── app/                          # Next.js App Router
│   ├── globals.css              # Global styles and Tailwind base
│   ├── layout.tsx               # Root layout with providers
│   ├── page.tsx                 # Landing page
│   ├── loading.tsx              # Global loading component
│   ├── not-found.tsx            # 404 error page
│   │
│   ├── (components)/            # Shared component library
│   │   ├── auth/                # Authentication components
│   │   │   ├── AuthForm.tsx     # Unified auth form
│   │   │   ├── components/      # Auth sub-components
│   │   │   └── hooks/           # Auth-related hooks
│   │   ├── buttons/             # Reusable button components
│   │   ├── icons/               # SVG icon components
│   │   ├── klair/               # Klair-specific components
│   │   │   ├── VideoUpload.tsx  # Main upload interface
│   │   │   ├── VideoChat.tsx    # Conversational AI chat
│   │   │   ├── ClipList.tsx     # Clip browsing interface
│   │   │   ├── enhancement/     # Video enhancement tools
│   │   │   ├── hooks/           # Klair-specific hooks
│   │   │   ├── modal-components/ # Modal content components
│   │   │   └── video-upload/    # Upload system components
│   │   ├── pricing/             # Subscription and pricing
│   │   └── ui/                  # Base UI components
│   │
│   ├── klair/                   # Main application pages
│   │   ├── layout.tsx           # Klair app layout
│   │   ├── page.tsx             # Video analysis dashboard
│   │   ├── clips/               # Clip management pages
│   │   │   └── [taskId]/        # Individual clip pages
│   │   ├── history/             # Analysis history
│   │   │   ├── components/      # History-specific components
│   │   │   ├── hooks/           # History management hooks
│   │   │   └── types.ts         # History type definitions
│   │   └── shared/              # Shared Klair utilities
│   │       ├── hooks/           # Common hooks
│   │       ├── services/        # API service layer
│   │       ├── types/           # Type definitions
│   │       └── utils/           # Utility functions
│   │
│   ├── pricing/                 # Subscription pages
│   ├── profile/                 # User profile management
│   ├── sign-in/                 # Authentication pages
│   └── sso-callback/            # SSO callback handling
│
├── lib/                         # Utility libraries
│   ├── utils.ts                 # General utilities
│   └── clerk.ts                 # Clerk configuration
│
├── public/                      # Static assets
│   ├── images/                  # Image assets
│   ├── icons/                   # Icon files
│   └── favicons/                # Favicon variants
│
├── components.json              # shadcn/ui configuration
├── next.config.mjs              # Next.js configuration
├── tailwind.config.ts           # Tailwind CSS configuration
├── tsconfig.json                # TypeScript configuration
├── package.json                 # Dependencies and scripts
└── middleware.tsx               # Next.js middleware (Clerk auth)
```

---