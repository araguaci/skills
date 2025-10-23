# CURSOR Rules for PPTX Skill

## Overview
This skill provides presentation creation, editing, and analysis for PowerPoint files. It covers both html2pptx for creation and OOXML editing for existing presentations.

## Workflow Decision Tree Rules

### Reading and Analyzing Content
**Text Extraction:**
```bash
# Convert document to markdown
python -m markitdown path-to-file.pptx
```

**Raw XML Access:**
- Comments, speaker notes, slide layouts
- Animations, design elements, complex formatting
- Unpack: `python ooxml/scripts/unpack.py <office_file> <output_dir>`

## Creating New Presentation Rules

### Without Template
**MANDATORY Workflow:**
1. **READ ENTIRE FILE**: Read `html2pptx.md` completely (MANDATORY)
2. Create HTML file for each slide with proper dimensions (720pt × 405pt for 16:9)
3. Create and run JavaScript file using `html2pptx.js` library
4. **Visual validation**: Generate thumbnails and inspect for layout issues

### Design Principles
**CRITICAL Requirements:**
- State content-informed design approach BEFORE writing code
- Use web-safe fonts only: Arial, Helvetica, Times New Roman, Georgia, Courier New, Verdana, Tahoma, Trebuchet MS, Impact
- Create clear visual hierarchy through size, weight, and color
- Ensure readability: strong contrast, appropriately sized text, clean alignment
- Be consistent: repeat patterns, spacing, and visual language across slides

### Color Palette Selection
**Creative Color Guidelines:**
- Think beyond defaults: What colors genuinely match this specific topic?
- Consider multiple angles: Topic, industry, mood, energy level, target audience, brand identity
- Be adventurous: Try unexpected combinations
- Build your palette: Pick 3-5 colors that work together
- Ensure contrast: Text must be clearly readable on backgrounds

### Layout Tips
**When Creating Slides with Charts or Tables:**
- **Two-column layout (PREFERRED)**: Header spanning full width, then two columns below
- **Full-slide layout**: Let featured content take up entire slide
- **NEVER vertically stack**: Do not place charts/tables below text in single column

## Template-Based Creation Rules

### Template Analysis
**MANDATORY Steps:**
1. **Extract template text AND create visual thumbnail grid**
2. **Analyze template and save inventory to file**
3. **Create presentation outline based on template inventory**
4. **Duplicate, reorder, and delete slides using `rearrange.py`**
5. **Extract ALL text using the `inventory.py` script**
6. **Generate replacement text and save to JSON file**
7. **Apply replacements using the `replace.py` script**

### Template Inventory Rules
**Required Structure:**
```markdown
# Template Inventory Analysis
**Total Slides: [count]**
**IMPORTANT: Slides are 0-indexed (first slide = 0, last slide = count-1)**

## [Category Name]
- Slide 0: [Layout code if available] - Description/purpose
- Slide 1: [Layout code] - Description/purpose
```

### Layout Selection Rules
**CRITICAL Guidelines:**
- Match layout structure to actual content
- Single-column layouts: Use for unified narrative
- Two-column layouts: Use ONLY when you have exactly 2 distinct items
- Three-column layouts: Use ONLY when you have exactly 3 distinct items
- Image + text layouts: Use ONLY when you have actual images to insert
- Quote layouts: Use ONLY for actual quotes from people
- Never use layouts with more placeholders than you have content

## Editing Existing Presentations Rules

### OOXML Workflow
**MANDATORY Steps:**
1. **READ ENTIRE FILE**: Read `ooxml.md` (~500 lines) completely
2. Unpack the presentation: `python ooxml/scripts/unpack.py <office_file> <output_dir>`
3. Edit the XML files (primarily `ppt/slides/slide{N}.xml`)
4. **CRITICAL**: Validate immediately after each edit: `python ooxml/scripts/validate.py <dir> --original <file>`
5. Pack the final presentation: `python ooxml/scripts/pack.py <input_directory> <office_file>`

## Visual Validation Rules

### Thumbnail Generation
**MANDATORY Process:**
```bash
python scripts/thumbnail.py output.pptx workspace/thumbnails --cols 4
```

**Inspection Requirements:**
- **Text cutoff**: Text being cut off by header bars, shapes, or slide edges
- **Text overlap**: Text overlapping with other text or shapes
- **Positioning issues**: Content too close to slide boundaries
- **Contrast issues**: Insufficient contrast between text and backgrounds

### Layout Validation
**Quality Checks:**
- All text contained within slide boundaries
- Proper margins and spacing
- Clear visual hierarchy
- Professional appearance

## Code Style Guidelines

### Python Code Standards
**IMPORTANT Requirements:**
- Write concise code
- Avoid verbose variable names and redundant operations
- Avoid unnecessary print statements
- Focus on functionality

### Dependencies Management
**Required Dependencies:**
- **markitdown**: `pip install "markitdown[pptx]"`
- **pptxgenjs**: `npm install -g pptxgenjs`
- **playwright**: `npm install -g playwright`
- **react-icons**: `npm install -g react-icons react react-dom`
- **sharp**: `npm install -g sharp`
- **LibreOffice**: `sudo apt-get install libreoffice`
- **Poppler**: `sudo apt-get install poppler-utils`
- **defusedxml**: `pip install defusedxml`

## Error Prevention Rules

### Common Pitfalls
- ❌ Not reading documentation completely
- ❌ Poor layout selection
- ❌ Ignoring visual validation
- ❌ Not validating OOXML edits
- ❌ Poor color palette selection

### Best Practices
- ✅ Always read documentation completely
- ✅ Choose appropriate layouts
- ✅ Perform visual validation
- ✅ Validate OOXML edits immediately
- ✅ Select colors thoughtfully

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
- Add new creation capabilities
- Expand template features
- Improve error handling
- Enhance documentation

## Security Rules

### File Safety
- Validate file inputs
- Handle corrupted presentations
- Prevent path traversal
- Ensure proper permissions

### Data Safety
- Handle sensitive presentations
- Protect personal information
- Follow data privacy rules
- Implement secure practices
