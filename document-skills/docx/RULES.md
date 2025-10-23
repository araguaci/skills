# CURSOR Rules for DOCX Skill

## Overview
This skill provides comprehensive document creation, editing, and analysis with support for tracked changes, comments, formatting preservation, and text extraction. It covers both docx-js for creation and Document library for editing.

## Workflow Decision Tree Rules

### Reading/Analyzing Content
**Use Cases:**
- Text extraction
- Raw XML access
- Content analysis
- Document structure

### Creating New Document
**MANDATORY Workflow:**
- Use docx-js for creation
- Read `docx-js.md` completely (MANDATORY)
- Create JavaScript/TypeScript file
- Export as .docx using Packer.toBuffer()

### Editing Existing Document
**Two Approaches:**
- **Your own document + simple changes**: Basic OOXML editing
- **Someone else's document**: Redlining workflow (recommended default)
- **Legal, academic, business, or government docs**: Redlining workflow (required)

## Reading and Analysis Rules

### Text Extraction
**Pandoc Approach:**
```bash
# Convert document to markdown with tracked changes
pandoc --track-changes=all path-to-file.docx -o output.md
# Options: --track-changes=accept/reject/all
```

### Raw XML Access
**When Needed:**
- Comments
- Complex formatting
- Document structure
- Embedded media
- Metadata

**Unpacking Process:**
```bash
python ooxml/scripts/unpack.py <office_file> <output_directory>
```

**Key File Structures:**
- `word/document.xml` - Main document contents
- `word/comments.xml` - Comments referenced in document.xml
- `word/media/` - Embedded images and media files
- Tracked changes use `<w:ins>` (insertions) and `<w:del>` (deletions) tags

## Document Creation Rules

### docx-js Workflow
**MANDATORY Steps:**
1. **READ ENTIRE FILE**: Read `docx-js.md` (~500 lines) completely
2. Create JavaScript/TypeScript file using Document, Paragraph, TextRun components
3. Export as .docx using Packer.toBuffer()

**Dependencies:**
- Assume all dependencies are installed
- Refer to dependencies section if not available

## Document Editing Rules

### Document Library Workflow
**MANDATORY Steps:**
1. **READ ENTIRE FILE**: Read `ooxml.md` (~600 lines) completely
2. Unpack the document: `python ooxml/scripts/unpack.py <office_file> <output_directory>`
3. Create and run Python script using Document library
4. Pack the final document: `python ooxml/scripts/pack.py <input_directory> <office_file>`

### Redlining Workflow Rules
**CRITICAL Requirements:**
- Implement ALL changes systematically
- Group related changes into batches of 3-10 changes
- Test each batch before moving to next
- Use minimal, precise edits

**Batching Strategy:**
- Group by section: "Batch 1: Section 2 amendments"
- Group by type: "Batch 1: Date corrections"
- Group by complexity: Start with simple text replacements
- Sequential: "Batch 1: Pages 1-3"

**Principle: Minimal, Precise Edits**
- Only mark text that actually changes
- Break replacements into: [unchanged text] + [deletion] + [insertion] + [unchanged text]
- Preserve original run's RSID for unchanged text

## Tracked Changes Implementation Rules

### Workflow Steps
**MANDATORY Process:**
1. **Get markdown representation**: Convert document to markdown with tracked changes
2. **Identify and group changes**: Review document and identify ALL changes needed
3. **Read documentation and unpack**: Read `ooxml.md` completely, unpack document
4. **Implement changes in batches**: Group changes logically and implement together
5. **Pack the document**: Convert unpacked directory back to .docx
6. **Final verification**: Comprehensive check of complete document

### Location Methods
**For Finding Changes in XML:**
- Section/heading numbers (e.g., "Section 3.2", "Article IV")
- Paragraph identifiers if numbered
- Grep patterns with unique surrounding text
- Document structure (e.g., "first paragraph", "signature block")
- **DO NOT use markdown line numbers** - they don't map to XML structure

### Batch Implementation
**For Each Batch:**
- **Map text to XML**: Grep for text in `word/document.xml`
- **Create and run script**: Use `get_node` to find nodes, implement changes, then `doc.save()`
- **Note**: Always grep `word/document.xml` immediately before writing script

## Document Conversion Rules

### Converting to Images
**Two-Step Process:**
1. **Convert DOCX to PDF**:
   ```bash
   soffice --headless --convert-to pdf document.docx
   ```

2. **Convert PDF pages to JPEG images**:
   ```bash
   pdftoppm -jpeg -r 150 document.pdf page
   ```

**Options:**
- `-r 150`: Sets resolution to 150 DPI
- `-jpeg`: Output JPEG format
- `-f N`: First page to convert
- `-l N`: Last page to convert

## Code Style Guidelines

### Python Code Standards
**IMPORTANT Requirements:**
- Write concise code
- Avoid verbose variable names and redundant operations
- Avoid unnecessary print statements
- Focus on functionality

### Dependencies Management
**Required Dependencies:**
- **pandoc**: `sudo apt-get install pandoc`
- **docx**: `npm install -g docx`
- **LibreOffice**: `sudo apt-get install libreoffice`
- **Poppler**: `sudo apt-get install poppler-utils`
- **defusedxml**: `pip install defusedxml`

## Error Prevention Rules

### Common Pitfalls
- ❌ Not reading documentation completely
- ❌ Skipping tracked changes workflow
- ❌ Poor batching strategy
- ❌ Not preserving RSID for unchanged text
- ❌ Using markdown line numbers for XML mapping

### Best Practices
- ✅ Always read documentation completely
- ✅ Follow redlining workflow for complex edits
- ✅ Use proper batching strategy
- ✅ Preserve original formatting
- ✅ Use XML structure for mapping

## Documentation Rules

### Code Documentation
- Document complex operations
- Include error handling
- Provide usage examples
- Note common pitfalls

### User Instructions
- Clear workflow guidelines
- Step-by-step processes
- Troubleshooting guides
- Best practices

## Maintenance Rules

### Updates
- Keep dependencies current
- Update workflow patterns
- Maintain compatibility
- Test with new versions

### Extensions
- Add new editing capabilities
- Expand tracked changes features
- Improve error handling
- Enhance documentation

## Security Rules

### File Safety
- Validate file inputs
- Handle corrupted documents
- Prevent path traversal
- Ensure proper permissions

### Data Safety
- Handle sensitive documents
- Protect personal information
- Follow data privacy rules
- Implement secure practices
