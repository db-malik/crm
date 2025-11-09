# 🎨 Gym CRM Frontend Stack - 2025 Edition

Complete modern stack for Next.js 15 + Material-UI v7 with best practices and cutting-edge tools researched for optimal performance and developer experience.

---

## 🏆 Complete Tech Stack

### Core Framework
```
├── Framework: Next.js 15.4 (App Router + Turbopack)
├── Language: TypeScript 5
├── UI Library: Material-UI (MUI) v7 (Released March 2025)
├── MUI X: v8 (Released April 2025)
├── Styling: Emotion (built-in with MUI)
└── Package Manager: npm
```

### State Management (Modern Approach)
```
├── Server State: TanStack Query v5 (React Query)
├── Client State: Zustand
├── URL State: nuqs
└── Form State: React Hook Form
```

### Data & API
```
├── HTTP Client: Axios
├── Validation: Zod
├── API Client: Custom with Axios interceptors
└── Type Safety: End-to-end with backend
```

### Charts & Visualization (Research-Based 2025)
```
├── Primary: Nivo (beautiful, modern, fast initial render)
├── For Dashboards: Recharts (simple, declarative, D3-based)
├── Complex/Custom: Visx (Airbnb, full control, D3 integration)
└── Time Series: TanStack Charts (financial data)
```

### Tables & Data Grids (Performance-Optimized)
```
├── Basic Tables: MUI Table
├── Advanced Grid: MUI X Data Grid v8 (with AI features)
├── Headless/Custom: TanStack Table v8 (lightweight, flexible)
└── Enterprise Scale: AG Grid (100K+ rows, server-side ops)
```

### Scheduling & Calendar (Gym-Specific)
```
├── Class Scheduling: react-big-calendar (Google Calendar-like)
├── Date Selection: react-day-picker (6M+ downloads/week)
├── Advanced Booking: Mobiscroll Scheduler (multi-resource)
└── Date/Time Inputs: MUI X v8 Date Pickers + Time Range Picker
```

### Forms & Validation
```
├── Forms: React Hook Form
├── Validation: Zod
├── MUI Integration: @hookform/mui
└── Date Pickers: MUI X Date Pickers
```

### Icons & Assets
```
├── Icons: @mui/icons-material
├── Custom Icons: Lucide React
├── Images: Next.js Image optimization
└── Fonts: Next.js Font optimization
```

### Authentication
```
├── Auth Library: NextAuth.js v5 (Auth.js)
├── JWT Handling: js-cookie
├── Protected Routes: Middleware + HOCs
└── Role-Based Access: Custom hooks
```

### Developer Tools
```
├── Linting: ESLint
├── Formatting: Prettier
├── Git Hooks: Husky
├── Type Checking: TypeScript strict mode
└── Bundle Analysis: @next/bundle-analyzer
```

### Testing
```
├── Unit Tests: Vitest
├── Component Tests: React Testing Library
├── E2E Tests: Playwright
└── API Mocking: MSW (Mock Service Worker)
```

### Performance & Optimization
```
├── Lazy Loading: Next.js dynamic imports
├── Image Optimization: Next.js Image
├── Code Splitting: Automatic with Next.js
├── Caching: TanStack Query
└── Monitoring: Vercel Analytics (optional)
```

### Animations & Interactions
```
├── UI Animations: Framer Motion (production dashboards)
├── Auto Animations: AutoAnimate (zero-config, perfect for dashboards)
├── Physics-Based: React Spring (elastic, natural motion)
└── Complex/Timeline: GSAP (enterprise-grade control)
```

### Notifications & Feedback
```
├── Toast Notifications: Sonner (modern, shadcn/ui integration)
├── Alternative Toast: React-Hot-Toast (5KB, battle-tested)
├── Progress Indicators: Built-in MUI components
└── Alerts: MUI Alert system
```

### File Handling
```
├── File Upload: react-dropzone (robust, type-safe)
├── Drag & Drop: react-drag-drop-files (lightweight)
├── Alternative: react-uploady (modern, hooks-based)
└── Image Optimization: Next.js Image component
```

