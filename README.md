# Danyal Iqbal | Portfolio Website

A fast, accessible, single-page portfolio for **Danyal Iqbal**, a Systems and Computing Engineering student at the University of Guelph. It presents my experience, projects, technical skills and education in a clean two-column layout, and is built to be read well by both people and applicant tracking systems (ATS).

**Live site:** `https://danyal-cpu21.github.io/<repository-name>` *(replace with your deployed URL; if the repository is named `danyal-cpu21.github.io`, the address is `https://danyal-cpu21.github.io`)*

---

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Tech Stack](#tech-stack)
4. [Site Sections](#site-sections)
5. [Project Structure](#project-structure)
6. [Getting Started](#getting-started)
7. [Deploying to GitHub Pages](#deploying-to-github-pages)
8. [Customization](#customization)
9. [GitHub Integration](#github-integration)
10. [ATS and SEO Optimization](#ats-and-seo-optimization)
11. [Accessibility](#accessibility)
12. [Browser Support](#browser-support)
13. [Troubleshooting](#troubleshooting)
14. [Contact](#contact)

---

## Overview

This portfolio is a single self-contained `index.html` file. It has no build step, no framework and no dependencies to install, so it can be opened locally or hosted on any static host in a few minutes. The layout is inspired by Brittany Chiang's well-known developer portfolio: a fixed sidebar with navigation on the left and scrolling content on the right, restyled with a white background and teal accents.

## Features

- **Two-column layout.** A sticky sidebar keeps your name, title and navigation in view while the content scrolls.
- **Scroll-aware navigation.** The sidebar highlights the section you are currently reading.
- **Responsive design.** On tablets and phones the sidebar collapses into a header and the content becomes a single column.
- **GitHub integration.** Links point to my GitHub profile, and an optional "Latest on GitHub" section lists my most recently updated public repositories.
- **Print-friendly.** A dedicated print stylesheet produces a clean, one-column document if the page is printed or saved as a PDF.
- **No tracking and no cookies.** The page loads only two web fonts and makes one optional request to the public GitHub API.
- **Lightweight.** One HTML file with inline CSS and JavaScript, about 20 KB.

## Tech Stack

| Area | Details |
| --- | --- |
| Markup | Semantic HTML5 |
| Styling | Plain CSS with custom properties (variables), Flexbox and Grid |
| Scripting | Vanilla JavaScript (`IntersectionObserver` for scroll highlighting, `fetch` for the GitHub API) |
| Fonts | [Inter](https://fonts.google.com/specimen/Inter) and [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts, with system-font fallbacks |
| Hosting | GitHub Pages (any static host works) |

## Site Sections

1. **About.** A professional summary, a circuit-board banner illustration and relevant coursework.
2. **Experience.** Software Engineering Intern at Vali AI, Software Developer at GryphDex Engineering Club, and Sales Representative at Rogers Communications.
3. **Projects.**
   - *AI Message Clarity Checker:* a Python NLP tool that flags vague language, unclear ownership and imprecise deadlines.
   - *Autonomous Launching Wheel Chair:* an Arduino vehicle with a custom motor controller and servo-powered launcher.
   - *Campus Event Booking System:* a Java application with a waitlist engine, CSV persistence and a JUnit test suite.
   - *Room Light Heat Map:* a JavaScript and HTML5 Canvas web app that maps which parts of a room are too dark or too bright and suggests priced lighting ideas. [Live demo](https://danyal-cpu21.github.io/Room-light-heat-map/)
4. **Technical Skills.** Languages, hardware, software and concepts.
5. **Education.** B.Eng. in Systems and Computing Engineering, University of Guelph (expected June 2029).
6. **Contact.** Email address and a link to GitHub.

## Project Structure

```
.
├── index.html               # The entire website (HTML, CSS and JavaScript)
├── room-light-heat-map.jpg  # Screenshot used in the Room Light Heat Map project card
└── README.md                # This file
```

Keep `room-light-heat-map.jpg` in the same folder as `index.html`, or the project screenshot will not load. GitHub Pages looks for `index.html` in the root of the branch it serves. The file must be named exactly `index.html` (lowercase) and must not be inside a subfolder.

## Getting Started

### Run locally

1. Clone the repository:
   ```bash
   git clone https://github.com/danyal-cpu21/<repository-name>.git
   cd <repository-name>
   ```
2. Open `index.html` in any modern browser, or serve the folder with a simple local server:
   ```bash
   # Python 3
   python -m http.server 8000
   ```
   Then visit `http://localhost:8000`.

No installation, package manager or build tools are required.

## Deploying to GitHub Pages

1. Push `index.html` and `README.md` to the **root** of your repository on the `main` branch.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Select the `main` branch and the **/ (root)** folder, then click **Save**.
5. Wait one to two minutes. The progress of the deployment is visible in the **Actions** tab, and the live URL appears at the top of the Pages settings screen.
6. Hard refresh the site (Ctrl+Shift+R, or Cmd+Shift+R on Mac) if you still see an older version.

Other static hosts such as Netlify, Vercel and Cloudflare Pages also work: point them at the repository and leave the build command empty.

## Customization

All content and styling live in `index.html`.

### Update content

Each section is a `<section>` element with its own `id` (`about`, `experience`, `projects`, `skills`, `education`, `contact`). Experience, project and education entries are `<article class="card">` blocks. To add a new entry, copy an existing block and edit the text, dates and tags.

### Change colors

Colors are defined once as CSS variables at the top of the `<style>` block:

```css
:root{
  --bg:#ffffff;        /* page background */
  --surface:#f4f8fa;   /* card hover and contact box */
  --line:#e3eaef;      /* borders and dividers */
  --text:#52606d;      /* body text */
  --text-hi:#1f2933;   /* emphasized text */
  --head:#0b1b2b;      /* headings */
  --accent:#0e7c86;    /* links, tags and highlights */
}
```

Change these values to retheme the entire site.

### Change fonts

Replace the Google Fonts `<link>` in the `<head>` and update the `--sans` and `--mono` variables. Keep a fallback stack so text still renders if the font fails to load.

### Add a resume download

Place your resume PDF in the repository root (for example `Danyal_Iqbal_Resume.pdf`) and add a link in the Contact section:

```html
<a class="btn" href="Danyal_Iqbal_Resume.pdf" download>Download Resume</a>
```

## GitHub Integration

The sidebar button, each project's "View on GitHub" link and the contact button point to `https://github.com/danyal-cpu21`.

At the bottom of `index.html`, the script defines the account name:

```js
var GITHUB_USER="danyal-cpu21";
```

When the page loads, it requests up to six of the most recently updated public repositories from the GitHub API, skips forks, and shows them in a **Latest on GitHub** section under Projects. If the request fails, is rate limited or returns nothing, the section stays hidden and the rest of the page is unaffected.

To point a project card at its own repository, change the `href` of that card's "View on GitHub" link, for example:

```html
<a href="https://github.com/danyal-cpu21/message-clarity-checker" target="_blank" rel="noopener">View on GitHub</a>
```

## ATS and SEO Optimization

- **Plain, selectable text.** All content is real HTML text, with no text embedded in images.
- **Standard headings.** Sections use recognizable names (Experience, Projects, Technical Skills, Education) and a logical `h1` to `h3` hierarchy.
- **Keyword-rich content.** Languages, tools and technologies from the resume (Java, C++, Python, C, VHDL, JavaScript, Arduino, NLP, JUnit and others) appear in readable text.
- **Structured data.** A JSON-LD `Person` block gives search engines and parsers my name, role, school, skills and GitHub profile.
- **Metadata.** A descriptive title and meta description are included for search results and link previews.
- **Print stylesheet.** Printing or saving to PDF produces a clean, single-column version of the page.

For best results with applications, also submit a standard one-page PDF resume, since many ATS tools expect an uploaded document.

## Accessibility

- Semantic landmarks (`header`, `nav`, `main`, `section`, `footer`) and labelled sections
- A "Skip to content" link for keyboard users
- Visible focus outlines on interactive elements
- Decorative graphics are hidden from screen readers
- Respect for the `prefers-reduced-motion` setting
- Text and background colors chosen for strong contrast

## Browser Support

The site works in current versions of Chrome, Edge, Firefox and Safari on desktop and mobile. Older browsers that lack `IntersectionObserver` simply skip the navigation highlighting; the rest of the page still works.

## Troubleshooting

| Problem | Likely cause and fix |
| --- | --- |
| The site shows only the README | `index.html` is missing from the repository root, is misnamed (for example `Index.html` or `index (1).html`) or is inside a folder. Rename it and move it to the root. |
| The site returns a 404 | Pages is not enabled or points at the wrong branch or folder. Recheck **Settings → Pages**. |
| Changes do not appear | Wait a couple of minutes for the deployment to finish, then hard refresh. |
| "Latest on GitHub" does not appear | The account has no public non-fork repositories, the GitHub API rate limit was reached, or the page is opened from a host that blocks outside requests. |
| Project screenshot is broken | `room-light-heat-map.jpg` is missing or is not in the same folder as `index.html`. Upload it to the repo root. |
| Fonts look different | The Google Fonts request was blocked. The page falls back to system fonts, which is expected. |

## Contact

- **GitHub:** [github.com/danyal-cpu21](https://github.com/danyal-cpu21)
- **Email:** Danyal.iq@outlook.com

---

© 2026 Danyal Iqbal. All rights reserved.
