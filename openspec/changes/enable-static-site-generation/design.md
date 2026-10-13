## Context

The starter template already has a `generate` script that runs `nuxt generate`, but its normal `build` script runs `nuxt build`, which targets the server output. The Nuxt config does not currently state prerendering behavior.

## Goals / Non-Goals

**Goals:**

- Make the normal production build produce static hosting output.
- Ensure the root and linked routes are pre-rendered, with build errors surfaced.
- Give the cloned project the `snow-portfolio` package name.

**Non-Goals:**

- Add hosting-provider-specific deployment configuration.
- Enumerate future data-driven routes before those routes exist.

## Decisions

- Keep `ssr: true` and use Nuxt's `generate` command for production builds. Static generation renders HTML at build time while leaving the generated client app interactive.
- Select Nitro's `static` preset and configure prerendering to include `/`, crawl internal links, and fail if a route errors. Any future route that is not reachable through an internal link must be added to the route list.
- Keep the existing `generate` script as an explicit alias for developers and hosting platforms that expect that command; make `build` run the same static generation command.
- Update the README with the static build command and output location.

## Risks / Trade-offs

- A dynamic route that is not linked and is not added to the prerender route list will not have its own static HTML file. Add each concrete path to Nitro's prerender routes when introducing such pages.
