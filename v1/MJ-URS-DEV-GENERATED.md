# MJ (MicroJobber) User Requirement Workflow

This document outlines the complete workflow for the MicroJobber (MJ) system, which facilitates job assignments for Active Ageing Centre (AAC) and Senior Care Centre (SCC) clients.

## Table of Contents
1. [Services and Payment Structure](#1-services-and-payment-structure)
2. [Publishing of Tasks](#2-publishing-of-tasks)
3. [MJ Onboarding](#3-mj-onboarding)
4. [Task Creation](#4-task-creation)
5. [Cancellation Policies](#5-cancellation-policies)
6. [No-Show Policies](#6-no-show-policies)
7. [Task Assignment](#7-task-assignment)
8. [Dashboards](#8-dashboards)
9. [Reporting](#9-reporting)
10. [SCC-Specific Requirements](#10-scc-specific-requirements)
11. [Potential Design & Development Problems](#11-potential-design--development-problems)

---

## 1. Services and Payment Structure

### 1.1 Available Services

#### A. Service Types

| # | Service | Client Type | Schedule | Payment | Min Payment | Thereafter |
|---|---------|-------------|----------|---------|-------------|------------|
| 1.1 | Chaperone | AAC (ad hoc SCC client) and SCC clients | Blocks of 1 hr | By Hour | 1 hr for first 1 hr | 0.50 round to 1 hr |
| 1.2 | Befriending | AAC clients | Blocks of 1 hr | By Hour | 1 hr for first 1 hr | 0.50 round to 1 hr |
| 1.3 | Home Assessments | AAC Clients / Prospect | Blocks of 1 hr | By Hour | 1 hr for first 1 hr | 0.50 round to 1 hr |
| 1.4 | Center Assistants | AAC | Blocks of 1 hr | By Hour | 1 hr for first 1 hr | 0.50 round to 1 hr |

#### B. Fee Tables (MJ Payment)
- Per hour rate varies by service type (e.g., Chaperone rate differs from Center Assistant rate)

### 1.2 Payment Logic

- **Start time - End Time**: System records actual working hours
- **Center staff amendments**: Staff can amend start/end time (configurable)
- **Payment extraction**: Periodically, users can extract via Excel the hours/jobs completed for MJ payment workflow with HR and Finance

---

## 2. Publishing of Tasks

### 2.1 Chaperone Service

#### Workflow Steps:

**a) Initiated by SCC Nurse**

**b) Determine complexity** (either assign to MJ or SCC staff)
   - Complexity levels: H (High), M (Medium), L (Low)

**Matching Criteria:**
- **Skills**: e.g., Wheelchair Transfer
- **Language**: e.g., Malay
- **Gender**: e.g., Male
- **Location**: Service Boundary/Postal Code (e.g., Postal Code 409051)

**c) Assign to SCC staff**
   - Normal CARES workflow to ensure task is created

**d) OR Open to AAC MJ Database**

**e) Publish in AAC MJ App**
   - Page: "Chaperone MJ Jobs Available"
   - Display information:
     - Date/Time
     - Task
     - Venue (FROM: based on MJ stays - TO: Nurse to indicate)
     - Estimate Time Slot (e.g., 2PM to 4PM)
     - Client Weight
     - Client Health Status (Functionality, Dementia?)
     - Simple Client Profile (age, gender, race, remarks)
   - Match/target job opportunity to only qualifying MJ who meet criteria

**f) MJ "Grab" Job & Waitlist Process**
   - **GRAB**: After job has been "grabbed" (i.e., Confirmed), Waitlist starts
   - **Slots**: 1 confirmed slot + 4 waitlist slots = 5 slots per job
   - **Cancellation Process** (Original, Complex):
     - Job published 5 days before task
     - First to grab gets confirmed (MJ1)
     - Slots 2-5 waitlisted chronologically
     - If MJ1 cancels 3 business days before, MJ2 gets 12 hours window to grab
     - If MJ2 doesn't grab after 12 hrs, opens for MJ3
   
   - **Proposed Simplified Process**:
     - Cancellation by MJ1
     - Anyone in waitlist can grab as long as confirmed at least 1 Biz Day before task
     - If no takers 1 Biz Day before, job is cancelled and client is informed
   
   - **End Result**: Inform Client of any cancellation 1 Biz Day before the Task

**g) Confirmation**
   - Once grab successful, MJ job status shows "confirmed" in MJ app
   - MJ app will also show schedule

---

### 2.2 Befriending Service

#### Workflow Steps:

**a) Initiated by AAC Staff**

**b) AAC Staff match jobs based on:**
   - **Skills**: Those who have completed training
   - **Language**
   - **Gender**
   - **Location**: Service Boundary
   - **UI Requirement**: Allow AAC Staff to conduct the match; if system can recommend, AAC confirms based on recommendation

**Publish in AAC MJ App** (optional):
- Page: "Befriending MJ Jobs Available"
- Display:
  - Date/Time
  - Task
  - Venue (FROM: based on MJ stays - TO: Nurse to indicate)
  - Estimate Time Slot (e.g., 2PM to 4PM)
  - Client Health Status (Functionality, Dementia?)
  - Simple Client Profile (age, gender, race, remarks)
- Match/target job to qualifying MJ who meet criteria

**Note**: Capability to publish is retained even if AAC staff normally doesn't publish (match done backend and "pooling" required). However, they may need to publish if normal pool is not available.

**c) Staff Assignment**
   - Staff will assign MJ to clients in CARES
   - **Note**: Offline, Staff will "pool" 3 to 4 cases for MJ to complete within 1 hr

**d) Recurring Tasks**
   - Recurring tasks can be scheduled for MJ
   - Example: MJ Peter always befriends Client John

