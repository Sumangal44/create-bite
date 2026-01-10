# create-bite <a href="https://npmjs.com/package/create-bite"><img src="https://img.shields.io/npm/v/create-bite" alt="npm package"></a>
[![Node.js Package](https://github.com/Sumangal44/create-bite/actions/workflows/npm-publish.yml/badge.svg)](https://github.com/Sumangal44/create-bite/actions/workflows/npm-publish.yml)
> Zero-config scaffolder for modern web apps. Pick a framework + template and get a ready-to-run project in seconds.

- Interactive prompts with pretty, colorful UI
- Sensible defaults for TypeScript or JavaScript
- Quick start for React, Vue, Svelte, Solid, Preact, Lit, Qwik, and Vanilla
- Optional “immediate” install + dev server startup

## Requirements

- Node.js: 20.19+ or 24.12+

## Scaffolding Your First Project

> **Compatibility Note:**
> create-bite requires [Node.js](https://nodejs.org/en/) version 20.19+, or 24.12+. Some templates may require higher versions.

With npm:

```bash
npm create bite@latest
```

With yarn:

```bash
yarn create bite
```

With pnpm:

```bash
pnpm create bite
```

With Bun:

```bash
bun create bite
```

With Deno:

```bash
deno run -A npm:create-bite
```

Then follow the prompts!

## Non‑Interactive Examples

Skip prompts by passing options. For example, to scaffold a Vue app in `my-vue-app`:

```bash
# npm 7+, extra double-dash is needed:
npm create bite@latest my-vue-app -- --template vue

# yarn
yarn create bite my-vue-app --template vue

# pnpm
pnpm create bite my-vue-app --template vue

# bun
bun create bite my-vue-app --template vue

# deno
deno run -A npm:create-bite my-vue-app --template vue
```

Use `.` to scaffold into the current directory:

```bash
npm create bite@latest . -- --template react
```

Create into nested folders:

```bash
npm create bite@latest packages/web -- --template svelte
```

## CLI Options

Run `create-bite --help` to see the full help. Abridged:

```
Usage: create-bite [OPTION]... [DIRECTORY]

Options:
	-t, --template NAME                   use a specific template
	-i, --immediate                       install dependencies and start dev
	--interactive / --no-interactive      force interactive / non-interactive mode
```

Additional behavior:

- Directory handling: if the target exists and is not empty, you’ll be prompted to remove files or cancel. Passing `--overwrite` skips the prompt and removes existing files.
- Immediate mode: pass `--immediate` (or `-i`) to install deps and start the dev server right away.
- Package manager: detected automatically from your environment; you can still run the generated project with any manager.

## Available Templates

Each framework has TypeScript and JavaScript variants. TypeScript variants end with `-ts`.

- `vanilla`, `vanilla-ts`
- `vue`, `vue-ts`
- `react`, `react-ts`, `react-swc`, `react-swc-ts`, `react-compiler`, `react-compiler-ts`
- `preact`, `preact-ts`
- `lit`, `lit-ts`
- `svelte`, `svelte-ts`
- `solid`, `solid-ts`
- `qwik`, `qwik-ts`

You can use `.` for the project name to scaffold in the current directory.

## Troubleshooting

- “This is not the tsc command you are looking for”: ensure `typescript` is installed in your devDependencies if you run `tsc` yourself. The CLI does not require `tsc` to scaffold.
- ESM/CommonJS errors in custom scripts: generated templates default to ESM in most ecosystems. If you modify tooling, align `type` in `package.json` and use appropriate imports.
- Corporate proxies / network: if dependency install is slow or blocked, use `--no-immediate` to skip the install step and run it later with your proxy configuration.

## Contributing

Issues and PRs are welcome. See the repository: https://github.com/sumangalkaran/create-bite

## License

MIT © Sumangal Karan

## Releasing (Auto Publish)

This repo is configured to auto-publish to npm when you push a version tag like `v1.2.3`.

- Setup once:
	- Create an npm Automation token in your npm account.
	- Add it as a GitHub secret named `NPM_TOKEN` in the repository settings.
- Release steps:
	- Bump version locally: `npm version patch` (or `minor`/`major`).
	- Push the commit and tag: `git push && git push --tags`.
	- GitHub Actions will run tests, build, and `npm publish` automatically.

Local testing before release:

```bash
npm ci
npm test
npm run build
npm pack --dry-run
```