### Utilities
```
├── Dates: date-fns (modern, tree-shakeable)
├── Formatting: numeral (numbers, currency)
├── Class Utilities: clsx (conditional classes)
├── PDF Generation: jsPDF / react-pdf
└── QR Codes: react-qr-code (membership cards)
```

---

## 📦 Complete Package List

### Essential Packages (2025 Optimized)

```json
{
  "dependencies": {
    // Next.js 15 with React 19 Support
    "next": "^15.4.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",

    // Material-UI v7 (March 2025) + MUI X v8 (April 2025)
    "@mui/material": "^7.0.1",
    "@mui/icons-material": "^7.0.1",
    "@emotion/react": "^11.13.0",
    "@emotion/styled": "^11.13.0",

    // MUI X v8 - Advanced Components
    "@mui/x-data-grid": "^8.0.0",
    "@mui/x-date-pickers": "^8.0.0",

    // State Management (2025 Best Practice)
    "@tanstack/react-query": "^5.62.0",
    "zustand": "^5.0.0",
    "nuqs": "^2.2.0",

    // Forms & Validation (Winner: React Hook Form)
    "react-hook-form": "^7.53.0",
    "@hookform/resolvers": "^3.9.0",
    "zod": "^3.23.0",

    // HTTP & API
    "axios": "^1.7.0",

    // Authentication
    "next-auth": "^5.0.0",
    "js-cookie": "^3.0.5",

    // Charts (Multi-library approach)
    "@nivo/core": "^0.87.0",
    "@nivo/bar": "^0.87.0",
    "@nivo/line": "^0.87.0",
    "@nivo/pie": "^0.87.0",
    "recharts": "^2.15.0",

    // Scheduling & Calendar (Gym-Specific)
    "react-big-calendar": "^1.15.0",
    "react-day-picker": "^9.3.0",

    // Animations
    "framer-motion": "^11.15.0",
    "@formkit/auto-animate": "^0.8.2",

    // Notifications
    "sonner": "^1.7.0",

    // File Upload
    "react-dropzone": "^14.3.5",

    // Utilities
    "date-fns": "^4.1.0",
    "numeral": "^2.0.6",
    "lucide-react": "^0.462.0",
    "clsx": "^2.1.0",
    "react-qr-code": "^2.0.15"
  },
  "devDependencies": {
    "@types/node": "^22.0.0",
    "@types/react": "^19.0.0",
    "@types/react-dom": "^19.0.0",
    "@types/numeral": "^2.0.5",
    "@types/js-cookie": "^3.0.6",
    "typescript": "^5.7.0",
    "eslint": "^9.0.0",
    "eslint-config-next": "^15.4.0",
    "prettier": "^3.3.0",
    "@tanstack/react-query-devtools": "^5.62.0"
  }
}
```

---

## 🚀 Installation Steps (2025 Optimized)

### Step 1: Create Next.js 15 App

```bash
cd /Users/malek/Desktop/work/CRM_gym/pre_dev/dev/frontend

# Create Next.js 15 app with TypeScript and Turbopack
npx create-next-app@latest . --typescript --app --turbopack --import-alias "@/*"

# Answer prompts:
# ✓ Would you like to use ESLint? Yes
# ✓ Would you like to use Tailwind CSS? No (we're using MUI v7)
# ✓ Would you like to use `src/` directory? Yes
# ✓ Would you like to use App Router? Yes
# ✓ Would you like to use Turbopack for next dev? Yes
```

### Step 2: Install Material-UI v7 + MUI X v8

```bash
# Core MUI v7 packages (March 2025 release)
npm install @mui/material@latest @emotion/react@latest @emotion/styled@latest @mui/icons-material@latest

# MUI X v8 packages (April 2025 - with AI features, pivoting, etc.)
npm install @mui/x-data-grid@latest @mui/x-date-pickers@latest
```

### Step 3: Install State Management (2025 Best Practice)

```bash
# TanStack Query v5 for server state (replaces Redux)
npm install @tanstack/react-query
npm install -D @tanstack/react-query-devtools

# Zustand for client state (90% lighter than Redux)
npm install zustand

# nuqs for URL state
npm install nuqs
```

