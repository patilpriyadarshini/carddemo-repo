# Business Calculation Rules - CardDemo COBOL Analysis

## Overview
This document contains business-level calculation rules extracted from the CardDemo COBOL codebase. Only business-relevant calculations are included (loan/premium calculations, tax/interest formulas, conditional business logic, aggregation/financial rules). Technical operations like file handling, validation, screen layout, and infrastructure logic are excluded.

## Business Calculation Rules

### RULE-CALC-001: Bill Payment Balance Calculation
- **Rule ID**: RULE-CALC-001
- **Rule Description**: Updates account current balance by subtracting the transaction amount when processing bill payments
- **COBOL Source Location**: COBIL00C.cbl, line 234
- **Involved Variables**: 
  - `ACCT-CURR-BAL` (Account Current Balance)
  - `TRAN-AMT` (Transaction Amount)
- **Input Conditions**: 
  - `CONF-PAY-YES` (Payment confirmation flag is set to 'Y')
  - Account balance must be greater than zero
- **Calculation Logic**: `COMPUTE ACCT-CURR-BAL = ACCT-CURR-BAL - TRAN-AMT`
- **Business Purpose**: Processes online bill payments by reducing the account balance by the payment amount

### RULE-CALC-002: Credit Limit Conversion
- **Rule ID**: RULE-CALC-002  
- **Rule Description**: Converts credit limit input from character format to numeric format for account updates
- **COBOL Source Location**: COACTUPC.cbl, lines 1079-1080
- **Involved Variables**:
  - `ACRDLIMI` (Credit Limit Input)
  - `ACUP-NEW-CREDIT-LIMIT-N` (New Credit Limit Numeric)
- **Input Conditions**: 
  - Credit limit input is not '*' or spaces
  - Input passes numeric validation test
- **Calculation Logic**: `COMPUTE ACUP-NEW-CREDIT-LIMIT-N = FUNCTION NUMVAL-C(ACRDLIMI OF CACTUPAI)`
- **Business Purpose**: Validates and converts credit limit changes for account management

### RULE-CALC-003: Cash Credit Limit Conversion  
- **Rule ID**: RULE-CALC-003
- **Rule Description**: Converts cash credit limit input from character format to numeric format
- **COBOL Source Location**: COACTUPC.cbl, lines 1093-1094
- **Involved Variables**:
  - `ACSHLIMI` (Cash Limit Input)
  - `ACUP-NEW-CASH-CREDIT-LIMIT-N` (New Cash Credit Limit Numeric)
- **Input Conditions**:
  - Cash limit input is not '*' or spaces  
  - Input passes numeric validation test
- **Calculation Logic**: `COMPUTE ACUP-NEW-CASH-CREDIT-LIMIT-N = FUNCTION NUMVAL-C(ACSHLIMI OF CACTUPAI)`
- **Business Purpose**: Manages cash advance limits for credit card accounts

### RULE-CALC-004: Current Balance Conversion
- **Rule ID**: RULE-CALC-004
- **Rule Description**: Converts current balance input from character format to numeric format
- **COBOL Source Location**: COACTUPC.cbl, lines 1107-1108  
- **Involved Variables**:
  - `ACURBALI` (Current Balance Input)
  - `ACUP-NEW-CURR-BAL-N` (New Current Balance Numeric)
- **Input Conditions**:
  - Current balance input is not '*' or spaces
  - Input passes numeric validation test  
- **Calculation Logic**: `COMPUTE ACUP-NEW-CURR-BAL-N = FUNCTION NUMVAL-C(ACUP-NEW-CURR-BAL-X)`
- **Business Purpose**: Updates account current balance during account maintenance

### RULE-CALC-005: Current Cycle Credit Conversion
- **Rule ID**: RULE-CALC-005
- **Rule Description**: Converts current cycle credit amount from character to numeric format
- **COBOL Source Location**: COACTUPC.cbl, lines 1121-1122
- **Involved Variables**:
  - `ACRCYCRI` (Current Cycle Credit Input)  
  - `ACUP-NEW-CURR-CYC-CREDIT-N` (New Current Cycle Credit Numeric)
