## Why

This personal website should deploy as static files without requiring a running Nuxt server. Making static generation the default production build gives the project a straightforward deployment path while retaining client-side interactivity.

## What Changes

- Configure Nuxt to pre-render the site's routes for static hosting.
- Make the standard production build generate the static site and retain an explicit `generate` script.
- Rename the package from the template name to `snow-portfolio`.

## Capabilities

### New Capabilities

- `static-site-generation`: Generate the website's routes as static HTML and assets for static hosting.

### Modified Capabilities

## Impact

- Affects `nuxt.config.ts`, `package.json`, and `README.md`.
- Static build output is written to Nuxt's `.output/public` directory.
