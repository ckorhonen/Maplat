<!-- OPENSPEC:START -->
# OpenSpec Instructions

These instructions are for AI assistants working in this project.

Always open `@/openspec/AGENTS.md` when the request:
- Mentions planning or proposals (words like proposal, spec, change, plan)
- Introduces new capabilities, breaking changes, architecture shifts, or big performance/security work
- Sounds ambiguous and you need the authoritative spec before coding

Use `@/openspec/AGENTS.md` to learn:
- How to create and apply change proposals
- Spec format and conventions
- Project structure and guidelines

Keep this managed block so 'openspec update' can refresh the instructions.

<!-- OPENSPEC:END -->

## Repository map and current toolchain

Keep the managed OpenSpec block above intact; read `openspec/AGENTS.md` for proposal-required changes and its explicit small-fix exceptions. The current implementation is the TypeScript/Vite `@maplat/ui` package: `src/` holds the UI, `demo/` examples, `assets/` resources, `scripts/build-sw.js` the service-worker build, and `openspec/` design/specification state. Older migration notes may describe retired Webpack/Jest behavior; use the current manifest and CI for commands.

Use Node 20 or 22 as in CI, pnpm >=9, and `pnpm install --frozen-lockfile`. Run `pnpm typecheck`, `pnpm test run` for a finite Vitest run, `pnpm build` for the package, and `pnpm build:demo` when the demo surface changes. `pnpm lint` is a fixing command: both ESLint and Prettier scripts write files, so inspect the diff and preserve unrelated work.

`pnpm dev` starts a service-worker watcher and Vite bound to the network. Use a controlled browser profile/map dataset, inspect rendering and interactions for UI changes, and distinguish coordinate/rendering evidence from live GPS or remote tile-provider behavior. Builds generate distribution files; include only intended artifacts. For Markdown-only work, inspect paths/links and run `git diff --check -- <changed-paths>`.

Complete the authorized change through relevant verification and repair of introduced failures. Resolve routine implementation choices directly; ask only for information or decisions that materially affect the result. If blocked, name the affected action and missing prerequisite, continue independent work, and close with changed paths, checks actually run, and unverified behavior.
