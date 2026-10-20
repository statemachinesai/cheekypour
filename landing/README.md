# CheekyPour landing page

A standalone, responsive HTML/CSS page for the open robotics Guinness-pouring benchmark. No build step or dependencies are required.

From the repository root, start the local preview:

```sh
python3 -m http.server 3000 --bind 127.0.0.1 --directory landing
```

Open http://localhost:3000. Stop the server with Ctrl+C.

This directory contains the standalone landing page. The leaderboard and community attempt gallery are future work.

The hero video is `assets/robot-pour.mp4`, an optimized H.264 web copy of `IMG_3481.mov` (about 1.3 MB), with `assets/robot-pour-poster.jpg` as its preview frame. The page displays it in a gentle 2:3 portrait crop aligned to the top, trimming only the bottom table space while retaining the full portrait source file. It autoplays muted on a loop. The source clip has no audio. Native browser controls let visitors pause or open fullscreen; `playsinline` keeps playback inline on mobile.

## Cloudflare hosting

The root `wrangler.jsonc` configures Cloudflare Workers to serve this directory as static assets. No Worker script or build step is needed. `.assetsignore` excludes this README and macOS metadata from uploads.

In Cloudflare, open **Workers & Pages**, create an application, and connect the `statemachinesai/cheekypour` GitHub repository with these settings:

- Project name: `cheekypour`
- Branch: `feat/landing-page`
- Root directory: repository root
- Build command: leave empty
- Deploy command: `npx wrangler deploy`

After deployment, verify the generated `workers.dev` URL. Add `cheekypour.com` through the Worker's **Settings > Domains & Routes > Add > Custom Domain** when the domain is available in the same Cloudflare account.

For a manual deployment with Node.js and npm installed, run `npx wrangler login` and then `npx wrangler deploy` from the repository root.

See Cloudflare's [static asset configuration](https://developers.cloudflare.com/workers/static-assets/binding/) and [Git build settings](https://developers.cloudflare.com/workers/ci-cd/builds/configuration/).
