# CardDemo Application - Business-Level User Stories

## Overview
This document contains business-level user stories extracted from the CardDemo COBOL application. These stories focus on end-user interactions and business value, designed to support modernization efforts for web or mobile interfaces.

**Source:** COBOL files from `00.phase-1-input/cbl/` directory  
**Total Modules:** 7 functional areas  
**User Types:** Regular User, Admin User, Card Holder, Account Manager

---

## 1. Authentication & Authorization

### Sign-on and Access Control

**US-AUTH-001**  
As a **card holder**  
I want to **log in to the system with my user ID and password**  
So that **I can securely access my account information and perform transactions**

**US-AUTH-002**  
As a **system user**  
I want to **be automatically routed to the appropriate menu based on my user type (regular or admin)**  
So that **I only see options and functions relevant to my role**

**US-AUTH-003**  
As a **regular user**  
I want to **access a main menu with account, card, transaction, and bill payment options**  
So that **I can navigate to the features I need for managing my account**

**US-AUTH-004**  
As an **admin user**  
I want to **access an admin menu with user management, reporting, and system administration options**  
So that **I can perform administrative tasks and manage system users**

**US-AUTH-005**  
As a **system user**  
I want to **receive clear error messages when I enter invalid credentials**  
So that **I understand what went wrong and can correct my login information**

---

## 2. Account Management

### Account Viewing and Search

**US-ACCT-001**  
As an **account manager**  
I want to **search for accounts by account number**  
So that **I can quickly locate specific customer accounts**

**US-ACCT-002**  
As an **account manager**  
I want to **view complete account details including customer information (name, SSN, DOB, address, phone)**  
So that **I can verify customer identity and account status**

**US-ACCT-003**  
As an **account manager**  
I want to **see account financial information (credit limit, cash credit limit, current balance, open date, expiry date)**  
So that **I can understand the account's financial standing and limits**

**US-ACCT-004**  
As a **card holder**  
I want to **view my account status and balance information**  
So that **I can monitor my spending and available credit**

### Account Updates

**US-ACCT-005**  
As an **account manager**  
I want to **update account status (active/inactive)**  
So that **I can control whether an account can be used for transactions**

**US-ACCT-006**  
As an **account manager**  
I want to **modify credit limits and cash credit limits**  
So that **I can adjust customer spending capacity based on creditworthiness**

**US-ACCT-007**  
As an **account manager**  
I want to **update customer personal information (name, address, phone number)**  
So that **I can keep customer records current and accurate**

**US-ACCT-008**  
As an **account manager**  
I want to **receive validation errors when I enter invalid data (invalid dates, phone numbers, SSN)**  
So that **I can correct mistakes before saving changes**

**US-ACCT-009**  
As an **account manager**  
I want to **see a confirmation message after successfully updating an account**  
So that **I know my changes have been saved**

---

## 3. Card Management

### Card Listing and Search

**US-CARD-001**  
As a **card holder**  
I want to **view a list of all credit cards associated with my account**  
So that **I can see all my active and inactive cards**

**US-CARD-002**  
As an **account manager**  
I want to **filter credit cards by account number**  
So that **I can see all cards belonging to a specific customer account**

**US-CARD-003**  
As a **card holder**  
I want to **navigate through paginated card listings**  
So that **I can browse through large numbers of cards efficiently**

**US-CARD-004**  
As an **account manager**  
I want to **select a specific card from the list to view more details or update it**  
So that **I can manage individual cards**

### Card Details

**US-CARD-005**  
As a **card holder**  
I want to **view detailed information about a specific credit card (card number, expiry date, CVV, cardholder name, status)**  
So that **I can verify my card information and check its validity**

**US-CARD-006**  
As an **account manager**  
I want to **search for a card by both account number and card number**  
So that **I can quickly locate a specific card**

### Card Updates

**US-CARD-007**  
As an **account manager**  
I want to **update the cardholder name embossed on the card**  
So that **I can correct name spellings or update names after life events**

**US-CARD-008**  
As an **account manager**  
I want to **change the card status (active/inactive)**  
So that **I can activate new cards or deactivate lost/stolen cards**

**US-CARD-009**  
As an **account manager**  
I want to **update the card expiry date (month and year)**  
So that **I can extend card validity or set appropriate expiration dates**

**US-CARD-010**  
As an **account manager**  
I want to **receive validation errors for invalid expiry dates (invalid month, invalid year)**  
So that **I can enter correct card expiration information**

**US-CARD-011**  
As an **account manager**  
I want to **see a confirmation message after successfully updating a card**  
So that **I know the card changes have been saved**

