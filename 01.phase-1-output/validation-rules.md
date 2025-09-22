# COBOL Business Validation Rules

This document contains all business-level validation rules extracted from the CardDemo COBOL codebase. Each rule represents a business constraint that must be enforced during data input and processing.

## Authentication & Security Validations

### RULE-VAL-001: User ID Required
**Description:** User ID field cannot be empty or contain only spaces/low-values
**COBOL Source:** COSGN00C.cbl, lines 118-122, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** USERIDI
**Validation Condition:** USERIDI OF COSGN0AI = SPACES OR LOW-VALUES
**Trigger Conditions:** When ENTER key is pressed on signon screen

### RULE-VAL-002: Password Required
**Description:** Password field cannot be empty or contain only spaces/low-values
**COBOL Source:** COSGN00C.cbl, lines 123-127, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** PASSWDI
**Validation Condition:** PASSWDI OF COSGN0AI = SPACES OR LOW-VALUES
**Trigger Conditions:** When ENTER key is pressed on signon screen

### RULE-VAL-003: Password Authentication
**Description:** Password must match the stored password for the user
**COBOL Source:** COSGN00C.cbl, lines 223-246, READ-USER-SEC-FILE paragraph
**Field(s) Involved:** SEC-USR-PWD, WS-USER-PWD
**Validation Condition:** SEC-USR-PWD = WS-USER-PWD
**Trigger Conditions:** After successful user lookup during authentication

## Account Management Validations

### RULE-VAL-004: Account ID Required
**Description:** Account ID field cannot be empty or contain only spaces/low-values
**COBOL Source:** COBIL00C.cbl, lines 159-164, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** ACTIDINI
**Validation Condition:** ACTIDINI OF COBIL0AI = SPACES OR LOW-VALUES
**Trigger Conditions:** When processing bill payment request

### RULE-VAL-005: Account Status Valid Values
**Description:** Account status must be 'Y' (active) or 'N' (inactive)
**COBOL Source:** COACTUPC.cbl, lines 192-195, WS-NON-KEY-FLAGS section
**Field(s) Involved:** WS-EDIT-ACCT-STATUS
**Validation Condition:** VALUES 'Y', 'N'
**Trigger Conditions:** During account update operations

### RULE-VAL-006: Account Balance Non-Negative for Payment
**Description:** Account must have a positive balance to make a payment
**COBOL Source:** COBIL00C.cbl, lines 198-205, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** ACCT-CURR-BAL
**Validation Condition:** ACCT-CURR-BAL <= ZEROS
**Trigger Conditions:** When processing bill payment

### RULE-VAL-007: Bill Payment Confirmation Required
**Description:** Bill payment confirmation must be 'Y' or 'N'
**COBOL Source:** COBIL00C.cbl, lines 173-190, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** CONFIRMI
**Validation Condition:** Valid values are 'Y', 'y', 'N', 'n', SPACES, LOW-VALUES
**Trigger Conditions:** When confirming bill payment

### RULE-VAL-008: SSN Part 1 Invalid Values
**Description:** First part of SSN cannot be 0, 666, or 900-999
**COBOL Source:** COACTUPC.cbl, lines 121-123, WS-EDIT-US-SSN section
**Field(s) Involved:** WS-EDIT-US-SSN-PART1-N
**Validation Condition:** VALUES 0, 666, 900 THRU 999
**Trigger Conditions:** During account update with SSN validation

### RULE-VAL-009: Phone Number Format Validation
**Description:** US phone number must follow (XXX)XXX-XXXX format with numeric parts
**COBOL Source:** COACTUPC.cbl, lines 82-116, WS-EDIT-US-PHONE-NUM section
**Field(s) Involved:** WS-EDIT-US-PHONE-NUMA-N, WS-EDIT-US-PHONE-NUMB-N, WS-EDIT-US-PHONE-NUMC-N
**Validation Condition:** Each part must be numeric (PIC 9(3), PIC 9(3), PIC 9(4))
**Trigger Conditions:** During account update with phone number entry

### RULE-VAL-010: FICO Score Range Validation
**Description:** FICO score must be within valid range (typically 300-850)
**COBOL Source:** COACTUPC.cbl, lines 231-234, WS-NON-KEY-FLAGS section
**Field(s) Involved:** WS-EDIT-FICO-SCORE-FLGS
**Validation Condition:** Must be valid numeric value within acceptable range
**Trigger Conditions:** During account update with FICO score entry

## Card Management Validations

