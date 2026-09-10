# red-dragon-im4car-proxy

Standalone Cloudflare Worker proxy for the IM4Car Partner API.

Public site: `red-dragon.by`

Upstream: `https://api.im4car.by/partner/v1`

The IM4Car token is never stored in this repository. The Worker reads it from the Cloudflare secret `IM4CAR_API_KEY`.

## Cloudflare secrets

Create these GitHub Actions secrets:

- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID`

Create this Cloudflare Worker secret:

- `IM4CAR_API_KEY`

## Tilda

After deployment set the catalog API base to the Worker URL plus `/api`, for example:

`https://red-dragon-im4car-proxy.<subdomain>.workers.dev/api`

Remove `API_KEY` from the Tilda code and remove the browser-side `Authorization` header.

## Proxied endpoints

`/api/reference`

`/api/brands`

`/api/listings`

`/api/cars`

Only GET and OPTIONS are accepted. Browser CORS is limited to `https://red-dragon.by` and `https://www.red-dragon.by`.
