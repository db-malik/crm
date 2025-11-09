# Frontend Website Sitemap - Gym CRM System
## Based on Shiftbase API & Screenshots Analysis

---

## 1. Authentication & Onboarding

### 1.1 Authentication Pages
- **`/login`** - User Login
  - Email/password authentication
  - Remember me option
  - Forgot password link
  - API: `POST /api/v1/auth/login`

- **`/register`** - New Account Registration
  - Business type selection (Retail, Hospitality, Healthcare, Recreation, Services, Transport, Production, Other)
  - Activity sector (Arts & Shows, Construction, Education, **Gyms**, Storage, Other)
  - Role selection (Employee, Owner, Executive, Director/Supervisor, Operations, Finance, Scheduler, HR, IT, Student, Other)
  - Current time management method
  - Scheduling challenges identification
  - Business impact assessment
  - Primary reason for solution
  - Expected features from Shiftbase

- **`/forgot-password`** - Password Reset Request
  - API: `POST /api/v1/auth/password/reset-request`

- **`/reset-password/:token`** - Set New Password
  - API: `PUT /api/v1/auth/password/set`

---

## 2. Main Dashboard

### 2.1 Dashboard Home
- **`/dashboard`** - Main Dashboard (Tableau de bord)
  - Personalized welcome message
  - Quick access widgets:
    - My overview (Ma vue d'ensemble)
    - My planning (Mon planning)
    - My timesheet (Ma feuille de temps)
    - My absences (Mon absence)
    - My plus and minus (Mes plus et mes moins)
  - Customizable dashboard option
  - Trial days remaining indicator
  - Plan confirmation CTA

---

## 3. Planning & Scheduling Module

### 3.1 Planning Overview
- **`/planning`** - Planning Calendar
  - View modes: Day, Week, Month, Employee, Team
  - Date range selector
  - Filter options
  - Actions menu
  - Add shift button with dropdown
  - API: `GET /api/v1/shifts`

### 3.2 Schedule Management
- **`/planning/schedule`** - Schedule View
  - Team/shift templates display
  - Employee assignments
  - Shift types with color coding:
    - Day shift (Quart de jour)
    - Night shift (Ramadan)
    - Various service shifts
  - Drag-and-drop scheduling
  - Conflict detection indicators
  - Open shifts counter
  - Scheduled shifts counter
  - API: `GET /api/v1/schedule`, `POST /api/v1/schedule/copy`

### 3.3 Shifts
- **`/planning/shifts`** - Shifts Management
  - Create shift
  - Edit shift
  - Delete shift
  - Batch operations
  - API: `POST /api/v1/shifts`, `PUT /api/v1/shifts/{id}`, `DELETE /api/v1/shifts/{id}`, `POST /api/v1/shifts/batch`

### 3.4 Open Shifts
- **`/planning/open-shifts`** - Open Shifts Management
  - List available shifts
  - Assign to employee
  - Multi-assign option
  - Employee requests
  - Take shift (employee self-service)
  - Withdraw request
  - API: `GET /api/v1/open-shifts`, `POST /api/v1/open-shifts`, `PUT /api/v1/open-shifts/{id}/assign`

### 3.5 Required Shifts
- **`/planning/required-shifts`** - Required Shifts/Staffing Needs
  - Define staffing requirements
  - API: `GET /api/v1/required-shifts`, `POST /api/v1/required-shifts`

### 3.6 Rosters
- **`/planning/rosters`** - Work Rosters
  - Create roster templates
  - Assign rosters
  - API: `GET /api/v1/rosters`, `POST /api/v1/rosters`

### 3.7 Team Days
- **`/planning/team-days`** - Team Work Days
  - Configure team working days
  - API: `GET /api/v1/team-days`, `POST /api/v1/team-days`

### 3.8 Planning Conflicts
- **`/planning/conflicts`** - Conflict Management
  - Availability conflicts
  - Schedule conflicts
  - Skills conflicts
  - Time conflicts
  - API: `GET /api/v1/planning/conflicts`, `GET /api/v1/planning/conflicts/availability`

### 3.9 Employability
- **`/planning/employability`** - Employee Availability Analysis
  - Check employee availability for shifts
  - API: `GET /api/v1/planning/employability/{id}`

---

## 4. Employees Management

### 4.1 Employees Directory
- **`/employees`** - Employees List
  - Search and filter employees
  - Employee cards with avatars
  - Contact information
  - Status indicators
  - Add employee button
  - API: `GET /api/v1/employees`

### 4.2 Employee Profile
- **`/employees/:id`** - Individual Employee Profile
  - Tabs:
    - Overview (Vue d'ensemble)
    - Edit (Modifier)
    - Teams and permissions (Équipes et autorisations)
    - Absence (Absences)
    - Plus minus (Plus/Moins)
    - Schedule
    - Timesheets
    - Contracts
  - Employee photo/avatar
  - Personal information
  - Contact details
  - Time off balance
  - Upcoming absences
  - Time distribution chart
  - API: `GET /api/v1/employees/{id}`, `PUT /api/v1/employees/{id}`

### 4.3 Add/Edit Employee
- **`/employees/new`** - Create Employee
- **`/employees/:id/edit`** - Edit Employee
  - Personal data
  - Employment information
  - Contract assignment
  - Team assignment
  - Skills assignment
  - Avatar upload
  - API: `POST /api/v1/employees`, `PUT /api/v1/employees/{id}`, `POST /api/v1/users/{id}/avatar`

### 4.4 Employee Teams
- **`/employees/:id/teams`** - Manage Employee Teams
  - Assign to teams
  - API: `PUT /api/v1/employees/{id}/teams`

### 4.5 Employee Balances
- **`/employees/:id/time-off-balance`** - Time Off Balance
  - Current balance
  - Upcoming balance
  - Balance distribution by type
  - API: `GET /api/v1/employees/{id}/time-off-balance`, `GET /api/v1/employees/{id}/upcoming-time-off-balance`

### 4.6 Deactivate/Anonymize
- **Employee Actions**
  - Deactivate employee
  - Reactivate employee
  - Anonymize (GDPR)
  - API: `DELETE /api/v1/employees/{id}`, `PUT /api/v1/users/{id}/activate`, `DELETE /api/v1/users/{id}/anonymize`

---

## 5. Time Tracking & Timesheets

### 5.1 Timesheet Overview
- **`/timesheet`** - Timesheet Management (Feuille de présence)
  - Daily/weekly timesheet view
  - View modes: Day, Week, Month, Employee, Team
  - Clock status indicators
  - Add work hours button
  - Approve timesheet
  - Service team totals
  - API: `GET /api/v1/timesheets`

### 5.2 Add/Edit Timesheet Entry
- **`/timesheet/add`** - Add Timesheet Entry
  - Date selection
  - Employee selection
  - Service/Department selection
  - Team selection
  - Start time
  - End time
  - Break duration (automatically calculated)
  - Notes
  - Notify employee option
  - API: `POST /api/v1/timesheets`, `POST /api/v1/timesheets/calculated-break`

### 5.3 Clock In/Out
- **`/timesheet/clock`** - Time Clock
  - Clock in/out interface
  - Current clocked-in employees
  - API: `POST /api/v1/timesheets/clock`, `GET /api/v1/timesheets/clocked-in`

### 5.4 Time Tracking Features
- **Time tracking capabilities:**
  - Check if employee is clocked in
  - Day status tracking
  - Conflict detection
  - Totals preview
  - Statements generation
  - API: `GET /api/v1/timesheets/is-clocked-in/{id}`, `GET /api/v1/timesheets/day-status`, `GET /api/v1/timesheets/conflicts`, `POST /api/v1/timesheets/totals-preview`

### 5.5 Batch Operations
- **`/timesheet/batch`** - Batch Timesheet Processing
  - API: `POST /api/v1/timesheets/batch`

### 5.6 Time Tracking Kiosks
- **`/kiosks`** - Kiosk Management
  - Create clock terminals
  - Configure kiosks
  - Invite employees to kiosk
  - API: `GET /api/v1/kiosks`, `POST /api/v1/kiosks`, `POST /api/v1/kiosks/{id}/invite`

### 5.7 Clock Locations & IPs
- **`/timesheet/clock-settings`** - Clock Settings
  - Clock IP management
  - Clock location management (geofencing)
  - Authorization checks
  - API: `GET /api/v1/clock-ips`, `GET /api/v1/clock-locations`, `POST /api/v1/clock/authorization-check`

### 5.8 PIN Codes
- **`/timesheet/pin`** - PIN Code Management
  - Generate kiosk PIN
  - Employee kiosk PIN
  - API: `GET /api/v1/pin/kiosk`, `POST /api/v1/pin/kiosk/regenerate`

---

## 6. Absence Management

### 6.1 Absences Overview
- **`/absences`** - Absences List
  - Calendar view (2 months side-by-side)
  - Absence types with color coding:
    - Public holiday (purple)
    - Vacation (yellow)
    - Sick (red)
  - Filter by status: Requests, Reviewed, Past
  - Add absence button
  - Approve/reject actions
  - Add to calendar option
  - API: `GET /api/v1/absences`

### 6.2 Add/Edit Absence
- **`/absences/new`** - Request Absence
- **`/absences/:id/edit`** - Edit Absence
  - Absence type dropdown (Vacances, Maladie, Fête nationale, Congé spécial, Congé maternité, etc.)
  - Leave balance display (Soldes des congés)
  - Partial day option
  - Date period selection
  - Intermediate hours selector (pull from planning)
  - Notes field
  - Selected employees table showing:
    - Contract hours
    - Planned hours
    - Absence hours
  - API: `POST /api/v1/absences`, `PUT /api/v1/absences/{id}`

### 6.3 Absence Approval
- **Approval workflow:**
  - Approve absence
  - Reject absence
  - API: `POST /api/v1/absences/{id}/approve`, `POST /api/v1/absences/{id}/reject`

### 6.4 Absence Types
- **`/settings/absence-types`** - Absence Types Configuration
  - Create absence types
  - Edit absence types
  - API: `GET /api/v1/absence-types`, `POST /api/v1/absence-types`

### 6.5 Absence Policies
- **`/settings/absence-policies`** - Absence Policies
  - Configure policies
  - API: `GET /api/v1/absence-policies`

### 6.6 Absentees
- **`/absences/absentees`** - Absentee Management
  - Track absent employees
  - Mark as returned
  - Bulk operations
  - Review absentees
  - API: `GET /api/v1/absentees`, `POST /api/v1/absentees`, `PUT /api/v1/absentees/mark-returned`

### 6.7 Absence Restrictions
- **`/settings/absence-restrictions`** - Absence Restrictions
  - Define restrictions
  - API: `GET /api/v1/absence-restrictions`, `POST /api/v1/absence-restrictions`

### 6.8 Mobile Absence Request
- **Mobile Interface:**
  - Employee self-service absence request
  - Employee name
  - Vacation type selection
  - Start date
  - End date
  - Duration
  - Notes
  - Submit button

---

## 7. Insights & Analytics

### 7.1 Insights Dashboard
- **`/insights`** - Analytics Dashboard (BETA)
  - Performance insights
  - Schedule insights
  - Scheduled vs worked analysis
  - Sentiment tracking
  - API: `GET /api/v1/insights/performance`, `GET /api/v1/insights/schedule`

### 7.2 Performance Insights
- **`/insights/performance`** - Performance Analytics
  - Performance charts
  - API: `GET /api/v1/insights/performance/{id}/chart`

### 7.3 Scheduled vs Worked
- **`/insights/scheduled-vs-worked`** - Hours Comparison
  - Compare planned vs actual hours
  - API: `GET /api/v1/insights/scheduled-vs-worked`

### 7.4 Sentiment
- **`/insights/sentiment`** - Employee Sentiment
  - Track employee mood/sentiment
  - Add sentiment to timesheet
  - API: `GET /api/v1/insights/sentiment`, `POST /api/v1/insights/sentiment/timesheet`

---

## 8. Reports Module

### 8.1 Reports Hub
- **`/reports`** - Reports Center
  - Favorite reports
  - Recurring reports
  - Requested reports
  - Report types dropdown
  - API: `GET /api/v1/reports/favorites`, `GET /api/v1/reports/recurring`, `GET /api/v1/reports/requested`

### 8.2 Request Report
- **`/reports/request`** - Request New Report
  - Report type selection
  - Parameters configuration
  - API: `POST /api/v1/reports/request`, `POST /api/v1/reports/describe`

### 8.3 Favorite Reports
- **`/reports/favorites`** - Manage Favorites
  - Save favorite reports
  - API: `POST /api/v1/reports/favorites`, `GET /api/v1/reports/favorites/{id}`

### 8.4 Recurring Reports
- **`/reports/recurring`** - Scheduled Reports
  - Create recurring reports
  - View projected runs
  - API: `POST /api/v1/reports/recurring`, `POST /api/v1/reports/recurring/projected-runs`

### 8.5 Download/Fetch Reports
- **Report actions:**
  - Fetch report
  - Check status
  - API: `GET /api/v1/reports/{id}/fetch`, `GET /api/v1/reports/{id}/status`

### 8.6 BI Reports (Available Types)
- **Available BI Reports:**
  - Absentee report
  - Availability report
  - Day log report
  - Time off balance details
  - Time off balance summary
  - Finished timesheet
  - Insights performance
  - Open shifts
  - Payroll
  - Payroll integration
  - Period overview
  - Permission groups
  - Plus & minus
  - Required shifts
  - Schedule summary
  - Schedule detail
  - Schedule vs timesheet
  - Sentiments
  - Skills
  - Timesheet summary
  - Timesheet detail
  - Timesheet integration
  - Turnover
  - Employees
  - API: `POST /api/v1/reports/bi/*`

---

## 9. Settings & Configuration

### 9.1 General Settings
- **`/settings`** - Settings Home
  - Généralités (General)
  - Abonnement (Subscription)
  - Sécurité (Security)
  - Organisation
  - Horaires (Schedules)
  - Employés (Employees)
  - Absence
  - Suivi du temps (Time Tracking)
  - Planning
  - App Center

### 9.2 Account Settings
- **`/settings/account`** - Account Configuration
  - Account information
  - Edit account details
  - Module management
  - API: `GET /api/v1/account`, `PUT /api/v1/account`, `GET /api/v1/account/modules`

### 9.3 Subscription
- **`/settings/subscription`** - Subscription Management
  - Current plan
  - Trial status
  - Upgrade options
  - Billing information

### 9.4 Security Settings
- **`/settings/security`** - Security & Permissions
  - User permissions management
  - Permission groups:
    - Administrateur (Administrator)
    - Directeur (Director)
    - Planificateur (Scheduler)
    - Employé (Employee)
  - Permission categories:
    - Nouvelles (News)
    - Utilisateurs (Users)
    - Horaires (Schedules)
    - Fichiers (Files)
    - Feuilles de présence (Timesheets)
  - Multi-factor authentication
  - Default permission role selection
  - API: `PUT /api/v1/users/{id}/permissions`

### 9.5 Organization Settings
- **`/settings/organization`** - Organization Structure
  - Departments management
  - Locations management
  - Teams management

### 9.6 Departments
- **`/settings/departments`** - Departments
  - Create department
  - Edit department
  - Delete/deactivate department
  - Activate deleted department
  - Validate deletion
  - API: `GET /api/v1/departments`, `POST /api/v1/departments`, `PUT /api/v1/departments/{id}/activate`

### 9.7 Department Settings
- **`/settings/departments/:id/settings`** - Department Configuration
  - Timesheet & clocking settings
  - Employee notifications
  - Insights notifications
  - Schedule notifications
  - Time tracking notifications
  - Schedule availability settings
  - Schedule settings
  - Timesheet settings
  - Department variations
  - API: `GET /api/v1/department-settings`, `PUT /api/v1/department-settings/{id}/*`

### 9.8 Department Targets
- **`/settings/departments/:id/targets`** - Department Goals
  - Set targets
  - Configure target settings
  - API: `GET /api/v1/department-targets`, `PUT /api/v1/department-targets`

### 9.9 Locations
- **`/settings/locations`** - Location Management
  - Add location
  - Edit location
  - Activate/deactivate location
  - API: `GET /api/v1/locations`, `POST /api/v1/locations`

### 9.10 Teams
- **`/settings/teams`** - Teams Configuration
  - Create team
  - Edit team
  - Delete team
  - Validate deletion
  - API: `GET /api/v1/teams`, `POST /api/v1/teams`

### 9.11 Schedule Settings (Horaires)
- **`/settings/schedules`** - Schedule/Shift Templates
  - Shift types management (shown for "Salle lac 1"):
    - Ordinaire (09:00 - 17:00) - Green
    - Ramadan soir (18:00 - 23:00) - Purple
    - Ramadan jour (10:00 - 16:00) - Red
    - Securité (08:00 - 16:00) - Pink
  - Create shift template
  - Edit shift times
  - Color coding
  - API: Custom shift/roster configuration

### 9.12 Contract Types
- **`/settings/contract-types`** - Contract Types
  - Create contract types
  - Edit contract types
  - Activate contract types
  - API: `GET /api/v1/contract-types`, `POST /api/v1/contract-types`, `POST /api/v1/contract-types/{id}/activate`

### 9.13 Contracts
- **`/settings/contracts`** - Contracts Management
  - Create contract
  - Edit contract
  - Delete contract
  - API: `GET /api/v1/contracts`, `POST /api/v1/contracts`

### 9.14 Skills Management
- **`/settings/skills`** - Skills & Competencies
  - Skill groups
  - Individual skills
  - API: `GET /api/v1/skills`, `POST /api/v1/skills`, `GET /api/v1/skill-groups`

### 9.15 Custom Fields
- **`/settings/custom-fields`** - Custom Fields
  - Create custom fields
  - Batch operations
  - API: `GET /api/v1/custom-fields`, `POST /api/v1/custom-fields`, `POST /api/v1/custom-fields/batch`

### 9.16 Holidays
- **`/settings/holidays`** - Public Holidays
  - Holiday groups
  - Country holidays
  - Process holidays
  - API: `GET /api/v1/holiday-groups`, `POST /api/v1/holidays/process`, `GET /api/v1/holidays/country/{code}`

### 9.17 Overtime Policies
- **`/settings/overtime`** - Overtime Configuration
  - Create overtime policies
  - Edit policies
  - API: `GET /api/v1/overtime-policies`, `POST /api/v1/overtime-policies`

---

## 10. Corrections & Adjustments

### 10.1 Corrections
- **`/corrections`** - Hours & Balance Corrections
  - Add correction
  - Batch corrections
  - Plus/minus balance
  - API: `GET /api/v1/corrections`, `POST /api/v1/corrections`, `POST /api/v1/corrections/batch`

### 10.2 Plus Minus Balance
- **`/corrections/plus-min-balance`** - Balance Overview
  - View plus/minus balances
  - API: `POST /api/v1/corrections/plus-min-balance`

---

## 11. Communication

### 11.1 News Feed
- **`/news`** - News & Information Messages
  - Create news item
  - View news
  - Comment on news
  - API: `GET /api/v1/news`, `POST /api/v1/news`, `POST /api/v1/news/{id}/comments`

### 11.2 Messaging
- **`/messages`** - Internal Messaging (Message d'information)
  - Send messages to users
  - API: `POST /api/v1/users/send-message`

### 11.3 Notifications
- **`/notifications`** - Notification Center
  - Notification count
  - Notification preferences
  - API: `GET /api/v1/user-notifications/count`

---

## 12. Integrations & Imports

### 12.1 iCal Feeds
- **`/settings/ical`** - Calendar Sync
  - Add iCal feed
  - Manage feeds
  - API: `GET /api/v1/ical-feeds`, `POST /api/v1/ical-feeds`

### 12.2 App Tokens
- **`/settings/api-tokens`** - API Token Management
  - Create token
  - Activate/deactivate token
  - API: `GET /api/v1/app-tokens`, `POST /api/v1/app-tokens`

### 12.3 Weather Integration
- **Weather features:**
  - Weather forecast display
  - API: `GET /api/v1/weather-forecasts`

---

## 13. User Management

### 13.1 Users List
- **`/settings/users`** - User Management
  - Create user
  - Invite users
  - Create/update many users
  - API: `GET /api/v1/users`, `POST /api/v1/users`, `POST /api/v1/users/invite`

### 13.2 User Permissions
- **`/settings/users/:id/permissions`** - User Permissions
  - Edit individual permissions
  - API: `PUT /api/v1/users/{id}/permissions`

### 13.3 User Profile
- **`/profile`** - Current User Profile
  - Edit profile
  - Change password
  - Upload avatar
  - API: `GET /api/v1/users/{id}`, `PUT /api/v1/users/{id}`, `PUT /api/v1/auth/password`

---

## 14. Availabilities

### 14.1 Availability Management
- **`/availabilities`** - Employee Availabilities
  - Set availabilities
  - Edit availability
  - First editable availability
  - Availability rules
  - API: `GET /api/v1/availabilities`, `POST /api/v1/availabilities`, `GET /api/v1/availabilities/rules`

---

## 15. Events & Calendar

### 15.1 Events
- **`/events`** - Calendar Events
  - Create event
  - Event sequences (recurring)
  - Batch event operations
  - API: `GET /api/v1/events`, `POST /api/v1/events`, `POST /api/v1/events/batch`

---

## 16. Time Off Balance

### 16.1 Balance Management
- **`/time-off-balance`** - Time Off Balance
  - Add balance
  - Edit balance
  - Activate/deactivate
  - Balance cycles per employee
  - API: `GET /api/v1/time-off-balance`, `POST /api/v1/time-off-balance`, `GET /api/v1/time-off-balance/employee/{id}/cycles`

---

## 17. Compliance & Legal

### 17.1 Compliance
- **`/compliance`** - Legal Compliance (Conformité juridique)
  - Regulatory compliance tracking
  - Labor law compliance
  - Working hours regulations
  - API: Compliance schemas

### 17.2 Minijob (Germany-specific)
- **`/minijob/:id/overview`** - Minijob Overview
  - German minijob management
  - API: `GET /api/v1/minijob/employees/{id}/overview`

---

## 18. Logs & Audit

### 18.1 System Logs
- **`/logs`** - Activity Logs
  - View logs
  - Create log entry
  - Edit log
  - API: `GET /api/v1/logs`, `POST /api/v1/logs`

---

## 19. HR Module

### 19.1 HR Dashboard
- **`/hr`** - HR Management
  - Department employees
  - API: `GET /api/v1/hr/departments/{id}/employees`

---

## 20. Mobile App Features

### 20.1 Mobile-Specific Pages
- **Mobile optimized interfaces:**
  - `/m/dashboard` - Mobile dashboard
  - `/m/clock` - Mobile clock in/out
  - `/m/schedule` - Mobile schedule view
  - `/m/absence/request` - Mobile absence request (shown in screenshot)
  - `/m/timesheet` - Mobile timesheet
  - `/m/profile` - Mobile profile

---

## Page Flow & User Journeys

### Journey 1: Manager - Schedule Creation
1. Login → `/login`
2. Dashboard → `/dashboard`
3. Planning → `/planning`
4. View team schedule → `/planning/schedule`
5. Add shift → `/planning/shifts/new`
6. Assign employees
7. Check conflicts → `/planning/conflicts`
8. Publish schedule

### Journey 2: Employee - Request Time Off
1. Login → `/login`
2. Dashboard → `/dashboard`
3. My absences → `/absences`
4. Request absence → `/absences/new`
5. Select type and dates
6. Submit for approval
7. Notification sent to manager

### Journey 3: Manager - Approve Timesheet
1. Login → `/login`
2. Dashboard → `/dashboard`
3. Timesheet → `/timesheet`
4. Review employee hours
5. Check for conflicts
6. Approve timesheet
7. Generate report → `/reports`

### Journey 4: Employee - Clock In/Out
1. Arrive at work location
2. Access kiosk or mobile → `/m/clock` or `/timesheet/clock`
3. Enter PIN
4. Clock in
5. Work shift
6. Clock out at end of shift
7. Break automatically calculated

### Journey 5: Admin - Onboard New Employee
1. Login → `/login`
2. Employees → `/employees`
3. Add employee → `/employees/new`
4. Fill personal details
5. Assign contract → Select contract type
6. Assign teams → `/employees/:id/teams`
7. Set permissions → `/settings/users/:id/permissions`
8. Upload avatar
9. Send invitation → Invite user
10. Employee receives email and activates account

---

## Key Functionalities Summary

### Planning & Scheduling
- Multi-view scheduling (day, week, month, employee, team)
- Drag-and-drop shift assignment
- Shift templates and rosters
- Open shifts management
- Conflict detection (availability, skills, time)
- Copy schedule functionality
- Required shifts/staffing levels

### Time Tracking
- Clock in/out (web, mobile, kiosk)
- Automatic break calculation
- Geofencing and IP restrictions
- PIN code authentication for kiosks
- Real-time clocked-in employees view
- Timesheet approval workflow
- Batch timesheet processing

### Absence Management
- Multiple absence types (vacation, sick, parental, etc.)
- Visual calendar with color coding
- Approval workflow
- Time off balance tracking
- Absence policies and restrictions
- Mobile absence requests
- Integration with schedule

### Employee Management
- Complete employee profiles
- Avatar/photo upload
- Team and department assignment
- Skills and competencies tracking
- Contract management
- Permission management
- Deactivation and anonymization (GDPR)

### Reporting & Analytics
- 25+ BI report types
- Favorite and recurring reports
- Performance insights
- Scheduled vs worked analysis
- Sentiment tracking
- Custom report parameters
- Export capabilities

### Settings & Configuration
- Granular permission system (4 default roles)
- Department-specific settings
- Multi-location support
- Customizable shift templates
- Contract types management
- Custom fields
- Holiday management
- Overtime policies

### Communication
- News feed with comments
- Internal messaging
- Notifications system
- Email notifications

### Integrations
- iCal calendar sync
- API token management
- Weather integration
- Payroll integration support
- External calendar integration

---

## Technical Notes

### API Integration
- Base URL: `https://api.shiftbase.com/api/v1`
- Authentication: Bearer Token
- Data format: JSON
- 287+ endpoints available
- Pagination support
- Batch operations for bulk updates
- Real-time conflict detection

### Mobile Support
- Responsive web design
- Dedicated mobile interfaces
- Mobile app features:
  - Clock in/out
  - Schedule viewing
  - Absence requests
  - Timesheet access
  - Profile management

### Security Features
- Multi-factor authentication support
- Role-based access control
- IP restrictions for time clock
- Geofencing for clock locations
- PIN code authentication
- GDPR compliance (anonymization)
- Audit logs

### Color Coding System
- **Green**: Regular shifts
- **Purple**: Special shifts (e.g., Ramadan evening)
- **Red**: Day shifts (e.g., Ramadan day)
- **Pink**: Security shifts
- **Orange**: Staff shifts
- **Yellow**: Vacation/time off
- **Blue**: Various service types

---

## Recommended Information Architecture

```
/
├── auth/
│   ├── login
│   ├── register
│   ├── forgot-password
│   └── reset-password/:token
├── dashboard
├── planning/
│   ├── schedule
│   ├── shifts
│   ├── open-shifts
│   ├── required-shifts
│   ├── rosters
│   ├── team-days
│   ├── conflicts
│   └── employability
├── employees/
│   ├── list
│   ├── :id/profile
│   ├── :id/teams
│   ├── :id/time-off-balance
│   ├── new
│   └── :id/edit
├── timesheet/
│   ├── overview
│   ├── add
│   ├── clock
│   ├── kiosks
│   ├── clock-settings
│   └── pin
├── absences/
│   ├── list
│   ├── new
│   ├── :id/edit
│   └── absentees
├── insights/
│   ├── dashboard
│   ├── performance
│   ├── scheduled-vs-worked
│   └── sentiment
├── reports/
│   ├── hub
│   ├── request
│   ├── favorites
│   └── recurring
├── settings/
│   ├── account
│   ├── subscription
│   ├── security
│   ├── departments
│   ├── locations
│   ├── teams
│   ├── schedules
│   ├── contract-types
│   ├── contracts
│   ├── skills
│   ├── custom-fields
│   ├── holidays
│   ├── overtime
│   ├── absence-types
│   ├── absence-policies
│   ├── ical
│   ├── api-tokens
│   └── users
├── corrections
├── news
├── messages
├── notifications
├── availabilities
├── events
├── time-off-balance
├── compliance
├── logs
├── hr
└── m/ (mobile)
    ├── dashboard
    ├── clock
    ├── schedule
    ├── absence/request
    ├── timesheet
    └── profile
```

---

**Document Version:** 1.0
**Created:** November 2025
**Based on:** Shiftbase API Documentation + Application Screenshots
**Target Application:** Gym CRM Management System
