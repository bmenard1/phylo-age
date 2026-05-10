# Phylo-Age

Take a photo of a plant. See how deep into time its lineage runs.

A single-file mobile web app: snap a photo, the plant gets identified by [Pl@ntNet](https://plantnet.org/), and you see species → genus → family → order → broader clades plotted on a 600-million-year time axis.

## Try it

Open `index.html` in any modern browser (or [host it as a static site](https://pages.github.com/) — there's no build step).

You'll need a free [Pl@ntNet API key](https://my.plantnet.org/) for identification (500 IDs/day on the free tier). The key lives only in your browser's localStorage.

## How it works

```
photo → Pl@ntNet → species + family
              ↓
       lineage lookup (≈100 plant families curated)
              ↓
   species · genus · family · order · seed plants ·
   vascular plants · land plants · etc.
              ↓
   horizontal timeline, oldest lineages on the left,
   "now" on the right, banded by geological period
```

Each lineage entry is a horizontal "lifeline" running from when that clade emerged up to today. A 470-million-year-old land-plant lineage stretches the full width of the chart; a 50-million-year-old daisy family is a short stub on the right.

## What's in the repo

| File | What it is |
|---|---|
| `index.html` | Entire app — HTML + CSS + JS, no dependencies |
| `README.md` | This file |
| `LICENSE` | MIT |

## Data sources

- **Family / order divergence times**: [TimeTree.org](http://www.timetree.org/), Magallón et al. 2015 (*American Journal of Botany*), Smith & Brown 2018, [OneZoom](https://www.onezoom.org/).
- **Geological time scale**: ICS chart v2023.
- **Plant identification**: [Pl@ntNet API](https://my.plantnet.org/).

Ages are family-level *crown ages* — when the lineage you're looking at became recognisably itself. A pine "is a pine" going back ~150 Myr; the species itself may be much younger.

## Limitations

- Pl@ntNet works best on close-ups of leaves, flowers, or fruit. Wide-shot forest photos often misidentify.
- The lineage database covers ~100 common plant families. If Pl@ntNet returns a family not in the database, you'll see the species name but no timeline.
- Species and genus ages are rough estimates — for popular taxa they're hand-curated; otherwise they're heuristics from the family age.

## License

MIT — see [LICENSE](LICENSE).
