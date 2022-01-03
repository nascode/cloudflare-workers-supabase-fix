# Cloudflare Workers With Supabase Fix

*You don't need this anymore. Now, Supabase user can bind custom fetch implementation. See https://supabase.com/docs/reference/javascript/initializing#custom-fetch-implementation*

Cloudflare Workers is an amazing serverless platform to be used as your app backend. Supabase is a Firebase-alike database service using PostgreSQL. I though they are a good match that complement each other.

However, Cloudflare Workers does not support `XMLHttpRequest` object and only support native `fetch`. This makes Supabase JS Clients does not work on Cloudflare Workers. Supabase JS Client internally uses `cross-fetch` package to polyfill `fetch` which inside of it, uses `XMLHttpRequest`.

To resolve this, I use `patch-package` to patch `cross-fetch` package as minimal as possible. A bit hacky, but it works!

This repo contains minimal Cloudflare Workers project with the patch automatically applied.
