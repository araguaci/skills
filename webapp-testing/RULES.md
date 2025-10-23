# CURSOR Rules for Webapp Testing Skill

## Overview
This skill provides a toolkit for interacting with and testing local web applications using Playwright. It supports verifying frontend functionality, debugging UI behavior, capturing browser screenshots, and viewing browser logs.

## Decision Tree Rules

### Static HTML vs Dynamic Webapp
**Static HTML Path:**
- Read HTML file directly to identify selectors
- Success → Write Playwright script using selectors
- Fails/Incomplete → Treat as dynamic (below)

**Dynamic Webapp Path:**
- Is server already running?
  - No → Run: `python scripts/with_server.py --help`
  - Yes → Reconnaissance-then-action pattern

### Reconnaissance-Then-Action Pattern
**MANDATORY Steps:**
1. Navigate and wait for networkidle
2. Take screenshot or inspect DOM
3. Identify selectors from rendered state
4. Execute actions with discovered selectors

## Server Management Rules

### Using with_server.py
**ALWAYS run `--help` first** to see usage. DO NOT read source until trying script first.

**Single Server:**
```bash
python scripts/with_server.py --server "npm run dev" --port 5173 -- python your_automation.py
```

**Multiple Servers:**
```bash
python scripts/with_server.py \
  --server "cd backend && python server.py" --port 3000 \
  --server "cd frontend && npm run dev" --port 5173 \
  -- python your_automation.py
```

### Server Lifecycle Management
**Features:**
- Manages server lifecycle automatically
- Supports multiple servers
- Handles startup and shutdown
- Provides ready-to-use automation environment

## Playwright Implementation Rules

### Basic Setup
**MANDATORY Structure:**
```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(headless=True)  # Always headless
    page = browser.new_page()
    page.goto('http://localhost:5173')  # Server already running
    page.wait_for_load_state('networkidle')  # CRITICAL: Wait for JS
    # ... automation logic
    browser.close()
```

### Critical Requirements
**ALWAYS include:**
- `page.wait_for_load_state('networkidle')` before inspection
- Headless mode for automation
- Proper browser cleanup
- Wait for JavaScript execution

## Reconnaissance Rules

### DOM Inspection
**Required Steps:**
```python
# Inspect rendered DOM
page.screenshot(path='/tmp/inspect.png', full_page=True)
content = page.content()
page.locator('button').all()
```

### Selector Identification
**Process:**
1. Take screenshot for visual reference
2. Inspect DOM content
3. Identify available elements
4. Use discovered selectors for actions

### Action Execution
**Implementation:**
- Use discovered selectors
- Execute actions systematically
- Verify results
- Handle errors gracefully

## Common Pitfall Rules

### Critical Error Prevention
**❌ DON'T:**
- Inspect DOM before waiting for networkidle on dynamic apps
- Skip networkidle wait
- Use headless=False for automation
- Forget to close browser

**✅ DO:**
- Always wait for `page.wait_for_load_state('networkidle')`
- Use headless=True for automation
- Close browser when done
- Wait for JavaScript execution

## Best Practices Rules

### Script Usage
**Guidelines:**
- Use bundled scripts as black boxes
- Consider whether scripts can help before custom solutions
- Use `--help` to see usage
- Invoke directly without reading source

### Playwright Best Practices
**Requirements:**
- Use `sync_playwright()` for synchronous scripts
- Always close browser when done
- Use descriptive selectors: `text=`, `role=`, CSS selectors, or IDs
- Add appropriate waits: `page.wait_for_selector()` or `page.wait_for_timeout()`

### Automation Patterns
**Common Approaches:**
- Element discovery and interaction
- Form filling and submission
- Navigation and page transitions
- Screenshot capture for verification

## Example Usage Rules

### Element Discovery
**Pattern:**
```python
# Discovering buttons, links, and inputs
buttons = page.locator('button').all()
links = page.locator('a').all()
inputs = page.locator('input').all()
```

### Static HTML Automation
**Usage:**
```python
# Using file:// URLs for local HTML
page.goto('file:///path/to/local/file.html')
```

### Console Logging
**Implementation:**
```python
# Capturing console logs during automation
page.on('console', lambda msg: print(f'Console: {msg.text}'))
```

## Error Prevention Rules

### Common Pitfalls
- ❌ Not waiting for networkidle
- ❌ Using headless=False
- ❌ Not closing browser
- ❌ Skipping JavaScript wait
- ❌ Reading script source unnecessarily

### Best Practices
- ✅ Always wait for networkidle
- ✅ Use headless=True
- ✅ Close browser properly
- ✅ Wait for JavaScript execution
- ✅ Use scripts as black boxes

## Documentation Rules

### Code Documentation
- Document automation patterns
- Explain selector strategies
- Include error handling
- Note common pitfalls

### User Instructions
- Clear setup instructions
- Common usage patterns
- Troubleshooting guides
- Best practices

## Maintenance Rules

### Updates
- Keep Playwright current
- Update automation patterns
- Maintain compatibility
- Test with new versions

### Extensions
- Add new automation patterns
- Expand testing capabilities
- Improve error handling
- Enhance debugging tools

## Security Rules

### Code Safety
- Validate inputs
- Handle errors gracefully
- Prevent resource leaks
- Ensure proper cleanup

### Testing Safety
- Use isolated environments
- Clean up after tests
- Handle sensitive data
- Follow security best practices
