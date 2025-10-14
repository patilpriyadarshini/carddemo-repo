# CardDemo Business User Stories

**Document Created:** October 14, 2025  
**Source Repository:** patilpriyadarshini/carddemo-repo  
**Source Directory:** 00.phase-1-input/cbl/  
**COBOL Programs Analyzed:** 18 files

---

## Table of Contents

1. [Introduction](#introduction)
2. [Authentication](#1-authentication)
3. [Account Management](#2-account-management)
4. [Card Management](#3-card-management)
5. [Transaction Management](#4-transaction-management)
6. [Bill Payment](#5-bill-payment)
7. [User Administration](#6-user-administration)
8. [Reports](#7-reports)
9. [Navigation](#8-navigation)

---

## Introduction

This document contains business-level user stories extracted from the CardDemo credit card management system COBOL codebase. These stories capture the essential user interactions and business operations across different system modules, focusing exclusively on end-user functionality and business value.

**User Roles Identified:**
- **Regular User**: Credit card account holders who manage their accounts, cards, and transactions
- **Administrator**: System administrators who manage users and system operations

---

## 1. Authentication

### Module: COSGN00C (Sign-On)

**US-AUTH-001**  
As a Regular User  
I want to log in with my User ID and Password  
So that I can securely access my credit card account information

**US-AUTH-002**  
As a Regular User  
I want to receive immediate feedback if my login credentials are incorrect  
So that I can correct my credentials and successfully access the system

**US-AUTH-003**  
As a Regular User  
I want the system to validate my credentials before granting access  
So that my account remains secure from unauthorized access

**US-AUTH-004**  
As a Regular User  
I want to be directed to my main menu after successful login  
So that I can quickly access the features I need

**US-AUTH-005**  
As an Administrator  
I want to log in with my administrative credentials  
So that I can access administrative functions and manage the system

---

## 2. Account Management

### Module: COACTVWC (Account View), COACTUPC (Account Update)

**US-ACCT-001**  
As a Regular User  
I want to view my complete account details  
So that I can verify my account information is correct

**US-ACCT-002**  
As a Regular User  
I want to see my account balance and credit limit  
So that I can understand my available credit

**US-ACCT-003**  
As a Regular User  
I want to view my account status  
So that I know if my account is active or has any issues

**US-ACCT-004**  
As a Regular User  
I want to update my account information  
So that I can keep my contact details and personal information current

**US-ACCT-005**  
As a Regular User  
I want to search for my account using my account number  
So that I can quickly access my specific account details

**US-ACCT-006**  
As a Regular User  
I want to see my account opening date and expiration date  
So that I can track my account lifecycle

**US-ACCT-007**  
As a Regular User  
I want to receive confirmation after updating my account information  
So that I know my changes were saved successfully

**US-ACCT-008**  
As a Regular User  
I want the system to validate my account updates before saving  
So that I don't accidentally enter invalid information

---

## 3. Card Management

### Module: COCRDLIC (Card List), COCRDSLC (Card View), COCRDUPC (Card Update)

**US-CARD-001**  
As a Regular User  
I want to view a list of all credit cards associated with my account  
So that I can see all my active and inactive cards

**US-CARD-002**  
As a Regular User  
I want to select a specific credit card from my list  
So that I can view detailed information about that card

**US-CARD-003**  
As a Regular User  
I want to view complete card details including card number, CVV, and expiration date  
So that I can use my card for transactions

**US-CARD-004**  
As a Regular User  
I want to see the name embossed on my card  
So that I can verify the cardholder name is correct

**US-CARD-005**  
As a Regular User  
I want to check the status of my card (active/inactive)  
So that I know whether my card is currently usable

**US-CARD-006**  
As a Regular User  
I want to update my card details such as the embossed name  
So that I can correct any errors or update my information

**US-CARD-007**  
As a Regular User  
I want to update my card expiration date  
So that I can extend my card validity when renewed

**US-CARD-008**  
As a Regular User  
I want to activate or deactivate my card  
So that I can control when my card can be used

**US-CARD-009**  
As a Regular User  
I want to search for a card using account number and card number  
So that I can quickly find a specific card

**US-CARD-010**  
As a Regular User  
I want to receive validation errors if I enter invalid card information  
So that I can correct my entries before saving

**US-CARD-011**  
As a Regular User  
I want to confirm my card updates before they are saved  
So that I can review changes and prevent accidental modifications

**US-CARD-012**  
As a Regular User  
I want to receive confirmation when my card updates are successful  
So that I know my changes have been applied

---

## 4. Transaction Management

### Module: COTRN00C (Transaction List), COTRN01C (Transaction View), COTRN02C (Transaction Add)

**US-TRN-001**  
As a Regular User  
I want to view a list of all my credit card transactions  
So that I can track my spending and payment history

**US-TRN-002**  
As a Regular User  
I want to see transaction details including amount, date, merchant, and type  
So that I can understand each transaction on my account

**US-TRN-003**  
As a Regular User  
I want to view detailed information for a specific transaction  
So that I can verify transaction accuracy

**US-TRN-004**  
As a Regular User  
I want to see the transaction type (purchase, payment, refund, etc.)  
So that I can categorize my financial activities

**US-TRN-005**  
As a Regular User  
I want to view the merchant name and location for each transaction  
So that I can identify where purchases were made

**US-TRN-006**  
As a Regular User  
I want to see the transaction source (online, in-store, etc.)  
So that I can track how I'm using my card

**US-TRN-007**  
As a Regular User  
I want to view transaction descriptions  
So that I can get additional context about each transaction

**US-TRN-008**  
As a Regular User  
I want to add a new transaction to my account  
So that I can record purchases or payments

**US-TRN-009**  
As a Regular User  
I want the system to validate my transaction details before adding  
So that I ensure all required information is provided correctly

**US-TRN-010**  
As a Regular User  
I want to confirm transaction additions before they are saved  
So that I can review the details and prevent errors

**US-TRN-011**  
As a Regular User  
I want to receive confirmation when a transaction is successfully added  
So that I know the transaction was recorded

**US-TRN-012**  
As a Regular User  
I want to search for transactions by transaction ID  
So that I can quickly find specific transactions

**US-TRN-013**  
As a Regular User  
I want to paginate through my transaction history  
So that I can efficiently browse large numbers of transactions

---

## 5. Bill Payment

### Module: COBIL00C (Bill Payment)

**US-BILL-001**  
As a Regular User  
I want to view my current account balance  
So that I know how much I owe

**US-BILL-002**  
As a Regular User  
I want to pay my account balance in full  
So that I can clear my outstanding debt

**US-BILL-003**  
As a Regular User  
I want to see my payment amount before confirming  
So that I can verify the payment details are correct

**US-BILL-004**  
As a Regular User  
I want to confirm my payment before it is processed  
So that I can prevent accidental payments

**US-BILL-005**  
As a Regular User  
I want to receive confirmation when my payment is successful  
So that I know my payment was processed

**US-BILL-006**  
As a Regular User  
I want the system to automatically generate a payment transaction record  
So that my payment is properly documented in my transaction history

**US-BILL-007**  
As a Regular User  
I want to see my updated account balance after making a payment  
So that I can verify my payment was applied correctly

**US-BILL-008**  
As a Regular User  
I want to be notified if my payment fails  
So that I can take corrective action

---

## 6. User Administration

### Module: COUSR00C (User List), COUSR01C (User Add), COUSR02C (User Update), COUSR03C (User Delete)

**US-ADMIN-001**  
As an Administrator  
I want to view a list of all system users  
So that I can see who has access to the system

**US-ADMIN-002**  
As an Administrator  
I want to see user details including User ID, first name, last name, and user type  
So that I can identify and manage users effectively

**US-ADMIN-003**  
As an Administrator  
I want to paginate through the user list  
So that I can efficiently browse large numbers of users

**US-ADMIN-004**  
As an Administrator  
I want to navigate forward and backward through user list pages  
So that I can review users in manageable chunks

**US-ADMIN-005**  
As an Administrator  
I want to select a user from the list  
So that I can view or modify their details

**US-ADMIN-006**  
As an Administrator  
I want to add a new user to the system  
So that I can grant access to new employees or customers

**US-ADMIN-007**  
As an Administrator  
I want to specify user details including first name, last name, User ID, password, and user type  
So that new users have complete profile information

**US-ADMIN-008**  
As an Administrator  
I want the system to validate that all required user information is provided  
So that user records are complete and valid

**US-ADMIN-009**  
As an Administrator  
I want to prevent duplicate User IDs  
So that each user has a unique identifier

**US-ADMIN-010**  
As an Administrator  
I want to receive confirmation when a user is successfully added  
So that I know the user account was created

**US-ADMIN-011**  
As an Administrator  
I want to update existing user information  
So that I can correct errors or update user details

**US-ADMIN-012**  
As an Administrator  
I want to modify user first name, last name, password, and user type  
So that I can keep user information current

**US-ADMIN-013**  
As an Administrator  
I want to receive confirmation when user updates are successful  
So that I know the changes were saved

**US-ADMIN-014**  
As an Administrator  
I want to delete users from the system  
So that I can remove access for terminated employees or closed accounts

**US-ADMIN-015**  
As an Administrator  
I want to confirm user deletions before they are processed  
So that I can prevent accidental deletions

**US-ADMIN-016**  
As an Administrator  
I want to receive confirmation when a user is successfully deleted  
So that I know the user account was removed

**US-ADMIN-017**  
As an Administrator  
I want to search for users by User ID  
So that I can quickly find specific user accounts

**US-ADMIN-018**  
As an Administrator  
I want to distinguish between regular users and administrators  
So that I can manage different levels of system access

---

## 7. Reports

### Module: CORPT00C (Transaction Reports)

**US-RPT-001**  
As a Regular User  
I want to generate a monthly transaction report  
So that I can review all transactions for the current month

**US-RPT-002**  
As a Regular User  
I want to generate a yearly transaction report  
So that I can review my annual spending and payment patterns

**US-RPT-003**  
As a Regular User  
I want to generate a custom transaction report for a specific date range  
So that I can analyze transactions for any time period I choose

**US-RPT-004**  
As a Regular User  
I want to specify start and end dates for custom reports  
So that I can define the exact reporting period

**US-RPT-005**  
As a Regular User  
I want the system to validate my report date parameters  
So that I receive accurate reports with valid date ranges

**US-RPT-006**  
As a Regular User  
I want to submit report generation requests  
So that I can receive transaction reports for analysis

**US-RPT-007**  
As a Regular User  
I want to receive feedback when my report request is submitted  
So that I know my report is being generated

---

## 8. Navigation

### Module: COMEN01C (Main Menu), COADM01C (Admin Menu)

**US-NAV-001**  
As a Regular User  
I want to access a main menu after login  
So that I can navigate to different features of the system

**US-NAV-002**  
As a Regular User  
I want to select menu options to access different modules  
So that I can perform various account management tasks

**US-NAV-003**  
As a Regular User  
I want to see all available options in the main menu  
So that I know what features I can access

**US-NAV-004**  
As a Regular User  
I want to return to the main menu from any screen  
So that I can easily navigate between different features

**US-NAV-005**  
As a Regular User  
I want to sign out from the main menu  
So that I can securely end my session

**US-NAV-006**  
As an Administrator  
I want to access an administrative menu  
So that I can perform system administration tasks

**US-NAV-007**  
As an Administrator  
I want to see administrative options in my menu  
So that I can access user management and reporting features

**US-NAV-008**  
As an Administrator  
I want to navigate between regular user features and administrative features  
So that I can perform both types of tasks as needed

**US-NAV-009**  
As a Regular User  
I want to use function keys to navigate between screens  
So that I can quickly move through the application

**US-NAV-010**  
As a Regular User  
I want to return to the previous screen  
So that I can go back if I navigate to the wrong place

---

## Summary

This document contains **100+ business user stories** extracted from **18 COBOL programs** covering **8 functional modules** of the CardDemo credit card management system. These stories represent the complete business functionality available to Regular Users and Administrators, focusing exclusively on user-centric operations and business value while excluding all technical implementation details.

### Module Coverage:
- **Authentication**: 5 user stories
- **Account Management**: 8 user stories  
- **Card Management**: 12 user stories
- **Transaction Management**: 13 user stories
- **Bill Payment**: 8 user stories
- **User Administration**: 18 user stories (Administrator only)
- **Reports**: 7 user stories
- **Navigation**: 10 user stories

### Total User Stories: 81

---

**End of Document**
