---
name: ui-ux-principles
description: Expert UI/UX design checklist covering visual design, interaction, accessibility (WCAG 2.1 AA), performance (Core Web Vitals), user feedback, information architecture, mobile-first responsive design, consistency, testing, and documentation. Use when designing or reviewing any user interface, component, page, or flow.
---

# UI/UX Principles

Act as an expert in UI and UX design principles for software development. Apply these as a design + review checklist on any UI work.

## Visual design
- Establish clear visual hierarchy to guide attention.
- Cohesive color palette reflecting the brand (ask for guidelines if unknown).
- Effective typography for readability and emphasis.
- Maintain sufficient contrast — WCAG 2.1 AA.
- Consistent style across the application.

## Interaction design
- Intuitive navigation patterns.
- Familiar UI components to reduce cognitive load.
- Clear calls-to-action.
- Responsive design for cross-device compatibility.
- Use animations judiciously.

## Accessibility
- Follow WCAG guidelines.
- Semantic HTML for screen reader compatibility.
- Alt text for images and non-text content.
- Full keyboard navigability for all interactive elements.
- Test with assistive technologies.

## Performance optimization
- Optimize images and assets.
- Lazy-load non-critical resources.
- Code splitting for initial load performance.
- Monitor Core Web Vitals (LCP, FID, CLS).
- Prefer CSS animations over JS where possible.
- Critical CSS for above-the-fold content.

## User feedback
- Clear feedback for user actions.
- Loading indicators for async operations.
- Clear error messages and recovery options.
- Analytics to track behavior and pain points.

## Information architecture
- Organize content logically.
- Clear labeling and categorization.
- Effective search functionality.
- Sitemap to visualize structure.

## Mobile-first design
- Design for mobile first, then scale up.
- Touch-friendly elements (min 44×44 px).
- Support gestures (swipe, pinch-to-zoom) where appropriate.
- Consider thumb zones for important interactive elements.

## Consistency
- Adhere to a design system.
- Consistent terminology.
- Consistent positioning of recurring elements.
- Visual consistency across sections.

## Testing and iteration
- A/B test critical design decisions.
- Heatmaps and session recordings for behavior analysis.
- Gather and incorporate user feedback.
- Iterate based on data.

## Documentation
- Comprehensive style guide.
- Document design patterns and component usage.
- User-flow diagrams for complex interactions.
- Organized, accessible design assets.

## Fluid layouts
- Relative units (%, em, rem) instead of fixed pixels.
- CSS Grid and Flexbox for flexible layouts.
- Mobile-first approach, scale up.

## Media queries
- Breakpoints driven by content needs, not specific devices.
- Test across devices and orientations.

## Images and media
- Responsive images with `srcset` and `sizes`.
- Lazy loading for images and videos.
- Responsive embedded media (iframes) via CSS.

## Typography
- Relative units (em, rem) for font sizes.
- Tune line-height and letter-spacing for small screens.
- Modular scale for consistency across breakpoints.

## Touch targets
- Minimum 44×44 px for interactive elements.
- Adequate spacing between targets.
- Hover states for desktop, focus states for touch/keyboard.

## Performance (mobile)
- Optimize assets for mobile networks.
- CSS animations over JS where possible.
- Critical CSS for above-the-fold content.

## Content prioritization
- Prioritize content for mobile views.
- Progressive disclosure.
- Off-canvas patterns for secondary content.

## Navigation
- Mobile-friendly patterns (hamburger, sticky header).
- Keyboard and screen reader accessible.

## Forms
- Layouts adapt to screen size.
- Appropriate input types for mobile.
- Inline validation with clear error messaging.

## Testing
- Use browser dev tools for responsiveness checks.
- Test on actual devices, not just emulators.
- Conduct usability testing across device types.

Stay current with responsive design techniques, browser capabilities, and UI/UX trends.
