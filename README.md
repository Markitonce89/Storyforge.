# StoryForge AI

**Your Story. Your Character. Your Universe.**

StoryForge AI helps creators build AI personas and storylines for faceless social media accounts. Pick a platform and niche, describe your persona in a few words, and StoryForge creates who they are, how they talk, what they post, and the ongoing story that keeps followers coming back.

## Features

- **AI Persona Creator** – fill in as much or as little as you like (only a name is required) and get a complete, original persona.
- **Profile bio** – sized for your platform, with an AI-generated label built in.
- **Consistent look** – a reusable image prompt so every generated photo looks like the same person.
- **Content plan** – content pillars, a posting voice, and five first posts with hooks, captions, hashtags and visual ideas.
- **Storyline** – an ongoing story arc broken into episodes, plus a secret revealed over time.
- **Gallery** – save personas, reopen their full profile anytime, copy them as text, or delete them. Saved in the browser for now.
- **Meet Seianna Monroe** – StoryForge's first AI persona. Fashion. Motorcycles. Freedom. And a past she doesn't talk about.

## Responsible use

Instagram, TikTok and YouTube require realistic AI-generated content to be labeled. StoryForge includes an AI-generated line in every bio it writes, and creators should also turn on each platform's own AI-content label when posting. Personas should be original, not copies of real people.

## How it works

```
StoryForge website  (GitHub Pages)
        ↓
Secure backend      (Cloudflare Worker – keeps the API key hidden)
        ↓
AI model            (Claude)
        ↓
AI persona, storyline, and posts
```

The API key never appears in the website's code. The site only talks to the backend, and the backend only accepts requests from the StoryForge site.

## Project files

| File | What it does |
|------|--------------|
| `index.html` | Homepage |
| `create.html` | AI Persona Creator |
| `gallery.html` | Saved personas |
| `worker.js` | Backend that calls the AI (deployed to Cloudflare, not GitHub Pages) |

## Setup

### 1. Website

1. In this repo, go to **Settings → Pages**.
2. Under **Branch**, choose `main` and `/ (root)`, then save.
3. The site will be live at the URL GitHub shows you in a minute or two.

### 2. Backend

1. Get an API key from [console.anthropic.com](https://console.anthropic.com).
2. In Cloudflare, go to **Workers & Pages → Create → Worker**, name it `storyforge-api`, and deploy.
3. Click **Edit code**, paste in `worker.js`, and deploy.
4. Under the Worker's **Settings → Variables and Secrets**, add a secret named `ANTHROPIC_API_KEY` with your key.
5. If your site uses a custom domain, add it to `ALLOWED_ORIGINS` at the top of `worker.js`.

### 3. Connect them

In `create.html`, replace `PASTE_YOUR_WORKER_URL_HERE` with your Worker's URL, for example:

```js
const API_URL = "https://storyforge-api.yourname.workers.dev";
```

> ⚠️ Never put your API key in any file in this repo. It belongs only in the Cloudflare secret.

## Roadmap

- [x] Homepage
- [x] AI Persona Creator
- [x] Gallery of saved personas
- [ ] Content calendar (weeks of posts from a persona's storyline)
- [ ] Story Creator (new episodes and plot twists for an existing persona)
- [ ] World Builder (locations and recurring side characters)
- [ ] User accounts so personas sync across devices
- [ ] Persona image generation

## License

© 2026 StoryForge AI. All rights reserved.
