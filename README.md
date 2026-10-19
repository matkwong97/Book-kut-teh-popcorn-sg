# Book Kut Teh & Popcorn SG — V2

Cloudflare Workers project with static frontend and Workers AI backend.

## Deploy to your existing Cloudflare account

1. Extract this ZIP. Keep `public/`, `src/`, and `wrangler.jsonc` together.
2. Create a new GitHub repository and upload all project files, preserving the folders.
3. In Cloudflare Dashboard → Workers & Pages → Create → Worker → Import a repository (names vary), connect the GitHub repository.
4. Build command: leave blank. Deploy command: `npx wrangler deploy`. Root directory: `/`.
5. Ensure Workers AI binding named `AI` is configured (already declared in `wrangler.jsonc`). Deploy and visit your `workers.dev` URL.

### Alternative: terminal deployment

Install Node.js 20+, then in this folder run:

```sh
npx wrangler login
npx wrangler deploy
```

**Do not use Pages direct upload:** This project includes an API Worker and cannot work as an HTML-only Pages upload.

## Data and limitations

- Book search: Open Library. Movie search: Apple's iTunes Search API; catalog is broad but not exhaustive.
- AI: Cloudflare Workers AI, model `@cf/meta/llama-3.1-8b-instruct`. Free allocation, rate limits and availability are subject to Cloudflare's current terms. No secret API key is needed for this Workers AI binding.
- AI can make mistakes, including fabricated plot details or chapter structures. Prompts explicitly ask it to admit uncertainty and avoid invented quotes.
- Search autocomplete is based on live search results; bookmarks are saved in browser localStorage and are device-specific.
- QR images are cropped from user-provided screenshots. Always test both codes in a banking app before sharing.
- For movie search, Apple may return multiple editions, regional results, or no match for obscure films.
