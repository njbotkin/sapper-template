# sapper-template

Issue: https://github.com/sveltejs/sapper/issues/835

A repro for a bug where `preload`s in `_layout.svelte` files fire too eagerly -- that is, they are needlessly marked as dirty.  Steps to repro:

- `git clone`
- `git checkout dynamic-route-layout-preload-bug`
- `npm i`
- `npm run dev`
- Open devtools for localhost:3000

Use the nav bar and go to `/one/two/ohai`.  Now navigate to `/one/two`.

Expected console output:

(empty)

Actual console output:

`/one/_layout.svelte preload fired`
`/one/two/_layout.svelte preload fired`

Note that (correctly) no preloads are fired when you navigate from `/one/two` to `/one`

Potentially helpful aside: if you remove return {} from preload in `_layout.svelte`, route preloads are always marked as dirty.  This could be considered a different bug, but I think it's closely related.