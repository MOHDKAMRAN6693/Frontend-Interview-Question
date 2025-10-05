# CSS/SCSS Interview Questions

## 🎯 Difficulty Levels
- **🟢 Beginner**: Basic CSS properties and selectors
- **🟡 Intermediate**: Layout, positioning, and responsive design
- **🔴 Advanced**: CSS Grid, Flexbox, animations, and optimization
- **🟣 Expert**: Performance, architecture, and advanced techniques

## 📋 Questions

### 🟢 Beginner Level

#### 1. What is CSS and how do you include it in HTML?
**Answer:**
CSS (Cascading Style Sheets) is a stylesheet language used to describe the presentation of HTML documents. There are three ways to include CSS:

```html
<!-- 1. Inline CSS -->
<div style="color: red; font-size: 16px;">Inline styling</div>

<!-- 2. Internal CSS -->
<head>
    <style>
        .internal { color: blue; }
    </style>
</head>

<!-- 3. External CSS -->
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

**Key Concepts:**
- CSS syntax
- Selectors
- Properties and values
- Cascade and inheritance

#### 2. What are CSS selectors and what are the different types?
**Answer:**
CSS selectors are patterns used to select HTML elements for styling:

```css
/* Element selector */
p { color: blue; }

/* Class selector */
.highlight { background-color: yellow; }

/* ID selector */
#header { font-size: 24px; }

