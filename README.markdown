# CSS Media Queries: A Comprehensive Guide

This repository provides a complete guide to CSS media queries, from beginner to advanced concepts, with practical examples to help you create responsive web designs that adapt to various devices and screen sizes.

## Table of Contents
1. [What Are Media Queries?](#what-are-media-queries)
2. [Basic Syntax](#basic-syntax)
3. [Beginner Concepts](#beginner-concepts)
   - [Targeting Screen Sizes](#targeting-screen-sizes)
   - [Common Breakpoints](#common-breakpoints)
4. [Intermediate Concepts](#intermediate-concepts)
   - [Logical Operators (and, or, not)](#logical-operators)
   - [Orientation](#orientation)
   - [Media Types](#media-types)
5. [Advanced Concepts](#advanced-concepts)
   - [Resolution and DPR](#resolution-and-dpr)
   - [Hover and Pointer](#hover-and-pointer)
   - [Prefers Color Scheme](#prefers-color-scheme)
   - [Dynamic Viewport Units](#dynamic-viewport-units)
6. [Best Practices](#best-practices)
7. [Example Project](#example-project)
8. [Resources](#resources)

## What Are Media Queries?
Media queries are a CSS feature used to apply styles based on the device's characteristics, such as screen width, height, orientation, or resolution. They are essential for creating responsive and adaptive web designs.

## Basic Syntax
A media query consists of a media type and one or more expressions that check for specific conditions. The basic syntax is:

```css
@media [media-type] and (condition) {
  /* CSS rules */
}
```

Example:
```css
@media screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```
This applies a light blue background to the body when the screen width is 600px or less.

## Beginner Concepts

### Targeting Screen Sizes
Media queries often target screen sizes using `min-width` or `max-width`.

- **max-width**: Applies styles if the viewport width is less than or equal to the specified value.
- **min-width**: Applies styles if the viewport width is greater than or equal to the specified value.

**Example: Changing font size for small screens**
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      font-size: 16px;
    }
    @media screen and (max-width: 768px) {
      body {
        font-size: 14px;
      }
    }
  </style>
</head>
<body>
  <p>This text changes size on smaller screens.</p>
</body>
</html>
```

### Common Breakpoints
Breakpoints define the points at which your design changes to accommodate different devices. Common breakpoints include:

- **Mobile**: 320px–480px
- **Tablet**: 481px–768px
- **Laptop**: 769px–1024px
- **Desktop**: 1025px and above

**Example: Responsive navigation**
```css
.nav {
  display: flex;
}
@media screen and (max-width: 600px) {
  .nav {
    flex-direction: column;
  }
}
```

## Intermediate Concepts

### Logical Operators
Media queries support logical operators (`and`, `or`, `not`) to combine conditions.

- **and**: Combines multiple conditions.
- **or**: Uses a comma to apply styles if any condition is true.
- **not**: Negates the query.

**Example: Combining conditions**
```css
@media screen and (min-width: 600px) and (max-width: 1024px) {
  .container {
    background-color: yellow;
  }
}
@media screen and (max-width: 600px), (min-width: 1200px) {
  .container {
    border: 2px solid black;
  }
}
```

### Orientation
The `orientation` feature targets the device's orientation: `portrait` or `landscape`.

**Example: Adjusting layout for orientation**
```css
@media screen and (orientation: landscape) {
  .content {
    display: flex;
  }
}
@media screen and (orientation: portrait) {
  .content {
    display: block;
  }
}
```

### Media Types
Media queries can target different media types, such as `screen`, `print`, or `all`.

**Example: Print styles**
```css
@media print {
  body {
    color: black;
    background-color: white;
  }
}
```

## Advanced Concepts

### Resolution and DPR
The `resolution` feature targets the device's pixel density, often used for high-DPI (Retina) displays. Use `min-resolution` or `max-resolution`.

**Example: High-resolution images**
```css
.image {
  background-image: url('low-res.jpg');
}
@media screen and (min-resolution: 2dppx) {
  .image {
    background-image: url('high-res.jpg');
  }
}
```

### Hover and Pointer
The `hover` and `pointer` features check if the device supports hovering or the type of pointing device.

**Example: Styling for touch devices**
```css
@media (hover: none) and (pointer: coarse) {
  .button {
    padding: 20px; /* Larger touch target */
  }
}
```

### Prefers Color Scheme
The `prefers-color-scheme` feature adapts to the user's system theme (light or dark).

**Example: Dark mode support**
```css
body {
  background-color: white;
  color: black;
}
@media (prefers-color-scheme: dark) {
  body {
    background-color: #333;
    color: white;
  }
}
```

### Dynamic Viewport Units
Modern media queries can use viewport units (`vw`, `vh`, `vmin`, `vmax`) for dynamic layouts.

**Example: Adjusting font size dynamically**
```css
@media screen and (max-width: 50vw) {
  h1 {
    font-size: 5vw;
  }
}
```

## Best Practices
- **Mobile-First Approach**: Start with base styles for smaller screens and progressively add styles for larger screens using `min-width`.
- **Use Relative Units**: Prefer `rem`, `em`, or `%` for scalability.
- **Test Across Devices**: Use browser dev tools or real devices to test responsiveness.
- **Avoid Overly Specific Breakpoints**: Use ranges that cover common device sizes.
- **Keep It Simple**: Combine queries logically to avoid overly complex rules.

## Example Project
Below is a simple responsive webpage using media queries.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Design Example</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
    }
    .container {
      display: grid;
      grid-template-columns: 1fr;
      gap: 20px;
    }
    .card {
      background-color: #f0f0f0;
      padding: 20px;
      border-radius: 8px;
    }
    /* Mobile-first */
    @media screen and (min-width: 768px) {
      .container {
        grid-template-columns: repeat(2, 1fr);
      }
    }
    @media screen and (min-width: 1024px) {
      .container {
        grid-template-columns: repeat(3, 1fr);
      }
    }
    @media (prefers-color-scheme: dark) {
      body {
        background-color: #222;
        color: white;
      }
      .card {
        background-color: #444;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="card">Card 1</div>
    <div class="card">Card 2</div>
    <div class="card">Card 3</div>
  </div>
</body>
</html>
```

This example demonstrates a mobile-first grid layout that adapts to different screen sizes and supports dark mode.

## Resources
- [MDN Web Docs: Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries)
- [CSS Tricks: A Complete Guide to Media Queries](https://css-tricks.com/a-complete-guide-to-css-media-queries/)
- [W3C CSS Media Queries Specification](https://www.w3.org/TR/css3-mediaqueries/)