# Business Calculation Rules Extraction

This folder contains the extracted business calculation rules from the COBOL codebase in the 00.phase-1-input folder.

## Contents

- `business-calculation-rules.md` - Comprehensive documentation of all business calculation rules
- `business-rules-dependencies.svg` - Visual diagram showing calculation rule relationships and dependencies
- `README.md` - This documentation file

## Extraction Criteria

Only business-level calculation rules were extracted, including:
- Financial calculations (balance updates, credit limits)
- Business logic computations (billing cycles, payment processing)
- Domain-specific calculations (account management, reporting)
- Conditional business calculations (account updates with validation)

Excluded from extraction:
- Input validation rules (field checks, format validation)
- Technical calculations (pagination, ID generation)
- Infrastructure logic (file handling, screen processing)
- System operations (database connections, error handling)

## Source Analysis

All 18 COBOL programs in the 00.phase-1-input/cbl/ folder were systematically analyzed for business calculation patterns.

## Summary

- **Total Business Calculation Rules Found**: 10
- **Primary Business Domain**: Credit card account management and bill payment processing
- **Key Financial Operations**: Balance updates, credit limit management, billing cycle tracking
- **Rule Dependencies**: Minimal - mostly isolated calculations within individual programs

## Business Rules Overview

1. **RULE-CALC-001**: Bill Payment Balance Calculation (COBIL00C.cbl)
2. **RULE-CALC-002**: Credit Limit Conversion (COACTUPC.cbl)
3. **RULE-CALC-003**: Cash Credit Limit Conversion (COACTUPC.cbl)
4. **RULE-CALC-004**: Current Balance Conversion (COACTUPC.cbl)
5. **RULE-CALC-005**: Current Cycle Credit Conversion (COACTUPC.cbl)
6. **RULE-CALC-006**: Current Cycle Debit Conversion (COACTUPC.cbl)
7. **RULE-CALC-007**: Report Date Range Calculation (CORPT00C.cbl)
8. **RULE-CALC-008**: Transaction ID Generation (COBIL00C.cbl)
9. **RULE-CALC-009**: Transaction List Pagination (COTRN00C.cbl)
10. **RULE-CALC-010**: Report Date Input Conversion (CORPT00C.cbl)