### RULE-VAL-011: Card Status Valid Values
**Description:** Card active status must be 'Y' (active) or 'N' (inactive)
**COBOL Source:** COCRDUPC.cbl, lines 89-91, FLG-YES-NO-CHECK section
**Field(s) Involved:** FLG-YES-NO-CHECK
**Validation Condition:** VALUES 'Y', 'N'
**Trigger Conditions:** During card update operations

### RULE-VAL-012: Card Expiry Month Range
**Description:** Card expiry month must be between 1 and 12
**COBOL Source:** COCRDUPC.cbl, lines 92-95, CARD-MONTH-CHECK section
**Field(s) Involved:** CARD-MONTH-CHECK-N
**Validation Condition:** VALUES 1 THRU 12
**Trigger Conditions:** During card update with expiry date entry

### RULE-VAL-013: Card Expiry Year Range
**Description:** Card expiry year must be between 1950 and 2099
**COBOL Source:** COCRDUPC.cbl, lines 96-99, CARD-YEAR-CHECK section
**Field(s) Involved:** CARD-YEAR-CHECK-N
**Validation Condition:** VALUES 1950 THRU 2099
**Trigger Conditions:** During card update with expiry date entry

### RULE-VAL-014: Account Number Required for Card
**Description:** Account number must be provided for card operations
**COBOL Source:** COCRDUPC.cbl, lines 177-178, WS-PROMPT-FOR-ACCT message
**Field(s) Involved:** Account number field
**Validation Condition:** Account number not provided
**Trigger Conditions:** When accessing card functions without account context

### RULE-VAL-015: Card Number Required
**Description:** Card number must be provided for card operations
**COBOL Source:** COCRDUPC.cbl, lines 179-180, WS-PROMPT-FOR-CARD message
**Field(s) Involved:** Card number field
**Validation Condition:** Card number not provided
**Trigger Conditions:** When accessing card functions without card context

### RULE-VAL-016: Card Name Required
**Description:** Card name must be provided and cannot be empty
**COBOL Source:** COCRDUPC.cbl, lines 181-182, WS-PROMPT-FOR-NAME message
**Field(s) Involved:** Card name field
**Validation Condition:** Card name not provided
**Trigger Conditions:** During card creation or update

### RULE-VAL-017: Card Name Alphabetic Only
**Description:** Card name can only contain alphabets and spaces
**COBOL Source:** COCRDUPC.cbl, lines 183-184, WS-NAME-MUST-BE-ALPHA message
**Field(s) Involved:** Card name field
**Validation Condition:** Must contain only alphabetic characters and spaces
**Trigger Conditions:** During card name validation

### RULE-VAL-018: Account Number Numeric and Non-Zero
**Description:** Account number must be a non-zero 11-digit number
**COBOL Source:** COCRDUPC.cbl, lines 189-192, SEARCHED-ACCT messages
**Field(s) Involved:** Account number field
**Validation Condition:** Must be numeric and non-zero, 11 digits
**Trigger Conditions:** During account number validation

### RULE-VAL-019: Card Number Numeric 16-Digit
**Description:** Card number must be a 16-digit numeric value
**COBOL Source:** COCRDUPC.cbl, lines 193-194, SEARCHED-CARD-NOT-NUMERIC message
**Field(s) Involved:** Card number field
**Validation Condition:** Must be numeric, 16 digits
**Trigger Conditions:** During card number validation

## Transaction Processing Validations

### RULE-VAL-020: Transaction ID Required
**Description:** Transaction ID cannot be empty or contain only spaces/low-values
**COBOL Source:** COTRN01C.cbl, lines 147-151, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** TRNIDINI
**Validation Condition:** TRNIDINI OF COTRN1AI = SPACES OR LOW-VALUES
**Trigger Conditions:** When viewing transaction details

### RULE-VAL-021: Account ID Numeric for Transaction
**Description:** Account ID must be numeric for transaction processing
**COBOL Source:** COTRN02C.cbl, lines 197-202, VALIDATE-INPUT-KEY-FIELDS paragraph
**Field(s) Involved:** ACTIDINI
**Validation Condition:** ACTIDINI OF COTRN2AI IS NOT NUMERIC
**Trigger Conditions:** During transaction creation with account ID

### RULE-VAL-022: Card Number Numeric for Transaction
**Description:** Card number must be numeric for transaction processing
**COBOL Source:** COTRN02C.cbl, lines 211-216, VALIDATE-INPUT-KEY-FIELDS paragraph
**Field(s) Involved:** CARDNINI
**Validation Condition:** CARDNINI OF COTRN2AI IS NOT NUMERIC
**Trigger Conditions:** During transaction creation with card number

