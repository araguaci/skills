# CURSOR Rules for MCP Builder Skill

## Overview
This skill provides a guide for creating high-quality MCP (Model Context Protocol) servers that enable LLMs to interact with external services through well-designed tools. It covers both Python (FastMCP) and Node/TypeScript (MCP SDK) implementations.

## Phase 1: Deep Research and Planning Rules

### Agent-Centric Design Principles
**MANDATORY Understanding:**
- Build for workflows, not just API endpoints
- Optimize for limited context
- Design actionable error messages
- Follow natural task subdivisions
- Use evaluation-driven development

### MCP Protocol Documentation
**REQUIRED Reading:**
- Fetch: `https://modelcontextprotocol.io/llms-full.txt`
- Study complete MCP specification
- Understand protocol guidelines
- Review best practices

### Framework Documentation
**Load Required Files:**
- MCP Best Practices: `./reference/mcp_best_practices.md`
- Python SDK: Fetch from GitHub README
- TypeScript SDK: Fetch from GitHub README
- Language-specific guides as needed

### API Documentation Study
**Exhaustive Research Required:**
- Official API reference documentation
- Authentication and authorization requirements
- Rate limiting and pagination patterns
- Error responses and status codes
- Available endpoints and parameters
- Data models and schemas

### Implementation Planning
**Comprehensive Plan Must Include:**
- Tool selection (most valuable endpoints)
- Shared utilities and helpers
- Input/Output design (validation models, response formats)
- Error handling strategy
- Character limits and truncation strategies

## Phase 2: Implementation Rules

### Project Structure Rules
**Python Implementation:**
- Single `.py` file or organized modules
- Use MCP Python SDK for tool registration
- Define Pydantic models for input validation
- Follow async/await patterns

**Node/TypeScript Implementation:**
- Proper project structure
- Set up `package.json` and `tsconfig.json`
- Use MCP TypeScript SDK
- Define Zod schemas for input validation

### Core Infrastructure Rules
**MANDATORY First Steps:**
- Create shared utilities before implementing tools
- API request helper functions
- Error handling utilities
- Response formatting functions
- Pagination helpers
- Authentication/token management

### Tool Implementation Rules
**For Each Tool:**
- Define input schema with proper constraints
- Write comprehensive docstrings/descriptions
- Implement tool logic using shared utilities
- Add tool annotations (readOnlyHint, destructiveHint, etc.)
- Support multiple response formats
- Respect pagination parameters
- Check character limits and truncate appropriately

### Language-Specific Best Practices
**Python Requirements:**
- Using MCP Python SDK with proper tool registration
- Pydantic v2 models with `model_config`
- Type hints throughout
- Async/await for all I/O operations
- Proper imports organization
- Module-level constants

**Node/TypeScript Requirements:**
- Using `server.registerTool` properly
- Zod schemas with `.strict()`
- TypeScript strict mode enabled
- No `any` types - use proper types
- Explicit Promise<T> return types
- Build process configured

## Phase 3: Review and Refine Rules

### Code Quality Review
**MANDATORY Checks:**
- DRY Principle: No duplicated code between tools
- Composability: Shared logic extracted into functions
- Consistency: Similar operations return similar formats
- Error Handling: All external calls have error handling
- Type Safety: Full type coverage
- Documentation: Every tool has comprehensive docstrings

### Testing and Building
**CRITICAL Testing Rules:**
- MCP servers are long-running processes
- Running them directly causes process to hang indefinitely
- Use evaluation harness (recommended)
- Run server in tmux to keep outside main process
- Use timeout when testing: `timeout 5s python server.py`

**Build Requirements:**
- Python: Verify syntax with `python -m py_compile`
- Node/TypeScript: Run `npm run build` and ensure completion
- Verify dist/index.js is created
- Test with evaluation harness

### Quality Checklist
**Use Language-Specific Checklists:**
- Python: See "Quality Checklist" in Python guide
- Node/TypeScript: See "Quality Checklist" in TypeScript guide

## Phase 4: Create Evaluations Rules

### Evaluation Purpose
**Understanding Required:**
- Evaluations test whether LLMs can effectively use MCP server
- Test realistic, complex questions
- Verify tool effectiveness

### Create 10 Evaluation Questions
**Process:**
1. Tool Inspection: List available tools and understand capabilities
2. Content Exploration: Use READ-ONLY operations to explore data
3. Question Generation: Create 10 complex, realistic questions
4. Answer Verification: Solve each question yourself to verify answers

### Evaluation Requirements
**Each Question Must Be:**
- Independent: Not dependent on other questions
- Read-only: Only non-destructive operations required
- Complex: Requiring multiple tool calls and deep exploration
- Realistic: Based on real use cases humans would care about
- Verifiable: Single, clear answer that can be verified by string comparison
- Stable: Answer won't change over time

### Output Format
**XML Structure Required:**
```xml
<evaluation>
  <qa_pair>
    <question>Complex question requiring multiple tool calls</question>
    <answer>Verifiable answer</answer>
  </qa_pair>
  <!-- More qa_pairs... -->
</evaluation>
```

## Error Prevention Rules

### Common Pitfalls
- ❌ Not reading documentation completely
- ❌ Skipping evaluation creation
- ❌ Poor error handling
- ❌ Inconsistent response formats
- ❌ Missing input validation

### Best Practices
- ✅ Read all documentation thoroughly
- ✅ Create comprehensive evaluations
- ✅ Implement proper error handling
- ✅ Maintain consistent formats
- ✅ Validate all inputs

## Documentation Rules

### Reference Files
**Load as Needed:**
- MCP Best Practices
- Python Implementation Guide
- TypeScript Implementation Guide
- Evaluation Guide

### Code Documentation
- Comprehensive docstrings for all tools
- Clear parameter descriptions
- Usage examples
- Error handling documentation

## Maintenance Rules

### Updates
- Keep dependencies current
- Update protocol documentation
- Maintain compatibility
- Test with new versions

### Extensions
- Add new tools
- Expand functionality
- Improve performance
- Enhance user experience

## Security Rules

### Code Safety
- Validate all inputs
- Sanitize data
- Handle errors gracefully
- Prevent security vulnerabilities

### API Security
- Use secure authentication
- Handle rate limiting
- Protect sensitive data
- Follow security best practices
