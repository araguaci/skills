# CURSOR Rules for Slack GIF Creator Skill

## Overview
This skill provides a toolkit for creating animated GIFs optimized for Slack, with validators for size constraints and composable animation primitives. It's designed for creating GIFs from descriptions like "make me a GIF for Slack of X doing Y".

## Slack Requirements Rules

### Message GIFs Constraints
**Size Limits:**
- Max size: ~2MB
- Optimal dimensions: 480x480
- Typical FPS: 15-20
- Color limit: 128-256
- Duration: 2-5s

### Emoji GIFs Constraints
**Strict Limits:**
- Max size: 64KB (strict limit)
- Optimal dimensions: 128x128
- Typical FPS: 10-12
- Color limit: 32-48
- Duration: 1-2s

**Emoji GIF Strategies:**
- Limit to 10-15 frames total
- Use 32-48 colors maximum
- Keep designs simple
- Avoid gradients
- Validate file size frequently

## Toolkit Structure Rules

### Three Types of Tools
1. **Validators** - Check if GIF meets Slack requirements
2. **Animation Primitives** - Composable building blocks for motion
3. **Helper Utilities** - Optional functions for common needs

**Complete creative freedom available in how tools are applied.**

## Core Validators Rules

### File Size Validation
**MANDATORY Usage:**
```python
from core.validators import check_slack_size

# Check if GIF meets size limits
passes, info = check_slack_size('emoji.gif', is_emoji=True)
# Returns: (True/False, dict with size details)
```

### Dimension Validation
**Required Checks:**
```python
from core.validators import validate_dimensions

# Check dimensions
passes, info = validate_dimensions(128, 128, is_emoji=True)
# Returns: (True/False, dict with dimension details)
```

### Complete Validation
**Comprehensive Checks:**
```python
from core.validators import validate_gif, is_slack_ready

# Run all validations
all_pass, results = validate_gif('emoji.gif', is_emoji=True)

# Or quick check
if is_slack_ready('emoji.gif', is_emoji=True):
    print("Ready to upload!")
```

## Animation Primitives Rules

### Shake Animation
**Usage Pattern:**
```python
from templates.shake import create_shake_animation

frames = create_shake_animation(
    object_type='emoji',
    object_data={'emoji': '😱', 'size': 80},
    num_frames=20,
    shake_intensity=15,
    direction='both'  # or 'horizontal', 'vertical'
)
```

### Bounce Animation
**Implementation:**
```python
from templates.bounce import create_bounce_animation

frames = create_bounce_animation(
    object_type='circle',
    object_data={'radius': 40, 'color': (255, 100, 100)},
    num_frames=30,
    bounce_height=150
)
```

### Spin/Rotate Animation
**Options:**
```python
from templates.spin import create_spin_animation, create_loading_spinner

# Clockwise spin
frames = create_spin_animation(
    object_type='emoji',
    object_data={'emoji': '🔄', 'size': 100},
    rotation_type='clockwise',
    full_rotations=2
)

# Loading spinner
frames = create_loading_spinner(spinner_type='dots')
```

### Pulse/Heartbeat Animation
**Variations:**
```python
from templates.pulse import create_pulse_animation, create_attention_pulse

# Smooth pulse
frames = create_pulse_animation(
    object_data={'emoji': '❤️', 'size': 100},
    pulse_type='smooth',
    scale_range=(0.8, 1.2)
)

# Heartbeat (double-pump)
frames = create_pulse_animation(pulse_type='heartbeat')
```

### Fade Animation
**Types:**
```python
from templates.fade import create_fade_animation, create_crossfade

# Fade in/out
frames = create_fade_animation(fade_type='in')
frames = create_fade_animation(fade_type='out')

# Crossfade between two emojis
frames = create_crossfade(
    object1_data={'emoji': '😊', 'size': 100},
    object2_data={'emoji': '😂', 'size': 100}
)
```