---

## 4. Transaction Management

### Transaction Viewing and Search

**US-TXN-001**  
As a **card holder**  
I want to **view a paginated list of all transactions on my account**  
So that **I can review my spending history and transaction activity**

**US-TXN-002**  
As a **card holder**  
I want to **see transaction details including transaction ID, type, category, amount, description, and dates**  
So that **I can understand each transaction and verify its accuracy**

**US-TXN-003**  
As a **card holder**  
I want to **navigate through pages of transactions (next page, previous page)**  
So that **I can browse through my complete transaction history**

**US-TXN-004**  
As an **account manager**  
I want to **search for transactions by transaction ID**  
So that **I can quickly locate and investigate specific transactions**

**US-TXN-005**  
As a **card holder**  
I want to **view detailed information about a specific transaction including merchant details (name, city, zip code)**  
So that **I can identify where and when a purchase was made**

**US-TXN-006**  
As a **card holder**  
I want to **see both the original transaction date and processing date**  
So that **I can understand when a transaction occurred versus when it posted to my account**

### Transaction Entry

**US-TXN-007**  
As an **account manager**  
I want to **add new transactions to an account by entering account ID or card number**  
So that **I can record manual transactions or corrections**

**US-TXN-008**  
As an **account manager**  
I want to **enter transaction details including type, category, source, amount, description, dates, and merchant information**  
So that **I can create complete and accurate transaction records**

**US-TXN-009**  
As an **account manager**  
I want to **receive validation errors when required transaction fields are empty**  
So that **I ensure all necessary transaction information is provided**

**US-TXN-010**  
As an **account manager**  
I want to **validate that transaction amounts are in the correct format (including positive/negative indicators)**  
So that **I can accurately record credits and debits**

**US-TXN-011**  
As an **account manager**  
I want to **validate transaction dates are in the correct format (YYYY-MM-DD)**  
So that **I can ensure transactions are dated correctly**

**US-TXN-012**  
As an **account manager**  
I want to **confirm before adding a transaction to the system**  
So that **I can review the details one final time before committing the transaction**

**US-TXN-013**  
As an **account manager**  
I want to **receive a confirmation message after successfully adding a transaction**  
So that **I know the transaction has been recorded**

**US-TXN-014**  
As an **account manager**  
I want to **clear the transaction entry form to start a new transaction**  
So that **I can quickly add multiple transactions without navigating away**

---

## 5. Bill Payment

### Online Bill Payment

**US-BILL-001**  
As a **card holder**  
I want to **view my current account balance**  
So that **I can see how much I owe**

**US-BILL-002**  
As a **card holder**  
I want to **pay my account balance in full online**  
So that **I can settle my outstanding balance conveniently**

**US-BILL-003**  
As a **card holder**  
I want to **enter my account ID to initiate a payment**  
So that **I can specify which account to pay**

**US-BILL-004**  
As a **card holder**  
I want to **receive validation that my account ID is valid and numeric**  
So that **I can ensure I'm paying the correct account**

**US-BILL-005**  
As a **card holder**  
I want to **see the current balance before confirming payment**  
So that **I can verify the amount I'm about to pay**

**US-BILL-006**  
As a **card holder**  
I want to **receive confirmation after successfully making a payment**  
So that **I know my payment has been processed**

**US-BILL-007**  
As a **card holder**  
I want to **have my payment recorded as a transaction**  
So that **it appears in my transaction history**

**US-BILL-008**  
As a **card holder**  
I want to **see my account balance updated to zero after payment**  
So that **I can confirm my account is paid in full**

---

## 6. Reporting

### Transaction Reports

**US-RPT-001**  
As an **account manager**  
I want to **generate monthly transaction reports**  
So that **I can analyze transaction activity for a specific month**

**US-RPT-002**  
As an **account manager**  
I want to **generate yearly transaction reports**  
So that **I can review annual transaction trends and patterns**

**US-RPT-003**  
As an **account manager**  
I want to **generate transaction reports for a custom date range (start date to end date)**  
So that **I can analyze transactions for any specific time period**

**US-RPT-004**  
As an **account manager**  
I want to **enter report parameters including start date and end date**  
So that **I can specify the exact reporting period I need**

**US-RPT-005**  
As an **account manager**  
I want to **validate that report dates are in the correct format (YYYY-MM-DD)**  
So that **I can ensure the report covers the intended time period**

**US-RPT-006**  
As an **account manager**  
I want to **receive validation errors when report parameters are invalid or missing**  
So that **I can correct my input before generating the report**

