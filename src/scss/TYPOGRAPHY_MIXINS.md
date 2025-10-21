# Typography Mixins Usage Guide

## Overview
All typography styles have been converted to SCSS mixins that can be reused across all component files. This ensures consistency and makes maintenance easier.

## Available Mixins

### Headline Mixins
- `@include sus-headline-1;` - Large headline (48px mobile, 72px desktop)
- `@include sus-headline-2;` - Medium headline (36px mobile, 55px desktop)  
- `@include sus-headline-3;` - Small headline (24px mobile, 42px desktop)
- `@include sus-headline-5;` - Extra small headline (24px mobile/desktop)

### Body Text Mixins
- `@include sus-body-big;` - Large body text (18px, weight 400)
- `@include sus-body-regular;` - Regular body text (16px, weight 400)
- `@include sus-body-big-highlight;` - Large highlighted text (18px, weight 700)
- `@include sus-body-cta-big;` - CTA button text (21px, weight 800)
- `@include sus-body-label-big;` - Large label text (18px, weight 800)

## How to Use in Component Files

### 1. Import the Typography Mixins
```scss
@use "../utils/variables" as *;
@use "../utils/typography-mixins" as *; // Add this line
```

### 2. Use Mixins in Your Selectors
```scss
.my-component__title {
  @include sus-headline-2;
  color: var(--sus-color-primary);
  text-align: center;
}

.my-component__description {
  @include sus-body-big;
  margin-bottom: 1rem;
}

.my-component__button {
  @include sus-body-cta-big;
  background-color: var(--sus-color-accent);
}
```

## Benefits

1. **Consistency**: All typography follows the same design system
2. **Maintainability**: Change typography rules in one place
3. **Mobile-First**: All mixins include responsive breakpoints
4. **Reusability**: Use the same typography across all components
5. **DRY Principle**: No duplicate typography code

## Example: Before vs After

### Before (Manual Typography)
```scss
.my-title {
  font-family: var(--sus-font-primary);
  font-size: 36px;
  font-weight: 800;
  line-height: 1;
  
  @media (min-width: $md) {
    font-size: 55px;
  }
}
```

### After (Using Mixin)
```scss
.my-title {
  @include sus-headline-2;
}
```

## Notes
- All mixins are mobile-first with desktop overrides
- Mixins include font-family, font-size, font-weight, and line-height
- You can still add additional properties like color, text-align, etc.
- The mixins are defined in `src/scss/utils/_typography-mixins.scss`
- Import the mixins file in any component that needs typography styles
