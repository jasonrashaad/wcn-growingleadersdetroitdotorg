# What Comes Next? LLC - Showcase Page Aesthetic Guide

## Overview
This guide provides complete specifications for creating professional showcase pages in the WCN house style. Use this document to replicate the interactive, bold aesthetic demonstrated in our coming soon page.

## Design Philosophy
- **Bold & Interactive**: Prominent visual elements with smooth animations
- **Professional Minimalism**: Clean layouts with purposeful visual hierarchy  
- **Brand Consistency**: Strict adherence to WCN color palette and typography
- **Single-File Simplicity**: Self-contained HTML files for easy deployment

## Color Palette

### Primary Colors
```css
:root {
  --wcn-primary: #216869;   /* Deep green - primary brand color */
  --wcn-accent1: #49a078;   /* Mid green - secondary accents */
  --wcn-accent2: #9cc5a1;   /* Light green - subtle highlights */
  --wcn-text: #dce1de;      /* Light gray - primary text on dark backgrounds */
  --wcn-black: #000000;     /* Pure black - deep backgrounds */
}
```

### Usage Guidelines
- **Primary**: CTAs, focus states, main branding elements
- **Accent1**: Hover states, secondary buttons, gradient endpoints
- **Accent2**: Subtle accents, floating elements, gradient text
- **Text**: All text on dark backgrounds
- **Black**: Background overlays, transparency layers

## Typography System

### Font Stack
```css
font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
```

### Hierarchy
- **Main Heading**: `clamp(2.5rem, 8vw, 4rem)` with gradient text effect
- **Subtitle**: `clamp(1.2rem, 4vw, 1.5rem)` in wcn-text color
- **By-line**: `clamp(1rem, 3vw, 1.2rem)` in wcn-accent2 color
- **Button Text**: `1.1rem` with 600 font-weight

### Gradient Text Effect
```css
.gradient-text {
  background: linear-gradient(45deg, var(--wcn-text), var(--wcn-accent2));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

## Layout Structure

### Responsive Grid
- **Desktop**: 2-column grid (logo | content)
- **Mobile**: Single column, stacked vertically
- **Container**: Max-width 1200px, centered with padding

### Logo Section
- **Dimensions**: 200px × 200px (150px on mobile)
- **Container**: Circular with glassmorphism background
- **Animation**: Floating effect with glow
- **File**: 512×512px PNG with transparent background

### Content Section  
- **Hierarchy**: Main heading ’ subtitle ’ by-line ’ CTA
- **Spacing**: Progressive margins (1.5rem ’ 2rem ’ 3rem)
- **Animation**: Staggered fade-in-up effects

## Background System

### Main Gradient
```css
background: linear-gradient(135deg, var(--wcn-primary) 0%, var(--wcn-accent1) 100%);
```

### Watermark Implementation
```css
.watermark-background {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}

.watermark-logo {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  transform: rotate(12deg) scale(1.5);
  opacity: 0.05;
  mix-blend-mode: soft-light;
  background-image: url('logo.png');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}
```

## Animation System

### Core Keyframes
```css
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

@keyframes glow {
  0%, 100% { box-shadow: 0 0 20px rgba(33, 104, 105, 0.3); }
  50% { box-shadow: 0 0 30px rgba(33, 104, 105, 0.5); }
}
```

### Animation Timing
- **Content Fade-in**: 0.8s ease-out with 0.2s stagger between elements
- **Logo Float**: 3s ease-in-out infinite
- **Glow Effect**: 2s ease-in-out infinite
- **Hover Transitions**: 0.3s ease

## Interactive Elements

### CTA Button Structure
```css
.cta-button {
  position: relative;
  display: inline-block;
  text-decoration: none;
  overflow: hidden;
  border-radius: 50px;
  transition: all 0.3s ease;
}

.cta-button::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(45deg, var(--wcn-accent2), var(--wcn-accent1));
  border-radius: 50px;
  opacity: 0.75;
  transition: opacity 0.3s ease;
}