### RULE-VAL-023: Transaction Type Code Required
**Description:** Transaction type code cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 252-257, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TTYPCDI
**Validation Condition:** TTYPCDI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-024: Transaction Category Code Required
**Description:** Transaction category code cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 258-263, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TCATCDI
**Validation Condition:** TCATCDI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-025: Transaction Source Required
**Description:** Transaction source cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 264-269, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TRNSRCI
**Validation Condition:** TRNSRCI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-026: Transaction Description Required
**Description:** Transaction description cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 270-275, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TDESCI
**Validation Condition:** TDESCI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-027: Transaction Amount Required
**Description:** Transaction amount cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 276-281, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TRNAMTI
**Validation Condition:** TRNAMTI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-028: Transaction Original Date Required
**Description:** Transaction original date cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 282-287, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TORIGDTI
**Validation Condition:** TORIGDTI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-029: Transaction Process Date Required
**Description:** Transaction process date cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 288-293, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TPROCDTI
**Validation Condition:** TPROCDTI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-030: Merchant ID Required
**Description:** Merchant ID cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 294-299, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** MIDI
**Validation Condition:** MIDI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-031: Merchant Name Required
**Description:** Merchant name cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 300-305, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** MNAMEI
**Validation Condition:** MNAMEI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-032: Merchant City Required
**Description:** Merchant city cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 306-311, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** MCITYI
**Validation Condition:** MCITYI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-033: Merchant ZIP Required
**Description:** Merchant ZIP code cannot be empty
**COBOL Source:** COTRN02C.cbl, lines 312-317, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** MZIPI
**Validation Condition:** MZIPI OF COTRN2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During transaction creation

### RULE-VAL-034: Transaction Type Code Numeric
**Description:** Transaction type code must be numeric
**COBOL Source:** COTRN02C.cbl, lines 323-328, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TTYPCDI
**Validation Condition:** TTYPCDI OF COTRN2AI NOT NUMERIC
**Trigger Conditions:** During transaction creation

### RULE-VAL-035: Transaction Category Code Numeric
**Description:** Transaction category code must be numeric
**COBOL Source:** COTRN02C.cbl, lines 329-334, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TCATCDI
**Validation Condition:** TCATCDI OF COTRN2AI NOT NUMERIC
**Trigger Conditions:** During transaction creation

### RULE-VAL-036: Transaction Amount Format
**Description:** Transaction amount must be in format -99999999.99
**COBOL Source:** COTRN02C.cbl, lines 340-348, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TRNAMTI
**Validation Condition:** Must have sign, 8 digits, decimal point, 2 decimal places
**Trigger Conditions:** During transaction creation

### RULE-VAL-037: Transaction Original Date Format
**Description:** Transaction original date must be in format YYYY-MM-DD
**COBOL Source:** COTRN02C.cbl, lines 354-363, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TORIGDTI
**Validation Condition:** Must follow YYYY-MM-DD format with numeric parts
**Trigger Conditions:** During transaction creation

### RULE-VAL-038: Transaction Process Date Format
**Description:** Transaction process date must be in format YYYY-MM-DD
**COBOL Source:** COTRN02C.cbl, lines 368-373, VALIDATE-INPUT-DATA-FIELDS paragraph
**Field(s) Involved:** TPROCDTI
**Validation Condition:** Must follow YYYY-MM-DD format with numeric parts
**Trigger Conditions:** During transaction creation

### RULE-VAL-039: Transaction Confirmation Required
**Description:** Transaction confirmation must be 'Y' or 'N'
**COBOL Source:** COTRN02C.cbl, lines 169-187, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** CONFIRMI
**Validation Condition:** Valid values are 'Y', 'y', 'N', 'n', SPACES, LOW-VALUES
**Trigger Conditions:** When confirming transaction creation

## User Management Validations

### RULE-VAL-040: First Name Required
**Description:** First name cannot be empty or contain only spaces/low-values
**COBOL Source:** COUSR01C.cbl, lines 118-123, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** FNAMEI
**Validation Condition:** FNAMEI OF COUSR1AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user creation

### RULE-VAL-041: Last Name Required
**Description:** Last name cannot be empty or contain only spaces/low-values
**COBOL Source:** COUSR01C.cbl, lines 124-129, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** LNAMEI
**Validation Condition:** LNAMEI OF COUSR1AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user creation

### RULE-VAL-042: User ID Required for Creation
**Description:** User ID cannot be empty or contain only spaces/low-values
**COBOL Source:** COUSR01C.cbl, lines 130-135, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** USERIDI
**Validation Condition:** USERIDI OF COUSR1AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user creation