**e) Option to Post Job**
   - Still retain option to post job in case normal pool not available

**f) No Grab Option**
   - Grab is NOT available for Befriending

**g) Confirmation**
   - Once assigned, MJ app will show schedule

---

### 2.3 Safe Steps Associate (Home Assessment)

**Capacity**: Minimum 2 MJ required

#### Workflow Steps:

**a) Initiated by AAC Staff**

**b) Determine complexity based on:**
   - **Skills**
   - **Language**
   - **Gender**
   - **Location**: Service Boundary

**c) Assign to SCC staff** (normal CARES workflow)
   - **Note**: To confirm if this is offline

**d) OR Open to AAC MJ Database**

**e) Publish in AAC MJ App**
   - Page: "Home Assessment MJ Jobs Available"
   - Display:
     - Date/Time
     - Task
     - Venue (FROM: based on MJ stays - TO: AAC staff to indicate home address of client)
     - Estimate Time Slot (e.g., 2PM to 4PM)
     - Client Weight??
     - Client Health Status (Functionality, Dementia?)
     - Simple Client Profile (age, gender, race, remarks)
   - Match/target job to qualifying MJ who meet criteria

**f) MJ Grab & Waitlist**
   - Waitlist starts only after slot has been taken
   - **Slots**: 1 slot taken + 4 slot waitlist = 5 slots per job
   - 12 hours respond time for each waitlister before pushed to next person

**g) Confirmation**
   - Once grab successful, MJ job status shows "confirmed"
   - MJ app will show schedule

---

### 2.4 Center Assistant Service

#### Workflow Steps:

**a) Initiated by AAC Staff**
   - Specify criteria

**b) System Availability**
   - System to provide list of MJ with the requisite:
     - **Skills**: Those who have completed training
     - **Language**
     - **Gender**
     - **Location**: Service Boundary

**c) Publish Jobs**
   - Target MJ that meet criteria and capacity
   - Example: Need 2 or 3 for specific job

**d) MJ Register Interest**
   - MJ cannot grab - confirmation is done by center staff
   - MJ registers interest
   - Staff confirms which MJ to assign job to

**e) AAC Staff Confirmation/Rejection**
   - AAC staff will confirm/reject in CARES
   - MJ will receive notification
   - Messaging examples: "Job Confirmed", "Job No Longer Available"

---

### 2.5 MJ Job Statuses

#### Status in MJ App:

| Status | Chaperone | Home Assessment | Center Assistant | Befriender |
|--------|-----------|----------------|------------------|------------|
| **Registered** | ✓ | ✓ | ✓ | ✓ |
| **Confirmed** | Depends on capacity | Up to 2 | Depends on capacity | Up to 2 |
| **Waitlisted** | Up to 4 | Up to 4 | Center staff assigns | - |
| **No longer available** | After 1 confirmed + 4 waitlisted | After 2 confirmed + 4 waitlisted | Event is over | Event is over or care staff |
| **Cancelled** | Staff cancels backend; if MJ cancelled | For home assessment if cannot get 2 pax 24hrs before, system auto-cancels | - | - |

**NOTE**: For Home Assessment, job published listing should also indicate the names of MJ(s) who have been confirmed for the job.

#### Job Status in Job Listing:

Jobs continue to be on listing until event is completed (immediately after event is completed):

| Status | Description | Notes |
|--------|-------------|-------|
| **Open** | Open for registration or waitlisting | - |
| **No Longer Available** | All slots including waitlist taken | Home Assessment job to indicate name(s) of those confirmed |
| **Cancelled** | e.g., client cancelled the job | Continue to show in listing until event date |

---

## 3. MJ Onboarding

### 3.1 Types of MJ

**Three Types:**
1. Pure MJ
2. Volunteer
3. Senior

**Status Combinations:**
- Pure MJ
- MJ + Senior
- MJ + Volunteer
- MJ + Vol + Senior

**Note**: Volunteer status impacts AAC KPI

**MJ Form (Indication of Interest)**:
- Currently on AAC UI
- In future, can be used by other departments

---

### 3.2 Training & OJT Requirements

#### System must capture:

**Attended Training** (4 Job Roles list from Maisarah)
- UI must allow user to update Training Status: NA, Pending, Scheduled, In Progress, Completed
- Example: Only completed OJT for Chaperone can be assigned to Chaperone Service

**Attended OJT (On the Job Training)**

#### Training Record for MJ (in MJ Profile):

| Service | OJT Status | Assignment | Notes |
|---------|-----------|------------|-------|
| Befriender | Pending / Not Yet Started | No | Error message if MJ assignment is "Yes" but OJT not completed |
| Home Assessment (Safe Step Assistant) | Scheduled | No | - |
| Chaperone | Completed | Yes | Condition check - cannot be assigned until OJT done |
| Center Assistant | In progress | No | - |

