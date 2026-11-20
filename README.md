# FarmersBuddy

A Next.js + Firebase + Genkit (Gemini AI) app that helps farmers and buyers with
crop disease diagnosis, soil management advice, climate guidance, market price
prediction, and a voice assistant.

## Setup

1. Install dependencies:
   ```bash
   npm install
   ```

2. Configure your Gemini API key (required for every AI feature: disease
   diagnosis, soil advice, climate guidance, market prediction, voice
   assistant):
   ```bash
   cp .env.example .env
   ```
   Then open `.env` and paste in a free API key from
   https://aistudio.google.com/app/apikey

3. (Optional) Firebase: the app ships with a working demo Firebase project in
   `src/firebase/config.ts` so sign-up/sign-in and Firestore work out of the
   box. If you want to use your own Firebase project instead, replace the
   values in that file with your own project's config from the Firebase
   console.

4. Run the app in development:
   ```bash
   npm run dev
   ```
   The app will be available at http://localhost:9002

5. Build for production:
   ```bash
   npm run build
   npm run start
   ```

Climate guidance fetches current conditions and a 7-day forecast from Open-Meteo.
Enter a city or district for local weather; a state name uses its capital as a
representative weather point. Suggested crops are matched to the resolved Indian
state or territory and the current Kharif, Rabi, or Zaid season; check local
agriculture department guidance before planting.

Leaf diagnosis uses Gemini image analysis when `GEMINI_API_KEY` is configured.
Without a key or if the AI request fails, the app provides low-confidence visual
screening from the uploaded image's color patterns; this cannot identify the
crop species or confirm a disease. Disease-risk guidance also uses the entered
farm location's current weather and forecast; the location is not repeated in
the diagnosis result. Enter the plant name to tailor the disease description to
the reported crop; image symptoms and local weather are used to explain likely
causes and recommendations.

## Scripts

- `npm run dev` — start the Next.js dev server (with Turbopack) on port 9002
- `npm run build` — create an optimized production build
- `npm run start` — run the production build
- `npm run typecheck` — run the TypeScript compiler with no output
- `npm run lint` — run Next.js/ESLint checks
- `npm run genkit:dev` — start the Genkit dev UI to inspect/test the AI flows directly
