# CardDemo COBOL Application Screen Flow Analysis

## Executive Summary

The CardDemo application implements a hierarchical menu-driven navigation system with role-based access control. The application starts with a centralized sign-on screen (COSGN00C) that routes users to either an Admin Menu (COADM01C) or Main Menu (COMEN01C) based on their user type. The system follows standard CICS navigation patterns using EXEC CICS XCTL commands for screen transitions and maintains session context through COMMAREA data structures.

## Authentication and Entry Point

| Screen ID/Title | Trigger/Option Value | Navigates To → [Target Screen ID] |
|----------------|---------------------|-----------------------------------|
| COSGN00C - Sign-on Screen | Valid Admin Credentials | → COADM01C (Admin Menu) |
| COSGN00C - Sign-on Screen | Valid User Credentials | → COMEN01C (Main Menu) |
| COSGN00C - Sign-on Screen | PF3 | → Exit Application |
| COSGN00C - Sign-on Screen | Invalid Credentials | → COSGN00C (Error Message) |

## Admin Menu Navigation (COADM01C)

| Screen ID/Title | Trigger/Option Value | Navigates To → [Target Screen ID] |
|----------------|---------------------|-----------------------------------|
| COADM01C - Admin Menu | Option 1 | → COUSR00C (User List) |
| COADM01C - Admin Menu | Option 2 | → COUSR01C (User Add) |
| COADM01C - Admin Menu | Option 3 | → COUSR02C (User Update) |
| COADM01C - Admin Menu | Option 4 | → COUSR03C (User Delete) |
| COADM01C - Admin Menu | PF3 | → COSGN00C (Sign-on Screen) |
| COADM01C - Admin Menu | Invalid Option | → COADM01C (Error Message) |

## Main Menu Navigation (COMEN01C)

| Screen ID/Title | Trigger/Option Value | Navigates To → [Target Screen ID] |
|----------------|---------------------|-----------------------------------|
| COMEN01C - Main Menu | Option 1 | → COACTVWC (Account View) |
| COMEN01C - Main Menu | Option 2 | → COACTUPC (Account Update) |
| COMEN01C - Main Menu | Option 3 | → COCRDLIC (Credit Card List) |
| COMEN01C - Main Menu | Option 4 | → COCRDSLC (Credit Card View) |
| COMEN01C - Main Menu | Option 5 | → COCRDUPC (Credit Card Update) |
| COMEN01C - Main Menu | Option 6 | → COTRN00C (Transaction List) |
| COMEN01C - Main Menu | Option 7 | → COTRN01C (Transaction View) |
| COMEN01C - Main Menu | Option 8 | → COTRN02C (Transaction Add) |
| COMEN01C - Main Menu | Option 9 | → CORPT00C (Transaction Reports) |
| COMEN01C - Main Menu | Option 10 | → COBIL00C (Bill Payment) |
| COMEN01C - Main Menu | PF3 | → COSGN00C (Sign-on Screen) |
| COMEN01C - Main Menu | Invalid Option | → COMEN01C (Error Message) |

## Transaction Processing Flow

| Screen ID/Title | Trigger/Option Value | Navigates To → [Target Screen ID] |
|----------------|---------------------|-----------------------------------|
| COTRN00C - Transaction List | Selection 'S' + Transaction ID | → COTRN01C (Transaction View) |
| COTRN00C - Transaction List | PF3 | → COMEN01C (Main Menu) |
| COTRN00C - Transaction List | PF7 | → COTRN00C (Previous Page) |
| COTRN00C - Transaction List | PF8 | → COTRN00C (Next Page) |
| COTRN01C - Transaction View | PF3 | → Previous Screen (Context-based) |
| COTRN01C - Transaction View | PF4 | → COTRN01C (Clear Screen) |
| COTRN01C - Transaction View | PF5 | → COTRN00C (Transaction List) |
| COTRN02C - Transaction Add | Confirm 'Y' | → COTRN02C (Success Message) |
| COTRN02C - Transaction Add | PF3 | → Previous Screen (Context-based) |
| COTRN02C - Transaction Add | PF4 | → COTRN02C (Clear Screen) |
| COTRN02C - Transaction Add | PF5 | → COTRN02C (Copy Last Transaction) |

## User Management Flow (Admin Only)

| Screen ID/Title | Trigger/Option Value | Navigates To → [Target Screen ID] |
|----------------|---------------------|-----------------------------------|
| COUSR00C - User List | Selection 'U' + User ID | → COUSR02C (User Update) |
| COUSR00C - User List | Selection 'D' + User ID | → COUSR03C (User Delete) |
| COUSR00C - User List | PF3 | → COADM01C (Admin Menu) |
| COUSR00C - User List | PF7 | → COUSR00C (Previous Page) |
| COUSR00C - User List | PF8 | → COUSR00C (Next Page) |
| COUSR01C - User Add | Valid Data + ENTER | → COUSR01C (Success Message) |
| COUSR01C - User Add | PF3 | → COADM01C (Admin Menu) |
| COUSR01C - User Add | PF4 | → COUSR01C (Clear Screen) |
| COUSR02C - User Update | Valid Data + ENTER | → COUSR02C (Success Message) |
| COUSR02C - User Update | PF3 | → COUSR00C (User List) |
| COUSR03C - User Delete | Confirm 'Y' | → COUSR03C (Success Message) |
| COUSR03C - User Delete | PF3 | → COUSR00C (User List) |

