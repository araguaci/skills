# CURSOR Rules for Template Skill

## Overview
This skill serves as a basic template to use as a starting point for new skills. It provides the minimal structure required for a skill and demonstrates the basic format.

## Template Structure Rules

### Minimal Required Structure
**MANDATORY Files:**
- `SKILL.md` (required) with YAML frontmatter and Markdown instructions

**Optional Files:**
- `LICENSE.txt` (recommended)
- `scripts/` directory (if needed)
- `references/` directory (if needed)
- `assets/` directory (if needed)

### YAML Frontmatter Rules
**Required Fields:**
- `name` - Unique identifier in hyphen-case
- `description` - Complete description of what skill does and when to use it

**Optional Fields:**
- `license` - License applied to the skill
- `allowed-tools` - List of pre-approved tools (Claude Code only)
- `metadata` - Map from string keys to string values

### Markdown Body Rules
**Content Requirements:**
- No restrictions on Markdown body
- Focus on information beneficial to Claude
- Include procedural knowledge and domain-specific details
- Reference bundled resources appropriately

## Template Usage Rules

### When to Use This Template
**ALWAYS use for:**
- Creating new skills from scratch
- Understanding skill structure
- Learning skill development patterns
- Starting skill development process

### Template Customization
**Required Changes:**
- Update `name` field to match skill purpose
- Update `description` field with specific functionality
- Replace template content with actual skill content
- Add necessary resources (scripts, references, assets)

### Template Structure
**Basic Format:**
```yaml
---
name: template-skill
description: Replace with description of the skill and when Claude should use it.
---

# Insert instructions below
```

## Skill Development Rules

### Using Template as Starting Point
**Process:**
1. Copy template structure
2. Update YAML frontmatter
3. Replace template content
4. Add necessary resources
5. Test and validate

### Customization Guidelines
**Required Updates:**
- Change name to match skill purpose
- Update description with specific functionality
- Replace template instructions with actual content
- Add resources as needed

### Resource Organization
**Optional Additions:**
- `scripts/` - Executable code for deterministic reliability
- `references/` - Documentation loaded as needed into context
- `assets/` - Files used in output (templates, icons, fonts)

## Quality Assurance Rules

### Template Validation
**Requirements:**
- Verify YAML frontmatter format
- Check required fields present
- Validate skill naming conventions
- Ensure proper structure

### Customization Validation
**After Customization:**
- Verify all required fields updated
- Check content relevance
- Validate resource references
- Test functionality

### Template Maintenance
**Ongoing Requirements:**
- Keep template current
- Update with best practices
- Maintain simplicity
- Ensure clarity

## Error Prevention Rules

### Common Pitfalls
- ❌ Not updating name field
- ❌ Keeping template description
- ❌ Not replacing template content
- ❌ Missing required fields
- ❌ Poor structure

### Best Practices
- ✅ Always update name and description
- ✅ Replace all template content
- ✅ Add necessary resources
- ✅ Follow skill development process
- ✅ Validate before use

## Documentation Rules

### Template Documentation
- Document template usage
- Explain customization process
- Include examples
- Maintain clarity

### Skill Documentation
- Document skill-specific content
- Include usage instructions
- Provide examples
- Maintain consistency

## Maintenance Rules

### Updates
- Keep template current
- Update with best practices
- Maintain simplicity
- Ensure clarity

### Extensions
- Add new template features
- Expand customization options
- Improve documentation
- Enhance usability

## Security Rules

### Template Safety
- Validate template structure
- Check for security issues
- Ensure proper permissions
- Follow security best practices

### Customization Safety
- Validate customizations
- Check for security issues
- Ensure proper permissions
- Follow security best practices