---

### 3.3 Job Matching Criteria

MJ jobs will be matched based on:

| Criteria | Details | Source |
|----------|---------|--------|
| **Skills** | Completed Training and OJT for specific job roles | As long as OJT completed, deemed fit to start being assigned for Service |
| **Language** | - | MJ Profile Form |
| **Gender** | - | MJ Profile Form |
| **Location** | Service Boundary or Postal Code | Based on address |
| **Interest** | Code Table | To email |
| **Background** | Remarks | MJ Profile Form |

---

### 3.4 Onboarding Process (MJ Profile Dashboard)

**Components:**

**Pre-screening** - Offline

**a) MJ Profile Form**

**b) Training Records**

**c) Assignment**
   - All jobs assigned, completed, cancelled to be displayed in MJ Profile Dashboard

**d) Attendance Tracking**

**e) MJ Profile Status:**
   - **Screening**
   - **Training**
   - **Active**: Still requires OJT for specific services to be completed before MJ can be assigned to that service
   - **Blacklisted**: Will not be assigned for ANY service. Can be changed from Blacklisted to Active
   - **Withdrawn**
   - **Suspended**
   - **Terminated**

**System Conditions**:
- Withdrawn, Suspended, Blacklisted, Terminated cannot be assigned
- Must reflect what they are being trained in, or skillset

---

## 4. Task Creation

### A. Chaperone Task Creation

#### 4.1 Task Creation by SCC Nurse
- SCC Nurse creates Task in CARES (respective SCC facility - note there are 5 SCC facilities)
- SCC Nurse determines if job can be assigned to MJ or assign to SCC staff

**a) If task is assigned to MJ:**
   - Job must be published 3 business days or more ahead of actual task
   - **Configurable**: Weekdays, exclude Public Holidays
   - **Rule**: If < 3 Business Days, job cannot be published
   - **Consideration**: Waitlist cancellation, alerts, non-cancellation policy, etc.
   - If within 24H cancellation due to multiple reasons, job itself may be canceled
   - A Matrix is likely required to detail permutations

**b) Urgent Jobs:**
   - If job is urgent (3-5 business days before), job appears as "urgent" in Job Listing
   - **Definition**: Configurable
   - **Impact**: Maybe higher cost or display differently on microjobber screen
   - **Rule**: If job 3-5 Business Days away

#### 4.2 System Match
- Based on system match, MJ will see task in app
- If job is urgent (posted 3-5 business days before), job appears as urgent

#### 4.3 MJ Confirmation
- MJ will confirm (Grab) the job from job listing

#### 4.4 Notifications
- SCC Nurse and AAC AE to be notified (job published and any confirmation)

#### 4.5 Waitlisting Rules
- Up to 4 MJ can be waitlisted
- **Configurable**

#### 4.6 Job Listing Display
- On the job listing, MJ will see if they have been confirmed or waitlisted
- Possibly have requirement for multiple MJ

---

### A: If No Takers

**4.5** If no MJ takes the job, 2 business days before job:
   - SCC (Nurse, AE) and AAC Staff to be notified

**4.6** SCC will notify client of the risk of no takers
   - AAC staff will also try to convince MJ to take

**4.7** If 1 business day (24 hrs) before job - no takers:
   - MJ portal job will be withdrawn

**4.8** SCC Nurse either:
   - Assign staff, OR
   - Cancel the job with client

---

### B: If MJ Confirmed the Job

- SCC Nurse, AE and AAC Staff will be notified
- SCC Nurse or AE will inform client (Offline)

**MJ Appointment Reminders** (via App notification):
1. Upon confirmation
2. 5 Business Days before
3. 24 hrs before (include cancellation policy and all center phone numbers)

**Geofencing**: To be activated

**MJ Attendance**:
- Used for AAC MJ payment
- MJ start and end service ⇒ Task Completed

**SCC Billing**:
- Based on scheduled task (e.g., 2-4 PM = 2 hrs)
- SCC staff can bill the client
- Number of hours can be amended (amendment required if more time needed, no amendment even if less time required)
- **Ignore MJ check-in and check-out time** - SCC billing is always based on scheduled time

**If Scheduled Time is Exceeded**:
- Notification to SCC staff to amend billing backend
- Example: Instead of 2-4 PM, job ended at 4:30 PM
- SCC staff notified to decide if want to amend the amount to bill

---

### B: Home Assessment Task Creation
(Follow similar workflow as Chaperone)

### C: Befriender Task Creation
(Follow similar workflow as Chaperone with staff assignment)

### D: Center Assistant Task Creation
(Follow similar workflow as Chaperone with registration/confirmation by staff)

---

## 5. Cancellation Policies

### A. Client Cancellation

#### SCC Business Rules:
- **24 hrs before job** (Tues-Fri)
- **For Monday appointments**: Cancel by Fri 5 PM

#### If Criteria NOT Met:
- **SCC**: Client will be charged in full (with option to cancel if valid reason)
- **AAC**: If criteria cannot be met, MJ will still be paid accordingly (e.g., for 1 hr)
- **AAC Staff**: Will go into CARES to "complete" the task and indicate timing with remarks "No Show" (naming to be discussed)

