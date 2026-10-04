# Label Platform (free version)

Upload or scan any food or drink label, in any language, and see what's inside:
sugar, salt and fat as teaspoons, daily-limit bars, and every ingredient in label order
with plain-English notes. Live camera, diet modes and simple swaps included.

It runs on Google's free Gemini API, so it costs nothing.

## Run it on your computer (free)
1. Install Node.js 20.6 or newer.
2. Get a free key at https://aistudio.google.com/apikey (Google account, no card needed).
3. In this folder:
   ```
   npm install
   cp .env.example .env     # paste your key into .env
   npm run dev
   ```
4. Open http://localhost:3000

The camera needs https or localhost, so it works on your laptop. For a phone, deploy it (below).

## Put it online (free)
Use a host with a free plan that runs Node, for example Render, and check its current free-plan terms
(free plans usually "sleep" when idle, so the first visit can take about a minute).
1. Push this folder to a GitHub repo (`.env` is git-ignored, so your key stays private).
2. New Web Service -> pick the repo -> Build `npm install`, Start `npm start`, plan Free.
3. Add the environment variable `GEMINI_API_KEY`.
4. Deploy and share the https link.

## Things to know
- Free-tier limits are low and change often. Check yours at https://aistudio.google.com/rate-limit.
  `DAILY_CAP` (default 80 scans a day in total) and `SCANS_PER_HOUR` (default 10 per visitor) keep you inside them. Raise them if your limits allow.
- On the free tier, Google may use what is sent to improve its products, so don't scan anything private.
- If `MODEL` stops working, pick a current Flash model from https://ai.google.dev/gemini-api/docs/models and set it in `.env`.
- Photos are not saved by this server.
- Quantities: labels only print exact amounts in the nutrition table. Ingredient bar lengths show label order unless a % is printed.
- Results come from reading a photo and are not medical advice.

## Files
- `server.js` - API route `/api/scan`, limits, the label-reading prompt
- `public/index.html` - the whole front-end
