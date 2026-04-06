# EduTrack Cafe

A desktop management system for a university-style programming cafe, built with C# and Windows Forms on .NET Framework 4.7.2. The application supports role-based workflows for **Admin**, **Lecturer**, **Trainer**, and **Student** users, with each role getting a dedicated interface and business operations.

This project demonstrates end-to-end development of a database-driven desktop system, from UI design and role-based navigation to SQL data operations and workflow rules.

## Project Highlights

- Multi-role authentication and access control from a single login screen
- Dedicated dashboards and operations for Admin, Lecturer, Trainer, and Student
- Full enrolment lifecycle: request, approve, update, assign, validate, complete
- Payment submission and admin validation process
- Trainer class scheduling with venue/time conflict checks
- Feedback collection and income-reporting capabilities for operational oversight

## Tech Stack

- **Language:** C#
- **Framework:** .NET Framework 4.7.2
- **UI:** Windows Forms
- **Database:** SQL Server LocalDB (`.mdf` / `.ldf`)
- **Data Access:** `System.Data.SqlClient` with parameterized SQL queries
- **Project Type:** Desktop `WinExe` application

## System Architecture

The application follows a practical layered structure:

- **Presentation Layer:** WinForms (`Login`, `Admin`, `Lecturer`, `Trainer`, `Student` forms and user controls)
- **Domain/Business Layer:** Classes such as `Students`, `Trainers`, `Lecturers`, `Admins`, `LoginUsers`, `CoachingClass`
- **Data Layer:** SQL queries executed through `SqlConnection`, `SqlCommand`, and `SqlDataReader`

### Core Entry Point

- `Program.cs` launches `LoginForm`
- `LoginForm` authenticates credentials and opens the role-specific main form

## Role-Based Features

### Admin

- View and update own profile
- Register and remove trainers
- Assign trainers to modules
- Validate or reject student payment evidence
- Assign students to trainers after payment validation
- View submitted trainer feedback
- View income reports

### Lecturer

- View and update own profile
- Register new students
- Enrol students into modules/intakes
- Review enrolment requests from students
- Update student enrolment records
- Remove completed enrolments

### Trainer

- View and update own profile
- Manage coaching classes (add, update, remove)
- Check schedule/venue availability
- Assign students to classes
- Submit feedback to administration
- View students list and fee-related information

### Student

- View and update own profile
- Request module enrolment
- Track timetable and pending requests
- Submit payment information (invoice/date)
- View assigned classes and training details

## Key Business Workflows

1. **Authentication & Role Routing**
   - User logs in using credentials in the `Login` table
   - System detects role and routes user to the correct dashboard

2. **Enrolment Management**
   - Student requests module
   - Lecturer reviews and processes enrolment
   - Admin validates payments and assigns trainers
   - Trainer assigns class; completion updates are applied when classes end

3. **Payment Validation**
   - Student uploads payment details
   - Admin validates or rejects entries
   - Rejections can trigger reassignment logic in enrolment records

4. **Class Scheduling**
   - Trainer creates or updates classes
   - System checks occupied venues and conflicting times

## Data Model (Main Tables)

The project logic references the following core tables:

- `Login`
- `Admin`
- `Lecturer`
- `Trainer`
- `Trainer_Module`
- `Student`
- `Enrolment`
- `Request`
- `Class`
- `Payment`
- `Feedback`

## Skills Demonstrated

This repository showcases:

- **Object-Oriented Programming (OOP):** domain classes, constructors for specific use-cases, encapsulation via properties
- **Desktop Application Development:** multi-form WinForms architecture and user-control-driven UI composition
- **Database Integration:** SQL Server LocalDB integration with CRUD workflows and transaction-like workflow sequencing
- **Role-Based System Design:** user-role isolation and feature authorization by account type
- **Data Validation & Workflow Rules:** business checks for enrolment duplication, payment status, and scheduling conflicts
- **Software Design for Real Use Cases:** academic operations modeled as maintainable application workflows

## Getting Started

### Prerequisites

- Windows OS
- Visual Studio (with .NET desktop development workload)
- .NET Framework 4.7.2 targeting pack
- SQL Server LocalDB

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/EduTrack-Cafe.git
   cd EduTrack-Cafe
   ```
2. Open `APU Programming Cafe.sln` in Visual Studio (legacy solution filename).
3. Ensure LocalDB is available and the `APU database.mdf` file is accessible.
4. Update connection strings in `App.config` so they match your local machine paths.
5. Build and run the solution.

### Important Configuration Note

Current connection strings contain machine-specific file paths. To run on another machine, replace them with local paths or move to an environment-based configuration strategy.

## Suggested Improvements (Roadmap)

- Centralize and secure connection string management
- Move SQL logic to repository/service classes for cleaner separation
- Add structured exception logging and user-friendly error handling
- Add unit/integration tests for core business workflows
- Migrate to async data access where appropriate
- Consider role/permission tables instead of role strings for scalability

## Repository Structure (High-Level)

- `Admin/` - Admin forms and user controls
- `Lecturer/` - Lecturer forms and enrolment management screens
- `Trainer/` - Trainer forms and coaching class management screens
- `Student/` - Student forms for requests, profile, timetable, payments
- `Login/` - Login and authentication UI
- Root domain classes (`Students.cs`, `Trainers.cs`, `Lecturers.cs`, `Admins.cs`, etc.)
- `APU Programming Cafe.sln` (legacy filename), project files, and LocalDB data files

## Author

Built as a practical academic management project to model real operational workflows in a training/education environment.

