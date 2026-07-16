# BIGMEAT — The Collected Files

An interactive archive for the shared-universe fiction anthology. Single self-contained `index.html`, no build step, no dependencies (fonts load from Google Fonts over the network).

## What's in here

- **Archive** — every story as a "case file," sorted into continuity strands, with a reader.
- **The peanut gallery** — toggle in any readable file to pin the group-chat marginalia next to the passages they're reacting to.
- **The Map** — a live network graph of how every file wires to every other via shared characters and threads.
- **Personnel** — the recurring cast, cross-linked to every file each one appears (and dies) in.
- **The Ledger** — every named death, searchable and sortable by victim, cause, and method.
- **Timeline** — 1969 → 3019 AD, in order.
- **Lexicon**, **Acclaim**, **The Exam** — the private vocabulary, the fake blurbs, and the playable quiz.

---

## Get it online

### Option A — GitHub Pages (recommended, given your setup)

From inside this folder:

```bash
git init
git add .
git commit -m "BIGMEAT archive v1"
gh repo create bigmeat --public --source=. --push
```

Then turn on Pages:

```bash
gh api -X POST repos/{owner}/bigmeat/pages -f source[branch]=main -f source[path]=/
```

(or: repo → **Settings → Pages → Source: main / root**). Live in ~1 minute at
`https://<your-username>.github.io/bigmeat/`.

No `gh` CLI? Create an empty repo named `bigmeat` on github.com, then:

```bash
git init && git add . && git commit -m "v1"
git branch -M main
git remote add origin https://github.com/<your-username>/bigmeat.git
git push -u origin main
```

…and flip on Pages in Settings.

### Option B — Netlify (drag & drop, zero terminal)

Go to app.netlify.com → **Add new site → Deploy manually** → drag this whole folder onto the drop zone. Instant URL; optional custom domain (e.g. a real `bigmeat.com`).

---

## Add the full stories

Story text lives in hidden blocks near the bottom of `index.html`:

```html
<script type="text/plain" data-body="meatsquad"> ... paste raw text here ... </script>
```

To transcribe a file:

1. Find its entry in the `STORIES` array and set `body:"somekey"`.
2. Add a matching `<script type="text/plain" data-body="somekey"> ... </script>` block and paste the raw prose. Blank lines separate paragraphs. No escaping needed — quotes, `$`, and backticks are all safe inside these blocks.

## Add margin commentary

In the `COMMENTS` object, key by story id; `after` is the paragraph index (0-based) the note should follow:

```js
boodram: [ {after:2, text:"OH MY GOD NOBODY TALKS TO HIM"} ],
```

## Add a death, a character, a term

Everything is a plain array near the top of the script: `DEATHS`, `PEOPLE`, `STORIES`, `LEXICON`, `ACCLAIM`, `QUIZ`. Add an object, save, refresh. The map, ledger counts, and cross-references all recompute themselves.

---

*www.BIGMEAT.com · "Wong ran so that Meat Horror could walk."*
