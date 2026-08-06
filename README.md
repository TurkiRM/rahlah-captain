# Rahlah — Captain app

A static single-page app (`index.html`) for going online, accepting dispatched or offered
cars, and running trips. Talks to the [rahlah-backend](../rahlah-backend) API over HTTP +
WebSocket, and uses `sw.js` for push notifications — this repo has no server of its own.

## Before deploying

Open `index.html`, find this block near the top of the `<script>` tag, and set it to your
deployed backend's URL:

```js
const CONFIGURED_API_BASE = ''; // e.g. 'https://rahlah-backend.onrender.com'
```

Leave it blank for local testing — it falls back to `http://localhost:3000`.

## Push notifications need HTTPS

`sw.js` (the service worker that makes push notifications work) only registers on a
**secure context** — `https://` in production, or `http://localhost` for local testing.
If you deploy this to Render's static-site hosting, that's HTTPS automatically, so no
extra setup needed there.

## Run it locally

No build step, no dependencies:

```bash
npx serve .
```

## Deploying to Render

`render.yaml` is a **Static Site** Blueprint. On Render: **New → Blueprint**, point it at
this repo. Set `CONFIGURED_API_BASE` in `index.html` to your live backend URL *before*
committing and deploying.
