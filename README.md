# Streamlining_Ticket_Assignment_for_Efficient_Support_Operations
# Objective:
The goal of this project is to implement an automated ticket assignment mechanism in ServiceNow for ABC Corporation’s support operations. This system ensures that incoming support tickets are routed to the most appropriate teams based on the nature of the issue. The initiative aims to:
Reduce time spent manually triaging tickets
Improve ticket resolution times
Enhance customer satisfaction
Optimize use of internal support resources

# Implementation Steps:
# 1. User Setup:
Location: ServiceNow → All → Users (under System Security)
Click New, input user details, and click Submit
Repeat for additional users

# 2. Group Setup:
Location: ServiceNow → All → Groups (under System Security)
Click New, input group details, and click Submit
Repeat for all necessary support groups

# 3. Role Setup:
Location: ServiceNow → All → Roles (under System Security)
Click New, define role attributes, and click Submit
Repeat as needed

# 4. Table Creation:
Location: ServiceNow → All → Tables (under System Definition)
Click New, provide the following details:
Label: Operations Related
Enable Create Module and Mobile Module
New Menu Name: Operations Related
Define necessary table columns
Click Submit
Issue Field Choices (Form Design):
Unable to login to platform
404 Error
Regarding Certificates
Regarding User Expired

# 5. Assign Roles & Users to Groups:
Certificates Group
Add Katherine Pierce as Group Member
Assign Certification_Role
Platform Group
Add Manne Niranjan as Group Member
Assign Platform_Role

# 6. Assign Roles to Table:
Location: ServiceNow → Tables → Operations Related Table
Under Application Access:
Read Access: Requires Platform_Role or Certification_Role
Write Access: Requires Platform_Role or Certification_Role

# 7. Create ACLs (Access Control List): 
Location: ServiceNow → All → ACL (under System Security)
Create 4 ACLs to enforce role-based field access
Add admin role under Requires Role where necessary

# 8. Flow Designer:
Flow 1: Certificates-Related Issues
Flow Name: Regarding Certificate
Application: Global
Run As: System User
Trigger: Record Created or Updated
Table: Operations Related
Condition: Issue is Regarding Certificates
Action:
Field: Assigned to group
Value: Certificates Group
Save and Activate       
Flow 2: Platform-Related Issues
Flow Name: Regarding Platform
Application: Global
Run As: System User
Trigger: Record Created or Updated
Table: Operations Related
Condition:
Issue is Unable to login to platform, OR
Issue is 404 Error, OR
Issue is Regarding User Expired
Action:
Field: Assigned to group
Value: Platform Group
Save and Activate

# Project Structure:
Streamlining-Ticket-Assignment/

├── Users/
│   ├── Katherine Pierce (Certificates Group)

│   └── Manne Niranjan (Platform Group)

├── Groups/
│   ├── Certificates Group

│   └── Platform Group

├── Roles/
│   ├── Certification_Role

│   └── Platform_Role

├── Tables/
│   └── u_operations_related

│       ├── Issue (Choice field)

│       ├── Assigned to Group

│       └── Other custom columns

├── ACLs/
│   ├── Read Access (Platform/Certification Roles)

│   ├── Write Access (Platform/Certification Roles)

│   └── Field-Level Restrictions

├── Flows/
│   ├── Regarding Certificate → Assigns to Certificates Group

│   └── Regarding Platform → Assigns to Platform Group

# Outcome:
With this automated ticket routing system in place:
Tickets are intelligently and automatically assigned to the correct support groups
Manual effort in triaging tickets is eliminated
Resolution time is significantly reduced
Customer satisfaction is increased due to faster response
Internal resources are used more efficiently





