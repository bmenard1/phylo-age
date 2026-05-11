# Phylo-Age & Geo-Age

Two mobile web apps that tell you how old the world around you is.

- **[Phylo-Age](index.html)** — photo of a plant → identified by [Pl@ntNet](https://plantnet.org/) → species → genus → family → order → broader clades plotted on a 500-million-year time axis.
- **[Geo-Age](rocks.html)** — your GPS location → bedrock formation + age from [Macrostrat](https://macrostrat.org/); optionally a photo of a rock → identified by [Claude vision](https://www.anthropic.com/). Both plotted on a log-scale 4.5-billion-year time axis with Earth-history anchors.

## Try them

Open `index.html` (plants) or `rocks.html` (rocks) in any modern browser. No build step. Each app is a single HTML file with all CSS/JS inlined.

API keys live only in your browser's localStorage:
- **Phylo-Age** needs a free [Pl@ntNet key](https://my.plantnet.org/) (500 IDs/day).
- **Geo-Age** works without a key for the bedrock lookup. Photo identification needs an [Anthropic key](https://console.anthropic.com/) (~$0.01 per photo).

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
| `index.html` | Phylo-Age (plants) — HTML + CSS + JS, no dependencies |
| `rocks.html` | Geo-Age (rocks) — HTML + CSS + JS, no dependencies |
| `favicon.svg` | Leaf icon |
| `README.md` | This file |
| `LICENSE` | MIT |

## Data sources

- **Plant family / order divergence times**: [TimeTree.org](http://www.timetree.org/), Magallón et al. 2015 (*American Journal of Botany*), Smith & Brown 2018, [OneZoom](https://www.onezoom.org/).
- **Bedrock geology**: [Macrostrat](https://macrostrat.org/) (CC-BY 4.0).
- **Geological time scale**: ICS chart v2023.
- **Plant identification**: [Pl@ntNet API](https://my.plantnet.org/).
- **Rock photo identification**: [Anthropic Claude](https://www.anthropic.com/).

Ages are family-level *crown ages* — when the lineage you're looking at became recognisably itself. A pine "is a pine" going back ~150 Myr; the species itself may be much younger.

## Limitations

**Phylo-Age** (plants)
- Pl@ntNet works best on close-ups of leaves, flowers, or fruit. Wide-shot forest photos often misidentify.
- The lineage database covers ~100 common plant families. If Pl@ntNet returns a family not in the database, you'll see the species name but no timeline.
- Species and genus ages are rough estimates — for popular taxa they're hand-curated; otherwise they're heuristics from the family age.

**Geo-Age** (rocks)
- The bedrock returned by Macrostrat is the geology *at the surface beneath your location* — what you literally pick up could be a glacial erratic, river cobble, or beach pebble that originated hundreds of km away. The bedrock age is the *local* answer, not always the rock-in-hand answer.
- Macrostrat coverage varies regionally — best for the US, Canada, and Europe; coarser in much of Africa, Asia, and the open ocean.
- Photo-based age estimates from Claude are heuristic guesses; trust the location-derived age more.

## License

MIT — see [LICENSE](LICENSE).
