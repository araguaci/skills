# CURSOR Rules for PDF Skill

## Overview
This skill provides comprehensive PDF manipulation toolkit for extracting text and tables, creating new PDFs, merging/splitting documents, and handling forms. It covers both Python libraries and command-line tools.

## Library Selection Rules

### Python Libraries
**pypdf - Basic Operations:**
- Merge PDFs
- Split PDFs
- Extract metadata
- Rotate pages
- Password protection

**pdfplumber - Text and Table Extraction:**
- Extract text with layout
- Extract tables
- Advanced table extraction with pandas
- Layout preservation

**reportlab - Create PDFs:**
- Basic PDF creation
- Multiple pages
- Styling and formatting
- Professional layouts

### Command-Line Tools
**pdftotext (poppler-utils):**
- Extract text
- Extract text preserving layout
- Extract specific pages

**qpdf:**
- Merge PDFs
- Split pages
- Rotate pages
- Remove password

**pdftk (if available):**
- Merge operations
- Split operations
- Rotate operations

## Common Tasks Rules

### Extract Text from Scanned PDFs
**OCR Requirements:**
```python
# Requires: pip install pytesseract pdf2image
import pytesseract
from pdf2image import convert_from_path

# Convert PDF to images
images = convert_from_path('scanned.pdf')

# OCR each page
text = ""
for i, image in enumerate(images):
    text += f"Page {i+1}:\n"
    text += pytesseract.image_to_string(image)
    text += "\n\n"
```

### Add Watermark
**Implementation:**
```python
from pypdf import PdfReader, PdfWriter

# Create watermark (or load existing)
watermark = PdfReader("watermark.pdf").pages[0]

# Apply to all pages
reader = PdfReader("document.pdf")
writer = PdfWriter()

for page in reader.pages:
    page.merge_page(watermark)
    writer.add_page(page)

with open("watermarked.pdf", "wb") as output:
    writer.write(output)
```

### Extract Images
**Command-line approach:**
```bash
# Using pdfimages (poppler-utils)
pdfimages -j input.pdf output_prefix
```

### Password Protection
**Implementation:**
```python
from pypdf import PdfReader, PdfWriter

reader = PdfReader("input.pdf")
writer = PdfWriter()

for page in reader.pages:
    writer.add_page(page)

# Add password
writer.encrypt("userpassword", "ownerpassword")

with open("encrypted.pdf", "wb") as output:
    writer.write(output)
```

## Quick Reference Rules

### Task-to-Tool Mapping
**Best Practices:**
- Merge PDFs: pypdf
- Split PDFs: pypdf
- Extract text: pdfplumber
- Extract tables: pdfplumber
- Create PDFs: reportlab
- Command line merge: qpdf
- OCR scanned PDFs: pytesseract
- Fill PDF forms: pdf-lib or pypdf (see forms.md)

### Library Selection Guidelines
**Choose Based on Task:**
- **pypdf**: Basic operations, merging, splitting
- **pdfplumber**: Text and table extraction
- **reportlab**: PDF creation and formatting
- **Command-line tools**: Batch operations, automation

## Error Prevention Rules

### Common Pitfalls
- ❌ Using wrong library for task
- ❌ Not handling encoding issues
- ❌ Ignoring file size limits
- ❌ Poor error handling
- ❌ Not validating inputs

### Best Practices
- ✅ Choose appropriate library for task
- ✅ Handle encoding properly
- ✅ Check file size limits
- ✅ Implement proper error handling
- ✅ Validate all inputs

## Documentation Rules

### Code Documentation
- Document library usage
- Include error handling
- Provide usage examples
- Note common pitfalls

### User Instructions
- Clear task-to-tool mapping
- Library selection guidelines
- Common usage patterns
- Troubleshooting guides

## Maintenance Rules

### Updates
- Keep libraries current
- Update usage patterns
- Maintain compatibility
- Test with new versions

### Extensions
- Add new libraries
- Expand functionality
- Improve error handling
- Enhance documentation

## Security Rules

### File Safety
- Validate file inputs
- Handle corrupted files
- Prevent path traversal
- Ensure proper permissions

### Data Safety
- Handle sensitive data
- Protect personal information
- Follow data privacy rules
- Implement secure practices
