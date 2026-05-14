# Design System Inspired by Linear

## 1. Visual Theme & Atmosphere

Linear's design system embodies a minimalist, sophisticated approach to product development interfaces. The visual language prioritizes clarity and precision with a dark-mode-first aesthetic that reduces cognitive load during intense focus work. Deep blacks and near-blacks form the foundation, accented by cool grays and a subtle indigo accent that provides depth without distraction. The system is intentionally sparse and purposeful—every element serves function, creating an environment where AI-assisted workflows and human collaboration can coexist seamlessly. The typography is clean and modern, using variable-weight Inter for flexibility across scales, while monospace Berkeley Mono grounds technical content. Generous whitespace and restrained color usage reflect a workspace designed for sustained concentration and precision.

**Key Characteristics**
- Dark-mode dominant with carefully calibrated neutral scale
- Minimalist, distraction-free interface aesthetic
- Cool, professional color palette emphasizing clarity
- Precise typographic hierarchy supporting AI workflows
- Intentional use of micro-interactions and subtle elevation
- High contrast between interactive and passive elements
- Designed for teams and autonomous agents working in parallel

## 2. Color Palette & Roles

### Primary
- **Brand Primary** (`#5E6AD2`): Primary interactive accent, used sparingly for key CTAs and status indicators in AI-driven workflows
- **Brand Accent Light** (`#828FFF`): Secondary accent for hover states and supporting interactive elements

### Interactive
- **Button Default** (`#8A8F98`): Neutral button text for secondary actions
- **CTA Background** (`#E5E5E6`): Light neutral background for prominent call-to-action buttons
- **Link Active** (`#5E6AD2`): Primary link color and interactive focus state

### Neutral Scale
- **Surface Darkest** (`#08090A`): Deepest background layer for modals and overlays
- **Surface Dark** (`#0F1011`): Primary dark surface for content containers
- **Surface Base** (`#141516`): Secondary dark surface layer
- **Surface Gray Mid** (`#23252A`): Tertiary neutral for dividers and subtle backgrounds
- **Surface Gray** (`#383B3F`): Lighter gray for secondary text and borders
- **Surface Text Secondary** (`#62666D`): Secondary text color, used for supporting copy (most frequently used)
- **Surface Text Tertiary** (`#8A8F98`): Tertiary text for disabled or muted states
- **Surface Border Light** (`#B4BCD0`): Light border for subtle separation in dark mode

### Surface & Borders
- **Surface Light** (`#F7F8F8`): Primary light background for cards and containers (425 uses)
- **White** (`#FFFFFF`): Pure white for maximum contrast and primary text in light contexts (221 uses)
- **Border Default** (`#D0D6E0`): Primary border color for light surfaces (112 uses)
- **Border Subtle** (`#E2E4E7`): Subtle border for reduced visual weight
- **Border Lighter** (`#E5E5E6`): Lightest border for minimal separation

## 3. Typography Rules

### Font Family
**Primary:** Inter Variable (400, 510, 590 weights) with fallback: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`

**Secondary:** Berkeley Mono (400 weight) with fallback: `"SF Mono", Monaco, "Cascadia Code", monospace`

### Hierarchy

| Role | Font | Size | Weight | Line Height | Letter Spacing | Notes |
|------|------|------|--------|-------------|-----------------|-------|
| Display 1 | Inter Variable | 64px | 510 | 64px | 0px | Hero headlines, main page titles |
| Display 2 | Inter Variable | 48px | 510 | 48px | 0px | Section headlines, major headings |
| Heading 3 | Inter Variable | 20px | 590 | 26.6px | 0px | Card titles, subsection heads |
| Heading 4 | Inter Variable | 16px | 590 | 24px | 0px | Form labels, emphasis text |
| Body | Inter Variable | 15px | 400 | 24px | 0px | Primary body copy, descriptions |
| Body Span | Inter Variable | 16px | 400 | 24px | 0px | Secondary body, content blocks |
| Link | Inter Variable | 14px | 510 | 21px | 0px | Navigation links, inline links |
| Button | Inter Variable | 13px | 400 | 19.5px | 0px | Button labels, small actions |
| Code Small | Berkeley Mono | 12.25px | 400 | 15.925px | 0px | Inline code, technical references |
| Code | Berkeley Mono | 14px | 400 | 24px | 0px | Code blocks, technical content |

### Principles
- Use weight `510` for semi-bold emphasis and navigational elements
- Weight `590` reserved for small, scannable headings and form labels
- Regular weight `400` for all body content and accessibility
- Maintain 24px line height for body content to ensure readability in dark mode
- Monospace reserved exclusively for code, identifiers, and technical variables
- Leading scale maintains 1.0–1.6× multiplier from base size for visual rhythm
- Letter spacing remains neutral (0px) across all sizes for modern, clean appearance

## 4. Component Stylings

### Buttons

#### Primary Button
- **Background:** `#E5E5E6`
- **Text Color:** `#08090A`
- **Font Size:** `13px`
- **Font Weight:** `510`
- **Padding:** `0px 12px`
- **Height:** `32px`
- **Border Radius:** `9999px`
- **Border:** `1px solid #E5E5E6`
- **Box Shadow:** `rgba(0, 0, 0, 0) 0px 8px 2px 0px, rgba(0, 0, 0, 0.01) 0px 5px 2px 0px, rgba(0, 0, 0, 0.04) 0px 3px 2px 0px, rgba(0, 0, 0, 0.07) 0px 1px 1px 0px, rgba(0, 0, 0, 0.08) 0px 0px 1px 0px`
- **Line Height:** `19.5px`
- **Hover State:** Increase shadow intensity and darken background slightly

