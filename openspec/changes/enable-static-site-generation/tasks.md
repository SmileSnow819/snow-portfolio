## 1. Configure static generation

- [x] 1.1 Rename the package to `snow-portfolio` and make the production `build` script use `nuxt generate`, retaining `generate`; verify the package scripts and name in `package.json`.
- [x] 1.2 Configure Nuxt SSR and Nitro's static preset to prerender `/` and linked routes, failing on errors; verify the final `nuxt.config.ts` contains these settings.
- [x] 1.3 Document the static build command and `.output/public` deployment directory in the README; verify the README names both.
- [x] 1.4 Install dependencies, run the project check and static build, and confirm `.output/public/index.html` exists.
