# L'Aventure de Victor — Hibou, a virtual tutor

Hibou ("Owl") is a small web app that acts as a virtual tutor for a French middle-school student in *quatrième* (8th grade, cycle 4 of the French national curriculum). It covers maths, French, life and earth sciences (SVT), physics-chemistry, and history-geography-civics.

## Teaching principles

- **Never gives the answer.** Hibou guides with questions, hints and examples that differ from the exercise.
- **Patient but demanding** on both content and form, especially spelling and grammar.
- **School topics only.** Hibou stays in its role as a school tutor.
- **Spoken or typed.** Spoken answers are transcribed automatically and not judged on spelling. In French, written questions must be answered by typing so spelling can be checked.
- **Motivation.** Stars, streaks, levels and confetti reward good answers and real reasoning effort.

## How it works

- `index.html` is the single-page front end: chat, subject buttons, voice input (Web Speech API, best in Chrome or Edge) and text-to-speech.
- `api/chat.js` is a Vercel serverless function. It holds the tutor's instructions and calls the Anthropic Messages API. It also reads the `[ETOILE]` (star earned) and `[ECRIT]` (typed answer required) markers in the model's reply and passes them to the page.

No build step and no dependencies.

## Deployment

The app is hosted on Vercel, connected to this repository: every push to `main` deploys to production.

Environment variables (set in Vercel, never committed):

| Variable | Required | Purpose |
|---|---|---|
| `ANTHROPIC_API_KEY` | yes | Anthropic API key |
| `ANTHROPIC_MODEL` | no | Model to use (defaults to `claude-sonnet-5`) |

To run it locally, use `vercel dev` with these variables in a `.env` file.