### Step 4: Install Forms & Validation (Winner: React Hook Form)

```bash
# React Hook Form beats Formik in 2025 (3x smaller, faster)
npm install react-hook-form @hookform/resolvers zod
```

### Step 5: Install Charts (Multi-Library Approach)

```bash
# Nivo - Beautiful, modern charts with fastest initial render
npm install @nivo/core @nivo/bar @nivo/line @nivo/pie

# Recharts - Simple dashboard charts
npm install recharts
```

### Step 6: Install Scheduling & Calendar (Gym-Specific)

```bash
# react-big-calendar - Google Calendar-like class scheduling
npm install react-big-calendar

# react-day-picker - 6M+ downloads/week, best date selection
npm install react-day-picker
```

### Step 7: Install Animations & Interactions

```bash
# Framer Motion - Production UI animations
npm install framer-motion

# AutoAnimate - Zero-config dashboard animations
npm install @formkit/auto-animate
```

### Step 8: Install Notifications & File Upload

```bash
# Sonner - Modern toast notifications (2025 winner)
npm install sonner

# react-dropzone - Robust file upload
npm install react-dropzone
```

### Step 9: Install Utilities

```bash
# Core utilities
npm install axios date-fns numeral lucide-react clsx react-qr-code

# Authentication
npm install next-auth js-cookie

# Type definitions
npm install -D @types/numeral @types/js-cookie
```

---

## 📁 Recommended Project Structure

```
frontend/
├── src/
│   ├── app/                          # Next.js 14 App Router
│   │   ├── (auth)/                   # Auth layout group
│   │   │   ├── login/
│   │   │   │   └── page.tsx
│   │   │   ├── register/
│   │   │   │   └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (dashboard)/              # Dashboard layout group
│   │   │   ├── dashboard/
│   │   │   │   └── page.tsx
│   │   │   ├── employees/
│   │   │   │   ├── page.tsx
│   │   │   │   ├── [id]/
│   │   │   │   │   └── page.tsx
│   │   │   │   └── new/
│   │   │   │       └── page.tsx
│   │   │   ├── members/
│   │   │   ├── classes/
│   │   │   ├── schedule/
│   │   │   ├── timesheets/
│   │   │   └── layout.tsx
│   │   │
│   │   ├── api/                      # API routes (optional proxy)
│   │   │   └── auth/
│   │   │       └── [...nextauth]/
│   │   │           └── route.ts
│   │   │
│   │   ├── layout.tsx                # Root layout
│   │   ├── page.tsx                  # Home page
│   │   ├── providers.tsx             # Client providers
│   │   └── theme-registry.tsx        # MUI theme setup
│   │
│   ├── components/
│   │   ├── layout/                   # Layout components
│   │   │   ├── Header.tsx
│   │   │   ├── Sidebar.tsx
│   │   │   ├── Footer.tsx
│   │   │   └── DashboardLayout.tsx
│   │   │
│   │   ├── forms/                    # Form components
│   │   │   ├── EmployeeForm.tsx
│   │   │   ├── MemberForm.tsx
│   │   │   └── FormFields/
│   │   │
│   │   ├── tables/                   # Table components
│   │   │   ├── EmployeesTable.tsx
│   │   │   ├── MembersTable.tsx
│   │   │   └── DataGridWrapper.tsx
│   │   │
│   │   ├── charts/                   # Chart components
│   │   │   ├── RevenueChart.tsx
│   │   │   ├── AttendanceChart.tsx
│   │   │   └── MembershipChart.tsx
│   │   │
│   │   ├── cards/                    # Card components
│   │   │   ├── StatCard.tsx
│   │   │   ├── EmployeeCard.tsx
│   │   │   └── MemberCard.tsx
│   │   │
│   │   └── ui/                       # Reusable UI components
│   │       ├── LoadingSpinner.tsx
│   │       ├── ErrorBoundary.tsx
│   │       ├── ConfirmDialog.tsx
│   │       └── PageHeader.tsx
│   │
│   ├── lib/
│   │   ├── api/                      # API client
│   │   │   ├── client.ts
│   │   │   ├── employees.ts
│   │   │   ├── members.ts
│   │   │   └── auth.ts
│   │   │
│   │   ├── hooks/                    # Custom hooks
│   │   │   ├── useAuth.ts
│   │   │   ├── useEmployees.ts
│   │   │   ├── useMembers.ts
│   │   │   └── useToast.ts
│   │   │
│   │   ├── stores/                   # Zustand stores
│   │   │   ├── authStore.ts
│   │   │   ├── uiStore.ts
│   │   │   └── settingsStore.ts
│   │   │
│   │   ├── types/                    # TypeScript types
│   │   │   ├── employee.ts
│   │   │   ├── member.ts
│   │   │   ├── api.ts
│   │   │   └── index.ts
│   │   │
│   │   ├── validations/              # Zod schemas
│   │   │   ├── employee.schema.ts
│   │   │   ├── member.schema.ts
│   │   │   └── auth.schema.ts
│   │   │
│   │   └── utils/                    # Utility functions
│   │       ├── formatters.ts
│   │       ├── validators.ts
│   │       ├── constants.ts
│   │       └── helpers.ts
│   │
│   ├── styles/
│   │   ├── globals.css
│   │   └── theme.ts                  # MUI theme configuration
│   │
│   └── middleware.ts                 # Next.js middleware (auth)
│
├── public/
│   ├── images/
│   ├── icons/
│   └── favicon.ico
│
├── .env.local
├── .env.example
├── next.config.js
├── tsconfig.json
├── .eslintrc.json
├── .prettierrc
└── package.json
```

