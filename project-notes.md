# Project Notes — Portal Numeral: Topographic Field

## Project Context

This project was created for the Google I/O 2026 "Code the Countdown" challenge.

The brief was to build a creative coded experience in Google Canvas or AI Studio featuring a large central number from 1 to 10, then submit a public share link before the deadline.

## Core Concept

A huge numeral acts as a portal into a living monochrome topographic field.

The number remains the visual hero at all times, while the interior of its shape reveals an animated cartographic structure. Each digit from 1 to 10 changes the internal logic of the field so the experience feels varied while staying visually coherent.

## Creative Goals

- Make the number instantly readable on a large screen
- Create a refined and memorable visual identity
- Avoid generic particle-demo aesthetics
- Keep the experience minimal, elegant, and broadcast-friendly
- Use a single main interaction only
- Build something stable enough to submit quickly

## Artistic Direction

The visual system was intentionally kept:

- monochrome
- high contrast
- minimal
- mathematical
- topographic rather than cosmic
- elegant rather than flashy

The project avoids RGB glitch effects, cyberpunk styling, and noisy sci-fi particle clouds.

## Interaction Design

The interaction is intentionally simple:

- mouse movement changes pressure, contour density, and parallax depth
- digit buttons allow switching from 1 to 10
- the numeral remains the dominant anchor at all times

The goal was immediate comprehension, not a complex game mechanic.

## Technical Structure

The project uses:

- a single self-contained HTML file
- a full-screen WebGL canvas
- a large text mask layered above the generative field
- shader-based contour generation
- per-digit structural differences
- a static fallback when WebGL is unavailable

## Iteration History

### Version 1

The first version established the main structure:

- full-screen WebGL background
- large numeral mask
- digit selector
- generative contour-like field
- mouse-driven movement
- basic structural changes per digit

Strengths:
- strong concept alignment
- lightweight and clean structure
- simple interaction
- visually coherent monochrome output

Weaknesses:
- still too close to a generic shader-demo feeling
- topographic identity not distinctive enough
- some digit differences were too subtle
- fallback handling needed improvement

### Version 2

The second version refined the project significantly:

- proper WebGL fallback behavior
- sharper cartographic line logic
- reduced noise contribution for a cleaner result
- stronger structural differences for key digits
- clearer hierarchy between major and minor contour lines
- improved robustness without changing the overall architecture

Key highlighted digits:
- 1: strong vortex / funnel behavior
- 3: precise grid / lattice structure
- 7: strong diagonal shear field
- 10: clearly dual-field topology

## Design Decisions

### Why monochrome

Monochrome helped avoid generic "AI art" aesthetics and kept the piece more elegant, readable, and broadcast-safe.

### Why topographic lines

Topographic lines gave the project a more specific identity than random particles or abstract glow effects. The result feels more structural and intentional.

### Why a minimal UI

The challenge is centered on the number itself. Any heavy interface would weaken the visual focus.

### Why one-file architecture

A single HTML file is easy to share, archive, run, and submit under deadline pressure.

## Final Evaluation

The final result is a compact interactive artwork that balances:

- legibility
- originality
- simplicity
- performance
- conceptual clarity

It is not the most extreme or technically complex direction possible, but it is strong, coherent, and suitable for submission.

## Short Project Description

Portal Numeral: Topographic Field is a fullscreen interactive artwork in which a giant numeral reveals a living internal landscape made of monochrome topographic lines. Each digit from 1 to 10 generates a distinct field behavior while preserving a clean, readable, broadcast-friendly composition.