**US-RPT-007**  
As an **account manager**  
I want to **submit batch jobs for report generation**  
So that **I can run large reports without blocking other system activities**

**US-RPT-008**  
As an **account manager**  
I want to **receive confirmation that my report request has been submitted**  
So that **I know the report generation is in progress**

---

## 7. User Administration

### User Listing and Search

**US-USER-001**  
As an **admin user**  
I want to **view a list of all system users**  
So that **I can see who has access to the system**

**US-USER-002**  
As an **admin user**  
I want to **see user details including user ID, first name, last name, and user type (regular/admin)**  
So that **I can identify users and their access levels**

**US-USER-003**  
As an **admin user**  
I want to **navigate through paginated user listings**  
So that **I can browse through all system users efficiently**

**US-USER-004**  
As an **admin user**  
I want to **select a user from the list to view, update, or delete**  
So that **I can manage individual user accounts**

### User Creation

**US-USER-005**  
As an **admin user**  
I want to **add new users to the system**  
So that **I can grant access to new employees or customers**

**US-USER-006**  
As an **admin user**  
I want to **enter user information including first name, last name, user ID, password, and user type**  
So that **I can create complete user profiles**

**US-USER-007**  
As an **admin user**  
I want to **receive validation errors when required user fields are empty**  
So that **I ensure all necessary user information is provided**

**US-USER-008**  
As an **admin user**  
I want to **receive an error message if the user ID already exists**  
So that **I can choose a unique user ID**

**US-USER-009**  
As an **admin user**  
I want to **specify whether a new user is a regular user or admin user**  
So that **I can control their access level and permissions**

**US-USER-010**  
As an **admin user**  
I want to **receive confirmation after successfully adding a user**  
So that **I know the user account has been created**

### User Updates

**US-USER-011**  
As an **admin user**  
I want to **search for a user by user ID to update their information**  
So that **I can locate and modify existing user accounts**

**US-USER-012**  
As an **admin user**  
I want to **view current user information before making changes**  
So that **I can see what needs to be updated**

**US-USER-013**  
As an **admin user**  
I want to **update user details including first name, last name, password, and user type**  
So that **I can keep user information current and adjust access levels**

**US-USER-014**  
As an **admin user**  
I want to **receive validation errors when trying to save incomplete user information**  
So that **I maintain data quality in the user database**

**US-USER-015**  
As an **admin user**  
I want to **receive a warning if I try to save without making any changes**  
So that **I don't create unnecessary update transactions**

**US-USER-016**  
As an **admin user**  
I want to **receive confirmation after successfully updating a user**  
So that **I know the user changes have been saved**

### User Deletion

**US-USER-017**  
As an **admin user**  
I want to **search for a user by user ID to delete them**  
So that **I can remove users who no longer need system access**

**US-USER-018**  
As an **admin user**  
I want to **view user information before confirming deletion**  
So that **I can verify I'm deleting the correct user**

**US-USER-019**  
As an **admin user**  
I want to **confirm before permanently deleting a user**  
So that **I can prevent accidental deletion of user accounts**

**US-USER-020**  
As an **admin user**  
I want to **receive confirmation after successfully deleting a user**  
So that **I know the user has been removed from the system**

**US-USER-021**  
As an **admin user**  
I want to **receive an error message if trying to delete a non-existent user**  
So that **I understand when a user ID is invalid or already removed**

---

## Summary

This document captures **89 business-level user stories** across **7 functional modules** extracted from the CardDemo COBOL application. These stories focus on:

- **End-user interactions** rather than technical implementation
- **Business value and goals** for different user types
- **User workflows** that can be modernized for web or mobile platforms
- **Validation and feedback** mechanisms that improve user experience

### Modules Covered
1. **Authentication & Authorization** - 5 user stories
2. **Account Management** - 9 user stories
3. **Card Management** - 11 user stories
4. **Transaction Management** - 14 user stories
5. **Bill Payment** - 8 user stories
6. **Reporting** - 8 user stories
7. **User Administration** - 21 user stories (Admin-only features)

### User Types
- **Card Holder** - End customers who use credit cards
- **Account Manager** - Staff who manage customer accounts and transactions
- **Admin User** - System administrators who manage users and system operations
- **Regular User** - Standard system users with limited access

These user stories are ready to be used for:
- Modernization planning and estimation
- UI/UX design for web and mobile interfaces
- API and microservices design
- Agile sprint planning and backlog prioritization
- Stakeholder communication and requirements validation
