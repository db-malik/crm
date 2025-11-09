# Gym CRM System - Product Requirements & User Stories
## Comprehensive Notion-Style Tickets

**Project:** Gym CRM Management System
**Version:** 1.0
**Date:** November 2025
**Document Type:** Product Requirements Document (PRD)

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [System Architecture Overview](#system-architecture-overview)
3. [Subscription Plans](#subscription-plans)
4. [User Roles & Permissions](#user-roles--permissions)
5. [Core Features](#core-features)
6. [Detailed User Stories](#detailed-user-stories)
7. [Technical Requirements](#technical-requirements)

---

## Executive Summary

### Vision
Create a comprehensive SaaS-based Gym CRM system that enables gym owners to manage multiple locations, schedule staff, track time, manage members, and provide seamless employee and member experiences through web and mobile applications.

### Target Users
- **Super Admin:** Platform administrator managing all workspaces
- **Gym Owner:** Owner of one or multiple gym locations
- **Gym Manager:** Manager overseeing all locations for an owner
- **Club Manager:** Manager of a single gym location
- **Team Lead (Planificateur):** Shift scheduler and team manager
- **Employee:** Gym staff (trainers, receptionists, cleaners, etc.)
- **Member:** Gym members (future phase)

### Key Differentiators
- Multi-location support with centralized management
- Custom-built API inspired by Shiftbase architecture with gym-specific enhancements
- Mobile-first employee experience (Android/iOS)
- Flexible subscription plans based on locations
- Modular feature system per workspace
- Gym-specific features: member management, class booking, personal training sessions

---

## System Architecture Overview

### Platform Structure

```
Platform (SaaS)
│
├── Super Admin Dashboard
│   ├── Workspace Management
│   ├── Feature Toggle per Workspace
│   ├── Subscription Management
│   └── Custom Feature Development
│
└── Workspaces (Client Spaces)
    ├── Workspace 1 (Gym Chain A)
    │   ├── Location 1
    │   ├── Location 2
    │   └── Location 3 (max per site)
    │
    └── Workspace 2 (Gym Chain B)
        ├── Location 1
        └── Location 2
```

### Technology Stack
- **Backend API:** Custom REST API (287+ endpoints inspired by Shiftbase architecture)
  - Enhanced with gym-specific endpoints (members, classes, PT sessions, equipment tracking)
  - Built on Node.js/Express or Python/Django (TBD)
- **Database:** PostgreSQL (see gym_crm_schema.dbml)
- **Frontend:** Web Application + Mobile Apps (iOS/Android)
- **Authentication:** Role-based access control (RBAC) with JWT tokens
- **Real-time:** WebSocket for live updates (clock in/out, schedule changes)

---

## Subscription Plans

### Plan Structure

#### 1. **Solo Plan**
- **Price:** Monthly/Annual billing
- **Scope:** Single gym location
- **Users:** Unlimited employees
- **Features:**
  - Basic scheduling
  - Time tracking
  - Member management
  - Mobile app access

#### 2. **Site Plan**
- **Price:** Monthly/Annual billing (scaled)
- **Scope:** Up to 3 locations per site
- **Users:** Unlimited employees
- **Features:**
  - All Solo features
  - Multi-location dashboard
  - Cross-location reporting
  - Advanced analytics

#### 3. **Enterprise Plan**
- **Price:** Monthly/Annual billing (custom)
- **Scope:** Multiple sites (unlimited locations)
- **Users:** Unlimited employees
- **Features:**
  - All Site features
  - Custom feature development
  - Dedicated support
  - API access
  - White-label options

### Feature Toggles per Workspace
Super Admin can enable/disable features per workspace based on:
- Subscription plan
- Custom requests
- Beta features
- Regional requirements

---

## User Roles & Permissions

### Role Hierarchy

```
Super Admin (Platform)
    │
    ├── Owner (Workspace Admin)
    │   │
    │   ├── System Administrator (All Locations)
    │   │   │
    │   │   ├── Club Manager (Single Location)
    │   │   │   │
    │   │   │   ├── Team Lead (Planificateur/Chef d'équipe)
    │   │   │   │   │
    │   │   │   │   └── Employee (Staff)
    │   │   │   │       │
    │   │   │   │       └── Timesheet Employee (Pointeuse)
```

### Permission Matrix

| Permission Category | Super Admin | Owner | System Admin | Club Manager | Team Lead | Employee |
|-------------------|-------------|--------|--------------|--------------|-----------|----------|
| **Workspace Management** |
| Create workspace | ✓ | | | | | |
| Delete workspace | ✓ | | | | | |
| Toggle features | ✓ | | | | | |
| View all workspaces | ✓ | | | | | |
| **Organization** |
| Manage subscription | ✓ | ✓ | | | | |
| Manage locations | ✓ | ✓ | ✓ | | | |
| Create locations | ✓ | ✓ | ✓ | | | |
| Delete locations | ✓ | ✓ | | | | |
| **Users & Employees** |
| Invite via email | ✓ | ✓ | ✓ | ✓ | | |
| Add employees | ✓ | ✓ | ✓ | ✓ | | |
| Modify employees | ✓ | ✓ | ✓ | ✓ | | |
| Delete employees | ✓ | ✓ | ✓ | | | |
| View all employees | ✓ | ✓ | ✓ | Own location | Own team | |
| Assign teams | ✓ | ✓ | ✓ | ✓ | | |
| Manage contracts | ✓ | ✓ | ✓ | ✓ | | |
| **Planning & Scheduling** |
| Create schedules (all) | ✓ | ✓ | ✓ | ✓ | | |
| Create shifts (team) | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Modify shifts | ✓ | ✓ | ✓ | ✓ | ✓ | Own shifts* |
| Delete shifts | ✓ | ✓ | ✓ | ✓ | | |
| View schedules (all) | ✓ | ✓ | ✓ | Own location | Own team | Own schedule |
| Drag & drop planning | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Manage templates | ✓ | ✓ | ✓ | ✓ | ✓ | |
| **Time Tracking** |
| View all timesheets | ✓ | ✓ | ✓ | Own location | Own team | |
| Add timesheets | ✓ | ✓ | ✓ | ✓ | ✓ | Own |
| Modify timesheets | ✓ | ✓ | ✓ | ✓ | | Own |
| Approve timesheets | ✓ | ✓ | ✓ | ✓ | | |
| Clock in/out (all) | ✓ | | | | | |
| Clock in/out (self) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| View clock status | ✓ | ✓ | ✓ | ✓ | ✓ | Own |
| **Absences** |
| Request absence | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Approve absence (all) | ✓ | ✓ | ✓ | | | |
| Approve absence (team) | ✓ | ✓ | ✓ | ✓ | ✓ | |
| View all absences | ✓ | ✓ | ✓ | Own location | Own team | Own |
| Manage absence types | ✓ | ✓ | ✓ | | | |
| **Messaging** |
| Send to all (workspace) | ✓ | ✓ | | | | |
| Send to all locations | ✓ | ✓ | ✓ | | | |
| Send to location | ✓ | ✓ | ✓ | ✓ | | |
| Send to team | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Send to employee | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Receive messages | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Availability** |
| View availability (all) | ✓ | ✓ | ✓ | Own location | Own team | |
| Set availability | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Modify availability | ✓ | ✓ | ✓ | ✓ | | Own |
| **Reports & Analytics** |
| View all reports | ✓ | ✓ | ✓ | | | |
| View location reports | ✓ | ✓ | ✓ | ✓ | | |
| View team reports | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Generate reports | ✓ | ✓ | ✓ | ✓ | | |
| Export data | ✓ | ✓ | ✓ | | | |

*\*With manager approval*

---

## Core Features

### Feature 1: Multi-Workspace Management

**Priority:** P0 (Critical)
**Epic:** Platform Foundation
**Dependencies:** None

#### Description
Super Admin capability to manage multiple isolated workspaces (gym businesses), each with independent configurations, locations, users, and data.

#### Acceptance Criteria
- [ ] Super Admin can create new workspace with unique identifier
- [ ] Each workspace is completely isolated (data, users, settings)
- [ ] Super Admin can view list of all workspaces
- [ ] Super Admin can access any workspace
- [ ] Super Admin can deactivate/reactivate workspace
- [ ] Workspace includes owner information and contact details
- [ ] Activity logs for all workspace-level changes

#### User Stories

**US-001: Create Workspace**
```gherkin
Given I am logged in as Super Admin
When I navigate to the workspace management page
And I click "Create New Workspace"
And I fill in workspace details:
  | Field               | Value                    |
  | Workspace Name      | Gold's Gym Chain         |
  | Owner Name          | John Smith               |
  | Owner Email         | john@goldsgym.com        |
  | Plan Type           | Enterprise               |
  | Max Locations       | 10                       |
Then a new workspace is created
And an invitation email is sent to the owner
And I can see the workspace in my dashboard
```

**US-002: Toggle Features per Workspace**
```gherkin
Given I am logged in as Super Admin
And I am viewing a workspace "Gold's Gym Chain"
When I access the feature toggle panel
Then I can see all available features:
  | Feature              | Status    |
  | Planning             | Enabled   |
  | Time Tracking        | Enabled   |
  | Member Management    | Disabled  |
  | Custom Reporting     | Enabled   |
And I can enable/disable each feature
And changes are immediately applied to the workspace
```

---

### Feature 2: Location Management

**Priority:** P0 (Critical)
**Epic:** Organization Structure
**Dependencies:** Workspace Management

#### Description
Gym owners and system administrators can create and manage multiple gym locations within their workspace. Each location has independent settings, staff, and operations.

#### Acceptance Criteria
- [ ] Owner can create up to plan limit of locations
- [ ] Each location has unique name, address, timezone
- [ ] System enforces location limits per subscription plan
- [ ] Locations can be activated/deactivated
- [ ] Each location can have custom settings
- [ ] Departments can be created per location
- [ ] Staff can be assigned to one or multiple locations

#### User Stories

**US-010: Create Gym Location**
```gherkin
Given I am logged in as Owner or System Admin
And I have not reached my location limit
When I navigate to "Settings > Locations"
And I click "Add Location"
And I fill in location details:
  | Field          | Value                           |
  | Name           | Downtown Fitness                |
  | Address        | 123 Main St, New York, NY 10001 |
  | Timezone       | America/New_York                |
  | Phone          | +1 212-555-0100                 |
  | Manager        | Sarah Johnson                   |
Then the location is created
And I can assign employees to this location
And the location appears in all location dropdowns
```

**US-011: Location Settings**
```gherkin
Given I am a Club Manager for "Downtown Fitness"
When I access "Location Settings"
Then I can configure:
  | Setting Category          | Options                                    |
  | Working Hours             | Monday-Sunday times                        |
  | Time Clock Settings       | GPS radius, IP restrictions                |
  | Break Policies            | Auto-calculate breaks                      |
  | Notifications             | Email/SMS for shifts, absences             |
  | Shift Types               | Morning, Evening, Night (custom colors)    |
And changes apply only to this location
```

---

### Feature 3: Team & Employee Management

**Priority:** P0 (Critical)
**Epic:** Workforce Management
**Dependencies:** Location Management

#### Description
Complete employee lifecycle management including hiring, team assignments, contracts, skills, and permissions.

#### Acceptance Criteria
- [ ] Managers can invite employees via email
- [ ] Employee profiles include personal and employment data
- [ ] Employees can be assigned to teams
- [ ] Multiple contracts per employee supported
- [ ] Skills and certifications tracked
- [ ] Role-based permissions per employee
- [ ] Employee deactivation preserves historical data

#### User Stories

**US-020: Invite Employee via Email**
```gherkin
Given I am a Club Manager
When I navigate to "Employees > Add Employee"
And I enter employee email "trainer@gym.com"
And I select role "Employee"
And I select location "Downtown Fitness"
And I select teams ["Personal Training", "Morning Shift"]
And I click "Send Invitation"
Then an invitation email is sent with app installation link
And the employee status is "Pending Activation"
And I receive notification when they activate their account
```

**US-021: Employee Completes Profile**
```gherkin
Given I received an invitation email as a new employee
When I click the activation link
And I download and install the mobile app
And I create my account with password
Then I am prompted to complete my profile:
  | Field                 | Required |
  | Photo                 | No       |
  | Phone Number          | Yes      |
  | Emergency Contact     | Yes      |
  | Date of Birth         | No       |
  | Address               | No       |
And I set my availability preferences
And I can access my schedule immediately
```

**US-022: Assign Employee to Teams**
```gherkin
Given I am a Club Manager
And I am viewing employee "Alex Martinez"
When I go to "Teams & Permissions" tab
Then I can see all available teams:
  | Team Name            | Department      | Current Status |
  | Personal Training    | Fitness         | Assigned       |
  | Morning Shift        | Operations      | Assigned       |
  | Yoga Instructors     | Classes         | Not Assigned   |
And I can add/remove team assignments
And changes are reflected in scheduling immediately
```

---

### Feature 4: Planning & Scheduling (Drag & Drop)

**Priority:** P0 (Critical)
**Epic:** Workforce Scheduling
**Dependencies:** Team & Employee Management

#### Description
Visual drag-and-drop shift scheduling with multiple views (month, week, day), conflict detection, shift templates, and team-based planning.

#### Acceptance Criteria
- [ ] Drag and drop shifts between employees
- [ ] Multiple view modes: Month, Week, Day, Team, Employee
- [ ] Shift templates for recurring schedules
- [ ] Real-time conflict detection (availability, skills, time)
- [ ] Copy schedule from previous week/month
- [ ] Shift color coding by type
- [ ] Employee can modify their shifts with approval
- [ ] Notifications sent when schedule published/changed

#### User Stories

**US-030: Create Shift with Drag & Drop**
```gherkin
Given I am a Team Lead viewing the weekly schedule
When I drag the "Morning Shift (08:00-16:00)" template
And I drop it on "Alex Martinez" on "Monday, Jan 15"
Then the shift is created with:
  | Field           | Value                    |
  | Employee        | Alex Martinez            |
  | Date            | January 15, 2025         |
  | Start Time      | 08:00                    |
  | End Time        | 16:00                    |
  | Break Duration  | 60 minutes (auto-calc)   |
  | Status          | Scheduled                |
And conflict detection runs automatically
And Alex receives a notification about the new shift
```

**US-031: Conflict Detection**
```gherkin
Given I am planning a shift for "Sarah Johnson"
When I try to assign shift "16:00-22:00" on Tuesday
And Sarah already has a shift "08:00-16:00" on Tuesday
Then I see a warning:
  "⚠ Conflict: Employee has insufficient rest time (8h minimum required)"
And I can choose to:
  | Option                          | Action                               |
  | Assign anyway                   | Creates shift with warning flag      |
  | Adjust times                    | Modify start/end times               |
  | Assign to another employee      | Opens employee selector              |
```

**US-032: Apply Shift Template**
```gherkin
Given I am a Club Manager
And I have a template "Standard Week - Personal Training Team"
When I select week "January 15-21, 2025"
And I click "Apply Template"
And I select template "Standard Week - Personal Training Team"
Then all shifts from the template are applied:
  | Day       | Employee       | Shift Type      | Time        |
  | Monday    | Trainer A      | Morning         | 06:00-14:00 |
  | Monday    | Trainer B      | Evening         | 14:00-22:00 |
  | Tuesday   | Trainer A      | Morning         | 06:00-14:00 |
  | ...       | ...            | ...             | ...         |
And I can modify individual shifts after applying
```

**US-033: Employee Modifies Own Shift**
```gherkin
Given I am an employee
And I have a scheduled shift "08:00-16:00" tomorrow
When I view my schedule in the mobile app
And I select the shift
And I request modification:
  | Field      | Current    | Requested  |
  | Start Time | 08:00      | 09:00      |
  | Reason     | -          | "Medical appointment at 8am" |
Then a modification request is sent to my manager
And the shift status changes to "Modification Pending"
And my manager receives a notification
And manager can approve/reject with one tap
```

---

### Feature 5: Time Tracking (Clock In/Out)

**Priority:** P0 (Critical)
**Epic:** Time & Attendance
**Dependencies:** Employee Management, Location Management

#### Description
Multi-method time tracking with mobile app (GPS + photo), biometric kiosks, and web-based clock in/out. Automatic break calculation and timesheet approval workflow.

#### Acceptance Criteria
- [ ] Employees clock in via mobile app with location verification
- [ ] Optional photo capture on clock in
- [ ] Optional fingerprint/face recognition (future)
- [ ] GPS geofencing to restrict clock location
- [ ] IP restriction for web-based clocking
- [ ] Automatic break duration calculation
- [ ] Manager can add/edit timesheets manually
- [ ] Timesheet approval workflow
- [ ] Integration with scheduled shifts

#### User Stories

**US-040: Clock In via Mobile App with Location**
```gherkin
Given I am an employee with mobile app installed
And I am at "Downtown Fitness" location
And GPS is enabled on my phone
When I open the app at 08:05 AM
And I tap "Clock In"
Then the app verifies my GPS location:
  | Check                  | Status     |
  | Within geofence radius | ✓ Passed   |
  | Location accuracy      | ✓ 10m      |
And optionally captures my photo (if enabled)
And creates timesheet record:
  | Field              | Value                    |
  | Clock In Time      | 08:05 AM                 |
  | Clock In Method    | Mobile App               |
  | Location           | Downtown Fitness         |
  | GPS Coordinates    | 40.7128, -74.0060        |
And I see confirmation "Clocked In at 08:05 AM"
```

**US-041: Clock Out with Auto Break Calculation**
```gherkin
Given I clocked in at 08:05 AM
And I am clocking out at 16:10 PM
When I tap "Clock Out"
Then the system calculates:
  | Calculation              | Value          |
  | Total Time               | 8h 5min        |
  | Auto Break (6-8h shift)  | 30min          |
  | Worked Hours             | 7h 35min       |
  | Scheduled Hours          | 8h 0min        |
  | Variance                 | -25min         |
And creates timesheet with status "Pending Approval"
And my manager can review the variance
```

**US-042: Manager Adds Timesheet for Employee**
```gherkin
Given I am a Club Manager
And employee "John Doe" forgot to clock in yesterday
When I navigate to "Timesheet > Add Work Hours"
And I select employee "John Doe"
And I select date "January 14, 2025"
And I enter:
  | Field          | Value                    |
  | Service        | Personal Training        |
  | Team           | Morning Shift            |
  | Start Time     | 08:00                    |
  | End Time       | 16:00                    |
  | Break          | 60 minutes (auto-calc)   |
  | Notes          | Forgot to clock in       |
  | Notify Employee| Yes                      |
Then timesheet is created with status "Approved"
And John receives notification with timesheet details
```

**US-043: Geofence Violation**
```gherkin
Given I am an employee attempting to clock in
And I am NOT within the allowed GPS radius
When I tap "Clock In"
Then I see error message:
  "❌ You are not at an authorized location.
   Please clock in from Downtown Fitness (123 Main St)
   Your current distance: 2.3 km away"
And clock in is blocked
And I can send a location override request to manager
```

---

### Feature 6: Absence Management

**Priority:** P0 (Critical)
**Epic:** Time Off Management
**Dependencies:** Employee Management

#### Description
Complete absence request and approval system with multiple absence types, leave balance tracking, visual calendar, and mobile request capability.

#### Acceptance Criteria
- [ ] Employees request absences via web or mobile
- [ ] Multiple absence types (vacation, sick, parental, etc.)
- [ ] Leave balance tracking by type and year
- [ ] Manager approval workflow
- [ ] Visual calendar with color-coded absences
- [ ] Partial day absences supported
- [ ] Integration with scheduling (shows conflicts)
- [ ] Email notifications for requests/approvals

#### User Stories

**US-050: Employee Requests Absence via Mobile**
```gherkin
Given I am an employee using the mobile app
When I tap "Request Time Off"
And I select absence type "Vacation"
And I see my leave balance:
  | Type           | Total    | Used  | Pending | Remaining |
  | Vacation       | 25 days  | 10    | 5       | 10 days   |
And I select dates:
  | Field      | Value              |
  | Start Date | February 10, 2025  |
  | End Date   | February 14, 2025  |
  | Duration   | 5 days             |
And I enter notes "Family trip to Europe"
And I tap "Submit Request"
Then absence request is created with status "Pending"
And my manager receives notification
And my leave balance shows:
  | Type           | Total    | Used  | Pending | Remaining |
  | Vacation       | 25 days  | 10    | 10      | 5 days    |
```

**US-051: Manager Approves/Rejects Absence**
```gherkin
Given I am a Club Manager
And I receive an absence request notification
When I open the absence request from "Alex Martinez"
Then I see request details:
  | Field           | Value                    |
  | Employee        | Alex Martinez            |
  | Type            | Sick Leave               |
  | Dates           | Jan 20-21, 2025          |
  | Duration        | 2 days                   |
  | Reason          | Doctor appointment       |
  | Leave Balance   | 10 days remaining        |
  | Schedule Impact | 2 shifts need coverage   |
And I can:
  | Option          | Action                                      |
  | Approve         | Approves and updates balance                |
  | Reject          | Requires rejection reason                   |
  | Request Info    | Sends message to employee                   |
And if I approve:
  - Absence status changes to "Approved"
  - Leave balance is deducted
  - Employee receives approval notification
  - Scheduled shifts are marked "Absent - Approved"
```

**US-052: Absence Calendar View**
```gherkin
Given I am a manager viewing the absence calendar
When I navigate to "Absences"
Then I see a 2-month calendar view with color-coded absences:
  | Color    | Absence Type        |
  | Purple   | Public Holiday      |
  | Yellow   | Vacation            |
  | Red      | Sick Leave          |
  | Green    | Parental Leave      |
  | Blue     | Special Leave       |
And I can filter by:
  - Status: Requests, Reviewed, Past
  - Location
  - Team
  - Employee
And I can add absence directly from calendar
```

---

### Feature 7: Messaging & Notifications

**Priority:** P1 (High)
**Epic:** Communication
**Dependencies:** Employee Management, Team Management

#### Description
Multi-level messaging system allowing communication from managers to employees at various organizational levels (all employees, location, team, individual).

#### Acceptance Criteria
- [ ] Send message to all employees in workspace
- [ ] Send message to all employees in location
- [ ] Send message to all employees in team
- [ ] Send message to individual employee
- [ ] Rich text formatting supported
- [ ] Push notifications to mobile app
- [ ] Email notifications as fallback
- [ ] Message read receipts
- [ ] Message history and archives

#### User Stories

**US-060: Manager Sends Message to Team**
```gherkin
Given I am a Team Lead
When I navigate to "Messages > Send Message"
And I select recipients "Personal Training Team"
And I compose message:
  """
  Subject: Team Meeting Tomorrow

  Hi team,

  We have a mandatory team meeting tomorrow at 2 PM in the break room.
  Please confirm your attendance.

  Topics:
  - New equipment training
  - Q1 performance review
  - Schedule changes for February

  Thanks!
  """
And I click "Send"
Then the message is sent to all 12 team members
And they receive push notification on mobile app
And they receive email notification
And I can see delivery status:
  | Status      | Count |
  | Delivered   | 12    |
  | Read        | 0     |
```

**US-061: Employee Receives and Responds**
```gherkin
Given I am an employee
When I receive a message from my manager
Then I see a push notification on my phone
And I tap the notification
And the app opens to the message
And I can:
  | Option          | Action                        |
  | Reply           | Send message back to manager  |
  | Mark as Read    | Updates read receipt          |
  | Archive         | Moves to archive folder       |
And manager sees my read receipt
```

**US-062: Owner Broadcasts to All Locations**
```gherkin
Given I am an Owner with 5 locations
When I navigate to "Messages > Broadcast"
And I select "All Locations"
And I compose urgent message about policy change
And I enable "Require Read Confirmation"
Then message is sent to all 127 employees across 5 locations
And I see real-time delivery dashboard:
  | Location           | Employees | Delivered | Read |
  | Downtown Fitness   | 25        | 25        | 12   |
  | Uptown Gym         | 30        | 30        | 8    |
  | Westside Location  | 28        | 28        | 15   |
  | Eastside Fitness   | 22        | 22        | 10   |
  | Southside Gym      | 22        | 22        | 7    |
And I can send reminder to employees who haven't read
```

---

### Feature 8: Availability Preferences

**Priority:** P1 (High)
**Epic:** Scheduling Optimization
**Dependencies:** Employee Management

#### Description
Employees can set their availability preferences (days/times they can/cannot work), which are visible to managers during shift planning.

#### Acceptance Criteria
- [ ] Employees set weekly availability patterns
- [ ] Recurring and one-time availability supported
- [ ] Preferred, available, and unavailable states
- [ ] Manager visibility during shift planning
- [ ] Conflict warnings when scheduling outside availability
- [ ] Effective date ranges for availability changes
- [ ] Mobile app availability management

#### User Stories

**US-070: Employee Sets Availability**
```gherkin
Given I am an employee
When I navigate to "My Availability"
Then I see a weekly calendar grid
And I can set my availability for each day:
  | Day       | Time Slot      | Status        |
  | Monday    | 06:00-14:00    | Available     |
  | Monday    | 14:00-22:00    | Unavailable   |
  | Tuesday   | 06:00-10:00    | Preferred     |
  | Tuesday   | 10:00-18:00    | Available     |
  | Wednesday | All Day        | Unavailable   |
And I can set effective dates:
  | Start Date        | End Date          |
  | January 15, 2025  | March 15, 2025    |
And I save my availability
And manager is notified of availability changes
```

**US-071: Manager Views Availability During Planning**
```gherkin
Given I am a Team Lead planning shifts
When I drag a shift "18:00-22:00" to employee "Sarah"
And Sarah marked 18:00-22:00 as "Unavailable"
Then I see a warning indicator:
  "⚠ Outside availability: Sarah is unavailable 18:00-22:00"
And I can:
  | Option                    | Action                           |
  | Assign anyway             | Creates shift with warning       |
  | View availability         | Opens Sarah's availability       |
  | Find available employee   | Filters employees available      |
And if I assign anyway, Sarah receives notification asking for confirmation
```

---

### Feature 9: Reports & Analytics

**Priority:** P1 (High)
**Epic:** Business Intelligence
**Dependencies:** All data-generating features

#### Description
Comprehensive reporting system with 25+ pre-built reports covering timesheets, schedules, absences, payroll, and performance analytics.

#### Acceptance Criteria
- [ ] 25+ pre-built report types
- [ ] Custom date range selection
- [ ] Location and team filtering
- [ ] Export to PDF, Excel, CSV
- [ ] Scheduled/recurring reports
- [ ] Favorite reports for quick access
- [ ] Visual charts and graphs
- [ ] Real-time data updates

#### User Stories

**US-080: Generate Timesheet Summary Report**
```gherkin
Given I am a Club Manager
When I navigate to "Reports > Request Report"
And I select report type "Timesheet Summary"
And I configure parameters:
  | Parameter       | Value                    |
  | Date Range      | January 1-31, 2025       |
  | Location        | Downtown Fitness         |
  | Department      | All                      |
  | Group By        | Employee                 |
Then report is generated showing:
  | Employee      | Scheduled Hours | Worked Hours | Overtime | Variance |
  | Alex M.       | 160             | 162          | 2        | +2       |
  | Sarah J.      | 160             | 158          | 0        | -2       |
  | John D.       | 120             | 125          | 5        | +5       |
  | Total         | 440             | 445          | 7        | +5       |
And I can export as PDF or Excel
```

**US-081: Schedule Recurring Report**
```gherkin
Given I am a System Administrator
When I navigate to "Reports > Recurring Reports"
And I click "Create Recurring Report"
And I configure:
  | Field          | Value                         |
  | Report Type    | Payroll Report                |
  | Frequency      | Monthly (1st of month)        |
  | Recipients     | hr@gym.com, owner@gym.com     |
  | Format         | Excel                         |
  | Next Run       | February 1, 2025 at 9:00 AM   |
Then the report is scheduled
And runs automatically on the 1st of each month
And sends via email to recipients
```

---

### Feature 10: Mobile App (Android/iOS)

**Priority:** P0 (Critical)
**Epic:** Mobile Experience
**Dependencies:** All core features

#### Description
Native mobile application for employees with core features: clock in/out, view schedule, request absence, set availability, receive notifications, and communicate with managers.

#### Acceptance Criteria
- [ ] Available on Google Play and App Store
- [ ] Biometric login (fingerprint, Face ID)
- [ ] GPS-based clock in/out with photo
- [ ] Push notifications for schedule changes
- [ ] Offline mode for viewing schedule
- [ ] QR code for quick clock in
- [ ] Real-time sync with web platform
- [ ] Dark mode support

#### User Stories

**US-090: Employee Mobile App First Launch**
```gherkin
Given I am a new employee
When I install the app from invitation email
And I open the app for the first time
Then I see onboarding screens:
  1. "Welcome to [Gym Name]"
  2. "Clock In/Out with GPS"
  3. "View Your Schedule"
  4. "Request Time Off"
  5. "Stay Connected"
And I create my account:
  | Field               | Value                  |
  | Email               | auto-filled            |
  | Password            | Set by employee        |
  | Biometric Login     | Optional setup         |
And I grant permissions:
  | Permission          | Purpose                |
  | Location            | Clock in verification  |
  | Camera              | Photo capture          |
  | Notifications       | Schedule updates       |
Then I land on my dashboard with today's schedule
```

**US-091: Clock In with Photo via Mobile**
```gherkin
Given I am at my gym location
And I open the mobile app
When I tap "Clock In" button
Then app verifies my GPS location
And prompts "Take a photo to confirm identity"
And I take a selfie
Then the app:
  - Uploads photo to server
  - Records GPS coordinates
  - Creates timesheet entry
  - Shows confirmation "Clocked In at 08:05 AM"
And I can see:
  | Display              | Value                  |
  | Clock In Time        | 08:05 AM               |
  | Elapsed Time         | 00:00:15 (live timer)  |
  | Today's Schedule     | 08:00 AM - 04:00 PM    |
```

**US-092: View Schedule on Mobile**
```gherkin
Given I open the mobile app
When I tap "My Schedule"
Then I see my shifts in list view:

  TODAY
  ✓ Morning Shift
    08:00 AM - 04:00 PM
    Personal Training Floor

  TOMORROW
  - Evening Shift
    02:00 PM - 10:00 PM
    Front Desk

  UPCOMING (Next 7 days)
  - 5 shifts scheduled

And I can:
  - Tap shift to see details
  - Switch to calendar view
  - Request shift change
  - Add to device calendar
And shifts update in real-time if manager makes changes
```

---

## Detailed User Stories by Role

### As Super Admin (Platform Administrator)

#### Epic: Workspace Management

**US-SA-001: Monitor Platform Health**
```gherkin
Given I am logged in as Super Admin
When I access the admin dashboard
Then I can see:
  | Metric                    | Value     |
  | Total Workspaces          | 127       |
  | Active Users (24h)        | 1,456     |
  | API Calls (24h)           | 234,567   |
  | Storage Used              | 45.2 GB   |
  | Active Subscriptions      | 125       |
  | Expiring Trials (7 days)  | 12        |
And I can drill down into each metric
```

**US-SA-002: Custom Feature Development**
```gherkin
Given I am Super Admin
And client "Gold's Gym" requests custom feature
When I navigate to their workspace settings
And I enable "Custom Features" panel
And I add feature flag:
  | Feature Name         | member_biometric_checkin     |
  | Description          | Face recognition for members |
  | Status               | Development                  |
  | ETA                  | March 15, 2025               |
Then the feature flag is created
And visible only to this workspace
And I can toggle it on/off for testing
```

**US-SA-003: Manage Subscription Plans**
```gherkin
Given I am Super Admin
When I view workspace "Downtown Fitness Co."
Then I can see their current plan:
  | Plan Details         | Value              |
  | Plan Type            | Site Plan          |
  | Monthly Cost         | $299               |
  | Max Locations        | 3                  |
  | Current Locations    | 2                  |
  | Billing Cycle        | Monthly            |
  | Next Billing         | Feb 15, 2025       |
  | Status               | Active             |
And I can:
  - Upgrade/downgrade plan
  - Apply discount
  - Extend trial
  - Pause subscription
  - View billing history
```

---

### As Owner (Gym Business Owner)

#### Epic: Multi-Location Management

**US-OWN-001: Overview Dashboard**
```gherkin
Given I am an Owner with 3 locations
When I log into my dashboard
Then I see aggregated metrics across all locations:

  WORKFORCE
  | Location           | Employees | Active Today | Scheduled This Week |
  | Downtown Fitness   | 25        | 18           | 25                  |
  | Uptown Gym         | 30        | 22           | 28                  |
  | Westside Location  | 28        | 21           | 27                  |

  TIME TRACKING
  | Location           | Clocked In | Hours Today | Overtime This Week |
  | Downtown Fitness   | 12         | 156.5       | 12.5               |
  | Uptown Gym         | 15         | 187.2       | 8.0                |
  | Westside Location  | 14         | 172.8       | 15.2               |

  ABSENCES
  | Location           | Pending | Approved This Week | Sick Days MTD |
  | Downtown Fitness   | 3       | 5                  | 12            |
  | Uptown Gym         | 2       | 4                  | 8             |
  | Westside Location  | 4       | 6                  | 15            |
```

**US-OWN-002: Cross-Location Reporting**
```gherkin
Given I am an Owner
When I generate a "Labor Cost Report"
And I select:
  | Parameter          | Value                  |
  | Date Range         | January 2025           |
  | Locations          | All (3 locations)      |
  | Group By           | Location, Department   |
Then I see consolidated report:
  | Location/Dept      | Scheduled | Actual  | Labor Cost | Variance |
  | Downtown Fitness   |           |         |            |          |
  |   Personal Training| 320h      | 335h    | $8,375     | +$375    |
  |   Front Desk       | 160h      | 158h    | $2,370     | -$30     |
  | Uptown Gym         |           |         |            |          |
  |   Personal Training| 280h      | 290h    | $7,250     | +$250    |
  | ...                |           |         |            |          |
  | TOTAL              | 1,520h    | 1,567h  | $39,175    | +$1,175  |
And I can export for accounting system
```

**US-OWN-003: Manage System Administrators**
```gherkin
Given I am an Owner
When I navigate to "Settings > System Administrators"
Then I can see my admin team:
  | Name           | Email                | Locations    | Last Login     |
  | Sarah Johnson  | sarah@gym.com        | All          | 2 hours ago    |
  | Mike Davis     | mike@gym.com         | All          | 1 day ago      |
And I can:
  - Invite new system admin via email
  - Assign access to specific locations
  - Remove admin access
  - View audit log of admin actions
```

---

### As System Administrator (Multi-Location Admin)

#### Epic: Cross-Location Operations

**US-SYS-001: Manage All Locations**
```gherkin
Given I am a System Administrator
When I access "Locations" module
Then I can see all 3 locations:
  | Location           | Manager        | Employees | Status  | Actions      |
  | Downtown Fitness   | Sarah Johnson  | 25        | Active  | View, Edit   |
  | Uptown Gym         | Mike Davis     | 30        | Active  | View, Edit   |
  | Westside Location  | Alex Martinez  | 28        | Active  | View, Edit   |
And I can:
  - Create new location (within plan limit)
  - Edit location settings
  - Assign/change location managers
  - View location-specific reports
  - Deactivate location (with confirmation)
```

**US-SYS-002: Transfer Employee Between Locations**
```gherkin
Given I am a System Administrator
And employee "John Trainer" works at Downtown Fitness
When I navigate to employee profile
And I select "Transfer to Another Location"
And I choose:
  | Field              | Value                    |
  | From Location      | Downtown Fitness         |
  | To Location        | Uptown Gym               |
  | Transfer Date      | February 1, 2025         |
  | Keep Teams         | Yes (where applicable)   |
  | Notify Employee    | Yes                      |
  | Notify Managers    | Both locations           |
Then transfer is processed:
  - Future shifts at Downtown cancelled (with notice)
  - Employee assigned to Uptown Gym
  - Teams mapped to equivalent at new location
  - Notifications sent
  - Transfer logged in audit trail
```

**US-SYS-003: Create Shift Template for All Locations**
```gherkin
Given I am a System Administrator
When I create a shift template
And I name it "Standard Personal Training Week"
And I configure:
  | Day       | Shift Name    | Time        | Breaks | Required Skills     |
  | Monday    | Morning PT    | 06:00-14:00 | 60min  | Personal Training   |
  | Monday    | Evening PT    | 14:00-22:00 | 60min  | Personal Training   |
  | Tuesday   | Morning PT    | 06:00-14:00 | 60min  | Personal Training   |
  | ...       | ...           | ...         | ...    | ...                 |
And I select "Available to all locations"
Then the template is saved
And all location managers can use it for planning
```

---

### As Club Manager (Single Location Manager)

#### Epic: Location-Specific Management

**US-CLB-001: Daily Operations Dashboard**
```gherkin
Given I am a Club Manager at Downtown Fitness
When I log in at start of day
Then I see my location dashboard:

  TODAY'S SNAPSHOT
  | Metric                  | Value              |
  | Employees Scheduled     | 18                 |
  | Currently Clocked In    | 12                 |
  | Not Clocked In (late)   | 2 ⚠                |
  | Classes Today           | 8                  |
  | Members Checked In      | 67                 |

  ALERTS
  ⚠ 2 employees late (not clocked in)
  ⚠ 3 pending absence requests
  ℹ 1 shift needs coverage tomorrow

  QUICK ACTIONS
  - Add timesheet
  - Create shift
  - Send message to team
  - View reports
```

**US-CLB-002: Handle Employee Late Arrival**
```gherkin
Given I am a Club Manager
And employee "Sarah" was scheduled at 08:00
And it's now 08:15 and she hasn't clocked in
When I tap the alert "Sarah - Not Clocked In"
Then I see options:
  | Option              | Action                              |
  | Call Employee       | Opens phone to call Sarah           |
  | Send Message        | Send "Are you coming?" message      |
  | Add Timesheet       | Manually add late clock in          |
  | Mark Absent         | Mark as absent for today            |
And if I select "Add Timesheet"
And I enter clock in time "08:15"
And I check "Notify employee"
Then timesheet is created
And Sarah receives notification with late arrival note
```

**US-CLB-003: Approve Pending Requests**
```gherkin
Given I am a Club Manager
When I navigate to "Pending Approvals"
Then I see all items requiring my attention:

  ABSENCES (3)
  - Alex Martinez: Vacation Feb 10-14 (5 days)
  - Sarah Johnson: Sick Leave Jan 20 (1 day)
  - John Trainer: Personal Leave Jan 25 (1 day)

  SHIFT CHANGES (1)
  - Mike Davis: Modify shift Jan 18 (9:00 start → 10:00 start)

  TIMESHEETS (2)
  - Jane Smith: Missing clock out Jan 15
  - Tom Wilson: Overtime 10.5 hours this week

And I can:
  - Approve all
  - Review individually
  - Bulk approve by type
  - Reject with reason
And all decisions notify employees immediately
```

---

### As Team Lead (Planificateur / Chef d'équipe)

#### Epic: Team Scheduling & Management

**US-TL-001: Create Team Weekly Schedule**
```gherkin
Given I am a Team Lead for "Personal Training Team"
When I create schedule for week "Jan 15-21"
Then I see my team members:
  | Trainer        | Availability  | Skills              | Hours This Week |
  | Alex Martinez  | Full-time     | PT, Nutrition       | 32/40          |
  | Sarah Johnson  | Part-time     | PT, Yoga            | 18/25          |
  | John Trainer   | Full-time     | PT, Strength        | 35/40          |
  | Jane Smith     | Part-time     | PT, Pilates         | 12/20          |
And I can:
  - Drag shifts from template library
  - See real-time availability conflicts
  - Ensure each trainer hits their target hours
  - Balance morning/evening coverage
  - Assign specific clients to trainers (if applicable)
```

**US-TL-002: Handle Shift Coverage Request**
```gherkin
Given I am a Team Lead
And trainer "Alex" calls in sick for tomorrow's shift
When I navigate to "Open Shifts"
And I create open shift:
  | Field           | Value                    |
  | Original Shift  | Tomorrow 10:00-18:00     |
  | Team            | Personal Training        |
  | Required Skill  | Personal Training Cert   |
  | Priority        | Urgent                   |
  | Notes           | "Alex sick, need cover"  |
Then eligible team members receive notification:
  "🔔 Open Shift Available
   Tomorrow 10:00-18:00 at Downtown Fitness
   Tap to claim this shift"
And I see who views/claims in real-time
And I can assign if no one claims within 30 minutes
```

**US-TL-003: Review Team Performance**
```gherkin
Given I am a Team Lead
When I access "Team Performance" report
And I select:
  | Parameter       | Value                    |
  | Team            | Personal Training        |
  | Period          | January 2025             |
Then I see team metrics:
  | Trainer        | Scheduled | Worked | Overtime | Absences | Late Arrivals |
  | Alex Martinez  | 160h      | 162h   | 2h       | 0        | 1             |
  | Sarah Johnson  | 100h      | 98h    | 0h       | 2        | 0             |
  | John Trainer   | 160h      | 165h   | 5h       | 1        | 3             |
  | Jane Smith     | 80h       | 82h    | 2h       | 0        | 0             |
And I can identify:
  - Who consistently works overtime
  - Attendance patterns
  - Top performers
  - Areas for improvement
```

---

### As Employee (General Staff)

#### Epic: Employee Self-Service

**US-EMP-001: View My Schedule**
```gherkin
Given I am an employee
When I open the mobile app
Then I land on "My Schedule" with this week's shifts:

  TODAY - Monday, Jan 15
  ✓ Morning Shift
    08:00 AM - 04:00 PM
    Personal Training Floor
    [Clock In] button

  TOMORROW - Tuesday, Jan 16
  - Evening Shift
    02:00 PM - 10:00 PM
    Front Desk

  WEDNESDAY - Jan 17
  - Off

  UPCOMING
  📅 5 shifts in next 7 days

And I can:
  - Tap shift to see details
  - Request shift change
  - Add to device calendar
  - Set availability for future
```

**US-EMP-002: Request Shift Modification**
```gherkin
Given I have a shift tomorrow 08:00-16:00
And I need to start at 09:00 instead
When I tap the shift
And I select "Request Change"
And I modify start time to 09:00
And I enter reason "Doctor appointment at 8 AM"
And I tap "Send Request"
Then my manager receives notification:
  "📬 Shift Change Request
   Employee: Sarah Johnson
   Shift: Tomorrow 08:00-16:00
   Requested: 09:00-16:00
   Reason: Doctor appointment at 8 AM
   [Approve] [Reject] [Message]"
And I see status "Change Pending"
And I receive push notification when manager responds
```

**US-EMP-003: Check My Hours This Week**
```gherkin
Given I am an employee
When I navigate to "My Hours" in the app
Then I see current week summary:

  WEEK OF JAN 15-21, 2025

  | Day       | Scheduled | Worked  | Status    |
  | Monday    | 8:00      | 8:05    | Approved  |
  | Tuesday   | 8:00      | -       | Scheduled |
  | Wednesday | Off       | -       | -         |
  | Thursday  | 8:00      | -       | Scheduled |
  | Friday    | 8:00      | -       | Scheduled |
  | Saturday  | 6:00      | -       | Scheduled |
  | Sunday    | Off       | -       | -         |

  TOTALS
  Scheduled: 38 hours
  Worked: 8.05 hours
  Remaining: 29.95 hours

And I can:
  - View detailed timesheet for each day
  - See break durations
  - Check overtime hours
  - Download as PDF
```

**US-EMP-004: Communicate with Manager**
```gherkin
Given I am an employee
When I need to message my manager
And I tap "Messages" in the app
And I tap "New Message"
Then I can select recipient:
  | Option            | Description                    |
  | My Manager        | Sarah Johnson (Club Manager)   |
  | My Team Lead      | Alex Martinez (Team Lead)      |
  | HR                | hr@gym.com                     |
And I compose message:
  "Hi Sarah, I wanted to discuss my schedule for next month.
   I'll have limited availability due to evening classes.
   Can we meet this week?"
And I send
Then manager receives push notification
And I get read receipt when manager opens it
```

---

### As Timesheet Employee (Pointeuse - Clock Specialist)

#### Epic: Time Clock Operations

**US-TSE-001: Clock In via Kiosk**
```gherkin
Given I am at the gym kiosk terminal
When I tap "Clock In" on the kiosk screen
And I enter my PIN code "1234"
Or I use fingerprint scanner (if enabled)
Then the kiosk:
  - Verifies my identity
  - Checks I'm not already clocked in
  - Records clock in time
  - Shows confirmation:
    "✓ Clocked In
     Sarah Johnson
     08:05 AM
     Have a great shift!"
And my manager sees me in "Currently Clocked In" list
```

**US-TSE-002: Clock In via QR Code**
```gherkin
Given I am an employee with mobile app
And my gym has QR codes posted
When I arrive at work
And I open the app camera
And I scan the gym's QR code
Then the app:
  - Verifies location
  - Clocks me in instantly
  - Shows confirmation
And I didn't need to navigate through menus
```

**US-TSE-003: Forgot to Clock Out**
```gherkin
Given I clocked in yesterday at 08:00
And I forgot to clock out
And I'm now home at 6 PM
When I open the mobile app
Then I see notification:
  "⚠ You forgot to clock out yesterday
   Your shift was scheduled 08:00-16:00

   [Add Clock Out Time]"
And I can:
  | Option                | Action                              |
  | Add Clock Out         | Enter clock out time (requires approval) |
  | Message Manager       | Explain and request manual entry    |
And if I add clock out time:
  - Request goes to manager for approval
  - Manager can approve/modify
  - Timesheet updated upon approval
```

---

## API Development Strategy

### Why Custom Development vs Integration?

**Decision Rationale:**
1. **Full Control:** Complete ownership of features, data, and roadmap
2. **Gym-Specific Features:** Need member management, class booking, PT sessions not in Shiftbase
3. **Cost Efficiency:** No per-user licensing fees to third-party service
4. **Customization:** Can modify any feature to match exact gym workflows
5. **Data Ownership:** All data stays within our infrastructure
6. **Scalability:** No vendor limitations on users, locations, or API calls
7. **Branding:** White-label capability for enterprise clients

**Shiftbase as Reference Architecture:**
- Use their proven API structure (287+ endpoints) as blueprint
- Learn from their workforce management best practices
- Adopt similar endpoint naming conventions for familiarity
- Implement their tested permission models
- Reference their data schemas for core workforce tables

**Our Custom Enhancements:**
```diff
Shiftbase Core (What we adopt):
+ Employee management
+ Shift scheduling & planning
+ Time tracking & clock in/out
+ Absence management
+ Team organization
+ Reporting & analytics
+ Multi-location support

Gym-Specific Additions (What we build):
+ Member management & profiles
+ Membership plans & subscriptions
+ Class scheduling & booking
+ Personal training sessions
+ Equipment tracking
+ Member check-in system
+ Class capacity management
+ Trainer-client matching
+ Gym-specific KPIs & reports
```

### API Development Principles

**1. RESTful Best Practices**
- Use proper HTTP methods (GET, POST, PUT, PATCH, DELETE)
- Resource-based URLs (e.g., `/api/v1/employees/{id}`)
- Stateless requests with JWT tokens
- HATEOAS for resource navigation (optional)

**2. Consistent Response Format**
```json
// Success Response
{
  "success": true,
  "data": { ... },
  "meta": {
    "timestamp": "2025-11-09T10:30:00Z",
    "version": "1.0"
  }
}

// Error Response
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The email field is required",
    "field": "email",
    "details": { ... }
  }
}

// Paginated Response
{
  "success": true,
  "data": [ ... ],
  "meta": {
    "pagination": {
      "current_page": 1,
      "per_page": 20,
      "total": 156,
      "total_pages": 8,
      "next": "/api/v1/employees?page=2",
      "prev": null
    }
  }
}
```

**3. Versioning Strategy**
- URL versioning: `/api/v1/`, `/api/v2/`
- Maintain backward compatibility for at least 2 major versions
- Deprecation warnings 6 months before removal
- Clear migration guides for breaking changes

**4. Authentication & Authorization**
- JWT tokens with refresh token mechanism
- Role-based access control (RBAC) on all endpoints
- Permission checks at controller level
- API key authentication for third-party integrations (Phase 3)

**5. Documentation Standards**
- OpenAPI 3.0 specification for all endpoints
- Auto-generated interactive documentation (Swagger/Redoc)
- Code examples in multiple languages
- Postman collection for easy testing

---

## Technical Requirements

### Custom API Development (Inspired by Shiftbase)

#### API Architecture

**RESTful Design Principles**
- Resource-based endpoints following REST conventions
- JSON request/response format
- Versioned API (v1, v2, etc.)
- Comprehensive error handling with standard HTTP status codes
- Rate limiting and throttling for API stability

**Core API Modules** (287+ endpoints total)

| Module | Example Endpoints | Description | Gym-Specific Enhancements |
|--------|------------------|-------------|--------------------------|
| **Authentication** | `/api/v1/auth/login`<br>`/api/v1/auth/refresh-token`<br>`/api/v1/auth/logout` | User authentication & session management | 2FA support, biometric token exchange |
| **Employees** | `/api/v1/employees`<br>`/api/v1/employees/{id}`<br>`/api/v1/employees/batch` | Employee CRUD operations | Certification tracking, skills matrix |
| **Shifts** | `/api/v1/shifts`<br>`/api/v1/shifts/batch`<br>`/api/v1/shifts/conflicts` | Shift scheduling & management | Class instructor scheduling, equipment allocation |
| **Timesheets** | `/api/v1/timesheets/clock`<br>`/api/v1/timesheets`<br>`/api/v1/timesheets/approve` | Time tracking & attendance | GPS verification, photo capture, biometric validation |
| **Absences** | `/api/v1/absences`<br>`/api/v1/absences/{id}/approve`<br>`/api/v1/absence-types` | Leave management | Trainer coverage matching |
| **Teams** | `/api/v1/teams`<br>`/api/v1/team-members`<br>`/api/v1/team-days` | Team organization | Specialized teams (PT, yoga, spin, etc.) |
| **Locations** | `/api/v1/locations`<br>`/api/v1/locations/{id}/settings` | Multi-location management | Equipment inventory per location |
| **Members** | `/api/v1/members`<br>`/api/v1/memberships`<br>`/api/v1/members/check-in` | Member management | ⭐ Gym-specific: membership plans, check-ins |
| **Classes** | `/api/v1/classes`<br>`/api/v1/classes/bookings`<br>`/api/v1/class-types` | Class scheduling & booking | ⭐ Gym-specific: capacity management, waitlists |
| **Personal Training** | `/api/v1/pt-sessions`<br>`/api/v1/pt-packages`<br>`/api/v1/pt-sessions/book` | PT session management | ⭐ Gym-specific: trainer-client matching |
| **Reports** | `/api/v1/reports/request`<br>`/api/v1/reports/bi/payroll`<br>`/api/v1/reports/favorites` | Business intelligence | Custom gym KPIs (retention, attendance) |
| **Messaging** | `/api/v1/messages/send`<br>`/api/v1/notifications`<br>`/api/v1/news` | Internal communication | Push notifications, in-app messaging |
| **Workspaces** | `/api/v1/workspaces`<br>`/api/v1/workspaces/{id}/features` | Multi-tenant management | ⭐ Custom: feature toggles per workspace |

⭐ = Custom endpoints not in original Shiftbase architecture

#### Data Consistency & Caching

**Caching Strategy**
- Redis for session management and frequently accessed data
- In-memory caching for location/department/team lists
- Cache invalidation on data updates
- CDN caching for static assets

**Database Optimization**
- Indexed queries for all foreign keys
- Partitioning for timesheets table (by date)
- Read replicas for reporting queries
- Connection pooling for performance

#### Error Handling & Resilience

**API Error Responses**
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The email field is required",
    "field": "email",
    "status": 422
  }
}
```

**Error Categories**
- **400 Bad Request:** Invalid input data
- **401 Unauthorized:** Missing/invalid authentication
- **403 Forbidden:** Insufficient permissions
- **404 Not Found:** Resource doesn't exist
- **422 Unprocessable Entity:** Validation errors
- **429 Too Many Requests:** Rate limit exceeded
- **500 Internal Server Error:** Server-side error
- **503 Service Unavailable:** Maintenance mode

**Retry Logic**
- Exponential backoff for failed requests
- Circuit breaker pattern for external services
- Graceful degradation when subsystems fail
- Queue system for background jobs (shift notifications, report generation)

### Mobile App Technical Specs

**Platform Requirements**
- **iOS:** 14.0 and above
- **Android:** API Level 26 (Android 8.0) and above
- **Framework:** React Native or Flutter (TBD)

**Offline Capabilities**
- View schedule (cached up to 30 days)
- View timesheets (cached last 90 days)
- Queue clock in/out when offline (sync when online)
- Read messages (cached last 100 messages)

**Security**
- Biometric authentication (Face ID, Touch ID, Fingerprint)
- Encrypted local storage
- SSL pinning for API calls
- Auto-logout after 15 minutes inactivity
- No sensitive data in logs

**Push Notifications**
```json
{
  "notification_types": [
    "shift_assigned",
    "shift_modified",
    "shift_reminder_1h",
    "absence_approved",
    "absence_rejected",
    "message_received",
    "schedule_published",
    "timesheet_approved",
    "late_clock_in_warning"
  ]
}
```

### Database Schema

See `gym_crm_schema.dbml` for complete database design.

**Architecture:** PostgreSQL with multi-tenant isolation per workspace

**Core Tables (Workforce Management):**
- `users` - System authentication and authorization
- `employees` - Employee profiles with Shiftbase-inspired fields
- `locations` - Multi-location gym management
- `departments` - Organizational units per location
- `teams` - Work teams and team memberships
- `shifts` - Scheduled work shifts
- `timesheets` - Time tracking and clock in/out records
- `absences` - Time off requests and leave management
- `availabilities` - Employee availability preferences
- `contracts` - Employment contracts and compensation
- `skills` - Employee skills and certifications

**Gym-Specific Tables (Custom Extensions):**
- `members` - Gym member profiles
- `memberships` - Active membership subscriptions
- `membership_plans` - Available membership tiers
- `classes` - Group fitness class schedules
- `class_bookings` - Member class reservations
- `class_types` - Class categories (Yoga, Spin, CrossFit, etc.)
- `pt_sessions` - Personal training appointments
- `pt_packages` - PT session bundles
- `member_pt_packages` - Member-purchased PT packages

**System Tables:**
- `workspaces` - Multi-tenant workspace isolation (implied in schema)
- `permissions` - Granular permission definitions
- `api_tokens` - API authentication tokens
- `activity_logs` - Audit trail for all actions
- `custom_fields` - Flexible custom field definitions
- `sync_logs` - Background job tracking (not for Shiftbase sync)

**Indexes & Optimization:**
- Composite indexes on frequently queried fields (employee_id + date for timesheets)
- Full-text search indexes for employee/member names
- Partitioning strategy for timesheet and attendance tables by month
- Foreign key constraints with cascade rules for data integrity

### Performance Requirements

**Response Times**
- Page load: < 2 seconds
- API calls: < 500ms (95th percentile)
- Clock in/out: < 1 second
- Real-time updates: < 5 seconds

**Scalability**
- Support up to 10,000 employees per workspace
- Handle 100 concurrent users per location
- Store 5 years of historical data
- Process 50,000 clock in/out transactions per day

**Availability**
- 99.9% uptime SLA
- Scheduled maintenance windows: Sundays 2-4 AM
- Automatic failover for critical services
- Data backup every 6 hours

### Security & Compliance

**Data Protection**
- GDPR compliance (EU users)
- Data encryption at rest (AES-256)
- Data encryption in transit (TLS 1.3)
- Role-based access control (RBAC)
- Audit logs for all sensitive operations

**Authentication**
- Password complexity requirements
- 2FA optional for admin roles
- Session timeout after 30 minutes inactivity
- Password reset via email verification
- Account lockout after 5 failed attempts

**Data Retention**
- Active employee data: Indefinite
- Terminated employee data: 7 years (configurable)
- Timesheets: 7 years (legal requirement)
- Audit logs: 3 years
- Deleted data: Soft delete with 30-day recovery

---

## Success Metrics

### Key Performance Indicators (KPIs)

**User Adoption**
- 90% of employees active on mobile app within 30 days
- 95% of shifts created using drag-and-drop interface
- 80% of absence requests submitted via mobile

**Operational Efficiency**
- 50% reduction in scheduling time vs manual methods
- 99% accuracy in timesheet records
- 90% first-time clock-in success rate (no location errors)
- Average manager approval time < 24 hours

**Business Impact**
- 20% reduction in labor cost variance
- 15% reduction in absenteeism
- 25% improvement in shift coverage
- 98% employee satisfaction with app

**Technical Performance**
- 99.9% API uptime
- < 100ms API response time (95th percentile)
- < 100ms database query time (avg)
- < 5MB mobile app data usage per day per user
- < 1% API error rate
- 100% endpoint test coverage

---

## Release Roadmap

### Phase 1: MVP (Months 1-3)
- [ ] Workspace management (Super Admin)
- [ ] Location and employee management
- [ ] Basic scheduling (drag & drop)
- [ ] Time tracking (clock in/out)
- [ ] Mobile app (iOS/Android) - core features
- [ ] Basic reporting
- [ ] Core API development (authentication, employees, shifts, timesheets)

### Phase 2: Enhanced Features (Months 4-6)
- [ ] Absence management
- [ ] Availability preferences
- [ ] Messaging system
- [ ] Shift templates
- [ ] Advanced conflict detection
- [ ] Biometric clock in (fingerprint)
- [ ] Push notifications
- [ ] Recurring reports

### Phase 3: Advanced Analytics (Months 7-9)
- [ ] 25+ BI reports (payroll, labor cost, attendance, etc.)
- [ ] Performance insights dashboard
- [ ] Sentiment tracking
- [ ] Custom dashboards per role
- [ ] Labor cost optimization algorithms
- [ ] Predictive scheduling (AI-based)
- [ ] Public API documentation and developer portal
- [ ] Webhook system for real-time integrations
- [ ] OAuth 2.0 for third-party app access

### Phase 4: Member Management (Months 10-12)
- [ ] Member profiles
- [ ] Membership plans
- [ ] Class booking
- [ ] Personal training sessions
- [ ] Member check-in
- [ ] Member mobile app
- [ ] Payment integration

---

## Appendix

### Glossary

| Term | Definition |
|------|------------|
| **Workspace** | Isolated tenant space for a gym business (owner + all their locations) |
| **Location** | Physical gym site/branch |
| **Department** | Organizational unit within a location (e.g., Personal Training, Front Desk) |
| **Team** | Group of employees working together (e.g., Morning Shift Team) |
| **Shift** | Scheduled work period for an employee |
| **Timesheet** | Record of actual hours worked |
| **Pointeuse** | French term for time clock/employee who clocks in |
| **Planificateur** | French term for scheduler/planner |
| **Chef d'équipe** | French term for team leader |

### References

**Source Documentation (Shiftbase-inspired architecture):**
- Shiftbase API Reference (for architectural inspiration): `SHIFTBASE_API_README_EN.md`
- Complete Endpoint Catalog (287+ endpoints): `SHIFTBASE_API_ENDPOINTS_COMPLETE_EN.md`

**Project-Specific Documentation:**
- Frontend Sitemap & User Flows: `FRONTEND_SITEMAP.md`
- Database Schema (PostgreSQL): `gym_crm_schema.dbml`
- Role-Based Permissions Matrix: `permissions/permissions_roles.md`
- User Permissions by Module:
  - `permissions/utilisateurs_permissions.md`
  - `permissions/horaires_permissions.md`
  - `permissions/feuilles_presence_permissions.md`
  - `permissions/absence_permissions.md`
  - Additional permission files in `/permissions` directory

**Technical Notes:**
- Our API will be custom-developed based on Shiftbase's proven architecture
- We extend their workforce management model with gym-specific features
- All 287+ endpoints will be built from scratch, not integrated
- Database schema includes both Shiftbase-inspired tables and custom gym tables

---

**Document Control**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | Nov 9, 2025 | Product Owner | Initial creation based on requirements analysis |
| 1.1 | Nov 9, 2025 | Product Owner | Updated to reflect custom API development (not integration) |

**Approvals**

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Product Owner | | | |
| Tech Lead | | | |
| Stakeholder | | | |

---

*End of Document*
