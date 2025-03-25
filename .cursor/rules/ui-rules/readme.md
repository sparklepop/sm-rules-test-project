Any rules related to react, html, css, angular, frontend development, etc... belong in this folder.

---
description: Apply when creating or modifying any UI components to ensure consistent styling and UX patterns
globs: src/components/**/*.tsx, src/components/**/*.jsx, src/pages/**/*.tsx, src/pages/**/*.jsx
alwaysApply: false
---

# StrongMind UI Component Standards

## Context

- Ensures consistent UI/UX across StrongMind applications
- Maintains design system compliance
- Promotes maintainable styling patterns

## Critical Rules

- Check @https://ux.strongmind.com/ FIRST before creating custom components
- Use StrongMind UX library components with their default styling when available
- Implement Tailwind utility classes for custom styling needs
- Group related Tailwind classes using consistent ordering:
  1. Layout (flex, grid, position)
  2. Spacing (margin, padding)
  3. Sizing (width, height)
  4. Typography
  5. Colors and visual effects
- Extract commonly repeated Tailwind class combinations into reusable components
- Document any deviations from the UX library patterns with clear justification
- Use semantic HTML elements as base components when possible

## Examples

<example>
  // Using StrongMind UX library component
  import { Button } from '@strongmind/ui'
  
  // Good - Using UX library with Tailwind for custom positioning
  <Button 
    variant="primary" 
    className="mt-4 ml-auto"
  >
    Submit
  </Button>

  // Good - Consistent class ordering
  <div className="flex items-center p-4 w-full text-sm text-gray-700 bg-white">
    {children}
  </div>
</example>

<example type="invalid">
  // Bad - Custom button when UX library provides one
  <button className="px-4 py-2 bg-blue-500 text-white rounded">
    Submit
  </button>

  // Bad - Inconsistent class ordering
  <div className="text-sm bg-white flex w-full items-center p-4">
    {children}
  </div>
</example>