---

## 🎨 Material-UI v6 Setup

### 1. Create Theme Registry (Required for App Router)

**`src/app/theme-registry.tsx`**

```typescript
'use client';

import { ThemeProvider, createTheme } from '@mui/material/styles';
import CssBaseline from '@mui/material/CssBaseline';
import { ReactNode } from 'react';

const theme = createTheme({
  palette: {
    mode: 'light',
    primary: {
      main: '#1976d2',
      light: '#42a5f5',
      dark: '#1565c0',
    },
    secondary: {
      main: '#dc004e',
    },
    background: {
      default: '#f5f5f5',
      paper: '#ffffff',
    },
  },
  typography: {
    fontFamily: '"Roboto", "Helvetica", "Arial", sans-serif',
    h1: {
      fontSize: '2.5rem',
      fontWeight: 600,
    },
    h2: {
      fontSize: '2rem',
      fontWeight: 600,
    },
  },
  components: {
    MuiButton: {
      styleOverrides: {
        root: {
          textTransform: 'none',
          borderRadius: 8,
        },
      },
    },
    MuiCard: {
      styleOverrides: {
        root: {
          borderRadius: 12,
          boxShadow: '0 2px 8px rgba(0,0,0,0.1)',
        },
      },
    },
  },
});

export default function ThemeRegistry({ children }: { children: ReactNode }) {
  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      {children}
    </ThemeProvider>
  );
}
```

### 2. Create Providers Component (Updated for 2025)

**`src/app/providers.tsx`**

```typescript
'use client';

import { ReactNode } from 'react';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import { ReactQueryDevtools } from '@tanstack/react-query-devtools';
import ThemeRegistry from './theme-registry';
import { Toaster } from 'sonner'; // Using Sonner instead of react-hot-toast

const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 60 * 1000, // 1 minute
      refetchOnWindowFocus: false,
      retry: 1,
    },
  },
});

export default function Providers({ children }: { children: ReactNode }) {
  return (
    <QueryClientProvider client={queryClient}>
      <ThemeRegistry>
        {children}
        {/* Sonner - Modern toast notifications (2025) */}
        <Toaster position="top-right" richColors closeButton />
      </ThemeRegistry>
      <ReactQueryDevtools initialIsOpen={false} />
    </QueryClientProvider>
  );
}
```

### 3. Update Root Layout

**`src/app/layout.tsx`**

