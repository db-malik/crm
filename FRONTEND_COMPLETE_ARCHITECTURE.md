# 🏗️ Gym CRM Frontend - Complete Architecture & Technical Specification
## Next.js 15 + Material-UI v7 + Multi-Language + Theming

**Document Version:** 2.0
**Created:** January 2025
**Last Updated:** January 2025
**Research-Based:** 8 web searches, 2025 best practices

---

## 📋 Table of Contents

1. [Technology Stack](#technology-stack)
2. [Project Structure](#project-structure)
3. [Complete UI Component Library](#complete-ui-component-library)
4. [Theming System (Light/Dark)](#theming-system-lightdark)
5. [Translation System (French/English)](#translation-system-frenchenglish)
6. [State Management Architecture](#state-management-architecture)
7. [API Integration Layer](#api-integration-layer)
8. [Routing & Navigation](#routing--navigation)
9. [Authentication & Authorization](#authentication--authorization)
10. [Performance Optimization](#performance-optimization)

---

## 🚀 Technology Stack

### Core Framework & UI
```yaml
Framework: Next.js 15.4
  - App Router (React Server Components)
  - Turbopack (700x faster than webpack)
  - React 19 support
  - Edge Runtime capabilities

UI Library: Material-UI (MUI) v7.0.1
  - Released: March 26, 2025
  - ESM support
  - CSS layers compatibility
  - React 19 ready
  - 94K+ GitHub stars

MUI X: v8.0.0
  - Released: April 2025
  - AI assistance features
  - Data Grid pivoting
  - Server-side aggregation
  - Funnel & Radar charts
  - Time Range Picker
  - Tree View lazy loading
  - New animation engine
```

### State Management (2025 Best Practice)
```yaml
Server State: TanStack Query v5.62.0
  - 40% smaller bundle than Redux
  - Automatic caching
  - Background refetching
  - Optimistic updates
  - DevTools included

Client State: Zustand v5.0.0
  - 90% lighter than Redux
  - No boilerplate
  - TypeScript-first
  - DevTools support

URL State: nuqs v2.2.0
  - Type-safe URL params
  - React hooks for URL state

Form State: React Hook Form v7.53.0
  - 12KB vs Formik 44KB (3.6x smaller)
  - Isolated re-renders
  - Active maintenance
```

### Data Visualization
```yaml
Charts:
  - Nivo v0.87.0 (beautiful, modern, fast render)
  - Recharts v2.15.0 (simple dashboards)
  - TanStack Charts (financial data)

Scheduling & Calendar:
  - react-big-calendar v1.15.0 (Google Calendar-like)
  - react-day-picker v9.3.0 (6M+ downloads/week)
  - MUI X v8 Date Pickers (Time Range support)
```

### Forms & Validation
```yaml
Forms: React Hook Form v7.53.0
Validation: Zod v3.23.0
Resolvers: @hookform/resolvers v3.9.0
```

### Animations & Interactions
```yaml
UI Animations: Framer Motion v11.15.0
Auto Animations: AutoAnimate v0.8.2
Physics-Based: React Spring (optional)
```

### Utilities & Tools
```yaml
HTTP Client: Axios v1.7.0
Date Utilities: date-fns v4.1.0
Number Formatting: numeral v2.0.6
Icons: Lucide React v0.462.0
Notifications: Sonner v1.7.0 (modern, ARIA support)
File Upload: react-dropzone v14.3.5
QR Codes: react-qr-code v2.0.15
Class Utilities: clsx v2.1.0
```

### Authentication
```yaml
Auth: NextAuth.js v5.0.0
Cookies: js-cookie v3.0.5
```

### Development Tools
```yaml
Language: TypeScript 5.7.0
Linting: ESLint 9.0.0
Formatting: Prettier 3.3.0
Package Manager: npm
```

---

## 📁 Project Structure

```
frontend/
├── .env.local                          # Environment variables
├── .env.example
├── next.config.js                      # Next.js configuration
├── tsconfig.json                       # TypeScript configuration
├── package.json
├── middleware.ts                       # Edge middleware (auth, subdomain)
│
├── public/
│   ├── locales/                        # Translation files
│   │   ├── en/
│   │   │   ├── common.json
│   │   │   ├── dashboard.json
│   │   │   ├── planning.json
│   │   │   ├── employees.json
│   │   │   ├── timesheets.json
│   │   │   ├── absences.json
│   │   │   ├── settings.json
│   │   │   └── errors.json
│   │   └── fr/
│   │       ├── common.json
│   │       ├── dashboard.json
│   │       ├── planning.json
│   │       ├── employees.json
│   │       ├── timesheets.json
│   │       ├── absences.json
│   │       ├── settings.json
│   │       └── errors.json
│   ├── images/
│   ├── fonts/
│   └── favicon.ico
│
└── src/
    ├── app/                            # Next.js 15 App Router
    │   ├── [lang]/                     # Language dynamic route
    │   │   ├── (auth)/                 # Authentication group
    │   │   │   ├── layout.tsx
    │   │   │   ├── login/
    │   │   │   │   └── page.tsx
    │   │   │   ├── register/
    │   │   │   │   └── page.tsx
    │   │   │   ├── forgot-password/
    │   │   │   │   └── page.tsx
    │   │   │   └── reset-password/
    │   │   │       └── [token]/
    │   │   │           └── page.tsx
    │   │   │
    │   │   ├── (dashboard)/            # Main dashboard group
    │   │   │   ├── layout.tsx          # Dashboard layout
    │   │   │   ├── page.tsx            # Dashboard home
    │   │   │   │
    │   │   │   ├── planning/
    │   │   │   │   ├── page.tsx
    │   │   │   │   ├── schedule/
    │   │   │   │   ├── shifts/
    │   │   │   │   ├── open-shifts/
    │   │   │   │   ├── conflicts/
    │   │   │   │   └── rosters/
    │   │   │   │
    │   │   │   ├── employees/
    │   │   │   │   ├── page.tsx
    │   │   │   │   ├── [id]/
    │   │   │   │   └── new/
    │   │   │   │
    │   │   │   ├── timesheet/
    │   │   │   │   ├── page.tsx
    │   │   │   │   ├── clock/
    │   │   │   │   ├── kiosks/
    │   │   │   │   └── clock-settings/
    │   │   │   │
    │   │   │   ├── absences/
    │   │   │   │   ├── page.tsx
    │   │   │   │   ├── new/
    │   │   │   │   └── [id]/
    │   │   │   │
    │   │   │   ├── insights/
    │   │   │   │   ├── page.tsx
    │   │   │   │   ├── performance/
    │   │   │   │   ├── scheduled-vs-worked/
    │   │   │   │   └── sentiment/
    │   │   │   │
    │   │   │   ├── reports/
    │   │   │   │   ├── page.tsx
    │   │   │   │   ├── favorites/
    │   │   │   │   └── recurring/
    │   │   │   │
    │   │   │   └── settings/
    │   │   │       ├── layout.tsx
    │   │   │       ├── page.tsx
    │   │   │       ├── account/
    │   │   │       ├── departments/
    │   │   │       ├── teams/
    │   │   │       ├── users/
    │   │   │       └── security/
    │   │   │
    │   │   ├── layout.tsx              # Root language layout
    │   │   └── page.tsx                # Root redirect
    │   │
    │   ├── api/                        # API routes
    │   │   ├── auth/
    │   │   ├── proxy/
    │   │   └── upload/
    │   │
    │   ├── layout.tsx                  # Root layout (providers)
    │   ├── page.tsx                    # Language redirect
    │   ├── error.tsx
    │   ├── not-found.tsx
    │   └── providers.tsx               # Client providers
    │
    ├── components/
    │   ├── layout/                     # Layout components
    │   ├── dashboard/                  # Dashboard widgets
    │   ├── planning/                   # Planning components
    │   ├── employees/                  # Employee components
    │   ├── timesheet/                  # Timesheet components
    │   ├── absences/                   # Absence components
    │   ├── insights/                   # Analytics components
    │   ├── reports/                    # Report components
    │   ├── settings/                   # Settings components
    │   ├── forms/                      # Form components
    │   ├── tables/                     # Table components
    │   ├── charts/                     # Chart components
    │   ├── modals/                     # Modal components
    │   ├── ui/                         # Base UI components (MUI)
    │   └── shared/                     # Shared components
    │
    ├── lib/
    │   ├── api/                        # API client
    │   │   ├── client.ts
    │   │   ├── employees.ts
    │   │   ├── shifts.ts
    │   │   ├── timesheets.ts
    │   │   ├── absences.ts
    │   │   └── reports.ts
    │   ├── hooks/                      # Custom hooks
    │   │   ├── useAuth.ts
    │   │   ├── useTranslation.ts
    │   │   ├── useTheme.ts
    │   │   └── useToast.ts
    │   ├── utils/
    │   │   ├── date.ts
    │   │   ├── format.ts
    │   │   └── validation.ts
    │   ├── validations/                # Zod schemas
    │   ├── constants/
    │   └── i18n/                       # Internationalization
    │       ├── config.ts
    │       ├── translations.ts
    │       └── languages.ts
    │
    ├── types/                          # TypeScript types
    │   ├── api/
    │   ├── models/
    │   ├── components/
    │   └── index.ts
    │
    ├── store/                          # Zustand stores
    │   ├── slices/
    │   │   ├── authSlice.ts
    │   │   ├── themeSlice.ts
    │   │   ├── languageSlice.ts
    │   │   └── uiSlice.ts
    │   └── index.ts
    │
    ├── styles/
    │   ├── globals.css
    │   ├── theme.ts                    # MUI theme configuration
    │   └── themes/
    │       ├── lightTheme.ts
    │       └── darkTheme.ts
    │
    └── config/
        ├── site.ts
        ├── navigation.ts
        └── languages.ts
```

---

## 🎨 Complete UI Component Library

### Base UI Components (MUI v7 + Custom)

```typescript
// src/components/ui/

// Form Controls
export { Button } from '@mui/material'              // MUI Button
export { TextField } from '@mui/material'          // Text input
export { Select } from '@mui/material'             // Select dropdown
export { Autocomplete } from '@mui/material'       // Autocomplete
export { Checkbox } from '@mui/material'           // Checkbox
export { Radio, RadioGroup } from '@mui/material'  // Radio buttons
export { Switch } from '@mui/material'             // Toggle switch
export { Slider } from '@mui/material'             // Slider
export { Rating } from '@mui/material'             // Star rating

// Data Display
export { Card, CardContent, CardHeader, CardActions } from '@mui/material'
export { Chip } from '@mui/material'                // Badge/Tag
export { Avatar, AvatarGroup } from '@mui/material' // User avatar
export { Badge } from '@mui/material'               // Notification badge
export { Tooltip } from '@mui/material'             // Hover tooltip
export { Alert } from '@mui/material'               // Alert messages
export { Skeleton } from '@mui/material'            // Loading skeleton
export { Divider } from '@mui/material'             // Horizontal line
export { List, ListItem, ListItemText } from '@mui/material'
export { Table, TableBody, TableCell, TableHead, TableRow } from '@mui/material'

// Navigation
export { Tabs, Tab } from '@mui/material'          // Tab navigation
export { Breadcrumbs } from '@mui/material'        // Breadcrumb trail
export { Stepper, Step, StepLabel } from '@mui/material' // Step indicator
export { Pagination } from '@mui/material'          // Page pagination
export { BottomNavigation } from '@mui/material'    // Mobile bottom nav

// Feedback
export { Dialog, DialogTitle, DialogContent, DialogActions } from '@mui/material'
export { Snackbar } from '@mui/material'           // Toast (use Sonner)
export { CircularProgress, LinearProgress } from '@mui/material'
export { Backdrop } from '@mui/material'

// Layout
export { Container } from '@mui/material'
export { Grid } from '@mui/material'
export { Stack } from '@mui/material'
export { Box } from '@mui/material'
export { Paper } from '@mui/material'
export { AppBar, Toolbar } from '@mui/material'
export { Drawer } from '@mui/material'

// MUI X Components
export { DataGrid } from '@mui/x-data-grid'        // Data table
export { DatePicker } from '@mui/x-date-pickers'   // Date picker
export { TimePicker } from '@mui/x-date-pickers'   // Time picker
export { DateTimePicker } from '@mui/x-date-pickers' // DateTime picker
export { DateRangePicker } from '@mui/x-date-pickers' // Date range (v8)
export { TimeRangePicker } from '@mui/x-date-pickers' // Time range (v8 NEW)

// Icons
export * from '@mui/icons-material'                 // All MUI icons
export * from 'lucide-react'                        // Lucide icons (modern)
```

### Custom Gym CRM Components

```typescript
// src/components/

// Dashboard Components
├── dashboard/
│   ├── WelcomeCard.tsx                // Welcome message card
│   ├── QuickStatsGrid.tsx             // KPI stats grid
│   ├── RecentActivityFeed.tsx         // Activity timeline
│   ├── UpcomingShiftsWidget.tsx       // Next shifts preview
│   ├── TimesheetSummaryWidget.tsx     // Hours summary
│   ├── AbsencesCalendarWidget.tsx     // Mini calendar
│   ├── TeamPresenceWidget.tsx         // Who's working now
│   └── ActionButtonsGrid.tsx          // Quick actions

// Planning Components
├── planning/
│   ├── ScheduleCalendar.tsx           // Main schedule calendar
│   ├── WeekView.tsx                   // Week schedule view
│   ├── MonthView.tsx                  // Month schedule view
│   ├── DayView.tsx                    // Day schedule view
│   ├── EmployeeView.tsx               // Employee-specific view
│   ├── TeamView.tsx                   // Team view
│   ├── ShiftCard.tsx                  // Shift information card
│   ├── ShiftForm.tsx                  // Create/edit shift
│   ├── ShiftTemplateSelector.tsx      // Template picker
│   ├── DragDropShiftEditor.tsx        // Drag & drop schedule
│   ├── ConflictIndicator.tsx          // Conflict warning
│   ├── ConflictDialog.tsx             // Conflict resolution
│   ├── AvailabilityChecker.tsx        // Check availability
│   ├── OpenShiftCard.tsx              // Open shift display
│   ├── ShiftAssignmentDialog.tsx      // Assign employees
│   ├── RosterTemplateCard.tsx         // Roster template
│   └── ViewModeSwitcher.tsx           // Switch view modes

// Employee Components
├── employees/
│   ├── EmployeeList.tsx               // Employee list/grid
│   ├── EmployeeCard.tsx               // Employee card
│   ├── EmployeeGrid.tsx               // Grid view
│   ├── EmployeeTable.tsx              // Table view (MUI X)
│   ├── EmployeeForm.tsx               // Create/edit employee
│   ├── EmployeeProfile.tsx            // Profile view
│   ├── EmployeeAvatar.tsx             // Avatar with status
│   ├── EmployeeTabs.tsx               // Profile tabs
│   ├── TeamAssignmentForm.tsx         // Assign teams
│   ├── SkillsEditor.tsx               // Manage skills
│   ├── ContractEditor.tsx             // Manage contracts
│   ├── TimeOffBalanceCard.tsx         // Balance display
│   ├── UpcomingAbsencesCard.tsx       // Upcoming time off
│   ├── HoursDistributionChart.tsx     // Hours breakdown
│   ├── PerformanceChart.tsx           // Performance stats
│   └── StatusBadge.tsx                // Status indicator

// Timesheet Components
├── timesheet/
│   ├── TimesheetCalendar.tsx          // Timesheet calendar
│   ├── TimesheetTable.tsx             // Table view
│   ├── TimesheetEntry.tsx             // Single entry
│   ├── TimesheetForm.tsx              // Add/edit entry
│   ├── ClockInOutButton.tsx           // Clock button
│   ├── ClockStatus.tsx                // Current status
│   ├── ClockHistory.tsx               // Recent clocks
│   ├── CurrentlyClockedList.tsx       // Who's clocked in
│   ├── BreakCalculator.tsx            // Break calc display
│   ├── ApprovalButton.tsx             // Approve button
│   ├── BatchApprovalDialog.tsx        // Batch approval
│   ├── KioskPinPad.tsx                // Kiosk PIN entry
│   ├── KioskCard.tsx                  // Kiosk info card
│   ├── GeofenceMap.tsx                // Location map
│   └── ConflictWarning.tsx            // Time conflict

// Absence Components
├── absences/
│   ├── AbsenceCalendar.tsx            // 2-month calendar
│   ├── AbsenceCard.tsx                // Absence info card
│   ├── AbsenceForm.tsx                // Request absence
│   ├── AbsenceTypeSelector.tsx        // Type dropdown
│   ├── DateRangeSelector.tsx          // Date range picker
│   ├── PartialDaySelector.tsx         // Partial day options
│   ├── BalanceIndicator.tsx           // Time off balance
│   ├── EmployeeAbsenceTable.tsx       // Employee selector
│   ├── ApprovalWorkflow.tsx           // Approval UI
│   ├── AbsenceFilters.tsx             // Filter controls
│   ├── AbsenteeList.tsx               // Absentee tracking
│   ├── ColorLegend.tsx                // Color code legend
│   └── ExportToCalendar.tsx           // iCal export

// Insights Components
├── insights/
│   ├── PerformanceChart.tsx           // Performance graph
│   ├── ScheduledVsWorkedChart.tsx     // Comparison chart
│   ├── SentimentTracker.tsx           // Mood tracking
│   ├── KPICard.tsx                    // KPI display
│   ├── TrendIndicator.tsx             // Up/down trend
│   ├── ComparisonChart.tsx            // Period comparison
│   ├── HeatmapChart.tsx               // Heatmap
│   └── MetricsGrid.tsx                // Metrics dashboard

// Report Components
├── reports/
│   ├── ReportCard.tsx                 // Report card
│   ├── ReportBuilder.tsx              // Build report
│   ├── ReportTypeSelector.tsx         // Select type
│   ├── ReportParametersForm.tsx       // Parameters
│   ├── ReportViewer.tsx               // View report
│   ├── ReportTable.tsx                // Tabular data
│   ├── ReportChart.tsx                // Chart view
│   ├── ExportButtons.tsx              // Export options
│   ├── FavoriteReportsList.tsx        // Favorites
│   ├── RecurringReportsList.tsx       // Scheduled
│   └── ReportHistory.tsx              // Past reports

// Settings Components
├── settings/
│   ├── SettingsSidebar.tsx            // Settings nav
│   ├── DepartmentForm.tsx             // Department form
│   ├── DepartmentCard.tsx             // Department card
│   ├── TeamForm.tsx                   // Team form
│   ├── TeamCard.tsx                   // Team card
│   ├── LocationForm.tsx               // Location form
│   ├── ShiftTemplateForm.tsx          // Shift template
│   ├── ShiftTemplateCard.tsx          // Template card
│   ├── ContractTypeForm.tsx           // Contract type
│   ├── SkillForm.tsx                  // Skill form
│   ├── SkillGroupForm.tsx             // Skill group
│   ├── HolidayImporter.tsx            // Import holidays
│   ├── CustomFieldForm.tsx            // Custom field
│   ├── PermissionGroupForm.tsx        // Permissions
│   ├── UserInviteForm.tsx             // Invite users
│   └── SubscriptionCard.tsx           // Subscription info

// Form Components
├── forms/
│   ├── FormField.tsx                  // Form field wrapper
│   ├── FormSection.tsx                // Section grouping
│   ├── FormActions.tsx                // Submit/Cancel
│   ├── FormError.tsx                  // Error display
│   ├── FormSuccess.tsx                // Success message
│   ├── MultiStepForm.tsx              // Multi-step wizard
│   ├── FileUploadZone.tsx             // Drag & drop upload
│   ├── ImageUpload.tsx                // Image upload
│   ├── AvatarUpload.tsx               // Avatar upload
│   ├── ColorPicker.tsx                // Color selector
│   ├── TagInput.tsx                   // Tag input
│   ├── RichTextEditor.tsx             // Rich text
│   └── SearchableSelect.tsx           // Search dropdown

// Table Components
├── tables/
│   ├── DataTable.tsx                  // Base table
│   ├── ServerDataTable.tsx            // Server-side table
│   ├── TablePagination.tsx            // Pagination
│   ├── TableFilters.tsx               // Filter UI
│   ├── TableSearch.tsx                // Search box
│   ├── SortableHeader.tsx             // Sortable columns
│   ├── BulkActionsBar.tsx             // Bulk actions
│   ├── TableExport.tsx                // Export button
│   └── EmptyTableState.tsx            // Empty state

// Chart Components
├── charts/
│   ├── LineChart.tsx                  // Line chart (Nivo)
│   ├── BarChart.tsx                   // Bar chart (Nivo)
│   ├── PieChart.tsx                   // Pie chart (Nivo)
│   ├── AreaChart.tsx                  // Area chart (Recharts)
│   ├── DonutChart.tsx                 // Donut chart
│   ├── RadarChart.tsx                 // Radar chart (MUI X v8)
│   ├── FunnelChart.tsx                // Funnel chart (MUI X v8)
│   ├── HeatmapChart.tsx               // Heatmap
│   ├── TimeSeriesChart.tsx            // Time series
│   └── ChartLegend.tsx                // Chart legend

// Modal Components
├── modals/
│   ├── ConfirmDialog.tsx              // Confirmation
│   ├── DeleteDialog.tsx               // Delete confirm
│   ├── FormDialog.tsx                 // Form in modal
│   ├── FullScreenDialog.tsx           // Fullscreen
│   ├── SlideOver.tsx                  // Side panel
│   └── ImagePreview.tsx               // Image viewer

// Layout Components
├── layout/
│   ├── Header.tsx                     // Top header
│   ├── Sidebar.tsx                    // Main sidebar
│   ├── MobileSidebar.tsx              // Mobile drawer
│   ├── Footer.tsx                     // Footer
│   ├── Breadcrumbs.tsx                // Breadcrumb nav
│   ├── PageHeader.tsx                 // Page title/actions
│   ├── Container.tsx                  // Page container
│   ├── Section.tsx                    // Page section
│   ├── NotificationBell.tsx           // Notifications
│   ├── UserMenu.tsx                   // User dropdown
│   ├── ThemeToggle.tsx                // Light/dark toggle
│   ├── LanguageSwitcher.tsx           // FR/EN switcher
│   └── SearchCommand.tsx              // Command palette

// Shared Components
└── shared/
    ├── Loading.tsx                    // Loading spinner
    ├── LoadingSkeleton.tsx            // Skeleton loader
    ├── ErrorBoundary.tsx              // Error boundary
    ├── ErrorState.tsx                 // Error display
    ├── EmptyState.tsx                 // Empty state
    ├── NoResults.tsx                  // No search results
    ├── StatusBadge.tsx                // Status badge
    ├── ColorTag.tsx                   // Color-coded tag
    ├── DateRangePicker.tsx            // Date range
    ├── BackButton.tsx                 // Back navigation
    ├── CopyButton.tsx                 // Copy to clipboard
    ├── QRCode.tsx                     // QR code display
    └── ConfettiEffect.tsx             // Celebration effect
```

---

## 🎨 Theming System (Light/Dark)

### Theme Configuration

**`src/styles/theme.ts`**
```typescript
import { createTheme, ThemeOptions } from '@mui/material/styles'
import { frFR, enUS } from '@mui/material/locale'

// Common theme options
const commonOptions: ThemeOptions = {
  typography: {
    fontFamily: '"Inter", "Roboto", "Helvetica", "Arial", sans-serif',
    h1: {
      fontSize: '2.5rem',
      fontWeight: 700,
      lineHeight: 1.2,
    },
    h2: {
      fontSize: '2rem',
      fontWeight: 600,
      lineHeight: 1.3,
    },
    h3: {
      fontSize: '1.75rem',
      fontWeight: 600,
      lineHeight: 1.4,
    },
    h4: {
      fontSize: '1.5rem',
      fontWeight: 600,
      lineHeight: 1.4,
    },
    h5: {
      fontSize: '1.25rem',
      fontWeight: 600,
      lineHeight: 1.5,
    },
    h6: {
      fontSize: '1rem',
      fontWeight: 600,
      lineHeight: 1.5,
    },
    button: {
      textTransform: 'none',
      fontWeight: 500,
    },
  },
  shape: {
    borderRadius: 12,
  },
  components: {
    MuiButton: {
      styleOverrides: {
        root: {
          borderRadius: 8,
          padding: '10px 24px',
          boxShadow: 'none',
          '&:hover': {
            boxShadow: 'none',
          },
        },
        contained: {
          '&:hover': {
            boxShadow: '0 2px 8px rgba(0,0,0,0.15)',
          },
        },
      },
    },
    MuiCard: {
      styleOverrides: {
        root: {
          borderRadius: 16,
          boxShadow: '0 1px 3px rgba(0,0,0,0.05)',
          '&:hover': {
            boxShadow: '0 4px 12px rgba(0,0,0,0.1)',
          },
        },
      },
    },
    MuiTextField: {
      styleOverrides: {
        root: {
          '& .MuiOutlinedInput-root': {
            borderRadius: 8,
          },
        },
      },
    },
    MuiChip: {
      styleOverrides: {
        root: {
          borderRadius: 8,
          fontWeight: 500,
        },
      },
    },
  },
}

// Light theme
export const lightTheme = createTheme({
  ...commonOptions,
  palette: {
    mode: 'light',
    primary: {
      main: '#2563eb',      // Blue 600
      light: '#3b82f6',     // Blue 500
      dark: '#1d4ed8',      // Blue 700
      contrastText: '#ffffff',
    },
    secondary: {
      main: '#7c3aed',      // Violet 600
      light: '#8b5cf6',     // Violet 500
      dark: '#6d28d9',      // Violet 700
      contrastText: '#ffffff',
    },
    error: {
      main: '#dc2626',      // Red 600
      light: '#ef4444',     // Red 500
      dark: '#b91c1c',      // Red 700
    },
    warning: {
      main: '#f59e0b',      // Amber 500
      light: '#fbbf24',     // Amber 400
      dark: '#d97706',      // Amber 600
    },
    info: {
      main: '#0891b2',      // Cyan 600
      light: '#06b6d4',     // Cyan 500
      dark: '#0e7490',      // Cyan 700
    },
    success: {
      main: '#059669',      // Emerald 600
      light: '#10b981',     // Emerald 500
      dark: '#047857',      // Emerald 700
    },
    background: {
      default: '#f8fafc',   // Slate 50
      paper: '#ffffff',
    },
    text: {
      primary: '#0f172a',   // Slate 900
      secondary: '#64748b', // Slate 500
      disabled: '#cbd5e1',  // Slate 300
    },
    divider: '#e2e8f0',     // Slate 200
  },
}, enUS)

// Dark theme
export const darkTheme = createTheme({
  ...commonOptions,
  palette: {
    mode: 'dark',
    primary: {
      main: '#3b82f6',      // Blue 500
      light: '#60a5fa',     // Blue 400
      dark: '#2563eb',      // Blue 600
      contrastText: '#ffffff',
    },
    secondary: {
      main: '#8b5cf6',      // Violet 500
      light: '#a78bfa',     // Violet 400
      dark: '#7c3aed',      // Violet 600
      contrastText: '#ffffff',
    },
    error: {
      main: '#ef4444',      // Red 500
      light: '#f87171',     // Red 400
      dark: '#dc2626',      // Red 600
    },
    warning: {
      main: '#fbbf24',      // Amber 400
      light: '#fcd34d',     // Amber 300
      dark: '#f59e0b',      // Amber 500
    },
    info: {
      main: '#06b6d4',      // Cyan 500
      light: '#22d3ee',     // Cyan 400
      dark: '#0891b2',      // Cyan 600
    },
    success: {
      main: '#10b981',      // Emerald 500
      light: '#34d399',     // Emerald 400
      dark: '#059669',      // Emerald 600
    },
    background: {
      default: '#0f172a',   // Slate 900
      paper: '#1e293b',     // Slate 800
    },
    text: {
      primary: '#f1f5f9',   // Slate 100
      secondary: '#94a3b8', // Slate 400
      disabled: '#475569',  // Slate 600
    },
    divider: '#334155',     // Slate 700
  },
}, enUS)

// French variants
export const lightThemeFR = createTheme(lightTheme, frFR)
export const darkThemeFR = createTheme(darkTheme, frFR)
```

**`src/styles/themes/lightTheme.ts`**
```typescript
export const lightPalette = {
  // Primary Colors (Blue)
  primary: {
    50: '#eff6ff',
    100: '#dbeafe',
    200: '#bfdbfe',
    300: '#93c5fd',
    400: '#60a5fa',
    500: '#3b82f6',
    600: '#2563eb',  // Main
    700: '#1d4ed8',
    800: '#1e40af',
    900: '#1e3a8a',
  },

  // Shift Color Codes (from Shiftbase)
  shifts: {
    regular: '#10b981',      // Green - Regular shifts
    ramadanEvening: '#8b5cf6', // Purple - Special shifts
    ramadanDay: '#ef4444',    // Red - Day shifts
    security: '#ec4899',      // Pink - Security
    staff: '#f59e0b',         // Orange - Staff
    service: '#3b82f6',       // Blue - Service
  },

  // Absence Color Codes
  absences: {
    vacation: '#fbbf24',      // Yellow - Vacation
    sick: '#ef4444',          // Red - Sick leave
    publicHoliday: '#8b5cf6', // Purple - Public holiday
    special: '#06b6d4',       // Cyan - Special leave
    maternity: '#ec4899',     // Pink - Maternity
  },

  // Status Colors
  status: {
    active: '#10b981',        // Green
    inactive: '#94a3b8',      // Gray
    pending: '#f59e0b',       // Orange
    rejected: '#ef4444',      // Red
    approved: '#10b981',      // Green
  },
}
```

**`src/styles/themes/darkTheme.ts`**
```typescript
export const darkPalette = {
  // Same structure as light theme but with dark-mode friendly colors
  primary: {
    50: '#1e293b',
    100: '#334155',
    200: '#475569',
    300: '#64748b',
    400: '#94a3b8',
    500: '#cbd5e1',
    600: '#e2e8f0',
    700: '#f1f5f9',
    800: '#f8fafc',
    900: '#ffffff',
  },

  // Brighter colors for dark mode
  shifts: {
    regular: '#34d399',      // Brighter green
    ramadanEvening: '#a78bfa',
    ramadanDay: '#f87171',
    security: '#f472b6',
    staff: '#fbbf24',
    service: '#60a5fa',
  },

  absences: {
    vacation: '#fcd34d',
    sick: '#f87171',
    publicHoliday: '#a78bfa',
    special: '#22d3ee',
    maternity: '#f472b6',
  },

  status: {
    active: '#34d399',
    inactive: '#64748b',
    pending: '#fbbf24',
    rejected: '#f87171',
    approved: '#34d399',
  },
}
```

### Theme Provider Setup

**`src/app/providers.tsx`**
```typescript
'use client'

import { ReactNode, useMemo } from 'react'
import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
import { ReactQueryDevtools } from '@tanstack/react-query-devtools'
import { ThemeProvider, CssBaseline } from '@mui/material'
import { LocalizationProvider } from '@mui/x-date-pickers'
import { AdapterDateFns } from '@mui/x-date-pickers/AdapterDateFns'
import { Toaster } from 'sonner'
import { useStore } from '@/store'
import { lightTheme, darkTheme, lightThemeFR, darkThemeFR } from '@/styles/theme'
import { fr, enUS } from 'date-fns/locale'

const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 60 * 1000,
      refetchOnWindowFocus: false,
      retry: 1,
    },
  },
})

export default function Providers({ children }: { children: ReactNode }) {
  const { theme: themeMode, language } = useStore()

  // Select theme based on mode and language
  const theme = useMemo(() => {
    if (language === 'fr') {
      return themeMode === 'dark' ? darkThemeFR : lightThemeFR
    }
    return themeMode === 'dark' ? darkTheme : lightTheme
  }, [themeMode, language])

  // Select date locale
  const dateLocale = language === 'fr' ? fr : enUS

  return (
    <QueryClientProvider client={queryClient}>
      <ThemeProvider theme={theme}>
        <LocalizationProvider dateAdapter={AdapterDateFns} adapterLocale={dateLocale}>
          <CssBaseline />
          {children}
          <Toaster
            position="top-right"
            richColors
            closeButton
            theme={themeMode}
          />
        </LocalizationProvider>
      </ThemeProvider>
      <ReactQueryDevtools initialIsOpen={false} />
    </QueryClientProvider>
  )
}
```

### Theme Toggle Component

**`src/components/layout/ThemeToggle.tsx`**
```typescript
'use client'

import { IconButton, Tooltip } from '@mui/material'
import { Sun, Moon } from 'lucide-react'
import { useStore } from '@/store'
import { useTranslation } from '@/lib/hooks/useTranslation'

export default function ThemeToggle() {
  const { theme, toggleTheme } = useStore()
  const { t } = useTranslation()

  return (
    <Tooltip title={t('common.toggleTheme')}>
      <IconButton onClick={toggleTheme} color="inherit">
        {theme === 'dark' ? <Sun size={20} /> : <Moon size={20} />}
      </IconButton>
    </Tooltip>
  )
}
```

---

## 🌍 Translation System (French/English)

### Translation Structure

```
public/locales/
├── en/
│   ├── common.json              # Common UI strings
│   ├── dashboard.json           # Dashboard specific
│   ├── planning.json            # Planning module
│   ├── employees.json           # Employees module
│   ├── timesheets.json          # Timesheets module
│   ├── absences.json            # Absences module
│   ├── insights.json            # Analytics module
│   ├── reports.json             # Reports module
│   ├── settings.json            # Settings module
│   ├── auth.json                # Authentication
│   ├── errors.json              # Error messages
│   └── validation.json          # Form validation
│
└── fr/
    ├── common.json
    ├── dashboard.json
    ├── planning.json
    ├── employees.json
    ├── timesheets.json
    ├── absences.json
    ├── insights.json
    ├── reports.json
    ├── settings.json
    ├── auth.json
    ├── errors.json
    └── validation.json
```

### Translation Files

**`public/locales/en/common.json`**
```json
{
  "app": {
    "name": "Gym CRM",
    "tagline": "Complete gym management system"
  },
  "nav": {
    "dashboard": "Dashboard",
    "planning": "Planning",
    "employees": "Employees",
    "timesheet": "Timesheet",
    "absences": "Absences",
    "insights": "Insights",
    "reports": "Reports",
    "settings": "Settings",
    "messages": "Messages",
    "notifications": "Notifications",
    "profile": "Profile",
    "logout": "Logout"
  },
  "actions": {
    "add": "Add",
    "edit": "Edit",
    "delete": "Delete",
    "save": "Save",
    "cancel": "Cancel",
    "confirm": "Confirm",
    "close": "Close",
    "search": "Search",
    "filter": "Filter",
    "export": "Export",
    "import": "Import",
    "refresh": "Refresh",
    "viewMore": "View more",
    "viewLess": "View less",
    "selectAll": "Select all",
    "deselectAll": "Deselect all",
    "approve": "Approve",
    "reject": "Reject",
    "submit": "Submit",
    "reset": "Reset"
  },
  "status": {
    "active": "Active",
    "inactive": "Inactive",
    "pending": "Pending",
    "approved": "Approved",
    "rejected": "Rejected",
    "draft": "Draft",
    "published": "Published",
    "archived": "Archived"
  },
  "time": {
    "today": "Today",
    "yesterday": "Yesterday",
    "tomorrow": "Tomorrow",
    "thisWeek": "This week",
    "lastWeek": "Last week",
    "nextWeek": "Next week",
    "thisMonth": "This month",
    "lastMonth": "Last month",
    "nextMonth": "Next month",
    "custom": "Custom range"
  },
  "messages": {
    "loading": "Loading...",
    "saving": "Saving...",
    "deleting": "Deleting...",
    "success": "Success!",
    "error": "An error occurred",
    "noData": "No data available",
    "noResults": "No results found",
    "confirmDelete": "Are you sure you want to delete this item?",
    "unsavedChanges": "You have unsaved changes. Do you want to leave?",
    "savedSuccessfully": "Saved successfully",
    "deletedSuccessfully": "Deleted successfully"
  },
  "toggleTheme": "Toggle theme",
  "switchLanguage": "Switch language",
  "poweredBy": "Powered by"
}
```

**`public/locales/fr/common.json`**
```json
{
  "app": {
    "name": "Gym CRM",
    "tagline": "Système complet de gestion de salle de sport"
  },
  "nav": {
    "dashboard": "Tableau de bord",
    "planning": "Planning",
    "employees": "Employés",
    "timesheet": "Feuille de présence",
    "absences": "Absences",
    "insights": "Analyses",
    "reports": "Rapports",
    "settings": "Paramètres",
    "messages": "Messages",
    "notifications": "Notifications",
    "profile": "Profil",
    "logout": "Déconnexion"
  },
  "actions": {
    "add": "Ajouter",
    "edit": "Modifier",
    "delete": "Supprimer",
    "save": "Enregistrer",
    "cancel": "Annuler",
    "confirm": "Confirmer",
    "close": "Fermer",
    "search": "Rechercher",
    "filter": "Filtrer",
    "export": "Exporter",
    "import": "Importer",
    "refresh": "Actualiser",
    "viewMore": "Voir plus",
    "viewLess": "Voir moins",
    "selectAll": "Tout sélectionner",
    "deselectAll": "Tout désélectionner",
    "approve": "Approuver",
    "reject": "Rejeter",
    "submit": "Soumettre",
    "reset": "Réinitialiser"
  },
  "status": {
    "active": "Actif",
    "inactive": "Inactif",
    "pending": "En attente",
    "approved": "Approuvé",
    "rejected": "Rejeté",
    "draft": "Brouillon",
    "published": "Publié",
    "archived": "Archivé"
  },
  "time": {
    "today": "Aujourd'hui",
    "yesterday": "Hier",
    "tomorrow": "Demain",
    "thisWeek": "Cette semaine",
    "lastWeek": "Semaine dernière",
    "nextWeek": "Semaine prochaine",
    "thisMonth": "Ce mois",
    "lastMonth": "Mois dernier",
    "nextMonth": "Mois prochain",
    "custom": "Période personnalisée"
  },
  "messages": {
    "loading": "Chargement...",
    "saving": "Enregistrement...",
    "deleting": "Suppression...",
    "success": "Succès!",
    "error": "Une erreur s'est produite",
    "noData": "Aucune donnée disponible",
    "noResults": "Aucun résultat trouvé",
    "confirmDelete": "Êtes-vous sûr de vouloir supprimer cet élément?",
    "unsavedChanges": "Vous avez des modifications non enregistrées. Voulez-vous quitter?",
    "savedSuccessfully": "Enregistré avec succès",
    "deletedSuccessfully": "Supprimé avec succès"
  },
  "toggleTheme": "Changer le thème",
  "switchLanguage": "Changer de langue",
  "poweredBy": "Propulsé par"
}
```

**`public/locales/en/dashboard.json`**
```json
{
  "title": "Dashboard",
  "welcome": "Welcome back, {{name}}!",
  "widgets": {
    "myOverview": "My Overview",
    "myPlanning": "My Schedule",
    "myTimesheet": "My Timesheet",
    "myAbsences": "My Time Off",
    "myBalance": "My Balance"
  },
  "quickStats": {
    "totalEmployees": "Total Employees",
    "activeShifts": "Active Shifts",
    "pendingRequests": "Pending Requests",
    "hoursWorked": "Hours This Week"
  },
  "upcomingShifts": {
    "title": "Upcoming Shifts",
    "noShifts": "No upcoming shifts",
    "viewAll": "View all shifts"
  },
  "recentActivity": {
    "title": "Recent Activity",
    "noActivity": "No recent activity"
  }
}
```

**`public/locales/fr/dashboard.json`**
```json
{
  "title": "Tableau de bord",
  "welcome": "Bienvenue, {{name}}!",
  "widgets": {
    "myOverview": "Ma vue d'ensemble",
    "myPlanning": "Mon planning",
    "myTimesheet": "Ma feuille de temps",
    "myAbsences": "Mes absences",
    "myBalance": "Mon solde"
  },
  "quickStats": {
    "totalEmployees": "Total des employés",
    "activeShifts": "Quarts actifs",
    "pendingRequests": "Demandes en attente",
    "hoursWorked": "Heures cette semaine"
  },
  "upcomingShifts": {
    "title": "Prochains quarts",
    "noShifts": "Aucun quart à venir",
    "viewAll": "Voir tous les quarts"
  },
  "recentActivity": {
    "title": "Activité récente",
    "noActivity": "Aucune activité récente"
  }
}
```

### Translation Hook

**`src/lib/hooks/useTranslation.ts`**
```typescript
'use client'

import { useParams } from 'next/navigation'
import { useCallback, useMemo } from 'use'
import en from '@/public/locales/en'
import fr from '@/public/locales/fr'

type TranslationKey = string

const translations = {
  en,
  fr,
}

export function useTranslation(namespace?: string) {
  const params = useParams()
  const lang = (params?.lang as 'en' | 'fr') || 'en'

  const t = useCallback(
    (key: TranslationKey, params?: Record<string, string | number>) => {
      const keys = key.split('.')
      let value: any = translations[lang]

      // Navigate through nested keys
      for (const k of keys) {
        if (value && typeof value === 'object') {
          value = value[k]
        } else {
          return key // Return key if not found
        }
      }

      // Replace parameters
      if (params && typeof value === 'string') {
        Object.entries(params).forEach(([param, val]) => {
          value = value.replace(`{{${param}}}`, String(val))
        })
      }

      return value || key
    },
    [lang]
  )

  return { t, lang }
}
```

### Language Switcher Component

**`src/components/layout/LanguageSwitcher.tsx`**
```typescript
'use client'

import { useParams, useRouter, usePathname } from 'next/navigation'
import { IconButton, Menu, MenuItem, Tooltip } from '@mui/material'
import { Languages } from 'lucide-react'
import { useState } from 'react'

const languages = [
  { code: 'en', name: 'English', flag: '🇬🇧' },
  { code: 'fr', name: 'Français', flag: '🇫🇷' },
]

export default function LanguageSwitcher() {
  const params = useParams()
  const router = useRouter()
  const pathname = usePathname()
  const [anchorEl, setAnchorEl] = useState<null | HTMLElement>(null)

  const currentLang = (params?.lang as string) || 'en'
  const currentLanguage = languages.find(l => l.code === currentLang)

  const handleOpen = (event: React.MouseEvent<HTMLElement>) => {
    setAnchorEl(event.currentTarget)
  }

  const handleClose = () => {
    setAnchorEl(null)
  }

  const switchLanguage = (langCode: string) => {
    const newPathname = pathname.replace(`/${currentLang}`, `/${langCode}`)
    router.push(newPathname)
    handleClose()
  }

  return (
    <>
      <Tooltip title="Switch language">
        <IconButton onClick={handleOpen} color="inherit">
          <Languages size={20} />
          <span style={{ marginLeft: 8, fontSize: 14 }}>
            {currentLanguage?.flag}
          </span>
        </IconButton>
      </Tooltip>

      <Menu
        anchorEl={anchorEl}
        open={Boolean(anchorEl)}
        onClose={handleClose}
      >
        {languages.map((lang) => (
          <MenuItem
            key={lang.code}
            onClick={() => switchLanguage(lang.code)}
            selected={lang.code === currentLang}
          >
            <span style={{ marginRight: 12 }}>{lang.flag}</span>
            {lang.name}
          </MenuItem>
        ))}
      </Menu>
    </>
  )
}
```

### Middleware for Language Routing

**`middleware.ts`**
```typescript
import { NextResponse } from 'next/server'
import type { NextRequest } from 'next/server'

const locales = ['en', 'fr']
const defaultLocale = 'en'

export function middleware(request: NextRequest) {
  const pathname = request.nextUrl.pathname

  // Check if pathname is missing locale
  const pathnameIsMissingLocale = locales.every(
    (locale) => !pathname.startsWith(`/${locale}/`) && pathname !== `/${locale}`
  )

  if (pathnameIsMissingLocale) {
    // Redirect to default locale
    return NextResponse.redirect(
      new URL(`/${defaultLocale}${pathname}`, request.url)
    )
  }
}

export const config = {
  matcher: [
    // Skip API routes, static files, etc.
    '/((?!api|_next/static|_next/image|favicon.ico).*)',
  ],
}
```

---

## 📊 State Management Architecture

### Zustand Store Structure

**`src/store/index.ts`**
```typescript
import { create } from 'zustand'
import { devtools, persist } from 'zustand/middleware'

interface ThemeState {
  theme: 'light' | 'dark'
  toggleTheme: () => void
  setTheme: (theme: 'light' | 'dark') => void
}

interface LanguageState {
  language: 'en' | 'fr'
  setLanguage: (lang: 'en' | 'fr') => void
}

interface UIState {
  sidebarOpen: boolean
  toggleSidebar: () => void
  setSidebarOpen: (open: boolean) => void
}

interface AuthState {
  user: User | null
  setUser: (user: User | null) => void
  logout: () => void
}

type Store = ThemeState & LanguageState & UIState & AuthState

export const useStore = create<Store>()(
  devtools(
    persist(
      (set) => ({
        // Theme
        theme: 'light',
        toggleTheme: () => set((state) => ({
          theme: state.theme === 'light' ? 'dark' : 'light'
        })),
        setTheme: (theme) => set({ theme }),

        // Language
        language: 'en',
        setLanguage: (language) => set({ language }),

        // UI
        sidebarOpen: true,
        toggleSidebar: () => set((state) => ({
          sidebarOpen: !state.sidebarOpen
        })),
        setSidebarOpen: (sidebarOpen) => set({ sidebarOpen }),

        // Auth
        user: null,
        setUser: (user) => set({ user }),
        logout: () => set({ user: null }),
      }),
      {
        name: 'gym-crm-storage',
        partialize: (state) => ({
          theme: state.theme,
          language: state.language,
        }),
      }
    )
  )
)
```

---

## 🔌 API Integration Layer

**`src/lib/api/client.ts`**
```typescript
import axios from 'axios'

export const apiClient = axios.create({
  baseURL: process.env.NEXT_PUBLIC_API_URL || 'http://localhost:3000/api/v1',
  headers: {
    'Content-Type': 'application/json',
  },
})

// Request interceptor
apiClient.interceptors.request.use((config) => {
  const token = localStorage.getItem('auth_token')
  if (token) {
    config.headers.Authorization = `Bearer ${token}`
  }
  return config
})

// Response interceptor
apiClient.interceptors.response.use(
  (response) => response,
  (error) => {
    if (error.response?.status === 401) {
      // Redirect to login
      window.location.href = '/login'
    }
    return Promise.reject(error)
  }
)
```

---

**Created:** January 2025
**Stack:** Next.js 15.4 + Material-UI v7 + MUI X v8 + React 19
**Research:** 8 web searches, 2025 best practices
**Theme Support:** Light/Dark modes
**Languages:** French & English (i18n ready)
**Total Components:** 150+ custom components
**UI Library:** Material-UI v7 + MUI X v8
**State Management:** TanStack Query + Zustand
**Ready for:** Multi-tenant, Scalable, Production