#### If Criteria Met:
- SCC Staff will inform AAC of cancellation
- Cancel the task in CARES
- MJ will be notified of cancellation through App
- AAC staff will inform MJ of cancellation offline as well

---

### B. MJ Cancellation

**For all 4 jobs, cancellation policy:**

**General Rules:**
- If MJ cancels job, must be 2 business days before so AAC staff can bounce back to staff nurse to assign somebody else
- When MJ cancels on app, AAC staff receives notification
- MJ verbally lets staff know and staff can cancel on web
- MJ on waitlist will receive notification - to determine if MJ can receive notification on app
- MJ should grab job on app themselves; staff receives notification

#### For Chaperone and Home Assessment:

**Cancellation Timeline (Wednesday-Friday appointments):**
- 48 hrs before, MJ can cancel
- If no takers 1 business day before appointment - job will be automatically cancelled

**Example: Appointment 9AM on Wednesday**

| Appointment Day | MJ Cancellation Deadline | Waitlist Confirmation Deadline |
|----------------|--------------------------|-------------------------------|
| Monday | Previous Thursday 9AM | Friday 9AM |
| Tuesday | Previous Friday 9AM | Monday 9AM |
| Wednesday | Monday 9AM | Tuesday 9AM |
| Thursday | Tuesday 9AM | Wednesday 9AM |
| Friday | Wednesday 9AM | Thursday 9AM |

**Waitlist Confirmation Windows:**
- **Window 1**: 1st Waitlisted - 12 hrs from cancellation time of MJ
- **Window 2**: 2nd Waitlisted - 12 hrs from Window 1
- **Window 3**: 3rd Waitlisted - 12 hrs from Window 2
- **Window 4**: 4th Waitlisted - 12 hrs from Window 3

**If No Takers**: 1 business day before appointment, job automatically will be cancelled

**Public Holiday Rules:**
- If appointment or cancellation time is eve of or on PH, call center staff to discuss
- System will not allow any cancellation on a PH (if the timeline is on a PH)
- If MJ attempts to cancel after timeline, error message prompts them to contact center staff
- System will not allow cancellation

#### Questions and Suggestions:

**Current Questions to Client:**
1. Is there a need to do chronological acceptance of job?
2. Is there a need to only allow working hours cancellation?

**Suggestions:**
1. **Waitlist Process**: Open to all waitlisters to grab once job is cancelled
   - Alternative: Smaller window (1H, 2H etc), not business hours related
2. **Cancellation Timing**: Able to cancel anytime (out of business hours also possible) but not within 2 Business days

**Additional Rules:**
- If > 1 MJ "grab" the job, the 2nd MJ will be notified
- Think through process again
- SCC to be notified

---

## 6. No-Show Policies

### D. No Show (Client)

**SCC**: If No Show, Client will be charged in full (with option to cancel if valid reason)

**AAC**: If client No Show, MJ will still be paid accordingly

**AAC Staff**: Will go into CARES to "complete" the task and indicate timing with remarks "No Show" (naming to be discussed)

---

### E. No Show (MJ)

**Process:**
1. Client calls SCC to inform
2. SCC to indicate in CARES "Cancel" with Remarks "MJ No Show"
   - Remarks to be a standard list of dropdown reasons, including "others" with free text
3. AAC will flag in MJ profile - no show
4. After repeated No Show from MJ, AAC Staff can blacklist MJ

---

## 7. Task Assignment

**Date**: 7 May 26

**Purpose**: Task assignment is to provide service for a VG client

**Example**: Chaperone Service - MJ is assigned to chaperone SCC Senior
- System must be able to reflect this Chaperone appointment in the correct SCC facility and correct SCC client
- **Linkage**: To our Scheduling module

### Attendance

**Mobile**: "Start Attendance" for assigned task

**Dashboard**: Display assigned tasks on MJ CARES dashboard

---

## 8. Dashboards

### 1) AAC MJ Listing

**Features:**
- Training Status (e.g., pending, scheduled, completed)
- Job Listing (to specify, job listed by which facility - filters available)
  - Published
  - Takeup by MJ
  - Cancellations
  - Completed
- Job Registration/Assignment (Care staff manage the registration, confirmation, waitlisting etc)

### AAC MJ Engagement Dashboard

**Engagement Definition**: MJ with at least 1 job per month (in any service)

**Views:**
- **Month View** (by Year): See list of MJ - Engaged or Not Engaged
- **Quarter View**: Minimum of 3 engagements to be considered engaged

---

## 9. Reporting

### MJ Activity and Operational Reports

#### 1) AIC Reporting by Center and All Centers (By Month, Year)

**Metrics:**
- **No. of MJ**
- **Types of Roles Activated for**:
  - MJ Chaperone: 7
  - Home Assessment: 10
  - Befriender: 4
  - Center Assessment: 20
- **Hours activated**: Sum all MJ hours worked
- **Payment**: Sum all MJ payment pay

#### 2) Timesheet for HR to Process Payment to MJ
- Maisaah to provide

