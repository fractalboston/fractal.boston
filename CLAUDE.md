# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static website for Fractal Boston, a community organization. The site is built with vanilla HTML, CSS, and minimal JavaScript - no build tools or frameworks are used.

## Architecture

- **Static Site**: Pure HTML/CSS/JS with no build process
- **Main Page**: `index.html` - Community landing page with description, call-to-action, and Google Analytics
- **Interest Form**: `interest-form/index.html` - Simple redirect page to Google Forms
- **Styling**: 
  - `normalize.css` - CSS reset
  - `blocks.min.css` - External CSS framework
  - `styles.css` - Custom site styles
- **Assets**:
  - `font/` - Custom Fractul font files
  - `img/` - Logo and community images
- **Analytics**: Google Analytics (gtag) tracking for engagement events

## Development

Since this is a static site with no build process:
- Changes can be made directly to HTML/CSS/JS files
- Test by opening `index.html` in a browser or using a local server
- No package manager, dependencies, or build commands

## Workflow

- When you complete a discrete bit of work, commit and push it without being asked. Commits are easy to revert and the site is not critical, so default to shipping rather than waiting for explicit approval.

## Deployment

The site appears to be deployed via GitHub Pages (based on `CNAME` file presence).

## Key Features

- Community landing page with call-to-action button
- Newsletter signup (Substack embed)
- Interest form redirect to Google Forms
- Google Analytics event tracking for button clicks
- Responsive design with custom CSS