# CURSOR Rules for Algorithmic Art Skill

## Overview
This skill creates algorithmic art using p5.js with seeded randomness and interactive parameter exploration. It follows a two-step process: creating algorithmic philosophy, then implementing it in code.

## Critical Workflow Rules

### Step 0: ALWAYS Read Template First
**MANDATORY**: Before writing any HTML, read `templates/viewer.html` completely. This is the foundation - not inspiration.

**Fixed Elements (NEVER change):**
- Layout structure (header, sidebar, main canvas area)
- Anthropic branding (UI colors, fonts, gradients)
- Seed section in sidebar (display, prev/next/random/jump buttons)
- Actions section (regenerate, reset, download buttons)

**Variable Elements (customize per artwork):**
- p5.js algorithm (setup/draw/classes)
- Parameters object (define what the art needs)
- Parameters section in sidebar (controls for the art)
- Colors section (optional, only if art needs adjustable colors)

### Philosophy Creation Rules

**Structure Requirements:**
- Name the movement (1-2 words): "Organic Turbulence", "Quantum Harmonics", etc.
- Write 4-6 substantial paragraphs
- Emphasize craftsmanship REPEATEDLY
- Leave creative space for implementation
- Focus on algorithmic expression, not static images

**Content Guidelines:**
- Avoid redundancy - each algorithmic aspect mentioned once
- Emphasize "meticulously crafted algorithm", "product of deep computational expertise"
- Guide toward algorithmic expression, not static composition
- Beauty lives in the process, not the final frame

### Implementation Rules

**Technical Requirements:**
- ALWAYS use seeded randomness: `randomSeed(seed); noiseSeed(seed);`
- Canvas setup: `createCanvas(1200, 1200)`
- Parameters must emerge from philosophy, not pattern types
- Algorithm flows from philosophy, not menu options

**Parameter Design:**
- Focus on system properties that need tuning
- Consider: quantities, scales, probabilities, ratios, angles, thresholds
- Avoid thinking in "pattern types" - think "system properties"

**Craftsmanship Standards:**
- Balance: complexity without visual noise
- Color harmony: thoughtful palettes, not random RGB
- Composition: visual hierarchy even in randomness
- Performance: smooth execution
- Reproducibility: same seed = identical output

### Output Format Rules

**Required Outputs:**
1. Algorithmic Philosophy (.md file)
2. Single HTML Artifact (self-contained)

**HTML Artifact Requirements:**
- Everything inline (no external files except p5.js CDN)
- Works immediately in claude.ai or any browser
- Seed navigation (prev/next/random/jump)
- Parameter controls with real-time updates
- Reset and download buttons
- Anthropic branding preserved

### Creative Process Rules

**Workflow:**
1. Interpret user's intent - what aesthetic is sought?
2. Create algorithmic philosophy (4-6 paragraphs)
3. Implement in code - build algorithm expressing philosophy
4. Design appropriate parameters
5. Build matching UI controls

**Constants:**
- Anthropic branding (colors, fonts, layout)
- Seed navigation (always present)
- Self-contained HTML artifact

**Variables:**
- The algorithm itself
- The parameters
- The UI controls
- The visual outcome

## Code Quality Rules

### JavaScript/P5.js Standards
- Use descriptive variable names
- Comment complex algorithms
- Structure code with clear functions
- Handle edge cases gracefully

### HTML Structure Rules
- Copy template structure exactly
- Keep Anthropic branding unchanged
- Maintain sidebar layout (Seed → Parameters → Colors? → Actions)
- Replace only algorithm and parameter controls

### Performance Rules
- Optimize for real-time if animated
- Use efficient drawing methods
- Avoid unnecessary calculations in draw loop
- Test with various parameter ranges

## Error Prevention Rules

### Common Pitfalls
- ❌ Creating HTML from scratch
- ❌ Inventing custom styling
- ❌ Using system fonts or dark themes
- ❌ Changing sidebar structure
- ❌ Copying flow field examples instead of building unique algorithms

### Best Practices
- ✅ Copy template's exact HTML structure
- ✅ Keep Anthropic branding
- ✅ Maintain sidebar layout
- ✅ Replace only p5.js algorithm and parameter controls
- ✅ Build unique algorithms based on philosophy

## Testing Rules

### Validation Requirements
- Test with multiple seeds
- Verify parameter controls work
- Check file size and performance
- Ensure reproducibility
- Validate in different browsers

### Quality Checks
- No overlapping elements
- Proper contrast and readability
- Smooth animations
- Responsive controls
- Error-free execution

## Documentation Rules

### Code Comments
- Explain complex algorithms
- Document parameter purposes
- Note performance considerations
- Include usage examples

### User Instructions
- Clear parameter descriptions
- Intuitive control labels
- Helpful tooltips
- Logical control grouping

## Maintenance Rules

### Updates
- Keep p5.js version current
- Test with new browser versions
- Update CDN links if needed
- Maintain compatibility

### Extensions
- Add new animation primitives
- Expand parameter options
- Improve performance
- Enhance user experience

## Security Rules

### Code Safety
- Sanitize user inputs
- Validate parameter ranges
- Prevent infinite loops
- Handle memory efficiently

### External Dependencies
- Use trusted CDN sources
- Verify script integrity
- Monitor for updates
- Document dependencies
