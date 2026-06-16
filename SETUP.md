# Setup Guide

This guide is the operating playbook for turning this repo into a new AI-assisted web app.

## Core Goal

Build beautiful, shippable software. The repo should help agents produce real product interfaces that are performant, accessible, coherent, and useful beyond a demo screenshot.

## Non-Negotiables

- A human chooses the 2-3 main base UI libraries for each project.
- Agents should not default to plain shadcn/ui as the full design system.
- Agents may use shadcn tooling or primitives when helpful, but the result should not feel like a generic shadcn reskin.
- Specialist libraries are allowed when they solve a clear use case and do not count against the 2-3 base UI library limit.
- Use current documentation before integrating frameworks, SDKs, auth, database tooling, CLIs, or cloud services.
- Prefer Better Auth for Next.js and similar full-stack TypeScript apps unless the user chooses otherwise.
- Use Effect for application logic patterns across tech stacks.
- Use [RTK](https://github.com/rtk-ai/rtk) where useful to reduce token cost during AI-assisted development.
- Use the user's package manager preference. If no preference or lockfile exists, prefer Bun.
- Make small, meaningful Git commits throughout development.

## First Decisions

Before implementation, identify:

- Product type: landing page, SaaS app, dashboard, internal tool, marketplace, AI app, ecommerce, travel app, analytics app, game, or other.
- Tech stack: framework, runtime, deployment target, database, auth, payments, background jobs, email, storage, and analytics.
- Package manager: Bun, pnpm, npm, or yarn.
- Base UI libraries: human-selected 2-3 libraries from the curated shelf.
- Specialist libraries: charts, maps, sound, typography, motion, data grids, 3D, payments, or other domain-specific tools.
- Visual direction: density, radius, typography, color energy, motion level, brand personality, and accessibility constraints.

If the base UI libraries are not selected, the agent can shortlist options but should ask the human to choose before committing to the primary design system.

## Package Manager Rules

Check for an existing lockfile before installing anything:

```bash
ls bun.lock bun.lockb pnpm-lock.yaml package-lock.json yarn.lock 2>/dev/null
```

Follow the detected package manager:

- Bun: `bun install`, `bun add`, `bunx`
- pnpm: `pnpm install`, `pnpm add`, `pnpm dlx`
- npm: `npm install`, `npm install <pkg>`, `npx`
- yarn: `yarn install`, `yarn add`, `yarn dlx`

Do not create multiple lockfiles. Do not switch package managers unless the user explicitly asks.

## Git Rules

Make commits actively throughout development. Good commit points include:

- Initial scaffold or framework setup
- Package manager and dependency setup
- Base UI library installation
- Design token setup
- Auth and database setup
- A completed product screen or major workflow
- Verification, accessibility, performance, or polish fixes

Keep commits coherent and reviewable. Do not bundle unrelated work into one large final commit unless the user explicitly asks for that workflow.

## Documentation Rules

Use Context7 MCP for current docs whenever integrating or configuring:

- React, Next.js, Remix, Astro, Vite, SvelteKit, Nuxt, Express, Hono, or similar frameworks
- Better Auth
- Prisma, Drizzle, Neon, Supabase, Postgres libraries, or other database tooling
- Effect
- Tailwind CSS and UI/component libraries
- SDKs, APIs, CLI tools, and cloud services

Context7 flow:

1. Resolve the library ID with the library name and the user's exact question.
2. Pick the best matching current docs source.
3. Query docs with the full task context.
4. Implement using the fetched docs.

If Context7 does not have a useful source, use official docs or the library's own documentation.

## UI Library Policy

### Base UI Libraries

Base UI libraries shape the application's visual system. Use 2-3 at once only when they can be made coherent.

When comparing base libraries, check:

- Border radius and component geometry
- Typography defaults and density
- Color model and dark mode behavior
- Animation style and duration
- Form controls, menus, dialogs, tables, cards, nav, and command surfaces
- Accessibility defaults
- Installation complexity and maintainability
- Runtime performance and bundle impact
- Whether the components are genuinely useful in real product screens

Avoid combining libraries when their defaults clash too much in radius, motion, spacing, or visual language.

### Specialist Libraries

Specialist libraries can be added when the product needs them. They do not count as base UI libraries.

- [EvilCharts](https://evilcharts.com/) for charts.
- [FlightCN](https://flightcn.yencheng.dev/) for flight, travel, map, and location-oriented interfaces.
- [SoundCN](https://soundcn.xyz/) for subtle sound feedback.
- [Font Trio](https://www.fonttrio.xyz/) for font pairing.
- [Fluid Functionalism](https://www.fluidfunctionalism.com/) for fluid interactions and motion.
- [Animate UI](https://animate-ui.com/) for selective animation components.

Use these only when they fit the product. Do not add them just because they look impressive.

## Curated UI Shelf

Human-selected base UI candidates:

- [Asanshay DS](https://ds.asanshay.com/)
- [Beste UI](https://ui.beste.co/)
- [BeUI](https://beui.saura3h.xyz/)
- [BundUI](https://bundui.io/)
- [Cult UI](https://www.cult-ui.com/)
- [Componentry](https://www.componentry.fun/)
- [Cubby UI](https://www.cubby-ui.dev/)
- [Eldora UI](https://www.eldoraui.site/)
- [Emerald UI](https://www.emerald-ui.com/)

Useful optional enhancers:

- [Animate UI](https://animate-ui.com/)
- [SoundCN](https://soundcn.xyz/)
- [Font Trio](https://www.fonttrio.xyz/)
- [Fluid Functionalism](https://www.fluidfunctionalism.com/)
- [EvilCharts](https://evilcharts.com/)
- [FlightCN](https://flightcn.yencheng.dev/)

## Effect Policy

Use [Effect](https://effect.website/) for robust TypeScript application architecture where appropriate:

- Typed errors and recoverable failure paths
- Services and dependency layers
- Background jobs and workflows
- Data fetching and integration boundaries
- Validation and reliable domain logic

The large local Effect reference is available at:

```text
llms/effect-ts-llm.txt
```

It was downloaded for local agent reference. Do not load the entire file into context casually. Read only targeted sections when needed.

## Auth and Database Policy

For Next.js or similar full-stack apps:

- Prefer Better Auth.
- Use Context7 for Better Auth docs before setup.
- Use the installed Better Auth skills when available.
- Use Context7 for Prisma, Drizzle, Neon, Supabase, or other database libraries before setup.
- Make auth flows production-minded: sessions, CSRF posture, OAuth configuration, email/password rules, organization support, 2FA, and environment variables should be explicit.

## Skills Policy

This repo includes installed local skills in `.agents/skills`.

Expected skill coverage:

- Better Auth setup and best practices
- Email and password auth
- Two-factor auth
- Organization and RBAC patterns
- shadcn tooling
- Accessibility
- SEO
- Web best practices

Install additional skills with:

```bash
npx add-skill pproenca/dot-skills --list
npx add-skill pproenca/dot-skills --skill <skill-name>
```

Use project-local skills when they directly apply. Do not install unrelated skills just in case.

## Agent Workflow

1. Read [README.md](README.md), [SETUP.md](SETUP.md), and [AGENTS.md](AGENTS.md).
2. Detect the project stack and package manager.
3. Confirm or request the human-selected base UI libraries.
4. Fetch current docs with Context7 for the libraries and tools being installed.
5. Scaffold or update the app using the selected package manager.
6. Establish shared design tokens: radius, fonts, colors, shadows, spacing, motion timing, and icon style.
7. Build real product screens, not a marketing placeholder unless the user asked for one.
8. Commit meaningful milestones as the app takes shape.
9. Verify mobile and desktop layouts.
10. Run tests, type checks, linting, and build checks when available.
11. Update docs with any app-specific setup notes.

## Visual Quality Checklist

Before handoff, check:

- The first viewport communicates the actual product or app immediately.
- Components from different libraries feel like one system.
- Text fits in buttons, cards, tables, sidebars, modals, and mobile views.
- Loading, empty, error, disabled, hover, focus, and active states exist where users expect them.
- Motion is smooth and purposeful.
- Keyboard navigation works for interactive flows.
- Contrast is acceptable.
- The app is responsive across mobile and desktop.
- The build is shippable, not just visually interesting.

## Performance Checklist

Before adding a component library, consider:

- Does it ship excessive client JavaScript?
- Does it animate layout-heavy properties?
- Does it block interaction on first load?
- Does it require large global providers for tiny components?
- Is it easy to tree-shake?
- Can similar quality be achieved with a lighter specialist library or local component?

Avoid libraries that are laggy, hard to compose, or only impressive in isolated demos.

## Handoff Notes Template

When a project is ready, document:

- Stack and package manager
- Selected base UI libraries
- Specialist libraries used
- Auth and database choices
- Required environment variables
- Setup commands
- Test and build commands
- Deployment target
- Known tradeoffs or follow-up work