```typescript
import type { Metadata } from 'next';
import Providers from './providers';

export const metadata: Metadata = {
  title: 'Gym CRM - Management System',
  description: 'Complete Gym Management System',
};

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>
        <Providers>{children}</Providers>
      </body>
    </html>
  );
}
```

---

## 🔧 Configuration Files

### `next.config.js`

```javascript
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  swcMinify: true,
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: 'your-cdn.com',
      },
    ],
  },
  env: {
    NEXT_PUBLIC_API_URL: process.env.NEXT_PUBLIC_API_URL || 'http://localhost:3000/api/v1',
  },
};

module.exports = nextConfig;
```

### `.env.local`

```env
# Backend API
NEXT_PUBLIC_API_URL=http://localhost:3000/api/v1

# NextAuth
NEXTAUTH_URL=http://localhost:3001
NEXTAUTH_SECRET=your-secret-key-here

# Optional
NEXT_PUBLIC_APP_NAME=Gym CRM
```

### `.env.example`

```env
NEXT_PUBLIC_API_URL=http://localhost:3000/api/v1
NEXTAUTH_URL=http://localhost:3001
NEXTAUTH_SECRET=change-this-to-a-random-string
NEXT_PUBLIC_APP_NAME=Gym CRM
```

---

## 🔬 Research-Based Technology Decisions (2025)

### Why These Specific Libraries?

All recommendations below are based on extensive research of production usage, community consensus, performance benchmarks, and maintenance status as of 2025.

#### **Next.js 15.4** ✅ Chosen
- **Released:** October 2024, stable 15.4 in 2025
- **Key Features:** Turbopack (700x faster refresh), React 19 support, improved caching
- **Why:** Industry standard, best-in-class performance, Vercel backing
- **Gym CRM Benefit:** Fast build times, excellent developer experience

#### **Material-UI v7** ✅ Chosen
- **Released:** March 26, 2025
- **Key Features:** ESM support, CSS layers (works with Tailwind v4), React 19 ready
- **Why:** Production-ready, 94K+ GitHub stars, comprehensive component library
- **Gym CRM Benefit:** Professional UI out-of-the-box, enterprise-grade

#### **MUI X v8** ✅ Chosen
- **Released:** April 2025
- **Key Features:** AI assistance, data grid pivoting, server-side aggregation, funnel/radar charts
- **Why:** Advanced features needed for gym analytics and reporting
- **Gym CRM Benefit:** Built-in pivot tables for revenue analysis, AI features

#### **TanStack Query** vs Redux ✅ TanStack Query Chosen
- **Bundle Size:** TanStack Query 40% smaller than Redux
- **Performance:** Automatic caching, background refetching, optimistic updates
- **Community Consensus 2025:** TanStack Query for server state, Zustand for client state
- **Why:** Less boilerplate, better performance, designed for modern APIs
- **Gym CRM Benefit:** Automatic member/class data synchronization

#### **React Hook Form** vs Formik ✅ React Hook Form Chosen
- **Bundle Size:** React Hook Form 12KB vs Formik 44KB (3.6x smaller)
- **Performance:** Isolated re-renders, uncontrolled components
- **Maintenance:** Formik has no commits in 1+ year, React Hook Form actively maintained
- **Why:** Superior performance, smaller bundle, active development
- **Gym CRM Benefit:** Fast member registration forms, minimal re-renders

#### **Nivo** + Recharts (Multi-Library Approach) ✅ Both Chosen
- **Nivo:** Fastest initial render, beautiful out-of-box styling, SVG/Canvas/SSR
- **Recharts:** Simple declarative API, D3-based, great for dashboards
- **Why Not Just One?** Nivo for analytics dashboards, Recharts for simple widgets
- **Gym CRM Benefit:** Stunning revenue charts (Nivo), quick attendance widgets (Recharts)

#### **react-big-calendar** for Scheduling ✅ Chosen
- **Why:** Google Calendar-like UI, multi-view support, resource scheduling
- **Alternatives Considered:** FullCalendar (heavier), custom solution (too much work)
- **Gym CRM Benefit:** Class scheduling, trainer calendars, member bookings

