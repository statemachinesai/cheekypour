# CheekyPour landing page

A standalone, responsive HTML/CSS page for the open robotics Guinness-pouring benchmark. No build step or dependencies are required.

From the repository root, start the local preview:

```sh
python3 -m http.server 3000 --bind 127.0.0.1 --directory landing
```

Open http://localhost:3000. Stop the server with Ctrl+C.

This directory contains the standalone landing page. The leaderboard and community attempt gallery are future work.

The hero video is `assets/robot-pour.mp4`, an optimized H.264 web copy of `IMG_3481.mov` (about 1.3 MB), with `assets/robot-pour-poster.jpg` as its preview frame. The page displays it in a gentle 2:3 portrait crop aligned to the top, trimming only the bottom table space while retaining the full portrait source file. It autoplays muted on a loop. The source clip has no audio. Native browser controls let visitors pause or open fullscreen; `playsinline` keeps playback inline on mobile.
