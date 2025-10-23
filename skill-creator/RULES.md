# CURSOR Rules for Skill Creator Skill

## Overview
This skill provides guidance for creating effective skills that extend Claude's capabilities with specialized knowledge, workflows, or tool integrations. It follows a structured process for skill development.

## Skill Creation Process Rules

### Step 1: Understanding the Skill with Concrete Examples
**MANDATORY**: Skip only when usage patterns are already clearly understood.

**Process:**
- Clearly understand concrete examples of how skill will be used
- Can come from direct user examples or generated examples
- Validate with user feedback
- Conclude when there's clear sense of functionality

**Questions to Ask:**
- "What functionality should the skill support?"
- "Can you give some examples of how this skill would be used?"
- "What would a user say that should trigger this skill?"

### Step 2: Planning the Reusable Skill Contents
**Analysis Required:**
- Consider how to execute on examples from scratch
- Identify scripts, references, and assets that would be helpful
- Analyze each concrete example for reusable resources

**Example Analysis:**
- PDF rotation: Same code rewritten each time → `scripts/rotate_pdf.py`
- Frontend webapp: Same boilerplate each time → `assets/hello-world/` template
- BigQuery: Re-discovering schemas each time → `references/schema.md`

### Step 3: Initializing the Skill
**MANDATORY Command:**
```bash
scripts/init_skill.py <skill-name> --path <output-directory>
```

**What the script creates:**
- ✅ Skill directory at specified path
- ✅ SKILL.md template with proper frontmatter and TODO placeholders
- ✅ Example resource directories: `scripts/`, `references/`, `assets/`
- ✅ Example files in each directory

**After initialization:**
- Customize or remove generated SKILL.md and example files
- Delete example files not needed for the skill

### Step 4: Edit the Skill
**Focus Areas:**
- Create for another instance of Claude to use
- Include information beneficial and non-obvious to Claude
- Consider procedural knowledge, domain-specific details, reusable assets

**Start with Reusable Contents:**
- Implement `scripts/`, `references/`, and `assets/` files first
- Delete example files not needed
- Update SKILL.md with complete information

**Writing Style:**
- Use **imperative/infinitive form** (verb-first instructions)
- Use objective, instructional language
- Example: "To accomplish X, do Y" rather than "You should do X"

### Step 5: Packaging a Skill
**MANDATORY Command:**
```bash
scripts/package_skill.py <path/to/skill-folder>
```

**Optional output directory:**
```bash
scripts/package_skill.py <path/to/skill-folder> ./dist
```

**What the script does:**
1. **Validate** the skill automatically
2. **Package** the skill if validation passes
3. **Create** zip file named after the skill
4. **Report** errors if validation fails

### Step 6: Iterate
**Iteration Workflow:**
1. Use the skill on real tasks
2. Notice struggles or inefficiencies
3. Identify how SKILL.md or bundled resources should be updated
4. Implement changes and test again

## Skill Structure Rules

### Required Files
**MANDATORY:**
- `SKILL.md` (required) with YAML frontmatter and Markdown instructions

**Optional:**
- `scripts/` - Executable code for deterministic reliability
- `references/` - Documentation loaded as needed into context
- `assets/` - Files used in output (templates, icons, fonts)

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

## Resource Organization Rules

### Scripts (`scripts/`)
**When to Include:**
- Same code rewritten repeatedly
- Deterministic reliability needed
- Executable without loading into context

**Benefits:**
- Token efficient
- Deterministic
- May be executed without loading into context

### References (`references/`)
**When to Include:**
- Documentation Claude should reference while working
- Database schemas, API documentation, domain knowledge
- Company policies, detailed workflow guides

**Best Practices:**
- Keep SKILL.md lean
- Load only when Claude determines needed
- If files are large (>10k words), include grep search patterns
- Avoid duplication between SKILL.md and references

### Assets (`assets/`)
**When to Include:**
- Files used within output Claude produces
- Templates, images, icons, boilerplate code
- Fonts, sample documents that get copied or modified

**Benefits:**
- Separate output resources from documentation
- Enable Claude to use files without loading into context

## Progressive Disclosure Rules

### Three-Level Loading System
1. **Metadata (name + description)** - Always in context (~100 words)
2. **SKILL.md body** - When skill triggers (<5k words)
3. **Bundled resources** - As needed by Claude (Unlimited*)

*Unlimited because scripts can be executed without reading into context window.

## Quality Assurance Rules

### Validation Requirements
**Automatic Checks:**
- YAML frontmatter format and required fields
- Skill naming conventions and directory structure
- Description completeness and quality
- File organization and resource references

### Packaging Validation
**Before Packaging:**
- Verify all required fields present
- Check file organization
- Validate resource references
- Test functionality

### Post-Packaging
**After Packaging:**
- Test packaged skill
- Verify all files included
- Check functionality
- Validate distribution

## Error Prevention Rules

### Common Pitfalls
- ❌ Skipping concrete examples step
- ❌ Not planning reusable contents
- ❌ Poor YAML frontmatter
- ❌ Inconsistent writing style
- ❌ Missing validation

### Best Practices
- ✅ Always start with concrete examples
- ✅ Plan reusable resources thoroughly
- ✅ Use proper YAML frontmatter
- ✅ Follow imperative writing style
- ✅ Validate before packaging

## Documentation Rules

### Skill Documentation
- Document all bundled resources
- Explain usage patterns
- Include examples
- Maintain consistency

### Process Documentation
- Document creation process
- Include best practices
- Provide troubleshooting
- Maintain guidelines

## Maintenance Rules

### Updates
- Keep process current
- Update best practices
- Maintain consistency
- Test with new skills

### Extensions
- Add new resource types
- Expand validation
- Improve packaging
- Enhance guidelines

## Security Rules

### Code Safety
- Validate all inputs
- Sanitize data
- Handle errors gracefully
- Prevent security vulnerabilities

### Skill Safety
- Validate skill contents
- Check for malicious code
- Ensure proper permissions
- Follow security best practices
