# red-dragon-im4car-proxy

Standalone Cloudflare Worker proxy for the IM4Car Partner API.

Public site: `red-dragon.by`
Upstream: `https://api.im4car.by/partner/v1`

The IM4Car token is never stored in this repository. The Worker reads it from the Cloudflare Secret `IM4CAR_API_KEY`.

## Create from GitHub in Cloudflare

Choose **Workers & Pages → Create → Worker → Connect to Git** and select this repository:

`reddragonminsk-stack/red-dragon-im4car-proxy`

Branch: `main`
Root directory: `/`
Build command: `npx wrangler deploy`
Build output directory: leave empty

The repository already contains `worker.js` and `wrangler.toml`.

Worker name:

`red-dragon-im4car-proxy`

## Worker secret

After the Worker is created, open **Settings → Variables and Secrets → Add → Secret** and create:

`IM4CAR_API_KEY`

Value: the new IM4Car Partner API key.

Do not put the key into GitHub files, GitHub Actions, or Tilda JavaScript.

## Tilda

After deployment the catalog should use the Worker URL as `API_BASE` with `/api`, for example:

`https://red-dragon-im4car-proxy.<subdomain>.workers.dev/api`

Remove `API_KEY` from the Tilda code and remove the browser-side `Authorization` header.

## Proxied endpoints

`/api/reference`
`/api/brands`
`/api/listings`
`/api/cars`

Only GET and OPTIONS are accepted. Browser CORS is limited to `https://red-dragon.by` and `https://www.red-dragon.by`.
