# spring_project
ІПЗ-22 Лєвшов Олександр
# Деканат: звернення, довідки (Dean's office: applications, references)

## Project Overview
This project is designed to streamline the management of applications and references in the dean's office. It includes functionalities for managing students, faculty/staff, inquiries, and certificate issuance. The system uses a REST API to handle various operations.

## Functional Requirements

1. **User Authentication and Authorization**
   - Users can log in with their credentials.
   - Different user roles (faculty, staff, students) have specific permissions.

2. **Student Registration and Management**
   - New students can be registered with their details.
   - Student information can be updated and deleted.

3. **Faculty and Staff Management**
   - Faculty and staff details can be added, updated, and deleted.

4. **Inquiry Submission and Tracking**
   - Students can submit inquiries to the dean’s office.
   - The status of submitted inquiries can be tracked.

5. **Inquiry Processing**
   - Faculty and staff can view and process student inquiries.
   - Actions and results of inquiries are logged.

6. **Certificate Issuance**
   - Certificates can be issued based on processed inquiries.
   - Certificates are linked to the respective inquiries and students.

7. **Notifications and Alerts**
   - Students receive notifications about the status of their inquiries.
   - Faculty and staff receive alerts for new inquiries and pending actions.

8. **Report Generation**
   - Reports on inquiries, processing times, and certificate issuance can be generated.

9. **Search and Filter**
   - Search and filter functionalities are available for students, inquiries, and certificates.

10. **Audit Trail**
    - An audit trail of all actions performed by users is maintained.

## Mockups

1. **Login Page**
   - Fields: Username, Password
   - Buttons: Login, Forgot Password

2. **Dashboard**
   - Summary of pending inquiries, recent activities, and quick links to key functionalities.

3. **Student Management Page**
   - List of students with options to add, edit, delete, and search students.
   - Form for student registration/update.

4. **Faculty/Staff Management Page**
   - List of faculty/staff with options to add, edit, delete, and search faculty/staff.
   - Form for faculty/staff registration/update.

5. **Inquiry Submission Page**
   - Form for students to submit inquiries.
   - Fields: Inquiry Type, Description, Attachments

6. **Inquiry Tracking Page**
   - List of inquiries with status and actions.
   - Detailed view of each inquiry with processing history.

7. **Inquiry Processing Page**
   - Interface for faculty/staff to view and process inquiries.
   - Form for logging actions taken and results.

8. **Certificate Issuance Page**
   - List of issued certificates.
   - Form to issue new certificates linked to inquiries.

9. **Notifications Page**
   - List of notifications and alerts for the user.

10. **Reports Page**
    - Options to generate various reports with filters.

## System Behavior and REST API Endpoints

The REST API endpoints required for the functionalities described are listed below:

| **Functionality**                | **HTTP Method** | **Endpoint**                     | **Description**                        |
|----------------------------------|-----------------|----------------------------------|----------------------------------------|
| **User Authentication**          | POST            | `/api/login`                     | Authenticate user                      |
|                                  | POST            | `/api/logout`                    | Logout user                            |
| **Student Management**           | POST            | `/api/students`                  | Register new student                   |
|                                  | GET             | `/api/students`                  | Get list of students                   |
|                                  | GET             | `/api/students/{studentId}`      | Get details of a specific student      |
|                                  | PUT             | `/api/students/{studentId}`      | Update student information             |
|                                  | DELETE          | `/api/students/{studentId}`      | Delete student                         |
| **Faculty/Staff Management**     | POST            | `/api/faculty`                   | Add new faculty/staff                  |
|                                  | GET             | `/api/faculty`                   | Get list of faculty/staff              |
|                                  | GET             | `/api/faculty/{staffId}`         | Get details of a specific faculty/staff|
|                                  | PUT             | `/api/faculty/{staffId}`         | Update faculty/staff information       |
|                                  | DELETE          | `/api/faculty/{staffId}`         | Delete faculty/staff                   |
| **Inquiry Management**           | POST            | `/api/inquiries`                 | Submit new inquiry                     |
|                                  | GET             | `/api/inquiries`                 | Get list of inquiries                  |
|                                  | GET             | `/api/inquiries/{inquiryId}`     | Get details of a specific inquiry      |
|                                  | PUT             | `/api/inquiries/{inquiryId}`     | Update inquiry status                  |
|                                  | DELETE          | `/api/inquiries/{inquiryId}`     | Delete inquiry                         |
| **Inquiry Processing**           | POST            | `/api/inquirylog`                | Log actions taken on an inquiry        |
|                                  | GET             | `/api/inquirylog/{inquiryId}`    | Get log of actions for a specific inquiry|
| **Certificate Management**       | POST            | `/api/certificates`              | Issue new certificate                  |
|                                  | GET             | `/api/certificates`              | Get list of certificates               |
|                                  | GET             | `/api/certificates/{certificateId}`| Get details of a specific certificate|
|                                  | PUT             | `/api/certificates/{certificateId}`| Update certificate information       |
|                                  | DELETE          | `/api/certificates/{certificateId}`| Delete certificate                   |
| **Notifications**                | GET             | `/api/notifications`             | Get list of notifications for the user |
| **Reports**                      | GET             | `/api/reports/inquiries`         | Generate report on inquiries           |
|                                  | GET             | `/api/reports/certificates`      | Generate report on certificates        |


