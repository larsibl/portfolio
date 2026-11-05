# portfolio

Personal portfolio built with [SvelteKit](https://svelte.dev/docs/kit) and [Svelte 5](https://svelte.dev/docs/svelte), prerendered with `@sveltejs/adapter-static` and hosted on GitHub Pages at <https://larsibl.github.io/portfolio/>.

## Developing

Install dependencies with [Bun](https://bun.sh) and start the dev server:

```sh
bun install
bun run dev

# or start the server and open the app in a new browser tab
bun run dev -- --open
```

Type-check the project:

```sh
bun run check
```

## Building

To create a production build in `build/`:

```sh
bun run build
```

Preview it with `bun run preview`. Production builds are served from the `/portfolio` base path, so open <http://localhost:4173/portfolio/>.

## Deploying

Every push to `main` deploys the site through the GitHub Actions workflow in [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml). It can also be run manually from the **Actions** tab.

Requirements:

- Repository **Settings → Pages → Source** must be set to **GitHub Actions**.
- `bun.lock` must be committed, as CI installs with `--frozen-lockfile`.

Because the site lives under `/portfolio`, build internal links with `resolve()` from `$app/paths` rather than hard-coding root-relative URLs:

```svelte
<script lang="ts">
	import { resolve } from '$app/paths';
</script>

<a href={resolve('/about')}>About</a>
```

If the site moves to a custom domain, change `paths.base` in `vite.config.ts` to `''`.