#### 3) Chaperone Services (for billing purpose)
- Michelle to provide
- Tracking of clients utilization and charges
- Break down by centers and combined, month, years
- Include both tasks completed by SCC staff and MJ

---

## 10. SCC-Specific Requirements

### 1. Client Creation
- Create flag for "Non SCC client" in Client Listing
- User can filter SCC or Non SCC Clients and export etc

### 2. Service Creation
- Add service (code table) for Chaperone and GL code
- **Need from Finance**

### 3. Fee Table - Per Hour
**Requirements:**
- Customize new Fee Table based on CHAS Card colour
- New UI for CHAS Card info records including:
  - Card number
  - Colour
  - Start and end date
  - History
- New Fee Table with Subsidies based on CHAS Card Colour
- In-House Discount is applied based on active CHAS card colour
- **Note**: There is no subsidy applicable to Chaperone service

**To Do**: Filbert to send Fee Table with Fee, In-house Discount (based on CHAS Card)

---

## 11. Potential Design & Development Problems

This section identifies potential technical challenges, edge cases, and design concerns that should be addressed during system development.

### 11.1 Concurrency & Race Condition Issues

#### Problem 1: Job "Grab" Race Conditions
**Issue**: Multiple MJ may attempt to "grab" the same job simultaneously, potentially resulting in:
- Overbooking (more than intended confirmations)
- Incorrect waitlist positioning
- Data inconsistency between mobile app and backend

**Risk Level**: HIGH

**Considerations**:
- Database-level locking mechanisms required
- Optimistic vs pessimistic locking strategy
- Real-time slot availability updates to all viewing MJ
- Handling of failed transactions when slot just taken
- Network latency causing delayed "already taken" messages

**Recommended Solution**:
- Implement database transactions with row-level locking
- Use queue-based processing for grab requests
- Immediate websocket/push notification to all viewers when slot status changes
- Clear user feedback for failed grab attempts

---

#### Problem 2: Waitlist Management Complexity
**Issue**: Managing 4 sequential 12-hour confirmation windows with automatic progression
- Timer management across system restarts
- Multiple MJ receiving notifications at wrong times
- Handling of partial window completion (e.g., 8 hours into 12-hour window when MJ confirms)
- Time zone considerations

**Risk Level**: HIGH

**Considerations**:
- Need robust background job scheduler (e.g., Hangfire, Quartz.NET)
- What happens if notification service fails?
- Should windows run continuously or only during business hours?
- Edge case: What if all 4 waitlisters decline within 48 hours total?

---

### 11.2 Business Day & Time Calculations

#### Problem 3: Complex Business Day Logic
**Issue**: Multiple business rules depend on "business days" excluding weekends and public holidays:
- Different rules for Monday appointments vs other days
- Public holiday handling inconsistent ("call center staff to discuss")
- Different cancellation windows for different services
- System must know public holidays in advance (multi-year)

**Risk Level**: MEDIUM-HIGH

**Considerations**:
- Need centralized public holiday calendar management
- What happens when PH is announced last minute?
- Different regions may have different PH
- Leap years, daylight saving (if applicable)
- Edge case: 3 consecutive PH (long weekend)

**Example Edge Case**:
```
Monday appointment → Must cancel by previous Thursday 9 AM
What if previous Thursday is a PH?
- System blocks cancellation (per spec)
- But this is unfair to MJ
- No clear fallback rule specified
```

---

#### Problem 4: Time-Based Auto-Actions
**Issue**: System must automatically execute actions at specific times:
- Auto-cancel jobs if no takers 1 business day before
- Progress waitlist windows every 12 hours
- Send reminders at specific intervals
- Handle service boundaries for SCC facilities

**Risk Level**: MEDIUM

**Considerations**:
- What if system is down during scheduled action?
- Need idempotent operations (safe to retry)
- Time zone handling (server vs user location)
- Notification delivery failures

---

### 11.3 Payment & Billing Discrepancies

#### Problem 5: Dual Time Tracking Systems
**Issue**: Two different time records serve different purposes:
- **MJ Payment**: Based on actual check-in/check-out time
- **SCC Billing**: Based on scheduled time slot

**Risk Level**: MEDIUM

**Concerns**:
- What if scheduled is 2 hours but MJ works 3 hours?
  - MJ gets paid for 3 hours
  - Client charged for 2 hours
  - Who absorbs the cost difference?
- Manual amendment process introduces errors
- No clear approval workflow specified
- Potential for revenue leakage

**Example Scenario**:
```
Scheduled: 2 PM - 4 PM (2 hours)
Actual: 1:55 PM - 4:35 PM (2 hours 40 min)
MJ Payment: 3 hours (rounds to 3)
Client Billing: 2 hours (unless manually amended)
Gap: 1 hour cost not accounted for
```

---

#### Problem 6: Payment Rounding Logic
**Issue**: "0.50 round to 1 hr" is ambiguous
- Does 1.5 hours = 2 hours payment?
- Does 1.49 hours = 1 hour payment?
- Does 0.50 hours = 1 hour payment?
- What about 2.3 hours?

**Risk Level**: MEDIUM

**Clarification Needed**:
- Industry standard is usually "round up after 30 minutes"
- But "0.50 round to 1 hr" could mean "anything ≥ 0.50 rounds to next hour"

