# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MBAR (McKnight Brain Aging Registry) is a static website hosted on GitHub Pages at https://uab-it.github.io/mbar/. It provides information for researchers affiliated with the four McKnight Brain Research Foundation Institutes.

## Architecture

This is a static site using **htmx** for client-side page loading and **Tailwind CSS** (CDN v2.2.19) for styling. There is no build step, bundler, or package manager.

- `index.html` — Main entry point and shell (header, footer, nav, banner). Contains all navigation and layout chrome.
- `pages/` — Content fragments loaded dynamically via htmx into `#main-content` div:
  - `our_study.html` — "About MBAR" page content
  - `resources.html` — Resources page content
  - `publications.html` — Publications page content
  - `about_us.html` — "About Us" / team page content
- `404.html` — Catch-all redirect page for GitHub Pages SPA routing. Detects the URL path and uses htmx to load `index.html` then swap in the correct page fragment.
- `images/` — Static image assets (logos, photos)

## Key Patterns

**Navigation**: Links use htmx attributes (`hx-get`, `hx-push-url`, `hx-target="#main-content"`) to fetch page fragments and swap them into the main content area without full page reloads. Both desktop and mobile nav menus use this pattern.

**SPA Routing on GitHub Pages**: Since GitHub Pages doesn't support server-side routing, `404.html` acts as a catch-all. It reads the URL path and uses htmx to load the shell (`index.html`) then the appropriate page fragment.

**Styling**: Tailwind utility classes via CDN. One custom CSS variable: `--mcknight: #0073e6` with a `.blue` helper class for the brand color used in header/footer.

**Page fragments are not full HTML documents** — they contain only the content markup to be injected into `#main-content`. Do not add `<html>`, `<head>`, or `<body>` tags to files in `pages/`.

## Development

Open `index.html` directly in a browser or use any static file server (e.g., `python3 -m http.server`). There is no build, test, or lint configuration.

## Remote

- Origin: https://github.com/UAB-IT/mbar.git
- Deploys automatically via GitHub Pages from the `main` branch.
