# Agent Instructions

This repo is a cloneable starter for building beautiful, shippable web apps with AI assistance.

Before making app-level changes, read:

- [README.md](README.md)
- [SETUP.md](SETUP.md)

## Operating Rules

- Do not choose the main base UI libraries alone. Ask the human to select the 2-3 primary UI libraries unless they already did.
- Do not use plain shadcn/ui as the whole design system. shadcn can be useful tooling, but this repo is meant to avoid generic shadcn output.
- Specialist libraries such as charts, sound, maps, typography, and motion do not count against the 2-3 base UI library limit.
- Keep visual systems coherent across radius, spacing, typography, shadows, density, and motion.
- Prefer Bun if there is no user preference and no existing lockfile. Otherwise follow the existing lockfile.
- Do not mix package managers.
- Use Effect for TypeScript application logic patterns where appropriate.
- Use [RTK](https://github.com/rtk-ai/rtk) where useful to reduce token cost during AI-assisted development.
- Prefer Better Auth for Next.js and similar full-stack apps unless the user chooses another auth stack.
- Use installed skills from `.agents/skills` when relevant.
- Make small, meaningful Git commits throughout development after coherent milestones.

## Documentation Rules

Use Context7 MCP to fetch current documentation whenever working with a library, framework, SDK, API, CLI tool, or cloud service. This includes React, Next.js, Prisma, Drizzle, Better Auth, Tailwind CSS, Effect, database libraries, and component libraries.

Context7 flow:

1. Resolve the library ID.
2. Query docs with the full task context.
3. Implement from the fetched docs.

If Context7 does not have the needed source, use official documentation.

## Large LLM Reference

The file `llms/effect-ts-llm.txt` is intentionally large. Do not read it wholesale. Use targeted reads only when Effect-specific implementation details are needed.