- **Input Conditions**:
  - Cycle credit input is not '*' or spaces
  - Input passes numeric validation test
- **Calculation Logic**: `COMPUTE ACUP-NEW-CURR-CYC-CREDIT-N = FUNCTION NUMVAL-C(ACRCYCRI OF CACTUPAI)`
- **Business Purpose**: Tracks credit transactions within the current billing cycle

### RULE-CALC-006: Current Cycle Debit Conversion
- **Rule ID**: RULE-CALC-006  
- **Rule Description**: Converts current cycle debit amount from character to numeric format
- **COBOL Source Location**: COACTUPC.cbl, lines 1135-1136
- **Involved Variables**:
  - `ACRCYDBI` (Current Cycle Debit Input)
  - `ACUP-NEW-CURR-CYC-DEBIT-N` (New Current Cycle Debit Numeric)  
- **Input Conditions**:
  - Cycle debit input is not '*' or spaces
  - Input passes numeric validation test
- **Calculation Logic**: `COMPUTE ACUP-NEW-CURR-CYC-DEBIT-N = FUNCTION NUMVAL-C(ACRCYDBI OF CACTUPAI)`
- **Business Purpose**: Tracks debit transactions within the current billing cycle

### RULE-CALC-007: Report Date Range Calculation
- **Rule ID**: RULE-CALC-007
- **Rule Description**: Calculates end date for transaction reports by adding one month to start date
- **COBOL Source Location**: CORPT00C.cbl, lines 224-230
- **Involved Variables**:
  - `WS-CURDATE-MONTH` (Current Month)
  - `WS-CURDATE-YEAR` (Current Year)
  - `WS-CURDATE-N` (Date Numeric)
- **Input Conditions**: Valid start date provided for report generation
- **Calculation Logic**: 
  ```
  ADD 1 TO WS-CURDATE-MONTH
  IF WS-CURDATE-MONTH > 12
      ADD 1 TO WS-CURDATE-YEAR  
      MOVE 1 TO WS-CURDATE-MONTH
  COMPUTE WS-CURDATE-N = FUNCTION DATE-OF-INTEGER(FUNCTION INTEGER-OF-DATE(WS-CURDATE-N) - 1)
  ```
- **Business Purpose**: Defines date ranges for transaction reporting periods

### RULE-CALC-008: Transaction ID Generation
- **Rule ID**: RULE-CALC-008
- **Rule Description**: Generates sequential transaction IDs by incrementing the last transaction ID
- **COBOL Source Location**: COBIL00C.cbl, line 217
- **Involved Variables**:
  - `TRAN-ID` (Transaction ID)
  - `WS-TRAN-ID-NUM` (Working Storage Transaction ID Number)
- **Input Conditions**: Valid transaction record exists for reference
- **Calculation Logic**: `ADD 1 TO WS-TRAN-ID-NUM`
- **Business Purpose**: Ensures unique transaction identifiers for bill payment processing

### RULE-CALC-009: Transaction List Pagination
- **Rule ID**: RULE-CALC-009
- **Rule Description**: Calculates page numbers and indices for transaction list navigation
- **COBOL Source Location**: COTRN00C.cbl, lines 301, 306-307, 355, 364
- **Involved Variables**:
  - `WS-IDX` (Working Storage Index)
  - `CDEMO-CT00-PAGE-NUM` (Page Number)
- **Input Conditions**: Transaction records available for display
- **Calculation Logic**: 
  ```
  COMPUTE WS-IDX = WS-IDX + 1
  COMPUTE CDEMO-CT00-PAGE-NUM = CDEMO-CT00-PAGE-NUM + 1
  COMPUTE WS-IDX = WS-IDX - 1
  SUBTRACT 1 FROM CDEMO-CT00-PAGE-NUM
  ```