### Zoom Animation
**Effects:**
```python
from templates.zoom import create_zoom_animation, create_explosion_zoom

# Zoom in dramatically
frames = create_zoom_animation(
    zoom_type='in',
    scale_range=(0.1, 2.0),
    add_motion_blur=True
)

# Explosion zoom
frames = create_explosion_zoom(emoji='💥')
```

### Explode/Shatter Animation
**Variations:**
```python
from templates.explode import create_explode_animation, create_particle_burst

# Burst explosion
frames = create_explode_animation(
    explode_type='burst',
    num_pieces=25
)

# Particle burst
frames = create_particle_burst(particle_count=30)
```

### Wiggle/Jiggle Animation
**Types:**
```python
from templates.wiggle import create_wiggle_animation, create_excited_wiggle

# Jello wobble
frames = create_wiggle_animation(
    wiggle_type='jello',
    intensity=1.0,
    cycles=2
)

# Excited wiggle for emoji GIFs
frames = create_excited_wiggle(emoji='🎉')
```

### Slide Animation
**Directions:**
```python
from templates.slide import create_slide_animation, create_multi_slide

# Slide in from left with overshoot
frames = create_slide_animation(
    direction='left',
    slide_type='in',
    overshoot=True
)

# Multiple objects sliding in sequence
objects = [
    {'data': {'emoji': '🎯', 'size': 60}, 'direction': 'left', 'final_pos': (120, 240)},
    {'data': {'emoji': '🎪', 'size': 60}, 'direction': 'right', 'final_pos': (240, 240)}
]
frames = create_multi_slide(objects, stagger_delay=5)
```

### Flip Animation
**Axes:**
```python
from templates.flip import create_flip_animation, create_quick_flip

# Horizontal flip between two emojis
frames = create_flip_animation(
    object1_data={'emoji': '😊', 'size': 120},
    object2_data={'emoji': '😂', 'size': 120},
    flip_axis='horizontal'
)

# Quick flip for emoji GIFs
frames = create_quick_flip('👍', '👎')
```

### Morph/Transform Animation
**Types:**
```python
from templates.morph import create_morph_animation, create_reaction_morph

# Crossfade morph
frames = create_morph_animation(
    object1_data={'emoji': '😊', 'size': 100},
    object2_data={'emoji': '😂', 'size': 100},
    morph_type='crossfade'
)

# Spin morph (3D flip-like)
frames = create_morph_animation(morph_type='spin_morph')
```

### Move Effect Animation
**Motion Types:**
```python
from templates.move import create_move_animation

# Linear movement
frames = create_move_animation(
    object_type='emoji',
    object_data={'emoji': '🚀', 'size': 60},
    start_pos=(50, 240),
    end_pos=(430, 240),
    motion_type='linear',
    easing='ease_out'
)

# Arc movement (parabolic trajectory)
frames = create_move_animation(
    object_type='emoji',
    object_data={'emoji': '⚽', 'size': 60},
    start_pos=(50, 350),
    end_pos=(430, 350),
    motion_type='arc',
    motion_params={'arc_height': 150}
)
```

### Kaleidoscope Effect
**Applications:**
```python
from templates.kaleidoscope import apply_kaleidoscope, create_kaleidoscope_animation

# Apply to a single frame
kaleido_frame = apply_kaleidoscope(frame, segments=8)

# Or create animated kaleidoscope
frames = create_kaleidoscope_animation(
    base_frame=my_frame,
    num_frames=30,
    segments=8,
    rotation_speed=1.0
)
```

## Helper Utilities Rules

### GIF Builder (Assembly & Optimization)
**Usage:**
```python
from core.gif_builder import GIFBuilder

# Create builder with chosen settings
builder = GIFBuilder(width=480, height=480, fps=20)

# Add frames
for frame in my_frames:
    builder.add_frame(frame)

# Save with optimization
builder.save('output.gif',
             num_colors=128,
             optimize_for_emoji=False)
```

**Key Features:**
- Automatic color quantization
- Duplicate frame removal
- Size warnings for Slack limits
- Emoji mode (aggressive optimization)