---

### 11.4 Data Consistency & Synchronization

#### Problem 7: Multi-System Data Sync
**Issue**: Data must remain consistent across:
- MJ Mobile App
- AAC Staff Web Portal
- SCC Staff Web Portal (5 facilities)
- CARES core system

**Risk Level**: HIGH

**Concerns**:
- Mobile app may show stale data
- Staff may make conflicting updates
- Notification delivery delays
- Offline mode handling (mobile app)
- Conflict resolution strategy undefined

---

#### Problem 8: Status State Machine Complexity
**Issue**: Jobs have multiple states that can transition in complex ways:
- Registered → Confirmed → Completed
- Registered → Waitlisted → Confirmed → Completed
- Registered → Cancelled
- Confirmed → Cancelled → Waitlisted (bumps up)

**Risk Level**: MEDIUM

**Concerns**:
- Invalid state transitions possible
- No clear state machine diagram
- Edge case: Can a completed job be cancelled? (for payment disputes)
- Audit trail requirements unclear

---

### 11.5 Integration & External Dependencies

#### Problem 9: Geofencing Implementation
**Issue**: Geofencing requirement mentioned but details sparse
- GPS accuracy concerns (especially indoors)
- Battery drain on mobile devices
- What if MJ's phone has location disabled?
- Radius tolerance not specified
- Handling of GPS spoofing

**Risk Level**: MEDIUM

**Questions**:
- Is geofencing for check-in only or continuous monitoring?
- What happens if MJ starts outside geofence?
- Manual override process for legitimate issues?

---

#### Problem 10: CHAS Card Integration
**Issue**: Dynamic fee calculation based on CHAS card colour with history tracking
- Real-time CHAS card validation needed?
- Card expiry during appointment window
- Card colour changes between booking and appointment
- Multiple cards per client

**Risk Level**: MEDIUM-LOW

**Concerns**:
- Fee locked at booking time or appointment time?
- Retroactive adjustments if card status changes?
- Integration with national CHAS database?

---

### 11.6 User Experience & Edge Cases

#### Problem 11: Offline Process Dependencies
**Issue**: Multiple workflows depend on offline communication:
- "SCC Nurse or AE will inform client (Offline)"
- "MJ verbally let staff know"
- "Staff will 'pool' 3 to 4 cases offline"

**Risk Level**: MEDIUM

**Concerns**:
- System has no record of offline actions
- Audit trail incomplete
- Disputes difficult to resolve
- Training overhead for staff

---

#### Problem 12: Notification Overload
**Issue**: System sends many notifications to multiple parties:
- MJ: Job published, confirmation, reminders (×3), cancellations, waitlist status
- Staff: Job grabbed, cancellations, no takers, overtime alerts
- Client: (via staff offline - but could be direct in future)

**Risk Level**: LOW-MEDIUM

**Concerns**:
- Notification fatigue
- Channel preferences not specified (push, SMS, email)
- Opt-out strategy
- Failed delivery handling
- Language preferences

---

### 11.7 Scalability Concerns

#### Problem 13: Home Assessment Coordination
**Issue**: Minimum 2 MJ required for home assessment creates coordination complexity
- Both must confirm within same timeframe
- If one cancels, both must be replaced
- Names displayed to waitlisters before confirmation
- Privacy concerns showing peer names

**Risk Level**: MEDIUM

**Questions**:
- Can partial confirmation exist (1 of 2)?
- Timeout if only 1 confirms?
- Do the 2 MJ know each other beforehand?

---

#### Problem 14: Five SCC Facilities
**Issue**: System must handle 5 separate SCC facilities with potentially different:
- Staff access rights
- Service availability
- Client bases
- Reporting requirements

**Risk Level**: LOW-MEDIUM

**Concerns**:
- Multi-tenant architecture required
- Data segregation vs shared MJ pool
- Cross-facility assignments allowed?
- Different business rules per facility?

---

### 11.8 Security & Compliance

#### Problem 15: Personal Data Exposure
**Issue**: MJ can see client personal information:
- Age, gender, race
- Health status (dementia, functionality)
- Weight
- Home address (for home assessment)

**Risk Level**: HIGH

**Concerns**:
- PDPA compliance requirements
- Data minimization principle
- MJ background checks required?
- Data retention policy unclear
- Right to erasure (GDPR-style)

---

#### Problem 16: Payment Fraud Risks
**Issue**: Multiple opportunities for fraud:
- MJ claiming hours not worked
- Staff approving inflated hours
- GPS spoofing for geofence
- Collusion between MJ and staff
- Blacklisted MJ using different identity

**Risk Level**: MEDIUM

**Concerns**:
- Audit mechanisms unclear
- Approval workflow missing
- Biometric authentication needed?
- Penalty system undefined

---

### 11.9 Requirements Ambiguity

#### Problem 17: Conflicting Requirements
**Issue**: Some requirements contradict or are unclear:

1. **Cancellation timing**: "2 business days before" vs "48 hours before" - these differ for weekend appointments
2. **Waitlist process**: Original complex 12-hour sequential vs proposed "anyone can grab"
3. **Urgent jobs**: Higher cost mentioned as possibility but not confirmed
4. **System allows/blocks**: "System will not allow cancellation on PH" but also "call center staff to discuss"

