# Project Customizations

### Portfolio Case Study Management

When asked to update, format, or publish case studies in the `Shubhi-portfolio` workspace, strictly follow these guidelines:

1. **Source Content Formatting:**
   - Case studies are drafted as Markdown files in the `shubhicasestudy/shubhicasestudy/` directory.
   - Maintain the standard structure in these files: Title, Role/Company/Scope/Timeline metadata, Context & Challenge, Goals, Design Process, Solution, Impact, and Learnings.

2. **Publishing to the Website (`index.html`):**
   - The actual portfolio website is a single-page application built in `index.html`. 
   - Case studies are rendered via a hardcoded Javascript object named `CASES` at the bottom of `index.html`.
   - When adding a new case study to the live site, create a new entry in the `CASES` object with the following schema:
     - `cat`: Category (e.g., "AI · B2B SaaS Platform")
     - `title`: Full title string
     - `img`: URL for the cover image
     - `meta`: Array of key-value tuples (e.g., `[["Role", "Lead Product Designer"], ["Timeline", "2023 — 2024"]]`)
     - `challenge`: A concise summary paragraph of the "Context & Challenge" from the Markdown file.
     - `approach`: A concise summary paragraph combining "Design Process" and "Solution" from the Markdown file.
     - `stats`: Array of stat tuples (e.g., `[["3.2×", "Faster time-to-insight"]]`) extracted from the "Impact" section.
     - `gallery`: Array of 2 image URLs for the bottom gallery.
   - You must also add a corresponding `<div class="project-card" data-case="[key]">` element inside the `<section id="work">` in the DOM to make the case study visible on the main page.
