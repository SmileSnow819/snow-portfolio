## Purpose

The website can be deployed as static files while keeping its client-side interactions available after hydration.

## ADDED Requirements

### Requirement: Production builds generate a static website

The production build MUST emit static HTML and assets that can be hosted without a running Nuxt server.

#### Scenario: Build the website for static hosting

- **WHEN** the standard production build command completes successfully
- **THEN** the generated website is available as static files in Nuxt's public output directory

### Requirement: Pre-render all discoverable website routes

The static generation process MUST pre-render the root route and routes discovered from internal links. Routes that cannot be discovered from links MUST be explicitly listed for generation.

#### Scenario: Generate linked pages

- **WHEN** a page contains an internal link to another website route
- **THEN** static generation includes an HTML page for that linked route

#### Scenario: Generate a route that is not linked

- **WHEN** a website route cannot be discovered by following internal links
- **THEN** that route is included in the explicit static generation route list