**Risk Level**: MEDIUM-HIGH

**Resolution Needed**:
- Stakeholder alignment required
- Document decisions clearly
- Version control for business rules

---

#### Problem 18: Undefined Workflows
**Issue**: Key workflows mentioned but not detailed:
- Blacklisting process and criteria
- MJ performance evaluation
- Dispute resolution (MJ vs client complaints)
- Emergency job cancellation
- Force majeure handling (weather, health emergencies)

**Risk Level**: MEDIUM

---

### 11.10 Technical Architecture Concerns

#### Problem 19: Real-Time Requirements
**Issue**: System needs real-time updates for:
- Job slot availability
- Waitlist progression
- Cancellations
- Notifications

**Risk Level**: MEDIUM

**Technical Needs**:
- WebSocket or SignalR infrastructure
- Push notification service (FCM/APNS)
- Message queue system
- High availability requirements
- Load balancing

---

#### Problem 20: Reporting Complexity
**Issue**: Multiple complex reports required:
- Cross-facility aggregation
- Time-series data (monthly, quarterly, yearly)
- Different views for different stakeholders
- Export functionality
- Real-time vs batch reporting

**Risk Level**: LOW-MEDIUM

**Concerns**:
- Performance impact on transactional database
- Need for separate reporting database (OLAP)?
- Data warehouse considerations
- Historical data retention period

---

### 11.11 Testing Challenges

#### Problem 21: Complex Scenario Testing
**Issue**: Numerous edge cases and permutations make testing difficult:
- Different service types × different days × PH variations
- Waitlist progression scenarios
- Concurrent user actions
- Time-based automatic actions
- Multi-facility interactions

**Risk Level**: MEDIUM

**Testing Strategy Needed**:
- Comprehensive test case matrix
- Automated regression testing
- Mock time advancement for testing
- Load testing for concurrent grabs
- Integration testing across systems

---

### 11.12 Change Management

#### Problem 22: Configurable vs Hard-Coded Rules
**Issue**: Many rules marked as "configurable" but details unclear:
- Who can change configuration?
- Approval process for rule changes?
- Versioning of business rules
- Impact analysis when rules change
- Granularity of configuration (global vs facility-level)

**Risk Level**: MEDIUM

**Examples of Configurability**:
- Business day thresholds (3 days, 2 days, 1 day)
- Waitlist capacity (4 slots)
- Confirmation windows (12 hours)
- Urgent job definition (3-5 days)

---

### Summary of Risk Priorities

| Risk Level | Count | Immediate Action Required |
|------------|-------|---------------------------|
| HIGH | 5 | Design reviews, prototyping, stakeholder clarification |
| MEDIUM-HIGH | 3 | Detailed specification, architecture decisions |
| MEDIUM | 10 | Document assumptions, plan mitigation |
| MEDIUM-LOW | 2 | Monitor during development |
| LOW-MEDIUM | 2 | Address in detailed design phase |

### Recommended Next Steps

1. **Immediate**: Conduct workshops to resolve ambiguities and conflicting requirements
2. **Phase 1**: Design concurrency handling, state machine, and business day calculation engine
3. **Phase 2**: Define security model, audit trail, and data protection measures
4. **Phase 3**: Create comprehensive test scenarios and acceptance criteria
5. **Ongoing**: Establish change management process for business rules

---

## Summary of Key Business Rules

1. **Job Publication Lead Time**: Minimum 3 business days (configurable)
2. **Urgent Jobs**: 3-5 business days before = urgent status
3. **Waitlist Capacity**: Up to 4 MJ can be waitlisted
4. **Cancellation Window**: 
   - Client: 24 hrs before (Mon: cancel by Fri 5 PM)
   - MJ: 2 business days before
5. **Waitlist Confirmation Window**: 12 hours per waitlister
6. **Auto-Cancellation**: If no takers 1 business day before appointment
7. **No-Show Handling**: Different rules for SCC (charge client) vs AAC (pay MJ)
8. **Home Assessment Minimum**: Requires minimum 2 MJ
9. **Befriending**: No grab option, staff assigns
10. **Center Assistant**: Registration only, staff confirms
11. **Payment Rounding**: First 1 hr minimum, then 0.50 rounds to 1 hr
12. **Billing**: SCC bills based on scheduled time, not actual MJ attendance time
13. **Geofencing**: Activated for attendance tracking
14. **MJ Status Restrictions**: Withdrawn, Suspended, Blacklisted, Terminated cannot be assigned

---

## Document Version
- **Last Updated**: May 14, 2026
- **Source**: MJ User Requirement Gathering Excel Document

---

## 12. Pages Required

Based on the full scope of both modules, the following **31 pages/screens** are required across CARES (web) and C4Me (mobile).

---

### CARES Web — AAC/SCC Staff-Facing (21 pages)

#### MJ Registry (4 pages)
| # | Page | Purpose |
|---|------|---------|
| 1 | MJ List | Searchable, filterable roster of all MJs with status badges and quick-access to profiles |
| 2 | MJ Profile | Demographics, languages, skills, service boundary, MJ type, background notes, status |
| 3 | MJ Onboarding Form | Pre-registration, screening record, contract initiation, C4Me access provisioning |
| 4 | Training & OJT Record | Per-role training and OJT status table; eligibility engine output; assignment block if OJT incomplete |

