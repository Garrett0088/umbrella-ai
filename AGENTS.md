# AGENTS.md

Guidance for AI coding agents (Claude Code, Codex, and others) working in this repo.

## What this is

Umbrella AI is a one-page decision tool: "Should I bring an umbrella today?" It started as a class project at CSTU. Keep it small, fast, and fun.

## Structure

- `index.html`: the entire app, with HTML, CSS, and JavaScript in one file.
- `README.md`: user-facing overview.
- No build step, no framework, no package manager. Keep it that way unless the owner asks.

## Rules that must not break

1. **One scoring model.** The `MODEL` object in `index.html` is the single source of truth for every point value. Buttons, slider ticks, the formula line, the heatmap, and the rain animation all read from it. Never hard-code a point value anywhere else.
2. **Linear scoring.** Score = forecast + time + door view + mood. No hidden overrides or special cases. If a behavior needs to change, change the weights.
3. **Result bands.** 3 or less is No umbrella, 4 to 6 is Take a chance, 7 to 9 is Hoodie, 10 or more is Must bring. If you change a band, update the Dev mode labels and the README.
4. **AI and Dev mode run the same math.** The toggle only changes what's visible. Never branch the calculation on the mode.
5. **Live updates.** Every input change updates the result immediately. No submit button.
6. **Rain follows the score.** The animation's frequency and drop size scale with the same score range as the heatmap.

## Quality floor

- All option buttons stay the same width and height.
- Keyboard focus is visible on every control.
- Respect `prefers-reduced-motion`: no rain animation when it's set.
- Works on phones down to about 360px wide.
- Plain, friendly copy. Commas over em dashes.

## Secrets

- Never commit API keys, tokens, or `.env` files.
- This site runs on GitHub Pages, which serves static files only. Any key used in browser code is public. Prefer keyless APIs. If a keyed API is needed, route it through a small proxy (for example a Cloudflare Worker) and add a `.env.sample` listing the variable names only.

## v2 roadmap

- Weather API pre-selects the forecast button from the chance of rain. The user can still override it.
- Browser geolocation, with permission, for the local forecast.
- Separate rain chances for the morning trip and the trip home.
- Remember the user's usual commute time.
- Editable weights in Dev mode.

When adding API data, map it onto the existing buttons. Don't add new scoring inputs without updating the heatmap and README.

## Before you finish

- Open `index.html` and click through every button and slider stop in both modes.
- Check that the formula line and the highlighted heatmap cell match the result shown.
- Check the browser console for errors.