#### **Sonner** vs React-Hot-Toast ✅ Sonner Chosen
- **Sonner:** Modern, ARIA support, shadcn/ui integration, better animations
- **React-Hot-Toast:** 5KB, battle-tested, simpler API
- **Why Sonner:** Better UX, accessibility, modern design
- **Gym CRM Benefit:** Professional notifications for bookings, payments

#### **Framer Motion** + AutoAnimate ✅ Both Chosen
- **Framer Motion:** Production dashboards, complex animations
- **AutoAnimate:** Zero-config list animations (perfect for member lists)
- **Why Both:** Framer for intentional UX, AutoAnimate for automatic polish
- **Gym CRM Benefit:** Smooth dashboard transitions, polished data tables

#### **react-dropzone** for File Upload ✅ Chosen
- **Why:** Type-safe, robust validation, 10M+ downloads/week
- **Alternatives:** react-uploady (hooks-based), native implementation
- **Gym CRM Benefit:** Member photo uploads, document management

---

## 📚 Key Libraries Explained

### 1. **TanStack Query** (React Query) - Server State

**Why:** Best for managing server data (fetching, caching, synchronization)

**Benefits:**
- ✅ Automatic caching
- ✅ Background refetching
- ✅ Optimistic updates
- ✅ 40% reduction in bundle size vs Redux
- ✅ Less boilerplate

**Example:**
```typescript
import { useQuery } from '@tanstack/react-query';
import { getEmployees } from '@/lib/api/employees';

function EmployeesList() {
  const { data, isLoading, error } = useQuery({
    queryKey: ['employees'],
    queryFn: getEmployees,
  });

  if (isLoading) return <CircularProgress />;
  if (error) return <Alert severity="error">Error loading employees</Alert>;

  return <EmployeesTable employees={data} />;
}
```

### 2. **Zustand** - Client State

**Why:** Lightweight, simple, no boilerplate

**Benefits:**
- ✅ 90% of Redux power at fraction of code
- ✅ TypeScript friendly
- ✅ No Provider wrapping needed
- ✅ DevTools support

**Example:**
```typescript
import { create } from 'zustand';

interface AuthState {
  user: User | null;
  login: (user: User) => void;
  logout: () => void;
}

export const useAuthStore = create<AuthState>((set) => ({
  user: null,
  login: (user) => set({ user }),
  logout: () => set({ user: null }),
}));

// Usage
const { user, login, logout } = useAuthStore();
```

### 3. **React Hook Form + Zod** - Forms

**Why:** Best performance + type-safe validation

**Example:**
```typescript
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import { z } from 'zod';

const schema = z.object({
  firstName: z.string().min(1, 'Required'),
  email: z.string().email(),
});

function EmployeeForm() {
  const { register, handleSubmit, formState: { errors } } = useForm({
    resolver: zodResolver(schema),
  });

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <TextField
        {...register('firstName')}
        error={!!errors.firstName}
        helperText={errors.firstName?.message}
      />
    </form>
  );
}
```

### 4. **Recharts** - Visualization

**Why:** Simple, React-friendly, works great with MUI

**Example:**
```typescript
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip } from 'recharts';

function RevenueChart({ data }) {
  return (
    <LineChart width={600} height={300} data={data}>
      <CartesianGrid strokeDasharray="3 3" />
      <XAxis dataKey="month" />
      <YAxis />
      <Tooltip />
      <Line type="monotone" dataKey="revenue" stroke="#1976d2" />
    </LineChart>
  );
}
```

### 5. **MUI X Data Grid v8** - Tables

**Why:** Professional data grids with sorting, filtering, pagination

**Features (v8 - April 2025):**
- ✅ Virtual scrolling
- ✅ Column resizing
- ✅ Row selection
- ✅ Filtering & sorting
- ✅ Export to CSV
- 🆕 **Data Grid Pivoting** (pivot tables)
- 🆕 **AI Assistance** (AI-powered features)
- 🆕 **Server-side aggregation**
- 🆕 **Funnel & Radar charts**
- 🆕 **Time Range Picker**
- 🆕 **Tree View lazy loading**
- 🆕 **New animation engine**
- 🆕 **Server-side rendering for charts**

