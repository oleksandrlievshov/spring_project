# spring_project
ІПЗ-22 Лєвшов Олександр

# Функціональні вимоги
User Authentication and Authorization:

Users must be able to log in and log out securely.
Users must have roles (e.g., student, faculty staff, admin) with different permissions.
Student Inquiry Submission:

Students must be able to submit inquiries through a form.
The form must include fields for inquiry type, description, and attachments.
Inquiry Processing:

Faculty staff must be able to view and process student inquiries.
Actions taken on inquiries must be logged (e.g., status updates, comments).
Certificate Request and Issuance:

Students must be able to request certificates through an online form.
The system must track certificate requests and their statuses.
Inquiry Log Maintenance:

The system must log all actions taken on inquiries, including timestamps and responsible staff.
Dashboard and Notifications:

Users must have a dashboard displaying pending inquiries, requests, and status updates.
Users must receive notifications for important updates (e.g., inquiry processed, certificate ready).
User Profile Management:

Users must be able to view and edit their profiles, including contact information.
Reporting and Analytics:

The system must generate reports on inquiry statistics (e.g., number of inquiries processed, average processing time).
Admins must be able to export data in various formats (e.g., CSV, PDF).
Search and Filter Functionality:

Users must be able to search and filter inquiries and certificates by various criteria (e.g., date, status, type).
Data Security and Privacy:

The system must ensure the security and privacy of user data.
Data access must be restricted based on user roles.
Mockups
1. Login Page
Fields: Username, Password
Button: Login
Link: Forgot Password
2. Student Dashboard
Sections: Pending Inquiries, Pending Certificates, Recent Notifications
Buttons: Submit Inquiry, Request Certificate
3. Inquiry Submission Form
Fields: Inquiry Type (dropdown), Description (textarea), Attachments (file upload)
Button: Submit
4. Faculty Staff Dashboard
Sections: Inquiries to Process, Recent Actions
Buttons: Process Inquiry, Update Status
5. Inquiry Processing Page
Fields: Actions (textarea), Status (dropdown), Add Comment (textarea)
Button: Save
6. Certificate Request Form
Fields: Certificate Type (dropdown), Description (textarea)
Button: Submit
7. Admin Dashboard
Sections: Inquiries Overview, Certificates Overview, Reports
Buttons: Export Data, Generate Report
8. User Profile Page
Fields: First Name, Last Name, Email, Contact Info
Button: Save Changes
9. Search and Filter Page
Fields: Search Bar, Filters (date range, status, type)
Button: Apply Filters
10. Notifications Page
List: Notification items with links to related inquiries/certificates
System Behavior and REST API Endpoints
System Behavior
Authentication: Users authenticate with username and password, receiving a token for session management.
Inquiry Submission: When a student submits an inquiry, it is saved in the database and an entry is created in the inquirylog table.
Inquiry Processing: Faculty staff updates the status of an inquiry, which is logged in the inquirylog.
Certificate Requests: Student requests are logged and processed similarly to inquiries.
Notifications: System sends notifications based on events like status updates or new actions logged.
REST API Endpoints
User Authentication

POST /api/auth/login: Authenticate user and return token.
POST /api/auth/logout: Log out user.
User Management

GET /api/users/{userId}: Get user profile.
PUT /api/users/{userId}: Update user profile.
Inquiries

POST /api/inquiries: Submit a new inquiry.
GET /api/inquiries: Get list of inquiries (with filters).
GET /api/inquiries/{inquiryId}: Get details of a specific inquiry.
PUT /api/inquiries/{inquiryId}: Update inquiry status or details.
Inquiry Logs

GET /api/inquiries/{inquiryId}/logs: Get logs for a specific inquiry.
POST /api/inquiries/{inquiryId}/logs: Add a new log entry for an inquiry.
Certificates

POST /api/certificates: Request a new certificate.
GET /api/certificates: Get list of certificate requests (with filters).
GET /api/certificates/{certificateId}: Get details of a specific certificate.
PUT /api/certificates/{certificateId}: Update certificate request status or details.
Notifications

GET /api/notifications: Get list of notifications for the authenticated user.
Reports

GET /api/reports/inquiries: Get report on inquiries.
GET /api/reports/certificates: Get report on certificates.
These requirements and endpoints provide a comprehensive system for managing student inquiries and certificate requests, ensuring efficient processing and tracking within a faculty or academic department.