### RULE-VAL-043: Password Required for Creation
**Description:** Password cannot be empty or contain only spaces/low-values
**COBOL Source:** COUSR01C.cbl, lines 136-141, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** PASSWDI
**Validation Condition:** PASSWDI OF COUSR1AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user creation

### RULE-VAL-044: User Type Required
**Description:** User type cannot be empty or contain only spaces/low-values
**COBOL Source:** COUSR01C.cbl, lines 142-147, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** USRTYPEI
**Validation Condition:** USRTYPEI OF COUSR1AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user creation

### RULE-VAL-045: User ID Required for Update
**Description:** User ID cannot be empty for user update operations
**COBOL Source:** COUSR02C.cbl, lines 146-151, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** USRIDINI
**Validation Condition:** USRIDINI OF COUSR2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user update

### RULE-VAL-046: First Name Required for Update
**Description:** First name cannot be empty during user update
**COBOL Source:** COUSR02C.cbl, lines 186-191, UPDATE-USER-INFO paragraph
**Field(s) Involved:** FNAMEI
**Validation Condition:** FNAMEI OF COUSR2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user update

### RULE-VAL-047: Last Name Required for Update
**Description:** Last name cannot be empty during user update
**COBOL Source:** COUSR02C.cbl, lines 192-197, UPDATE-USER-INFO paragraph
**Field(s) Involved:** LNAMEI
**Validation Condition:** LNAMEI OF COUSR2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user update

### RULE-VAL-048: Password Required for Update
**Description:** Password cannot be empty during user update
**COBOL Source:** COUSR02C.cbl, lines 198-203, UPDATE-USER-INFO paragraph
**Field(s) Involved:** PASSWDI
**Validation Condition:** PASSWDI OF COUSR2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user update

### RULE-VAL-049: User Type Required for Update
**Description:** User type cannot be empty during user update
**COBOL Source:** COUSR02C.cbl, lines 204-209, UPDATE-USER-INFO paragraph
**Field(s) Involved:** USRTYPEI
**Validation Condition:** USRTYPEI OF COUSR2AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user update

## Date Validation Utilities

### RULE-VAL-050: Date Format Validation
**Description:** Dates must be validated using CEEDAYS API for proper format and validity
**COBOL Source:** CSUTLDTC.cbl, lines 116-149, A000-MAIN paragraph
**Field(s) Involved:** Date fields in YYYY-MM-DD format
**Validation Condition:** Various date validation conditions using CEEDAYS API
**Trigger Conditions:** When validating any date field across the application

### RULE-VAL-051: Month Range Validation
**Description:** Month must be between 1 and 12
**COBOL Source:** CSUTLDWY.cpy, lines 19-20, WS-VALID-MONTH condition
**Field(s) Involved:** WS-EDIT-DATE-MM-N
**Validation Condition:** VALUES 1 THROUGH 12
**Trigger Conditions:** During date validation processing

### RULE-VAL-052: Day Range Validation
**Description:** Day must be between 1 and 31
**COBOL Source:** CSUTLDWY.cpy, lines 28-29, WS-VALID-DAY condition
**Field(s) Involved:** WS-EDIT-DATE-DD-N
**Validation Condition:** VALUES 1 THROUGH 31
**Trigger Conditions:** During date validation processing

### RULE-VAL-053: February Day Validation
**Description:** February days must be between 1 and 28 (non-leap year)
**COBOL Source:** CSUTLDWY.cpy, lines 33-34, WS-VALID-FEB-DAY condition
**Field(s) Involved:** WS-EDIT-DATE-DD-N
**Validation Condition:** VALUES 1 THROUGH 28
**Trigger Conditions:** During February date validation

## Menu & Navigation Validations

### RULE-VAL-054: Admin Menu Option Numeric Validation
**Description:** Admin menu option must be numeric and within valid range
**COBOL Source:** COADM01C.cbl, lines 127-134, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** WS-OPTION
**Validation Condition:** WS-OPTION IS NOT NUMERIC OR WS-OPTION > CDEMO-ADMIN-OPT-COUNT OR WS-OPTION = ZEROS
**Trigger Conditions:** When processing admin menu option selection

### RULE-VAL-055: User Menu Option Numeric Validation
**Description:** User menu option must be numeric and within valid range
**COBOL Source:** COMEN01C.cbl, lines 127-134, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** WS-OPTION
**Validation Condition:** WS-OPTION IS NOT NUMERIC OR WS-OPTION > CDEMO-MENU-OPT-COUNT OR WS-OPTION = ZEROS
**Trigger Conditions:** When processing user menu option selection

