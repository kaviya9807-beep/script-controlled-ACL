Script-Controlled ACL – Restrict Record Access Based on Field Value

📌 Project Description

This ServiceNow project demonstrates how to implement script-controlled Access Control Lists (ACLs) to restrict users from accessing records based on user roles and field values.

In this project, users with the required role can access records based on the Branch field. EEE branch records are restricted to authorized users, while administrators have full access.

⏱️ Duration

3 Hours

🎯 Objectives

- Create users and custom roles in ServiceNow.
- Create a custom "Institution Details" table.
- Create records with different branch values.
- Configure Read, Create, Write, and Delete ACLs.
- Use scripts to control record-level access.
- Verify access using user impersonation.

👤 User Creation

Create a test user with the following details:

- User ID: EEE User
- First Name: EEE
- Last Name: User
- Email: eeeuser@gmail.com

🔐 Roles

Create the following custom roles:

- "bb1"
- "bb2"
- "bb3"
- "bb4"

Assign the required roles to the EEE User.

🗃️ Table Creation

Create a custom table with:

- Label: Institution Details
- Name: "u_institution_details"
- Extends: False

Fields

Field| Type
Student Roll Number| Auto Number
Student Name| Reference – User
Faculty Name| Reference – User
Branch| Choice
Email| String
Phone Number| String
Description| Multi String

Branch Choices

- ECE
- EEE
- CSE

Create multiple records using different branch values.

🔒 READ ACL

Create a Record ACL with:

- Operation: Read
- Name: "u_institution_details"
- Active: True
- Advanced: True
- Required Role: "bb1"
- Data Condition: Branch is EEE

Script

(function () {

    // Allow admin users full access
    if (gs.hasRole('admin')) {
        return true;
    }

    // Allow only EEE branch users to see EEE records
    if (gs.hasRole('bb1')) {
        return true;
    }

    // Deny access for all others
    return false;

})();

➕ CREATE ACL

Create a Record ACL with:

- Operation: Create
- Name: "u_institution_details"
- Active: True
- Required Role: "bb2"
- Data Condition: None

✏️ WRITE ACL

Create a Record ACL with:

- Operation: Write
- Name: "u_institution_details"
- Active: True
- Required Role: "bb3"
- Data Condition: None

🗑️ DELETE ACL

Create a Record ACL with:

- Operation: Delete
- Name: "u_institution_details"
- Active: True
- Required Role: "bb4"
- Data Condition: None

✅ Verification

Read Access

- User with "bb1" role can view EEE branch records.
- User without the required role cannot view the records.
- Admin can view all records.

Create Access

A user with "bb1" and "bb2" roles can access the New button and create records.

Write Access

A user with "bb1", "bb2", and "bb3" roles can view and edit EEE branch records.

Delete Access

A user with "bb1", "bb2", "bb3", and "bb4" roles can view, create, edit, and delete EEE branch records.

🏁 Outcome

By completing this project, learners understand how script-controlled READ, WRITE, CREATE, and DELETE ACLs enforce record-level security in ServiceNow.

The project demonstrates how user roles and record field values can be used together to control access to sensitive data across forms and lists.

🛠️ Technologies Used

- ServiceNow
- Access Control Lists (ACL)
- JavaScript
- User Roles
- Record-Level Security

📚 Project Type

ServiceNow – Script-Controlled ACL Micro Project
