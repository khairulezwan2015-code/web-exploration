# Page trace: github.com

## Total requests
- count: 91

## Largest resource
- file: user.json
- size: (largest in the trace)
- type: JSON API response (probably GitHub's `/user` endpoint with profile, settings, and feature flags)

## Slowest request
- file: user.json (same as largest)
- time: (slowest in the trace)
- why I think it's slow: it is one of the last requests to complete because the page waits on the user data before rendering authenticated UI; it also travels further (to a nearby API region) and includes a large payload.

## Non-200 responses (if any)
- none observed

## What I noticed
- `user.json` being both the largest and slowest is unusual — usually an image or JS bundle wins. This is likely because GitHub waits for the user authentication/session before rendering authenticated navigation, so this single API call blocks the rest of the page.
- 91 requests is on the low end for a heavy modern site (GitHub bundles aggressively).