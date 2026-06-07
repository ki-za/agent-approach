This folder is to help me prep for an interview process that I will undertake
Role: Forward Deployed Engineer - building one agent per month with each of our subscribing practices

Arka.Works is a AI Consultancy firm that tyipcally works with Architecture Practices to guide them through the new world of AI

I believe they're starting to look into agentic workflows

What is this directory for:
- is to catch me up to getting a full grasp on Arka.Works' needs.
- is to record my approach to a hypothetical task that I would get working within this role.
- is to contain the files and context and shared language that we will need
- is to contain to prototype agent that I will be using for my proactive example project.

## Current stage: Svelte HTML slide set

All site/application files for the client-facing workshop board live in `src/site/`.

Purpose:
- build an HTML slide set for checking the bid workflow with an architecture practice
- use `DESIGN.md` as the visual/design-token source
- use `PRODUCT.md` as the product intent and tone source
- keep the artifact workshop-first: inspectable, correctable, human-accountable

Implementation notes:
- Svelte 5 + Vite + Bun
- prefer small components and explicit slide/page data
- validate Svelte components with `bun run check:svelte` from `src/site/`
- verify the app with `bun run build` from `src/site/`