#### Secondary Button (Ghost)
- **Background:** `transparent`
- **Text Color:** `#8A8F98`
- **Font Size:** `13px`
- **Font Weight:** `400`
- **Padding:** `0px 12px`
- **Height:** `32px`
- **Border Radius:** `9999px`
- **Border:** `0px none`
- **Box Shadow:** `none`
- **Line Height:** `19.5px`
- **Hover State:** Text color shifts to `#B4BCD0`

#### Navigation Button
- **Background:** `transparent`
- **Text Color:** `#F7F8F8`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `0px`
- **Height:** `72px`
- **Border Radius:** `0px`
- **Border:** `0px none`
- **Box Shadow:** `none`
- **Line Height:** `24px`
- **Hover State:** Text color transitions to `#B4BCD0`

### Cards & Containers

#### Dark Card
- **Background:** `#0F1011`
- **Text Color:** `#F7F8F8`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `0px 24px 28px 24px`
- **Border Radius:** `8px`
- **Border:** `1px solid rgba(255, 255, 255, 0.05)`
- **Box Shadow:** `none`
- **Min Height:** `440px`
- **Max Width:** `328px`
- **Line Height:** `24px`

#### Navigation Container
- **Background:** `transparent`
- **Text Color:** `#F7F8F8`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `0px`
- **Height:** `72px`
- **Width:** `100%`
- **Border Radius:** `0px`
- **Border:** `0px none`
- **Box Shadow:** `rgba(0, 0, 0, 0.4) 0px 1px 0px 0px`
- **Line Height:** `24px`

### Inputs & Forms

#### Text Input Dark
- **Background:** `rgba(255, 255, 255, 0.02)`
- **Text Color:** `#D0D6E0`
- **Font Size:** `13.3333px`
- **Font Weight:** `400`
- **Padding:** `12px 14px`
- **Border Radius:** `6px`
- **Border:** `1px solid rgba(255, 255, 255, 0.08)`
- **Box Shadow:** `rgba(0, 0, 0, 0.2) 0px 0px 0px 1px`
- **Height:** `32px` (minimum)
- **Line Height:** `normal`
- **Focus State:** Border color to `#5E6AD2`, increase shadow

#### Search Input
- **Background:** `transparent`
- **Text Color:** `#F7F8F8`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Padding:** `1px 32px`
- **Border Radius:** `0px`
- **Border:** `0px none`
- **Box Shadow:** `none`
- **Height:** `64px`
- **Line Height:** `normal`
- **Placeholder Color:** `#62666D`

#### Code Input
- **Background:** `transparent`
- **Text Color:** `#000000` (transparent rendering for code display)
- **Font Size:** `14px`
- **Font Weight:** `400`
- **Font Family:** `Berkeley Mono`
- **Padding:** `0px 32px 0px 56px`
- **Border Radius:** `0px`
- **Border:** `0px none`
- **Box Shadow:** `none`
- **Min Height:** `432px`
- **Line Height:** `24px`

### Navigation

#### Header Navigation
- **Background:** `transparent`
- **Text Color:** `#F7F8F8`
- **Font Size:** `16px`
- **Font Weight:** `400`
- **Height:** `72px`
- **Display:** `flex`
- **Align Items:** `center`
- **Box Shadow:** `rgba(0, 0, 0, 0.4) 0px 1px 0px 0px`
- **Padding:** `0px 24px`

#### Navigation Link
- **Background:** `transparent`
- **Text Color:** `#F7F8F8`
- **Font Size:** `14px`
- **Font Weight:** `400`
- **Padding:** `0px 8px`
- **Border Radius:** `6px`
- **Height:** `32px`
- **Line Height:** `24px`
- **Hover State:** Background `rgba(255, 255, 255, 0.05)`, text `#B4BCD0`

### Links

#### Primary Link / CTA Link
- **Background:** `#5E6AD2`
- **Text Color:** `#FFFFFF`
- **Font Size:** `14px`
- **Font Weight:** `510`
- **Padding:** `0px 16px`
- **Border Radius:** `0px`
- **Height:** `32px`
- **Line Height:** `21px`
- **Hover State:** Background to `#6B7BFF`

#### Secondary Link
- **Background:** `transparent`
- **Text Color:** `#8A8F98`
- **Font Size:** `13px`
- **Font Weight:** `400`
- **Padding:** `0px 12px`
- **Border Radius:** `9999px`
- **Height:** `32px`
- **Line Height:** `19.5px`
- **Hover State:** Text color to `#B4BCD0`

## 5. Layout Principles

### Spacing System

**Base Unit:** `4px`

**Scale:** All spacing values follow a 4px increment system:
- `4px` – Minimal gap, icon spacing
- `8px` – Compact spacing, small gaps between inline elements
- `12px` – Small spacing, input padding
- `16px` – Standard padding for interactive elements and containers
- `20px` – Small margin between sections
- `24px` – Standard margi