.cta-content {
  position: relative;
  background: rgba(0, 0, 0, 0.4);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(220, 225, 222, 0.2);
  padding: 1rem 2rem;
  border-radius: 50px;
  color: var(--wcn-text);
  font-size: 1.1rem;
  font-weight: 600;
}
```

### Hover Effects
- **Scale**: `transform: scale(1.05)` on logo hover
- **Lift**: `transform: translateY(-2px)` on button hover  
- **Glow**: Enhanced box-shadow on interactive elements
- **Border**: Opacity increase on border colors

## Glassmorphism Effects

### Standard Glass Card
```css
.glass-element {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(220, 225, 222, 0.2);
  border-radius: 20px;
}
```

### Glass with Hover
```css
.glass-interactive:hover {
  background: rgba(255, 255, 255, 0.15);
  border-color: rgba(220, 225, 222, 0.4);
}
```

## Floating Elements

### Implementation
```css
.floating-element {
  position: absolute;
  width: 6px;
  height: 6px;
  background: var(--wcn-accent2);
  border-radius: 50%;
  opacity: 0.6;
  animation: float 4s ease-in-out infinite;
}
```

### Positioning Strategy
- 4 elements maximum per page
- Distributed across quadrants
- Staggered animation delays (0s, 1s, 2s, 3s)
- Avoid content overlap areas

## Accessibility Standards

### Focus States
```css
.interactive-element:focus-visible {
  outline: 3px solid var(--wcn-accent2);
  outline-offset: 4px;
}
```

### Requirements
- Semantic HTML structure with proper heading hierarchy
- Alt text for all images
- Sufficient color contrast (AAA standard)
- Keyboard navigation support
- Screen reader compatibility

## Implementation Checklist

### Required Assets
- [ ] Logo file: 512×512px PNG with transparent background named `logo.png`
- [ ] Single HTML file with embedded CSS (no external dependencies)

### Core Elements
- [ ] Watermark background with company logo
- [ ] WCN gradient background (primary ’ accent1)
- [ ] Responsive grid layout (2-col desktop, 1-col mobile)
- [ ] Floating logo with glassmorphism treatment
- [ ] Gradient text effects on main heading
- [ ] Interactive CTA button with hover effects
- [ ] Floating ambient elements (4 max)
- [ ] Staggered fade-in animations

### Content Template
- [ ] Main heading: Customizable primary message
- [ ] Subtitle: Supporting description
- [ ] By-line: "by What Comes Next?" (standard)
- [ ] CTA: Link to whatcomesnextllc.ai or custom destination

### Technical Requirements
- [ ] Mobile-responsive design (breakpoint at 768px)
- [ ] CSS custom properties for easy color customization
- [ ] Embedded fonts (system font stack)
- [ ] Optimized animations (transform/opacity only)
- [ ] Accessibility compliance (WCAG AA minimum)

## Customization Variables

### Quick Color Changes
Update these CSS custom properties to rebrand:
```css
:root {
  --wcn-primary: #[HEX];    /* Main brand color */
  --wcn-accent1: #[HEX];    /* Secondary brand color */
  --wcn-accent2: #[HEX];    /* Tertiary accent */
  --wcn-text: #[HEX];       /* Light text color */
}
```

### Content Customization Points
1. **Page Title**: Update `<title>` tag
2. **Main Heading**: Customize message
3. **Subtitle**: Update supporting text
4. **CTA Text**: Change button label
5. **CTA Link**: Update destination URL
6. **Logo**: Replace `logo.png` with client asset

## Performance Notes

### Optimization Techniques
- Single file deployment (no external requests)
- CSS-only animations (no JavaScript)
- System font stack (no web font loading)
- Optimized image loading with proper sizing
- Hardware-accelerated transforms

### File Size Target
- Complete HTML file: <50KB
- Logo PNG: <100KB
- Total page weight: <150KB

## Browser Support
- **Modern Browsers**: Full feature support
- **Gradient Fallbacks**: Solid color backgrounds
- **Animation Fallbacks**: Static states with hover effects
- **Backdrop-filter**: Graceful degradation to solid backgrounds

---

*This guide ensures consistent, professional showcase pages that reflect What Comes Next? LLC's brand standards and technical excellence.*