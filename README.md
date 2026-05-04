# Portal Numeral: Topographic Field

Interactive generative artwork created for Google I/O 2026 "Code the Countdown".

## Overview

Portal Numeral: Topographic Field is a fullscreen interactive web artwork where a huge central numeral acts as a portal into a living topographic field.

Each digit from 1 to 10 reveals a different internal field structure, creating a distinct visual topology while keeping the numeral as the dominant visual anchor.

## Features

- Fullscreen interactive experience
- WebGL generative topographic field
- Large central numeral as the visual hero
- Distinct internal field behavior for digits 1–10
- Mouse-driven pressure and parallax interaction
- Lightweight single-file HTML build
- Static fallback if WebGL is unavailable

## Files

- `index.html` — final interactive artwork
- `project-notes.md` — concept notes, prompts, and iteration history
- `LICENSE` — repository license

## Usage

Open `index.html` in a modern browser with WebGL support.

You can also use the shared Google Canvas or AI Studio link submitted for the Google I/O 2026 countdown challenge.

## Creative Direction

The project was designed to be:

- instantly readable on a large screen
- minimal and monochrome
- mathematically structured
- elegant rather than flashy
- suitable for looped broadcast display

The visual system avoids generic RGB glitch effects, noisy particle clouds, and overly busy sci-fi aesthetics.

## Technical Notes

The artwork uses:

- a full-screen WebGL canvas
- a large numeral mask layered above the generative field
- distinct shader-driven structures for different digits
- subtle mouse interaction for field pressure and parallax
- a fallback mode when WebGL is not available

## Context

This project was developed as a fast, refined, broadcast-friendly interactive artwork for the Google I/O 2026 "Code the Countdown" challenge.

## Author

Created by QIVERA VERA.
