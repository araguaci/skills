# CURSOR Rules for XLSX Skill

## Overview
This skill provides comprehensive spreadsheet creation, editing, and analysis with support for formulas, formatting, data analysis, and visualization. It covers both pandas for data analysis and openpyxl for formulas and formatting.

## Requirements for Outputs Rules

### All Excel Files
**MANDATORY Standards:**
- **Zero Formula Errors**: Every Excel model MUST be delivered with ZERO formula errors (#REF!, #DIV/0!, #VALUE!, #N/A, #NAME?)
- **Preserve Existing Templates**: Study and EXACTLY match existing format, style, and conventions when modifying files

### Financial Models
**Color Coding Standards (unless otherwise stated):**
- **Blue text (RGB: 0,0,255)**: Hardcoded inputs, and numbers users will change for scenarios
- **Black text (RGB: 0,0,0)**: ALL formulas and calculations
- **Green text (RGB: 0,128,0)**: Links pulling from other worksheets within same workbook
- **Red text (RGB: 255,0,0)**: External links to other files
- **Yellow background (RGB: 255,255,0)**: Key assumptions needing attention or cells that need to be updated

**Number Formatting Standards:**
- **Years**: Format as text strings (e.g., "2024" not "2,024")
- **Currency**: Use $#,##0 format; ALWAYS specify units in headers ("Revenue ($mm)")
- **Zeros**: Use number formatting to make all zeros "-", including percentages
- **Percentages**: Default to 0.0% format (one decimal)
- **Multiples**: Format as 0.0x for valuation multiples (EV/EBITDA, P/E)
- **Negative numbers**: Use parentheses (123) not minus -123

## Formula Construction Rules

### Assumptions Placement
**MANDATORY Requirements:**
- Place ALL assumptions (growth rates, margins, multiples, etc.) in separate assumption cells
- Use cell references instead of hardcoded values in formulas
- Example: Use `=B5*(1+$B$6)` instead of `=B5*1.05`

### Formula Error Prevention
**CRITICAL Checks:**
- Verify all cell references are correct
- Check for off-by-one errors in ranges
- Ensure consistent formulas across all projection periods
- Test with edge cases (zero values, negative numbers)
- Verify no unintended circular references

### Documentation Requirements
**For Hardcoded Values:**
- Comment or in cells beside (if end of table)
- Format: "Source: [System/Document], [Date], [Specific Reference], [URL if applicable]"
- Examples:
  - "Source: Company 10-K, FY2024, Page 45, Revenue Note, [SEC EDGAR URL]"
  - "Source: Bloomberg Terminal, 8/15/2025, AAPL US Equity"

## CRITICAL: Use Formulas, Not Hardcoded Values

### ❌ WRONG - Hardcoding Calculated Values
```python
# Bad: Calculating in Python and hardcoding result
total = df['Sales'].sum()
sheet['B10'] = total  # Hardcodes 5000

# Bad: Computing growth rate in Python
growth = (df.iloc[-1]['Revenue'] - df.iloc[0]['Revenue']) / df.iloc[0]['Revenue']
sheet['C5'] = growth  # Hardcodes 0.15
```

### ✅ CORRECT - Using Excel Formulas
```python
# Good: Let Excel calculate the sum
sheet['B10'] = '=SUM(B2:B9)'

# Good: Growth rate as Excel formula
sheet['C5'] = '=(C4-C2)/C2'
```

## Common Workflow Rules

### Step-by-Step Process
1. **Choose tool**: pandas for data, openpyxl for formulas/formatting
2. **Create/Load**: Create new workbook or load existing file
3. **Modify**: Add/edit data, formulas, and formatting
4. **Save**: Write to file
5. **Recalculate formulas (MANDATORY IF USING FORMULAS)**: Use the recalc.py script
6. **Verify and fix any errors**: Check JSON output for errors

### Recalculating Formulas
**MANDATORY Command:**
```bash
python recalc.py output.xlsx
```

**What the script does:**
- Automatically sets up LibreOffice macro on first run
- Recalculates all formulas in all sheets
- Scans ALL cells for Excel errors (#REF!, #DIV/0!, etc.)
- Returns JSON with detailed error locations and counts

## Library Selection Rules

### pandas - Best For
- Data analysis, bulk operations, and simple data export
- Reading and analyzing existing data
- Data manipulation and transformation
- Simple data export to Excel

### openpyxl - Best For
- Complex formatting, formulas, and Excel-specific features
- Creating new workbooks with formulas
- Advanced formatting and styling
- Excel-specific functionality

## Error Prevention Rules

### Common Pitfalls
- ❌ Hardcoding calculated values instead of using formulas
- ❌ Not recalculating formulas after creation
- ❌ Poor error handling
- ❌ Not validating formula references
- ❌ Ignoring Excel error codes

### Best Practices
- ✅ Always use Excel formulas for calculations
- ✅ Recalculate formulas after creation
- ✅ Implement proper error handling
- ✅ Validate all cell references
- ✅ Check for Excel error codes

## Formula Verification Checklist

### Essential Verification
- [ ] **Test 2-3 sample references**: Verify they pull correct values before building full model
- [ ] **Column mapping**: Confirm Excel columns match (e.g., column 64 = BL, not BK)
- [ ] **Row offset**: Remember Excel rows are 1-indexed (DataFrame row 5 = Excel row 6)

### Common Pitfalls
- [ ] **NaN handling**: Check for null values with `pd.notna()`
- [ ] **Far-right columns**: FY data often in columns 50+
- [ ] **Multiple matches**: Search all occurrences, not just first
- [ ] **Division by zero**: Check denominators before using `/` in formulas
- [ ] **Wrong references**: Verify all cell references point to intended cells

### Formula Testing Strategy
- [ ] **Start small**: Test formulas on 2-3 cells before applying broadly
- [ ] **Verify dependencies**: Check all cells referenced in formulas exist
- [ ] **Test edge cases**: Include zero, negative, and very large values

## Documentation Rules

### Code Documentation
- Document formula construction
- Include error handling
- Provide usage examples
- Note common pitfalls

### User Instructions
- Clear workflow guidelines
- Formula construction rules
- Error handling procedures
- Best practices

## Maintenance Rules

### Updates
- Keep libraries current
- Update formula patterns
- Maintain compatibility
- Test with new versions

### Extensions
- Add new formula capabilities
- Expand formatting options
- Improve error handling
- Enhance documentation

## Security Rules

### File Safety
- Validate file inputs
- Handle corrupted spreadsheets
- Prevent path traversal
- Ensure proper permissions

### Data Safety
- Handle sensitive data
- Protect personal information
- Follow data privacy rules
- Implement secure practices