### Text Rendering
**For Small GIFs:**
```python
from core.typography import draw_text_with_outline, TYPOGRAPHY_SCALE

# Text with outline (helps readability)
draw_text_with_outline(
    frame, "BONK!",
    position=(240, 100),
    font_size=TYPOGRAPHY_SCALE['h1'],  # 60px
    text_color=(255, 68, 68),
    outline_color=(0, 0, 0),
    outline_width=4,
    centered=True
)
```

### Color Management
**Professional Palettes:**
```python
from core.color_palettes import get_palette

# Get pre-made palette
palette = get_palette('vibrant')  # or 'pastel', 'dark', 'neon', 'professional'

bg_color = palette['background']
text_color = palette['primary']
accent_color = palette['accent']
```

### Visual Effects
**Impact Moments:**
```python
from core.visual_effects import ParticleSystem, create_impact_flash, create_shockwave_rings

# Particle system
particles = ParticleSystem()
particles.emit_sparkles(x=240, y=200, count=15)
particles.emit_confetti(x=240, y=200, count=20)

# Update and render each frame
particles.update()
particles.render(frame)

# Flash effect
frame = create_impact_flash(frame, position=(240, 200), radius=100)
```

### Easing Functions
**Smooth Motion:**
```python
from core.easing import interpolate

# Object falling (accelerates)
y = interpolate(start=0, end=400, t=progress, easing='ease_in')

# Object landing (decelerates)
y = interpolate(start=0, end=400, t=progress, easing='ease_out')

# Bouncing
y = interpolate(start=0, end=400, t=progress, easing='bounce_out')
```

## Optimization Strategies Rules

### Message GIFs (>2MB)
**Reduction Steps:**
1. Reduce frames (lower FPS or shorter duration)
2. Reduce colors (128 → 64 colors)
3. Reduce dimensions (480x480 → 320x320)
4. Enable duplicate frame removal

### Emoji GIFs (>64KB) - Be Aggressive
**Aggressive Optimization:**
1. Limit to 10-12 frames total
2. Use 32-40 colors maximum
3. Avoid gradients (solid colors compress better)
4. Simplify design (fewer elements)
5. Use `optimize_for_emoji=True` in save method

## Philosophy Rules

### Creative Process
**Workflow:**
1. **Understand creative vision** - What should happen? What's the mood?
2. **Design the animation** - Break into phases (anticipation, action, reaction)
3. **Apply primitives as needed** - Shake, bounce, move, effects - mix freely
4. **Validate constraints** - Check file size, especially for emoji GIFs
5. **Iterate if needed** - Reduce frames/colors if over size limits

**Goal: Creative freedom within Slack's technical constraints.**

## Error Prevention Rules

### Common Pitfalls
- ❌ Ignoring size constraints
- ❌ Poor optimization for emoji GIFs
- ❌ Not validating file size
- ❌ Using too many colors
- ❌ Creating too many frames

### Best Practices
- ✅ Always validate file size
- ✅ Use appropriate optimization
- ✅ Test with Slack constraints
- ✅ Optimize for emoji GIFs aggressively
- ✅ Validate frequently during creation

## Documentation Rules

### Code Documentation
- Document animation primitives
- Explain optimization strategies
- Include usage examples
- Note Slack constraints

### User Instructions
- Clear optimization guidelines
- Slack-specific requirements
- Creative freedom within constraints
- Technical limitations

## Maintenance Rules

### Updates
- Keep optimization strategies current
- Update Slack constraints
- Maintain compatibility
- Test with new Slack versions

### Extensions
- Add new animation primitives
- Expand optimization options
- Improve performance
- Enhance creative freedom

## Security Rules

### Code Safety
- Validate input parameters
- Handle edge cases gracefully
- Prevent memory issues
- Optimize for performance

### File Safety
- Validate file sizes
- Check format compatibility
- Handle errors gracefully
- Ensure proper cleanup