#### Job / Task Management (5 pages)
| # | Page | Purpose |
|---|------|---------|
| 5 | Job Publishing Form | Create job across all 4 service types; set matching criteria, lead time validation, geofence toggle, urgency flag |
| 6 | Job Dashboard | View all published jobs with live status (Published / Taken / Cancelled / Completed), filterable by facility and date |
| 7 | Job Detail | Confirmed MJs, waitlist queue, slot status, notification history, cancel/re-open actions |
| 8 | MJ Matching & Notification | Eligible MJ pool view; manual assign for Befriending and Centre Assistant; push notification trigger |
| 9 | Centre Assistant Registration Review | List of MJs who registered interest; staff confirm or reject; notification trigger to MJ |

#### Attendance & No-Show (2 pages)
| # | Page | Purpose |
|---|------|---------|
| 10 | Attendance Overview | All task check-ins and check-outs by date, job, and MJ; amendable by staff |
| 11 | No-Show Recording Form | Dropdown reason (MJ or client no-show), free text remarks, no-show flag written to MJ profile |

#### Cancellation Management (1 page)
| # | Page | Purpose |
|---|------|---------|
| 12 | Cancellation Form | Staff-side cancel for MJ verbal cancellation or client cancellation; business day deadline validation; waitlist promotion trigger |

#### Payment (3 pages)
| # | Page | Purpose |
|---|------|---------|
| 13 | Payment Verification Dashboard | All claims in "Payment Owing" state; verify individual claims; status transitions to Verified |
| 14 | Claim Detail | Actual timestamps, rate applied, rounding calculation, reimbursement items (taxi, transport, meal) |
| 15 | AP Listing Export | Filter by period / facility / status; export to Excel for HR/Finance payment processing |

#### SCC Chaperone Module (3 pages)
| # | Page | Purpose |
|---|------|---------|
| 16 | SCC Client Listing | Client list with Ad Hoc SCC Client flag; filterable and exportable by client type |
| 17 | Chaperone Schedule & Attendance | Schedule Chaperone appointments; record attendance by MJ or SCC staff; billing hour amendment |
| 18 | CHAS Fee Table Setup | Finance-configured table: CHAS card colour, standard fee, in-house discount %, net fee; card history per client |

#### Reporting (3 pages)
| # | Page | Purpose |
|---|------|---------|
| 19 | AIC Operational Report | MJ count, roles activated, hours worked, payments; filter by centre, month, year |
| 20 | MJ Engagement Dashboard | Monthly engaged/not-engaged per MJ (≥1 job = engaged); quarterly view (≥3 jobs = engaged) |
| 21 | Chaperone Utilisation Report | Client charges and utilisation; breakdown by SCC facility, month, year; includes both MJ and SCC staff completions |

---

### HR / Finance Config — CARES Web (1 page)

| # | Page | Purpose |
|---|------|---------|
| 22 | System Setup | Fee table by service role, code table, GL/dept code mapping; Finance-only access; pre-go-live configuration |

---

### C4Me Mobile — MJ-Facing (7 pages)

| # | Page | Purpose |
|---|------|---------|
| 23 | Job Listing | Eligible jobs for the MJ only (matching already applied); urgency flag visible; slot availability shown |
| 24 | Job Detail & Grab | Full job info (client profile, venue, time, health status); Grab or Register Interest button; slot counter |
| 25 | My Schedule | Confirmed and waitlisted jobs; upcoming reminders; assignment history |
| 26 | Attendance Check-In/Out | Start and End buttons; geofence validation for Chaperone; Incomplete option with reason dropdown |
| 27 | Pre-Task Confirmation | Yes/No response to 24-hour reminder; triggers waitlist re-open if No or no response after 6 hours |
| 28 | Payment Status | Per-job status: Submitted / Verified / Paid; reimbursement claim submission with photo upload |
| 29 | Cancellation Request | MJ cancels own confirmed job; business day deadline enforced; contact-centre prompt if deadline passed |

---

### C4Me Mobile — SCC Client / Senior-Facing (2 pages)

| # | Page | Purpose |
|---|------|---------|
| 30 | Appointment View | Upcoming Chaperone appointments with date, time, venue, and confirmation status |
| 31 | Cancel / Reschedule Request | Submit cancel or reschedule request; shows pending staff confirmation; no change takes effect until staff approves in CARES |

---

### Page Count Summary

| Platform | Section | Pages |
|----------|---------|-------|
| CARES Web | MJ Registry | 4 |
| CARES Web | Job / Task Management | 5 |
| CARES Web | Attendance & No-Show | 2 |
| CARES Web | Cancellation Management | 1 |
| CARES Web | Payment | 3 |
| CARES Web | SCC Chaperone Module | 3 |
| CARES Web | Reporting | 3 |
| CARES Web | HR / Finance Config | 1 |
| C4Me Mobile | MJ-Facing | 7 |
| C4Me Mobile | Client / Senior-Facing | 2 |
| **Total** | | **31** |