/* Attribute selector */
input[type="text"] { border: 1px solid #ccc; }

/* Descendant selector */
div p { margin: 10px; }

/* Child selector */
div > p { color: red; }

/* Adjacent sibling selector */
h1 + p { font-weight: bold; }

/* General sibling selector */
h1 ~ p { color: green; }

/* Pseudo-class selector */
a:hover { color: red; }

/* Pseudo-element selector */
p::before { content: "→ "; }
```

**Key Concepts:**
- Selector specificity
- CSS cascade
- Pseudo-classes and pseudo-elements
- Combinators

#### 3. What is the CSS box model?
**Answer:**
The CSS box model describes how elements are rendered with content, padding, border, and margin:

```css
.box {
    width: 200px;           /* Content width */
    height: 100px;          /* Content height */
    padding: 20px;          /* Space inside the border */
    border: 2px solid black; /* Border around padding */
    margin: 10px;           /* Space outside the border */
    box-sizing: border-box; /* Include padding and border in width/height */
}
```

**Key Concepts:**
- Content, padding, border, margin
- Box-sizing property
- Total element size calculation
- Box model visualization

#### 4. What is the difference between display: block, inline, and inline-block?
**Answer:**
These display values control how elements behave in the document flow:

```css
/* Block elements */
.block {
    display: block;
    width: 100%;           /* Takes full width */
    height: 50px;          /* Can set height */
    margin: 10px 0;        /* Vertical margins work */
}

/* Inline elements */
.inline {
    display: inline;
    width: 100px;          /* Width/height ignored */
    height: 50px;          /* Width/height ignored */
    margin: 10px 0;        /* Vertical margins don't work */
}

/* Inline-block elements */
.inline-block {
    display: inline-block;
    width: 100px;          /* Can set width/height */
    height: 50px;          /* Can set width/height */
    margin: 10px 0;        /* All margins work */
}
```

**Key Concepts:**
- Document flow
- Element behavior
- Width and height properties
- Margin collapsing

#### 5. How do you center elements in CSS?
**Answer:**
Multiple methods for centering elements:

```css
/* Method 1: Text-align for inline elements */
.center-text {
    text-align: center;
}

/* Method 2: Margin auto for block elements */
.center-block {
    width: 200px;
    margin: 0 auto;
}

/* Method 3: Flexbox */
.flex-center {
    display: flex;
    justify-content: center;  /* Horizontal centering */
    align-items: center;      /* Vertical centering */
    height: 100vh;
}

/* Method 4: CSS Grid */
.grid-center {
    display: grid;
    place-items: center;
    height: 100vh;
}

/* Method 5: Absolute positioning */
.absolute-center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

**Key Concepts:**
- Different centering techniques
- Flexbox and Grid
- Absolute positioning
- Transform property

### 🟡 Intermediate Level

#### 6. What are CSS positioning properties?
**Answer:**
CSS positioning controls how elements are positioned:

```css
/* Static positioning (default) */
.static {
    position: static;
}

/* Relative positioning */
.relative {
    position: relative;
    top: 10px;      /* Moves 10px down from normal position */
    left: 20px;     /* Moves 20px right from normal position */
}

/* Absolute positioning */
.absolute {
    position: absolute;
    top: 50px;      /* 50px from top of nearest positioned ancestor */
    right: 30px;    /* 30px from right of nearest positioned ancestor */
}

/* Fixed positioning */
.fixed {
    position: fixed;
    top: 0;         /* Always 0px from top of viewport */
    right: 0;       /* Always 0px from right of viewport */
    z-index: 1000;  /* Stays on top of other elements */
}

/* Sticky positioning */
.sticky {
    position: sticky;
    top: 0;         /* Sticks to top when scrolling */
    background: white;
}
```

**Key Concepts:**
- Positioning context
- Z-index stacking
- Viewport vs document positioning
- Sticky behavior

#### 7. How do you create responsive layouts with CSS Grid and Flexbox?
**Answer:**
Advanced layout techniques:

```css
/* CSS Grid Layout */
.grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    grid-template-rows: auto 1fr auto;
    grid-template-areas: 
        "header header"
        "sidebar main"
        "footer footer";
    gap: 20px;
    min-height: 100vh;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }

/* Responsive Grid */
@media (max-width: 768px) {
    .grid-container {
        grid-template-columns: 1fr;
        grid-template-areas: 
            "header"
            "main"
            "sidebar"
            "footer";
    }
}

/* Flexbox Layout */
.flex-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

.flex-header {
    flex: 0 0 auto;
}

.flex-main {
    flex: 1 0 auto;
    display: flex;
}

.flex-sidebar {
    flex: 0 0 250px;
}

.flex-content {
    flex: 1 1 auto;
}

.flex-footer {
    flex: 0 0 auto;
}

/* Responsive Flexbox */
@media (max-width: 768px) {
    .flex-main {
        flex-direction: column;
    }
    
    .flex-sidebar {
        flex: 0 0 auto;
    }
}
```

**Key Concepts:**
- Grid vs Flexbox
- Responsive design
- Layout patterns
- Media queries

#### 8. How do you create CSS animations and transitions?
**Answer:**
Animation and transition techniques:

```css
/* CSS Transitions */
.transition-example {
    background-color: blue;
    transition: all 0.3s ease-in-out;
    transform: scale(1);
}

.transition-example:hover {
    background-color: red;
    transform: scale(1.1);
}

/* CSS Animations */
@keyframes slideIn {
    0% {
        transform: translateX(-100%);
        opacity: 0;
    }
    50% {
        opacity: 0.5;
    }
    100% {
        transform: translateX(0);
        opacity: 1;
    }
}

.animate-slide {
    animation: slideIn 1s ease-out;
}

/* Advanced Animation */
@keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
    }
    40% {
        transform: translateY(-30px);
    }
    60% {
        transform: translateY(-15px);
    }
}

.bounce-animation {
    animation: bounce 2s infinite;
}

/* Performance-optimized animations */
.optimized-animation {
    will-change: transform, opacity;
    transform: translateZ(0); /* Force hardware acceleration */
}

.optimized-animation:hover {
    transform: translateZ(0) scale(1.05);
}
```

**Key Concepts:**
- Animation performance
- Keyframes
- Transform properties
- Hardware acceleration

#### 9. How do you implement CSS custom properties (variables)?
**Answer:**
Modern CSS features for maintainable code:

```css
:root {
    /* CSS Custom Properties */
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --font-size-base: 16px;
    --spacing-unit: 8px;
    --border-radius: 4px;
    --box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    
    /* Responsive variables */
    --container-width: 1200px;
    --header-height: 60px;
}

/* Using variables */
.button {
    background-color: var(--primary-color);
    padding: calc(var(--spacing-unit) * 2) calc(var(--spacing-unit) * 4);
    border-radius: var(--border-radius);
    box-shadow: var(--box-shadow);
    font-size: var(--font-size-base);
}

/* Dynamic variables with JavaScript */
.dynamic-theme {
    --theme-color: #ff0000;
    color: var(--theme-color);
}

/* Fallback values */
.safe-variable {
    background-color: var(--custom-color, #default-color);
}

/* Using calc() for responsive design */
.responsive-container {
    width: calc(100% - 2rem);
    max-width: calc(var(--container-width) - 2rem);
    margin: 0 auto;
    padding: calc(var(--spacing-unit) * 2);
}
```

**Key Concepts:**
- CSS custom properties
- Variable inheritance
- Fallback values
- Calc() function
- Responsive calculations

#### 10. What are CSS preprocessors and how do you use SCSS?
**Answer:**
SCSS (Sass) extends CSS with programming features:

```scss
// Variables
$primary-color: #007bff;
$secondary-color: #6c757d;
$font-size-base: 16px;
$spacing-unit: 8px;

// Mixins
@mixin button-style($bg-color, $text-color: white) {
    background-color: $bg-color;
    color: $text-color;
    padding: $spacing-unit * 2 $spacing-unit * 4;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    
    &:hover {
        background-color: darken($bg-color, 10%);
    }
}

// Nesting
.navbar {
    background-color: $primary-color;
    padding: $spacing-unit * 2;
    
    .nav-item {
        display: inline-block;
        margin-right: $spacing-unit * 2;
        
        a {
            color: white;
            text-decoration: none;
            
            &:hover {
                text-decoration: underline;
            }
        }
    }
}

// Functions
@function calculate-rem($size) {
    @return $size / $font-size-base * 1rem;
}

.text-large {
    font-size: calculate-rem(24px);
}

// Partials and imports
@import 'variables';
@import 'mixins';
@import 'components/buttons';
@import 'components/forms';

// Extends
%button-base {
    padding: $spacing-unit * 2;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.primary-button {
    @extend %button-base;
    @include button-style($primary-color);
}

.secondary-button {
    @extend %button-base;
    @include button-style($secondary-color);
}

// Loops
@for $i from 1 through 5 {
    .spacing-#{$i} {
        margin: $spacing-unit * $i;
    }
}

// Conditionals
@mixin responsive($breakpoint) {
    @if $breakpoint == mobile {
        @media (max-width: 768px) {
            @content;
        }
    } @else if $breakpoint == tablet {
        @media (max-width: 1024px) {
            @content;
        }
    } @else if $breakpoint == desktop {
        @media (min-width: 1025px) {
            @content;
        }
    }
}

.responsive-element {
    @include responsive(mobile) {
        font-size: 14px;
    }
    
    @include responsive(tablet) {
        font-size: 16px;
    }
    
    @include responsive(desktop) {
        font-size: 18px;
    }
}
```

**Key Concepts:**
- Variables and mixins
- Nesting and inheritance
- Functions and calculations
- Partials and imports
- Loops and conditionals

### 🔴 Advanced Level

#### 11. How do you optimize CSS for performance?
**Answer:**
Advanced optimization techniques:

```css
/* 1. Critical CSS - Above the fold */
.critical-css {
    /* Inline critical styles */
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    line-height: 1.6;
    color: #333;
}

/* 2. CSS Architecture - BEM Methodology */
.block {
    /* Block styles */
}

.block__element {
    /* Element styles */
}

.block--modifier {
    /* Modifier styles */
}

.block__element--modifier {
    /* Element with modifier */
}

/* 3. Performance Optimizations */
.optimized-selector {
    /* Use efficient selectors */
    transform: translateZ(0); /* Force hardware acceleration */
    will-change: transform;   /* Hint browser about changes */
}

/* 4. CSS Custom Properties for theming */
:root {
    --theme-primary: #007bff;
    --theme-secondary: #6c757d;
    --theme-background: #ffffff;
    --theme-text: #333333;
}

[data-theme="dark"] {
    --theme-primary: #0d6efd;
    --theme-secondary: #6c757d;
    --theme-background: #212529;
    --theme-text: #ffffff;
}

.themed-component {
    background-color: var(--theme-background);
    color: var(--theme-text);
    border: 1px solid var(--theme-primary);
}

/* 5. CSS containment for performance */
.contained-element {
    contain: layout style paint;
}

/* 6. Advanced animations with reduced motion */
@media (prefers-reduced-motion: reduce) {
    .animated-element {
        animation: none;
        transition: none;
    }
}
```

**Key Concepts:**
- Performance optimization
- CSS architecture
- BEM methodology
- Critical CSS
- Hardware acceleration
- Accessibility considerations

#### 12. How do you implement advanced CSS techniques like container queries?
**Answer:**
Modern CSS features:

```css
/* Container Queries */
.card-container {
    container-type: inline-size;
    container-name: card;
}

@container card (min-width: 300px) {
    .card {
        display: flex;
        flex-direction: row;
    }
    
    .card-image {
        flex: 0 0 150px;
    }
}

@container card (max-width: 299px) {
    .card {
        display: flex;
        flex-direction: column;
    }
}

/* Logical Properties */
.logical-layout {
    /* Instead of margin-left, margin-right */
    margin-inline-start: 1rem;
    margin-inline-end: 1rem;
    
    /* Instead of margin-top, margin-bottom */
    margin-block-start: 2rem;
    margin-block-end: 2rem;
    
    /* Instead of width, height */
    inline-size: 100%;
    block-size: auto;
    
    /* Instead of border-left, border-right */
    border-inline-start: 2px solid blue;
    border-inline-end: 2px solid red;
}

/* RTL Support with Logical Properties */
.rtl-friendly {
    padding-inline-start: 1rem;
    padding-inline-end: 2rem;
    text-align: start; /* Instead of text-align: left */
}

/* CSS Grid with logical properties */
.logical-grid {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    gap: 1rem;
    padding-inline: 2rem;
    margin-block: 1rem;
}
```

**Key Concepts:**
- Container queries
- Logical properties
- RTL support
- Modern CSS features
- Responsive design patterns

#### 13. How do you create a CSS framework or design system?
**Answer:**
Building a comprehensive design system:

```css
/* Design System Foundation */
:root {
    /* Color System */
    --color-primary-50: #eff6ff;
    --color-primary-100: #dbeafe;
    --color-primary-500: #3b82f6;
    --color-primary-900: #1e3a8a;
    
    /* Typography Scale */
    --font-size-xs: 0.75rem;
    --font-size-sm: 0.875rem;
    --font-size-base: 1rem;
    --font-size-lg: 1.125rem;
    --font-size-xl: 1.25rem;
    --font-size-2xl: 1.5rem;
    
    /* Spacing Scale */
    --space-1: 0.25rem;
    --space-2: 0.5rem;
    --space-4: 1rem;
    --space-8: 2rem;
    --space-16: 4rem;
    
    /* Border Radius */
    --radius-sm: 0.125rem;
    --radius-md: 0.375rem;
    --radius-lg: 0.5rem;
    --radius-xl: 0.75rem;
    
    /* Shadows */
    --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
    --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
    --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

/* Base Components */
.btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: var(--space-2) var(--space-4);
    border: 1px solid transparent;
    border-radius: var(--radius-md);
    font-size: var(--font-size-sm);
    font-weight: 500;
    line-height: 1.5;
    text-decoration: none;
    cursor: pointer;
    transition: all 0.15s ease-in-out;
}

.btn--primary {
    background-color: var(--color-primary-500);
    color: white;
}

.btn--primary:hover {
    background-color: var(--color-primary-600);
}

.btn--secondary {
    background-color: transparent;
    color: var(--color-primary-500);
    border-color: var(--color-primary-500);
}

.btn--large {
    padding: var(--space-3) var(--space-6);
    font-size: var(--font-size-base);
}

.btn--small {
    padding: var(--space-1) var(--space-2);
    font-size: var(--font-size-xs);
}

/* Card Component */
.card {
    background-color: white;
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-md);
    overflow: hidden;
}

.card__header {
    padding: var(--space-6);
    border-bottom: 1px solid #e5e7eb;
}

.card__body {
    padding: var(--space-6);
}

.card__footer {
    padding: var(--space-6);
    background-color: #f9fafb;
    border-top: 1px solid #e5e7eb;
}

/* Grid System */
.container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 var(--space-4);
}

.row {
    display: flex;
    flex-wrap: wrap;
    margin: 0 calc(var(--space-2) * -1);
}

.col {
    flex: 1;
    padding: 0 var(--space-2);
}

.col-1 { flex: 0 0 8.333333%; }
.col-2 { flex: 0 0 16.666667%; }
.col-3 { flex: 0 0 25%; }
.col-4 { flex: 0 0 33.333333%; }
.col-6 { flex: 0 0 50%; }
.col-8 { flex: 0 0 66.666667%; }
.col-12 { flex: 0 0 100%; }

/* Responsive Grid */
@media (max-width: 768px) {
    .col-md-1 { flex: 0 0 8.333333%; }
    .col-md-2 { flex: 0 0 16.666667%; }
    .col-md-3 { flex: 0 0 25%; }
    .col-md-6 { flex: 0 0 50%; }
    .col-md-12 { flex: 0 0 100%; }
}

/* Utility Classes */
.text-center { text-align: center; }
.text-left { text-align: left; }
.text-right { text-align: right; }

.mt-1 { margin-top: var(--space-1); }
.mt-2 { margin-top: var(--space-2); }
.mt-4 { margin-top: var(--space-4); }

.p-1 { padding: var(--space-1); }
.p-2 { padding: var(--space-2); }
.p-4 { padding: var(--space-4); }

.d-none { display: none; }
.d-block { display: block; }
.d-flex { display: flex; }
.d-grid { display: grid; }

/* Responsive Utilities */
@media (max-width: 768px) {
    .d-md-none { display: none; }
    .d-md-block { display: block; }
}

/* Animation System */
.animate-fade-in {
    animation: fadeIn 0.3s ease-in-out;
}

.animate-slide-up {
    animation: slideUp 0.3s ease-out;
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

@keyframes slideUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Theme System */
[data-theme="dark"] {
    --color-primary-500: #60a5fa;
    --color-background: #1f2937;
    --color-text: #f9fafb;
}

.theme-dark {
    background-color: var(--color-background);
    color: var(--color-text);
}
```

**Key Concepts:**
- Design system architecture
- Component-based CSS
- Utility classes
- Responsive design
- Theme system
- Maintainability

### 🟣 Expert Level

#### 14. How do you implement advanced CSS architecture patterns?
**Answer:**
Advanced CSS architecture for large-scale applications:

```css
/* 1. ITCSS (Inverted Triangle CSS) Architecture */

/* Settings - Variables and configuration */
:root {
    --color-primary: #007bff;
    --color-secondary: #6c757d;
    --font-family-base: 'Inter', sans-serif;
    --font-size-base: 16px;
    --spacing-unit: 8px;
    --breakpoint-sm: 576px;
    --breakpoint-md: 768px;
    --breakpoint-lg: 992px;
    --breakpoint-xl: 1200px;
}

/* Tools - Mixins and functions */
@mixin media-query($breakpoint) {
    @media (min-width: $breakpoint) {
        @content;
    }
}

@mixin button-variant($bg-color, $text-color: white) {
    background-color: $bg-color;
    color: $text-color;
    border: 1px solid $bg-color;
    
    &:hover {
        background-color: darken($bg-color, 10%);
        border-color: darken($bg-color, 10%);
    }
}

/* Generic - Reset and normalize */
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: var(--font-family-base);
    font-size: var(--font-size-base);
    line-height: 1.6;
    color: #333;
}

/* Elements - Base HTML elements */
h1, h2, h3, h4, h5, h6 {
    margin: 0 0 1rem 0;
    font-weight: 600;
    line-height: 1.2;
}

a {
    color: var(--color-primary);
    text-decoration: none;
    
    &:hover {
        text-decoration: underline;
    }
}

/* Objects - Layout patterns */
.o-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
}

.o-grid {
    display: grid;
    gap: 1rem;
    
    &--2-cols {
        grid-template-columns: repeat(2, 1fr);
    }
    
    &--3-cols {
        grid-template-columns: repeat(3, 1fr);
    }
    
    @include media-query(768px) {
        &--responsive {
            grid-template-columns: 1fr;
        }
    }
}

/* Components - UI components */
.c-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 0.5rem 1rem;
    border: 1px solid transparent;
    border-radius: 0.25rem;
    font-size: 1rem;
    font-weight: 500;
    text-decoration: none;
    cursor: pointer;
    transition: all 0.15s ease-in-out;
    
    &--primary {
        @include button-variant(var(--color-primary));
    }
    
    &--secondary {
        @include button-variant(transparent, var(--color-primary));
        border-color: var(--color-primary);
    }
    
    &--large {
        padding: 0.75rem 1.5rem;
        font-size: 1.125rem;
    }
    
    &--small {
        padding: 0.25rem 0.5rem;
        font-size: 0.875rem;
    }
}

.c-card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    
    &__header {
        padding: 1rem;
        border-bottom: 1px solid #e5e7eb;
    }
    
    &__body {
        padding: 1rem;
    }
    
    &__footer {
        padding: 1rem;
        background-color: #f9fafb;
        border-top: 1px solid #e5e7eb;
    }
}

/* Utilities - Utility classes */
.u-text-center { text-align: center; }
.u-text-left { text-align: left; }
.u-text-right { text-align: right; }

.u-mt-1 { margin-top: 0.25rem; }
.u-mt-2 { margin-top: 0.5rem; }
.u-mt-4 { margin-top: 1rem; }

.u-p-1 { padding: 0.25rem; }
.u-p-2 { padding: 0.5rem; }
.u-p-4 { padding: 1rem; }

.u-d-none { display: none; }
.u-d-block { display: block; }
.u-d-flex { display: flex; }
.u-d-grid { display: grid; }

/* Responsive utilities */
@include media-query(768px) {
    .u-md-none { display: none; }
    .u-md-block { display: block; }
}
```

**Key Concepts:**
- ITCSS architecture
- Scalable CSS
- Component organization
- Utility classes
- Maintainability

#### 15. How do you implement advanced CSS performance optimization?
**Answer:**
Advanced performance optimization techniques:

```css
/* 1. Critical CSS Inlining */
.critical-css {
    /* Above-the-fold styles */
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    line-height: 1.6;
    color: #333;
    margin: 0;
    padding: 0;
}

/* 2. CSS Containment */
.contained-element {
    contain: layout style paint;
}

.contained-element--strict {
    contain: strict;
}

/* 3. Hardware Acceleration */
.accelerated-element {
    transform: translateZ(0);
    will-change: transform;
}

.accelerated-element:hover {
    transform: translateZ(0) scale(1.05);
}

/* 4. Efficient Selectors */
/* Good - Specific and efficient */
.button-primary { }

/* Bad - Too generic */
div { }

/* Good - Direct descendant */
.nav > .nav-item { }

/* Bad - Deep nesting */
.nav .nav-list .nav-item .nav-link { }

/* 5. CSS Custom Properties for Performance */
:root {
    --theme-primary: #007bff;
    --theme-secondary: #6c757d;
    --theme-background: #ffffff;
    --theme-text: #333333;
}

.themed-component {
    background-color: var(--theme-background);
    color: var(--theme-text);
    border: 1px solid var(--theme-primary);
}

/* 6. Reduced Motion Support */
@media (prefers-reduced-motion: reduce) {
    .animated-element {
        animation: none;
        transition: none;
    }
}

/* 7. Print Styles */
@media print {
    .no-print {
        display: none;
    }
    
    .print-only {
        display: block;
    }
    
    body {
        font-size: 12pt;
        line-height: 1.4;
    }
}

/* 8. High DPI Support */
@media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
    .high-dpi-image {
        background-image: url('image@2x.png');
        background-size: 100% 100%;
    }
}

/* 9. CSS Grid with Subgrid */
.grid-layout {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    gap: 1rem;
}

.grid-item {
    display: grid;
    grid-template-rows: subgrid;
    grid-row: span 3;
}

/* 10. Advanced Animation Performance */
@keyframes optimizedSlide {
    from {
        transform: translateX(-100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

.optimized-animation {
    animation: optimizedSlide 0.3s ease-out;
    will-change: transform, opacity;
}

.optimized-animation:hover {
    animation-play-state: paused;
}
```

**Key Concepts:**
- Performance optimization
- CSS containment
- Hardware acceleration
- Efficient selectors
- Reduced motion
- Print styles
- High DPI support

## 🎯 Practice Exercises

### Beginner
1. Create a basic CSS layout with header, main, and footer
2. Style a form with proper spacing and colors
3. Implement basic responsive design

### Intermediate
1. Build a responsive navigation menu
2. Create a card component with hover effects
3. Implement a CSS Grid layout

### Advanced
1. Create a complex dashboard layout
2. Implement advanced animations
3. Build a responsive image gallery

### Expert
1. Design a complete CSS framework
2. Implement a theme system
3. Create performance-optimized animations

## 📚 Additional Resources

- [MDN CSS Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [CSS Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [CSS Custom Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
- [Sass Documentation](https://sass-lang.com/documentation)
