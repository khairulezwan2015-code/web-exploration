# Page trace: github.com

## Total requests
- count: 91

## Largest resource
- file: `github.githubassets.com/assets/51944.985a9ad99c1fb4d2.module.css`
- size: (largest in the trace)
- type: CSS module bundle (GitHub's component styles for the main UI)

## Slowest request
- file: same CSS module
- time: (slowest in the trace)
- why I think it's slow: large CSS bundles parse slowly in the browser and block first paint until parsed; first-time fetch also has no cache, so the round-trip to GitHub's CDN adds latency.

## Non-200 responses (if any)
- none observed

## What I noticed
- The largest/slowest resource being a CSS module is more typical than I expected — usually people assume images or JS. CSS parse is on the critical rendering path, so a large stylesheet delays the first visible paint.
- 91 requests is on the low end for a heavy modern site (GitHub bundles aggressively).