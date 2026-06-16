# AI Premium Frontend

A cloneable starter repo for building beautiful, shippable web apps with AI assistance.

The goal is not to collect every trendy component pack. The goal is to give an AI agent a strong taste floor: useful libraries, consistent product-grade UI decisions, modern app architecture, and enough constraints to avoid generic "same as every other shadcn site" output.

## How It Works

1. Clone this repo when starting a new AI-built web app.
2. Pick the application stack, package manager, and deployment target.
3. Have a human choose the main 2-3 base UI libraries before implementation starts.
4. Let the agent use specialist libraries where the use case calls for them.
5. Make Git commits actively throughout development so progress is easy to review, revert, and ship.
6. Require the agent to read current docs before integrating libraries, especially auth, database, framework, and CLI tooling.
7. Build the actual product experience first, then verify responsiveness, accessibility, performance, and production readiness.

See [SETUP.md](SETUP.md) for the full operating guide.

## Design Philosophy

Most shadcn-style libraries fail this project if they are slow, hard to work with, visually indistinguishable from every other UI kit, or impressive only in demos but not useful in real landing pages or software.

This repo favors libraries that help an app feel finished:

- Components should be practical in real products, not just screenshots.
- Styling should be coherent across radius, spacing, density, animation, and typography.
- Motion should improve interaction quality, not make the app feel laggy.
- Human taste should choose the base UI system. Agents can recommend, but should not independently decide the core design stack.
- Specialist libraries do not count against the 2-3 base UI library limit when they solve a narrow problem like charts, sound, maps, or typography.
- Agents should inspect shadcn-compatible registries before choosing libraries so the selected stack has the essential components the product needs.

## Curated Library Shelf

### App Architecture

- [Effect](https://effect.website/) should be used across tech stacks for robust TypeScript application logic, workflows, error handling, and service boundaries.
- The local long-form Effect reference is downloaded at [llms/effect-ts-llm.txt](llms/effect-ts-llm.txt). It is intentionally large, so agents should not load it wholesale unless there is a very specific need.
- [RTK](https://github.com/rtk-ai/rtk) is recommended for reducing token cost while working with AI agents.

### Broad UI Candidates

These are hand-picked candidate UI/component libraries. A human should choose the main 2-3 for a project based on the product style and use case.

- [Asanshay DS](https://ds.asanshay.com/)
- [Beste UI](https://ui.beste.co/)
- [BeUI](https://beui.saura3h.xyz/)
- [BundUI](https://bundui.io/)
- [Cult UI](https://www.cult-ui.com/)
- [Componentry](https://www.componentry.fun/)
- [Cubby UI](https://www.cubby-ui.dev/)
- [Eldora UI](https://www.eldoraui.site/)
- [Emerald UI](https://www.emerald-ui.com/)
- [Fluid Functionalism](https://www.fluidfunctionalism.com/) can also be used as a general UI component library for components like buttons, accordions, badges, switches, and tables.

### Interaction, Motion, Sound, and Typography

- [Animate UI](https://animate-ui.com/) can help many projects, but use only the components that fit the product.
- [SoundCN](https://soundcn.xyz/) is optional, but useful for subtle product microinteractions in dashboards and actual software.
- [Font Trio](https://www.fonttrio.xyz/) is useful for font pairing and typography exploration.
- [Fluid Functionalism](https://www.fluidfunctionalism.com/) is also recommended for fluid animations and high-quality interaction patterns.
- [Web Haptics](https://github.com/lochie/web-haptics) can be used for tactile web microinteractions where supported. Device and browser support varies, so implementations should always degrade gracefully.

### Specialist Libraries

These are use-case libraries and do not count as base UI libraries.

- [EvilCharts](https://evilcharts.com/) for chart-heavy experiences.
- [FlightCN](https://flightcn.yencheng.dev/) for flight, travel, map, or location-specific surfaces.

## Auth, Database, and Docs

For Next.js or similar full-stack frameworks, prefer the Better Auth stack unless the user explicitly chooses another approach.

When setting up Better Auth, Prisma, Drizzle, database clients, framework APIs, SDKs, CLI tools, or cloud services, use Context7 MCP to fetch current docs first. Do not rely on memory for integration details.

## UI Coverage Checks

When evaluating shadcn-compatible UI libraries, inspect their registries before committing to the stack. Confirm the selected libraries cover the essential components the product needs, including buttons, inputs, forms, selects, dialogs, dropdown menus, tooltips, accordions, tabs, tables, badges, switches, navigation, empty states, loading states, and command/search surfaces.

## Skills

This repo already includes an `.agents/skills` directory and `skills-lock.json` for common frontend, auth, accessibility, SEO, and best-practices skills.

To discover and install additional skills:

```bash
npx add-skill pproenca/dot-skills --list
npx add-skill pproenca/dot-skills --skill <skill-name>
```

Use the package manager preferred by the user and already present in the target app. If none is chosen yet, Bun is recommended.

## Package Manager Policy

Do not mix package managers in the same app.

Preference order when no project lockfile exists:

1. User choice
2. Bun
3. pnpm
4. npm
5. yarn

When a lockfile already exists, follow it.

## Git Policy

Agents should make small, meaningful commits throughout development instead of waiting until the end of a large task. Commit after coherent milestones such as scaffolding, installing libraries, adding auth, building a major screen, or finishing verification fixes.

## Repository Contents

- [README.md](README.md): quick explanation of the repo and library shelf.
- [SETUP.md](SETUP.md): detailed setup and agent workflow.
- [AGENTS.md](AGENTS.md): concise rules for AI coding agents.
- [.agents/skills](.agents/skills): installed local skills.
- [skills-lock.json](skills-lock.json): lockfile for installed skills.
- [llms](llms): large local LLM reference material.
