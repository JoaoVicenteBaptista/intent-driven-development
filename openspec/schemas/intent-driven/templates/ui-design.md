## Design Tokens

### Color Palette
<!-- Define OKLCH color tokens as CSS custom properties. Reference PRODUCT.md and DESIGN.md for brand colors. List each token, its value, and usage. -->

### Typography
<!-- Font families, weights, sizes (use clamp() where appropriate), line heights. One row per style. -->

### Spacing
<!-- Spacing scale with values. Use a consistent base unit. -->

### Borders & Radii
<!-- Border radius tokens and usage. -->

### Shadows
<!-- Elevation tokens and their values. -->

---

## Layouts

<!-- For each page/route in the change, provide an ASCII diagram showing grid structure, component placement, and responsive behavior. Include breakpoint definitions. -->

### <!-- Page name -->

```
<!-- ASCII layout diagram -->
```

### Responsive Breakpoints

<!-- Table of breakpoints and how layouts adapt at each -->

---

## Components

<!-- For each reusable UI component: -->

### <!-- Component name -->

**Props**: <!-- Data it accepts -->

**Variants**: <!-- Named visual/behavioral variants -->

**States**: <!-- default, hover, focus, active, disabled, loading, empty, error -->

**Responsive behavior**: <!-- How it adapts across breakpoints -->

---

## Pages

<!-- For each page in the change, describe component composition, data flow, and all states: -->

### <!-- Page name -->

**Components**: <!-- Which components are used -->

**Data**: <!-- API endpoints or data sources -->

**States**:
- **Loading**: <!-- Loading state appearance -->
- **Empty**: <!-- When there is no data to show -->
- **Error**: <!-- When data fetch fails -->
- **Edge cases**: <!-- Long content, missing optional fields, extreme values -->

---

## Motion

<!-- Animation specifications for transitions, micro-interactions, and hover effects. Include easing curves, durations, and @media (prefers-reduced-motion: reduce) fallbacks. -->

| Element | Trigger | Animation | Duration | Easing | Reduced Motion |
|---------|---------|-----------|----------|--------|----------------|
| <!-- --> | <!-- --> | <!-- --> | <!-- --> | <!-- --> | <!-- --> |

---

## Accessibility

<!-- Focus order, keyboard navigation, ARIA labels, alt text patterns, contrast compliance target. -->