### RULE-VAL-056: Admin Access Control Validation
**Description:** Regular users cannot access admin-only menu options
**COBOL Source:** COMEN01C.cbl, lines 136-143, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** CDEMO-USRTYP-USER, CDEMO-MENU-OPT-USRTYPE
**Validation Condition:** CDEMO-USRTYP-USER AND CDEMO-MENU-OPT-USRTYPE(WS-OPTION) = 'A'
**Trigger Conditions:** When regular user attempts to access admin option

## Reporting Validations

### RULE-VAL-057: Report Date Fields Required
**Description:** Custom report date fields cannot be empty
**COBOL Source:** CORPT00C.cbl, lines 259-300, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** SDTMMI, SDTDDI, SDTYYYYI, EDTMMI, EDTDDI, EDTYYYYI
**Validation Condition:** Date fields = SPACES OR LOW-VALUES
**Trigger Conditions:** When generating custom date range reports

### RULE-VAL-058: Report Month Range Validation
**Description:** Report month must be between 1 and 12
**COBOL Source:** CORPT00C.cbl, lines 329-336, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** SDTMMI, EDTMMI
**Validation Condition:** Month IS NOT NUMERIC OR Month > '12'
**Trigger Conditions:** During custom report date validation

### RULE-VAL-059: Report Day Range Validation
**Description:** Report day must be between 1 and 31
**COBOL Source:** CORPT00C.cbl, lines 338-345, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** SDTDDI, EDTDDI
**Validation Condition:** Day IS NOT NUMERIC OR Day > '31'
**Trigger Conditions:** During custom report date validation

### RULE-VAL-060: Report Year Numeric Validation
**Description:** Report year must be numeric
**COBOL Source:** CORPT00C.cbl, lines 347-353, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** SDTYYYYI, EDTYYYYI
**Validation Condition:** Year IS NOT NUMERIC
**Trigger Conditions:** During custom report date validation

## Additional Transaction Processing Validations

### RULE-VAL-061: Transaction ID Numeric for Listing
**Description:** Transaction ID must be numeric for transaction listing
**COBOL Source:** COTRN00C.cbl, lines 209-218, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** TRNIDINI
**Validation Condition:** TRNIDINI OF COTRN0AI IS NOT NUMERIC
**Trigger Conditions:** When filtering transaction list by transaction ID

### RULE-VAL-062: Transaction Selection Valid Values
**Description:** Transaction selection must be 'S' or 's' for view
**COBOL Source:** COTRN00C.cbl, lines 185-203, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** CDEMO-CT00-TRN-SEL-FLG
**Validation Condition:** Valid values are 'S', 's'
**Trigger Conditions:** When selecting transaction from list for viewing

## Additional Card Management Validations

### RULE-VAL-063: Account Number Numeric for Card Detail
**Description:** Account number must be numeric for card detail view
**COBOL Source:** COCRDSLC.cbl, lines 145-147, validation messages
**Field(s) Involved:** Account number field
**Validation Condition:** Must be non-zero 11-digit number
**Trigger Conditions:** When viewing card details

### RULE-VAL-064: Card Number Numeric for Card Detail
**Description:** Card number must be 16-digit numeric for card detail view
**COBOL Source:** COCRDSLC.cbl, lines 148-149, validation messages
**Field(s) Involved:** Card number field
**Validation Condition:** Must be 16-digit number
**Trigger Conditions:** When viewing card details

## Additional User Management Validations

### RULE-VAL-065: User ID Required for Deletion
**Description:** User ID cannot be empty for user deletion operations
**COBOL Source:** COUSR03C.cbl, lines 145-150, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** USRIDINI
**Validation Condition:** USRIDINI OF COUSR3AI = SPACES OR LOW-VALUES
**Trigger Conditions:** During user deletion process

### RULE-VAL-066: User Selection Valid Values for List
**Description:** User selection must be 'U' for update or 'D' for delete
**COBOL Source:** COUSR00C.cbl, lines 189-215, PROCESS-ENTER-KEY paragraph
**Field(s) Involved:** CDEMO-CU00-USR-SEL-FLG
**Validation Condition:** Valid values are 'U', 'u', 'D', 'd'
**Trigger Conditions:** When selecting user from list for operations

## Summary

Total validation rules extracted: 66
- Authentication & Security: 3 rules
- Account Management: 7 rules  
- Card Management: 12 rules
- Transaction Processing: 22 rules
- User Management: 12 rules
- Date Validation Utilities: 4 rules
- Menu & Navigation: 3 rules
- Reporting: 4 rules
- System Access Control: 1 rule

All validation rules focus on business logic and exclude calculation logic, technical validations, and BMS layout constraints as specified in the requirements.
