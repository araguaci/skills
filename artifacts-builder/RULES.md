# CURSOR Rules for Artifacts Builder Skill

## Overview
This skill provides a suite of tools for creating elaborate, multi-component claude.ai HTML artifacts using modern frontend web technologies (React, Tailwind CSS, shadcn/ui). It's designed for complex artifacts requiring state management, routing, or shadcn/ui components.

## Technology Stack Rules

### Required Technologies
**MANDATORY Stack:**
- React 18 + TypeScript
- Vite (build tool)
- Parcel (bundling)
- Tailwind CSS 3.4.1
- shadcn/ui theming system
- Node 18+ compatibility

### Project Structure Rules
**Initialization Requirements:**
- Path aliases (`@/`) configured
- 40+ shadcn/ui components pre-installed
- All Radix UI dependencies included
- Parcel configured for bundling via .parcelrc
- Node 18+ compatibility with auto-detection

## Workflow Rules

### Step 1: Initialize Project
**MANDATORY Command:**
```bash
bash scripts/init-artifact.sh <project-name>
cd <project-name>
```

**What the script creates:**
- ✅ React + TypeScript (via Vite)
- ✅ Tailwind CSS 3.4.1 with shadcn/ui theming
- ✅ Path aliases (`@/`) configured
- ✅ 40+ shadcn/ui components pre-installed
- ✅ All Radix UI dependencies included
- ✅ Parcel configured for bundling
- ✅ Node 18+ compatibility

### Step 2: Develop Your Artifact
**Development Guidelines:**
- Edit generated files to build the artifact
- Follow Common Development Tasks for guidance
- Use shadcn/ui components as needed
- Implement state management if required
- Add routing if necessary

### Step 3: Bundle to Single HTML File
**MANDATORY Command:**
```bash
bash scripts/bundle-artifact.sh
```

**Requirements:**
- Project must have `index.html` in root directory
- Creates `bundle.html` - self-contained artifact
- All JavaScript, CSS, and dependencies inlined
- Can be directly shared in Claude conversations

**What the script does:**
- Installs bundling dependencies (parcel, @parcel/config-default, parcel-resolver-tspaths, html-inline)
- Creates `.parcelrc` config with path alias support
- Builds with Parcel (no source maps)
- Inlines all assets into single HTML using html-inline

### Step 4: Share Artifact with User
**Final Step:**
- Share the bundled HTML file in conversation
- User can view it as an artifact immediately
- No additional setup required

### Step 5: Testing/Visualizing (Optional)
**When to Test:**
- Only if necessary or requested
- Avoid testing upfront to reduce latency
- Test after presenting artifact if issues arise
- Use available tools (Playwright, Puppeteer, other Skills)

## Design & Style Guidelines

### Anti-Patterns to Avoid
**CRITICAL - Avoid "AI Slop":**
- ❌ Excessive centered layouts
- ❌ Purple gradients
- ❌ Uniform rounded corners
- ❌ Inter font overuse

### Best Practices
**Design Principles:**
- ✅ Use diverse layouts and compositions
- ✅ Varied color palettes beyond purple
- ✅ Mixed corner radius treatments
- ✅ Appropriate font choices for context

## Technical Implementation Rules

### Bundle Artifact Requirements
**File Structure:**
- Must have `index.html` in root directory
- All dependencies must be installable
- Path aliases must be properly configured
- Parcel configuration must be correct

### Dependencies Management
**Bundling Dependencies:**
- parcel
- @parcel/config-default
- parcel-resolver-tspaths
- html-inline

**Installation Process:**
- Script installs dependencies automatically
- Creates proper configuration files
- Handles path alias resolution
- Inlines all assets

### Output Requirements
**Bundle.html Features:**
- Self-contained artifact
- All JavaScript inlined
- All CSS inlined
- All dependencies included
- Works immediately in Claude conversations

## Quality Assurance Rules

### Pre-Bundle Validation
**Check Before Bundling:**
- Verify `index.html` exists in root
- Ensure all imports are correct
- Check path aliases are working
- Validate TypeScript compilation

### Post-Bundle Validation
**Verify After Bundling:**
- Check `bundle.html` was created
- Verify all assets are inlined
- Test artifact functionality
- Ensure no external dependencies

### Testing Requirements
**When Testing:**
- Use appropriate tools for validation
- Check functionality across browsers
- Verify responsive design
- Test interactive elements

## Error Prevention Rules

### Common Pitfalls
- ❌ Missing `index.html` in root
- ❌ Incorrect path aliases
- ❌ Missing dependencies
- ❌ Poor Parcel configuration
- ❌ AI slop design patterns

### Best Practices
- ✅ Follow initialization script exactly
- ✅ Use proper project structure
- ✅ Configure dependencies correctly
- ✅ Avoid common design anti-patterns
- ✅ Test thoroughly before sharing

## Documentation Rules

### Project Documentation
- Document component usage
- Explain state management
- Describe routing implementation
- Include setup instructions

### Technical Documentation
- Bundle process explanation
- Dependency management
- Configuration details
- Troubleshooting guide

## Maintenance Rules

### Updates
- Keep dependencies current
- Update build tools
- Maintain compatibility
- Test with new versions

### Extensions
- Add new components
- Expand functionality
- Improve performance
- Enhance user experience

## Security Rules

### Code Safety
- Validate user inputs
- Sanitize data
- Prevent XSS attacks
- Handle errors gracefully

### Dependencies
- Use trusted packages
- Keep dependencies updated
- Monitor for vulnerabilities
- Document security considerations
