# Super School AI: Discover news feed

This repo holds the stories shown in the **Discover** tab (Super TV) of the Super School AI app.
The app downloads `news.json` when the phone is online, keeps a copy, and works offline without it.
Nothing about the student is sent: the app only reads this file.

Feed address: https://abinashspace.github.io/super-school-ai-news/news.json

## Add a story

Add an object to `stories` in `news.json` and commit. Pages updates in about a minute.

| Field | Meaning |
|---|---|
| `id` | Unique, never reused, e.g. `f-2026-11-14-middle` |
| `group` | `little` (Classes 1-5), `middle` (6-8) or `senior` (9-12) |
| `date` | `YYYY-MM-DD`. The story shows from **4 PM on that date** until 3:59 PM the next day |
| `image` | Either `{ "bundled": "<key>" }` for a photo already in the app, or a new photo (below) |
| `en` | `headline`, `summary`, `body` (list of paragraphs), `why`, `think` |
| `ta` | `headline`, `body`, `why`, `think` in Tamil (the translate button uses it) |

If no story has today's date for a group, the app shows its built-in stories, so gaps are safe.
To withdraw a story, delete it from the file.

Bundled photo keys: goStones, retina, signboard, cyclone, ganFace, digidoug, codingKids, typing,
leaf, echo, protein, waymo, gavel, datacenter, faceGate, euParliament, programmer, indiaGate.

## A new photo

Put the file in `images/` (JPEG or WebP, under 300 KB, about 1000 px wide) and use:

```json
"image": {
  "file": "images/example.jpg",
  "caption": "What the photo shows",
  "captionTa": "Tamil caption",
  "author": "Photographer",
  "license": "CC BY 4.0",
  "source": "https://commons.wikimedia.org/wiki/File:..."
}
```

Only use photos with a free licence (public domain, CC0, CC BY, CC BY-SA) and always fill in
author, licence and source.

## Rules the app applies

- The file must be under 512 KB and valid JSON, otherwise the app keeps its previous copy.
- A story missing a headline, body or Tamil text is ignored.
- Review every story before publishing: students trust it.
