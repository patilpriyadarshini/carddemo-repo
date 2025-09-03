# Business Validation Rules Extraction

This folder contains the extracted business validation rules from the COBOL codebase in the 00.cobol-code-base folder.

## Contents

- `validation-rules.md` - Comprehensive documentation of all business validation rules
- `validation-relationships.svg` - Visual diagram showing validation rule relationships and dependencies
- `validation-summary.md` - Executive summary of validation patterns found

## Extraction Criteria

Only business-level validation rules were extracted, including:
- Field-level input validations (non-empty, length checks, format constraints)
- Range validations (age ranges, score ranges)
- Code or value checks (status codes, valid values)
- Domain-specific validation (business rules)
- Conditional validations (dependent field requirements)

Excluded from extraction:
- Calculation logic (interest computation, amount derivation)
- Technical validations (system errors, DB exceptions)
- BMS layout constraints or display-only checks

## Source Analysis

All 18 COBOL programs in the 00.cobol-code-base/cbl/ folder were systematically analyzed for validation patterns.
