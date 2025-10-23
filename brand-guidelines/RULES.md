# CURSOR Rules for Brand Guidelines Skill

## Overview
This skill applies Anthropic's official brand colors and typography to any artifact that may benefit from having Anthropic's look-and-feel. It provides consistent visual identity across different document types.

## Core Brand Elements

### Color Palette Rules
**Main Colors (MANDATORY):**
- Dark: `#141413` - Primary text and dark backgrounds
- Light: `#faf9f5` - Light backgrounds and text on dark
- Mid Gray: `#b0aea5` - Secondary elements
- Light Gray: `#e8e6dc` - Subtle backgrounds

**Accent Colors (ROTATION):**
- Orange: `#d97757` - Primary accent
- Blue: `#6a9bcc` - Secondary accent
- Green: `#788c5d` - Tertiary accent

### Typography Rules
**Font Hierarchy (MANDATORY):**
- **Headings (24pt+)**: Poppins font with Arial fallback
- **Body Text**: Lora font with Georgia fallback
- **System Fallbacks**: Arial for headings, Georgia for body when custom fonts unavailable

## Application Rules

### When to Apply Brand Guidelines
**ALWAYS apply when:**
- User mentions "brand colors" or "style guidelines"
- Visual formatting is requested
- Company design standards apply
- Post-processing for professional appearance
- Corporate identity needs

**Keywords that trigger this skill:**
- branding, corporate identity, visual identity
- post-processing, styling, brand colors
- typography, Anthropic brand, visual formatting
- visual design, company design standards

### Smart Font Application Rules
**Automatic Font Detection:**
- Headings (24pt and larger): Apply Poppins font
- Body text: Apply Lora font
- Preserve existing font hierarchy
- Maintain readability across all systems

**Fallback Strategy:**
- Use system-installed fonts when available
- Automatic fallback to Arial (headings) and Georgia (body)
- No font installation required
- Works with existing system fonts

### Color Application Rules
**Text Styling:**
- Smart color selection based on background
- Preserve text hierarchy and formatting
- Maintain contrast for readability
- Apply brand colors consistently

**Shape and Accent Colors:**
- Non-text shapes use accent colors
- Cycle through orange, blue, and green accents
- Maintain visual interest while staying on-brand
- Use RGB color values for precise brand matching

## Technical Implementation Rules

### Font Management
**System Requirements:**
- Use system-installed Poppins and Lora fonts when available
- Provide automatic fallback to Arial (headings) and Georgia (body)
- No font installation required
- Works with existing system fonts

**Best Practices:**
- Pre-install Poppins and Lora fonts for best results
- Use RGB color values for precise brand matching
- Applied via appropriate library's RGBColor class
- Maintain color fidelity across different systems

### Color Application Standards
**RGB Color Values:**
- Use exact hex codes for brand colors
- Apply via library-specific RGBColor classes
- Maintain color fidelity across systems
- Ensure consistent brand representation

## Quality Assurance Rules

### Visual Consistency
**Brand Compliance:**
- All colors must match official brand palette
- Typography must follow hierarchy rules
- Maintain consistent visual identity
- Preserve professional appearance

### Readability Standards
**Contrast Requirements:**
- Ensure sufficient contrast between text and backgrounds
- Maintain readability across all systems
- Test with different background colors
- Preserve accessibility standards

### System Compatibility
**Cross-Platform Support:**
- Work with existing system fonts
- Provide appropriate fallbacks
- Maintain functionality across platforms
- Ensure consistent appearance

## Error Prevention Rules

### Common Pitfalls
- ❌ Using non-brand colors
- ❌ Ignoring font hierarchy
- ❌ Poor contrast ratios
- ❌ Inconsistent application
- ❌ Missing fallback fonts

### Best Practices
- ✅ Always use official brand colors
- ✅ Follow typography hierarchy
- ✅ Ensure proper contrast
- ✅ Apply consistently
- ✅ Include fallback fonts

## Documentation Rules

### Brand Guidelines
- Document all color codes
- Specify font requirements
- Include fallback strategies
- Maintain brand consistency

### Technical Specifications
- RGB color values for all brand colors
- Font specifications and fallbacks
- Application methods for different platforms
- Compatibility requirements

## Maintenance Rules

### Updates
- Keep brand guidelines current
- Update color codes if changed
- Maintain font specifications
- Preserve compatibility

### Extensions
- Add new brand elements
- Expand color palette
- Include additional fonts
- Enhance application methods

## Security Rules

### Brand Protection
- Use only official brand colors
- Maintain brand consistency
- Protect brand identity
- Follow brand guidelines

### Quality Control
- Validate color codes
- Check font availability
- Test across platforms
- Ensure brand compliance