- **Business Purpose**: Manages pagination for transaction listing screens

### RULE-CALC-010: Report Date Input Conversion
- **Rule ID**: RULE-CALC-010
- **Rule Description**: Converts date input fields from character to numeric format for report processing
- **COBOL Source Location**: CORPT00C.cbl, lines 305-327
- **Involved Variables**:
  - `SDTMMI`, `SDTDDI`, `SDTYYYYI` (Start Date Month, Day, Year Input)
  - `EDTMMI`, `EDTDDI`, `EDTYYYYI` (End Date Month, Day, Year Input)
  - `WS-NUM-99`, `WS-NUM-9999` (Numeric conversion variables)
- **Input Conditions**: Valid date input provided by user
- **Calculation Logic**: 
  ```
  COMPUTE WS-NUM-99 = FUNCTION NUMVAL-C(SDTMMI OF CORPT0AI)
  COMPUTE WS-NUM-99 = FUNCTION NUMVAL-C(SDTDDI OF CORPT0AI)
  COMPUTE WS-NUM-9999 = FUNCTION NUMVAL-C(SDTYYYYI OF CORPT0AI)
  COMPUTE WS-NUM-99 = FUNCTION NUMVAL-C(EDTMMI OF CORPT0AI)
  COMPUTE WS-NUM-99 = FUNCTION NUMVAL-C(EDTDDI OF CORPT0AI)
  COMPUTE WS-NUM-9999 = FUNCTION NUMVAL-C(EDTYYYYI OF CORPT0AI)
  ```
- **Business Purpose**: Validates and converts user-entered date ranges for transaction reporting

## Rule Dependencies

The business calculation rules have the following dependencies:

- **RULE-CALC-001** (Bill Payment) operates independently but uses **RULE-CALC-008** (Transaction ID Generation) to create unique transaction records
- **RULE-CALC-002 through RULE-CALC-006** (Account Updates) work together during account maintenance operations
- **RULE-CALC-007** (Report Date Range) works with **RULE-CALC-010** (Date Input Conversion) for report generation
- **RULE-CALC-009** (Pagination) operates independently for transaction list navigation

## Summary

- **Total Business Calculation Rules**: 10
- **Primary Business Domain**: Credit card account management and bill payment processing  
- **Key Financial Operations**: Balance updates, credit limit management, billing cycle tracking, transaction processing
- **Notable Absence**: No interest rate calculations, fees, penalties, or complex financial formulas found

## Source Analysis Coverage

All 18 COBOL programs in the 00.phase-1-input/cbl/ folder were systematically analyzed:
- COBIL00C.cbl ✓ (Bill Payment - 2 rules)
- COACTUPC.cbl ✓ (Account Update - 5 rules)  
- CORPT00C.cbl ✓ (Report Generation - 2 rules)
- COTRN00C.cbl ✓ (Transaction List - 1 rule)
- COTRN01C.cbl ✓ (Transaction View - no calculations)
- COTRN02C.cbl ✓ (Transaction Add - no calculations)
- COUSR00C.cbl ✓ (User List - no calculations)
- COUSR01C.cbl ✓ (User Add - no calculations)  
- COUSR02C.cbl ✓ (User Update - no calculations)
- COUSR03C.cbl ✓ (User Delete - no calculations)
- COMEN01C.cbl ✓ (Menu - no calculations)
- COCRDLIC.cbl ✓ (Card List - no calculations)
- COCRDSLC.cbl ✓ (Card Select - no calculations)
- COCRDUPC.cbl ✓ (Card Update - no calculations)
- COACTVWC.cbl ✓ (Account View - no calculations)
- COADM01C.cbl ✓ (Admin Menu - no calculations)
- COSGN00C.cbl ✓ (Sign-on - no calculations)
- CSUTLDTC.cbl ✓ (Date Utility - technical only)
