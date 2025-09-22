# CardDemo Application - Business User Stories

## Overview

This document contains business-level user stories extracted from the CardDemo COBOL application. These stories focus on end-user interactions and business processes that would be relevant for modernizing the system into a more user-centric application (e.g., web or mobile interface).

The user stories follow the format: **"As a [type of user] I want to [perform some business action] So that [business value/goal]"**

## Table of Contents

1. [Authentication & Access Management](#authentication--access-management)
2. [Navigation & Menu Systems](#navigation--menu-systems)
3. [User Management](#user-management)
4. [Credit Card Management](#credit-card-management)
5. [Account Management](#account-management)
6. [Transaction Management](#transaction-management)
7. [Bill Payment](#bill-payment)
8. [Reporting](#reporting)

---

## Authentication & Access Management

### User Sign-on and Authentication
- **As a** system user **I want to** sign into the CardDemo application with my user ID and password **So that** I can access my account information and perform banking operations securely
- **As a** system user **I want to** receive clear error messages when I enter invalid credentials **So that** I understand what went wrong and can correct my login attempt
- **As a** system user **I want to** be automatically directed to the appropriate menu based on my user type **So that** I can quickly access the features relevant to my role

### Role-based Access Control
- **As an** administrator **I want to** be automatically routed to the admin menu after successful login **So that** I can access administrative functions without additional navigation
- **As a** regular user **I want to** be automatically routed to the main user menu after successful login **So that** I can access customer-facing features appropriate to my role
- **As a** system user **I want to** have my access level validated during login **So that** I only see features and data appropriate to my role

---

## Navigation & Menu Systems

### Main Menu Navigation
- **As a** regular user **I want to** access a main menu with available options **So that** I can navigate to different features of the banking system
- **As a** regular user **I want to** see clearly labeled menu options **So that** I can easily find the functionality I need
- **As a** regular user **I want to** be able to exit the application safely **So that** I can end my session securely

### Administrative Menu Access
- **As an** administrator **I want to** access an administrative menu with management functions **So that** I can perform system administration tasks
- **As an** administrator **I want to** see admin-specific options in my menu **So that** I can manage users, accounts, and system settings
- **As an** administrator **I want to** navigate between different administrative functions **So that** I can efficiently perform multiple management tasks

---

## User Management

### User Listing and Browsing
- **As an** administrator **I want to** view a list of all system users **So that** I can see who has access to the system
- **As an** administrator **I want to** browse through users with pagination **So that** I can efficiently navigate through large numbers of users
- **As an** administrator **I want to** select a user from the list **So that** I can view or modify their details
- **As an** administrator **I want to** see user information like names and user types **So that** I can quickly identify specific users

### User Creation
- **As an** administrator **I want to** add new regular users to the system **So that** customers can access their accounts
- **As an** administrator **I want to** add new administrative users to the system **So that** I can delegate administrative responsibilities
- **As an** administrator **I want to** specify user details like first name, last name, user ID, password, and user type **So that** new users have complete profiles
- **As an** administrator **I want to** receive confirmation when a user is successfully added **So that** I know the operation completed successfully
- **As an** administrator **I want to** be prevented from creating duplicate user IDs **So that** each user has a unique identifier

### User Updates
- **As an** administrator **I want to** update existing user information **So that** user profiles remain current and accurate
- **As an** administrator **I want to** modify user details like names, passwords, and user types **So that** I can maintain accurate user records
- **As an** administrator **I want to** see the current user information before making changes **So that** I can make informed updates
- **As an** administrator **I want to** receive confirmation when user updates are successful **So that** I know changes were saved
- **As an** administrator **I want to** be notified if no changes were detected **So that** I don't perform unnecessary update operations

### User Deletion
- **As an** administrator **I want to** delete users from the system **So that** I can remove access for users who no longer need it
- **As an** administrator **I want to** see user details before confirming deletion **So that** I can verify I'm deleting the correct user
- **As an** administrator **I want to** receive confirmation when a user is successfully deleted **So that** I know the user has been removed from the system
- **As an** administrator **I want to** be prevented from deleting non-existent users **So that** I receive appropriate error messages

---

## Credit Card Management

### Credit Card Listing and Browsing
- **As a** regular user **I want to** view a list of credit cards associated with my account **So that** I can see all my available cards
- **As an** administrator **I want to** view all credit cards in the system **So that** I can manage the entire card portfolio
- **As a** user **I want to** browse through credit cards with pagination **So that** I can efficiently navigate through multiple cards
- **As a** user **I want to** filter credit cards by account number **So that** I can find specific cards quickly
- **As a** user **I want to** select a credit card from the list **So that** I can view detailed information or make updates

### Credit Card Details Viewing
- **As a** user **I want to** view detailed information about a specific credit card **So that** I can see all relevant card details
- **As a** user **I want to** see card information like card number, account ID, cardholder name, expiration date, and status **So that** I have complete visibility into card details
- **As a** user **I want to** access card details by providing account and card numbers **So that** I can quickly find specific card information

### Credit Card Updates
- **As an** administrator **I want to** update credit card information **So that** card details remain current and accurate
- **As an** administrator **I want to** modify card details like cardholder name, expiration date, and card status **So that** I can maintain accurate card records
- **As an** administrator **I want to** validate card information before saving changes **So that** only valid data is stored in the system
- **As an** administrator **I want to** receive confirmation when card updates are successful **So that** I know changes were saved properly
- **As an** administrator **I want to** be notified if no changes were detected **So that** I don't perform unnecessary update operations

---

## Account Management

### Account Viewing
- **As a** user **I want to** view detailed account information **So that** I can see my account status and balances
- **As a** user **I want to** see account details like account ID, customer information, balances, and limits **So that** I have complete visibility into my account
- **As a** user **I want to** access account information by providing an account number **So that** I can quickly find my account details
- **As a** user **I want to** see associated customer information with my account **So that** I can verify my personal details

### Account Updates
- **As an** administrator **I want to** update account information **So that** account details remain current and accurate
- **As an** administrator **I want to** modify account details like credit limits, cash credit limits, current balances, and account status **So that** I can maintain accurate account records
- **As an** administrator **I want to** update customer information associated with accounts **So that** personal details remain current
- **As an** administrator **I want to** validate account information before saving changes **So that** only valid data is stored in the system
- **As an** administrator **I want to** receive confirmation when account updates are successful **So that** I know changes were saved properly

---

## Transaction Management

### Transaction Listing and Browsing
- **As a** user **I want to** view a list of transactions **So that** I can see my transaction history
- **As a** user **I want to** browse through transactions with pagination **So that** I can efficiently navigate through my transaction history
- **As a** user **I want to** select a transaction from the list **So that** I can view detailed transaction information
- **As a** user **I want to** see transaction information like transaction ID, amount, date, and description **So that** I can understand my transaction activity

### Transaction Details Viewing
- **As a** user **I want to** view detailed information about a specific transaction **So that** I can see all relevant transaction details
- **As a** user **I want to** see complete transaction information including merchant details, amounts, dates, and transaction codes **So that** I have full visibility into transaction specifics
- **As a** user **I want to** access transaction details by providing a transaction ID **So that** I can quickly find specific transaction information

### Transaction Creation
- **As an** administrator **I want to** add new transactions to the system **So that** I can record transaction activity
- **As an** administrator **I want to** specify transaction details like account/card numbers, amounts, dates, merchant information, and transaction codes **So that** transactions have complete information
- **As an** administrator **I want to** validate transaction information before saving **So that** only valid transactions are recorded
- **As an** administrator **I want to** receive confirmation when transactions are successfully added **So that** I know the transaction was recorded
- **As an** administrator **I want to** be able to copy information from previous transactions **So that** I can efficiently create similar transactions

---

## Bill Payment

### Online Bill Payment
- **As a** customer **I want to** pay my account balance online **So that** I can conveniently make payments without visiting a branch
- **As a** customer **I want to** pay my full account balance **So that** I can clear my outstanding debt
- **As a** customer **I want to** see my current account balance before making a payment **So that** I know exactly how much I owe
- **As a** customer **I want to** receive confirmation when my payment is processed **So that** I know my payment was successful
- **As a** customer **I want to** have a transaction record created for my payment **So that** I have proof of payment for my records

### Payment Processing
- **As a** customer **I want to** have my account balance updated immediately after payment **So that** my account reflects the current amount owed
- **As a** customer **I want to** be prevented from making payments on invalid accounts **So that** I don't accidentally pay the wrong account
- **As a** customer **I want to** receive appropriate error messages if payment processing fails **So that** I understand what went wrong and can retry

---

## Reporting

### Monthly Transaction Reports
- **As a** user **I want to** generate monthly transaction reports **So that** I can analyze my transaction activity for a specific month
- **As a** user **I want to** automatically generate reports for the current month **So that** I can quickly access recent transaction data
- **As a** user **I want to** have reports submitted as batch jobs **So that** large reports don't impact system performance

### Yearly Transaction Reports
- **As a** user **I want to** generate yearly transaction reports **So that** I can analyze my transaction activity for an entire year
- **As a** user **I want to** automatically generate reports for the current year **So that** I can access comprehensive annual transaction data
- **As a** user **I want to** have yearly reports processed efficiently **So that** I can access large datasets without system delays

### Custom Date Range Reports
- **As a** user **I want to** generate transaction reports for custom date ranges **So that** I can analyze transaction activity for specific periods
- **As a** user **I want to** specify start and end dates for my reports **So that** I can get exactly the data I need
- **As a** user **I want to** validate date inputs before generating reports **So that** I only create reports with valid date ranges
- **As a** user **I want to** receive appropriate error messages for invalid date inputs **So that** I can correct my date selections

### Report Management
- **As a** user **I want to** submit report generation requests **So that** I can obtain transaction reports without manual processing
- **As a** user **I want to** have reports generated in the background **So that** I can continue using the system while reports are being created
- **As a** user **I want to** receive confirmation when report generation is initiated **So that** I know my request was received

---

## Summary

This document captures the core business functionality of the CardDemo application from an end-user perspective. These user stories focus on the business value and user interactions rather than technical implementation details, making them suitable for guiding the modernization of the system into contemporary web or mobile applications.

The stories are organized by functional areas and represent the complete business workflow from user authentication through transaction management and reporting, providing a comprehensive view of the system's business capabilities.