## Bill Payment Flow

| Screen ID/Title | Trigger/Option Value | Navigates To → [Target Screen ID] |
|----------------|---------------------|-----------------------------------|
| COBIL00C - Bill Payment | Account ID + Confirm 'Y' | → COBIL00C (Payment Processed) |
| COBIL00C - Bill Payment | PF3 | → Previous Screen (Context-based) |
| COBIL00C - Bill Payment | PF4 | → COBIL00C (Clear Screen) |

## Standard PF Key Navigation Patterns

| PF Key | Function | Behavior |
|--------|----------|----------|
| PF3 | Exit/Return | Returns to previous screen or main menu |
| PF4 | Clear | Clears current screen fields |
| PF5 | Special Function | Context-specific (Copy, List, etc.) |
| PF7 | Page Backward | Previous page in list screens |
| PF8 | Page Forward | Next page in list screens |
| ENTER | Process/Continue | Submits data or continues to next step |

## CICS Transaction IDs and Program Mappings

| Transaction ID | Program Name | Screen Function | BMS Map |
|---------------|--------------|-----------------|---------|
| CC00 | COSGN00C | Sign-on Screen | COSGN0A |
| CA00 | COADM01C | Admin Menu | COADM1A |
| CM00 | COMEN01C | Main Menu | COMEN1A |
| CT00 | COTRN00C | Transaction List | COTRN0A |
| CT01 | COTRN01C | Transaction View | COTRN1A |
| CT02 | COTRN02C | Transaction Add | COTRN2A |
| CU00 | COUSR00C | User List | COUSR0A |
| CU01 | COUSR01C | User Add | COUSR1A |
| CU02 | COUSR02C | User Update | COUSR2A |
| CU03 | COUSR03C | User Delete | COUSR3A |
| CB00 | COBIL00C | Bill Payment | COBIL0A |

## Menu Option Definitions

### Main Menu Options (COMEN02Y)
1. **Account View** (COACTVWC) - User access
2. **Account Update** (COACTUPC) - User access  
3. **Credit Card List** (COCRDLIC) - User access
4. **Credit Card View** (COCRDSLC) - User access
5. **Credit Card Update** (COCRDUPC) - User access
6. **Transaction List** (COTRN00C) - User access
7. **Transaction View** (COTRN01C) - User access
8. **Transaction Add** (COTRN02C) - User access
9. **Transaction Reports** (CORPT00C) - User access
10. **Bill Payment** (COBIL00C) - User access

### Admin Menu Options (COADM02Y)
1. **User List (Security)** (COUSR00C) - Admin only
2. **User Add (Security)** (COUSR01C) - Admin only
3. **User Update (Security)** (COUSR02C) - Admin only
4. **User Delete (Security)** (COUSR03C) - Admin only

## Screen Selection and Input Patterns

| Pattern | Usage | Example |
|---------|-------|---------|
| Numeric Options | Menu selection | 1-10 for main menu, 1-4 for admin menu |
| Selection Flags | List item actions | 'S' for Select, 'U' for Update, 'D' for Delete |
| Confirmation | Destructive actions | 'Y' for Yes, 'N' for No |
| Search Criteria | Filtering lists | Transaction ID, User ID, Account ID |
| Pagination | Large datasets | PF7/PF8 for backward/forward navigation |

## Error Handling and Validation Flows

| Error Condition | Screen Response | Navigation |
|----------------|-----------------|------------|
| Invalid Credentials | Error message on COSGN00C | Remain on sign-on |
| Invalid Menu Option | Error message on menu screen | Remain on current menu |
| Missing Required Fields | Field-specific error message | Remain on current screen |
| Record Not Found | "Not found" error message | Remain on current screen |
| Duplicate Key | "Already exists" error message | Remain on current screen |
| Access Denied | "No access" error message | Remain on current screen |

## Session Context Management

The application uses CARDDEMO-COMMAREA structure to maintain session context across screen transitions:
- **CDEMO-USER-ID**: Current user identifier
- **CDEMO-USER-TYPE**: User role (Admin/Regular)
- **CDEMO-FROM-PROGRAM**: Previous program for return navigation
- **CDEMO-TO-PROGRAM**: Target program for forward navigation
- **CDEMO-PGM-CONTEXT**: Program-specific context flags
- **CDEMO-PGM-REENTER**: Re-entry control flag

## Navigation Architecture Summary

The CardDemo application implements a structured navigation hierarchy:

1. **Entry Point**: Single sign-on screen with role-based routing
2. **Menu Structure**: Separate admin and user menus with numbered options
3. **Functional Areas**: Account management, card management, transactions, user administration
4. **Standard Patterns**: Consistent PF key usage, error handling, and return navigation
5. **Session Management**: Context preservation across screen transitions using COMMAREA
6. **Access Control**: Role-based menu options and screen access restrictions

This architecture provides a user-friendly, maintainable navigation system typical of enterprise CICS applications while ensuring proper security and data integrity controls.
