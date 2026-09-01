# Many Voices — a collection

A simple, free, publicly-hosted archive of saved results from the Many Voices tool.
Each saved question becomes its own page, with the audio player, print button, and
"Verify source" links all still working — none of it depends on the live tool or an
API key, since these are the fully self-contained files the tool's "Save this result
as HTML" button already produces.

## What's in this folder

```
many-voices-site/
├── index.html       ← the landing page listing everything (don't need to edit this)
├── manifest.json     ← the list of entries — you edit this each time you add one
├── results/           ← put your saved .html files in here
│   └── .gitkeep       ← a placeholder so this empty folder uploads correctly; ignore it
└── README.md          ← this file
```

## One-time setup (all done through github.com, no command line needed)

1. **Create the repository.**
   Go to [github.com/new](https://github.com/new). Name it `many-voices` (or anything
   you like). Set it to **Public** — GitHub Pages on a free account only serves public
   repos. Leave everything else default, then click **Create repository**.

2. **Upload these files.**
   On your new repo's page, click **"Add file" → "Upload files"**, then drag in
   `index.html`, `manifest.json`, `README.md`, and the whole `results` folder
   (including the `.gitkeep` file inside it). Scroll down and click **Commit changes**.

3. **Turn on GitHub Pages.**
   Go to your repo's **Settings** tab → **Pages** (left sidebar, under "Code and
   automation"). Under **Build and deployment → Source**, choose **"Deploy from a
   branch."** Under **Branch**, choose **main** and folder **/ (root)**, then click
   **Save**.

4. **Wait about a minute**, then refresh that same Settings → Pages screen. It'll show
   your live URL, something like:

   ```
   https://YOUR-USERNAME.github.io/many-voices/
   ```

   That's the link you can now email to anyone — it opens in any browser, on any
   device, with no attachment involved at all.

## Adding a new saved result (every time after that)

1. In the tool, ask your question and click **"⭳ Save this result as HTML."** This
   downloads a file like `many-voices_is-there-a-god.html`.

2. In your GitHub repo, open the **results** folder → **Add file → Upload files** →
   drag in that file → **Commit changes**.

3. Open **manifest.json** in your repo (click it, then the pencil/edit icon) and add
   one entry for it, matching this exact shape:

   ```json
   [
     {
       "title": "Is there a god?",
       "file": "results/many-voices_is-there-a-god.html",
       "date": "2026-08-27"
     }
   ]
   ```

   If there are already entries in the file, add a comma after the previous entry's
   closing `}` and add your new `{ ... }` block right after it — the list still needs
   to be one big `[ ... ]` array. The `date` field just controls sort order (newest
   first) — use whatever date makes sense to you.

4. **Commit changes.** Within about a minute, your new entry appears automatically on
   the live index page.

## A couple of things worth knowing

- **This repo is public.** Anyone with the link — or who finds the repo directly — can
  read every saved result. Given the content (religious Q&A with sourced answers)
  that's probably fine, but worth knowing going in. A private version requires a paid
  GitHub plan.
- **`index.html` won't work if you just double-click it on your computer.** It loads
  `manifest.json` via a `fetch()` call, which requires a real `http(s)` origin — this
  is the same local-file restriction that's come up before with the live tool. It only
  works once it's actually being served by GitHub Pages (or any other real web server).
- Nothing here calls any API or costs anything to run — it's entirely static files,
  so there's no usage limit, no server to maintain, and no ongoing cost.