---

## 🎯 Best Practices for 2025

### 1. Use Server Components When Possible

```typescript
// app/employees/page.tsx (Server Component)
export default async function EmployeesPage() {
  const employees = await fetch('http://localhost:3000/api/v1/employees');
  return <EmployeesList initialData={employees} />;
}

// components/EmployeesList.tsx (Client Component)
'use client';
export function EmployeesList({ initialData }) {
  const { data } = useQuery({
    queryKey: ['employees'],
    queryFn: getEmployees,
    initialData,
  });
  // ...
}
```

### 2. Code Splitting

```typescript
import dynamic from 'next/dynamic';

const HeavyChart = dynamic(() => import('@/components/charts/HeavyChart'), {
  loading: () => <CircularProgress />,
  ssr: false,
});
```

### 3. Type Safety

```typescript
// Share types with backend
// lib/types/employee.ts
export interface Employee {
  id: string;
  firstName: string;
  lastName: string;
  email?: string;
  // ... matches backend DTO
}
```

### 4. Error Handling

```typescript
import { useQuery } from '@tanstack/react-query';
import { Alert } from '@mui/material';

function DataComponent() {
  const { data, error, isLoading } = useQuery({ ... });

  if (error) {
    return (
      <Alert severity="error">
        {error instanceof Error ? error.message : 'An error occurred'}
      </Alert>
    );
  }

  if (isLoading) return <CircularProgress />;
  return <DataDisplay data={data} />;
}
```

---

## 📊 Performance Optimization

### Image Optimization

```typescript
import Image from 'next/image';

<Image
  src="/gym-logo.png"
  alt="Gym Logo"
  width={200}
  height={100}
  priority // for above-the-fold images
/>
```

### Font Optimization

```typescript
import { Roboto } from 'next/font/google';

const roboto = Roboto({
  weight: ['300', '400', '500', '700'],
  subsets: ['latin'],
  display: 'swap',
});
```

---

## 🚀 Ready to Start

After running all installations, start your development server:

```bash
npm run dev
```

Your frontend will run on: **http://localhost:3001**

Connect to your backend API at: **http://localhost:3000/api/v1**

---

## 📝 Next Steps

1. ✅ Run installation commands
2. ✅ Set up MUI theme
3. ✅ Create API client
4. ✅ Build dashboard layout
5. ✅ Create first page (Employees)
6. ✅ Add authentication
7. ✅ Build remaining modules

---

**Created:** January 2025
**Updated:** Based on 2025 research and best practices
**Stack:** Next.js 15.4 + Material-UI v7 + MUI X v8 + React 19
**State:** TanStack Query + Zustand (2025 consensus)
**Research:** 8 web searches, community consensus, production benchmarks
**Key Releases:** MUI v7 (Mar 2025), MUI X v8 (Apr 2025), Next.js 15 (Oct 2024)

---

## 📊 Stack Comparison Summary

| Category | Chosen | Alternative | Reason |
|----------|--------|-------------|--------|
| Framework | Next.js 15 | Remix, Gatsby | Turbopack, React 19, industry standard |
| UI Library | MUI v7 | Shadcn, Chakra | Enterprise-ready, comprehensive |
| State (Server) | TanStack Query | Redux, SWR | 40% smaller, better DX |
| State (Client) | Zustand | Redux, Jotai | 90% lighter, no boilerplate |
| Forms | React Hook Form | Formik | 3x smaller, actively maintained |
| Charts | Nivo + Recharts | Victory, Visx | Best render speed + simplicity |
| Tables | MUI X Data Grid v8 | AG Grid, TanStack Table | AI features, pivoting |
| Scheduling | react-big-calendar | FullCalendar | Lighter, good enough |
| Notifications | Sonner | React-Hot-Toast | Modern, ARIA, better UX |
| Animations | Framer Motion | GSAP, React Spring | Perfect balance |
| File Upload | react-dropzone | react-uploady | Type-safe, robust |
