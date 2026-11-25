# Jikan-AAR — Free Edge-Cached Jikan v4 REST API

[![Website](https://img.shields.io/badge/Live%20Portal-jikan.aarecords.tech-indigo)](https://jikan.aarecords.tech)
[![Base URL](https://img.shields.io/badge/API%20Endpoint-v4-emerald)](https://jikan.aarecords.tech/v4/anime/9253)
[![Zero API Key](https://img.shields.io/badge/Auth-No%20API%20Key%20Needed-blue)](https://jikan.aarecords.tech)
[![License: MIT](https://img.shields.io/badge/License-MIT-zinc)](LICENSE)

A **fast, free, drop-in Jikan v4 REST API mirror** with global edge caching and zero API keys required — hosted and maintained by **[Anime Akashic Records (AAR)](https://aarecords.tech)**.

---

## Why Jikan-AAR?
- **Drop-in Jikan v4 Compatibility:** Simply swap `https://api.jikan.moe/v4` with `https://jikan.aarecords.tech/v4` — identical JSON schemas and routes.
- **Zero API Keys Required:** Free public access for hobbyists, bots, apps, and open-source tools.
- **Global Edge Caching:** Served behind CloudFront + Redis/MongoDB caching layers with a dedicated multi-node proxy cluster for fast, reliable responses.
- **Rich Endpoints:** Anime, Manga, Characters, People, Episodes, Seasons, Top Charts, Genres, Producers, Reviews, and Recommendations.

---

## Quick Start

### `curl`
```bash
# Get Steins;Gate full metadata
curl "https://jikan.aarecords.tech/v4/anime/9253/full"

# Search anime
curl "https://jikan.aarecords.tech/v4/anime?q=frieren&limit=5"

# Get episode list
curl "https://jikan.aarecords.tech/v4/anime/9253/episodes"

# Get top airing anime
curl "https://jikan.aarecords.tech/v4/top/anime?filter=airing&limit=10"
```

### JavaScript / TypeScript
```js
const res = await fetch("https://jikan.aarecords.tech/v4/anime/9253/full");
const { data } = await res.json();
console.log(data.title, data.score, data.episodes);
```

### Python
```python
import requests

resp = requests.get("https://jikan.aarecords.tech/v4/anime", params={"q": "cowboy bebop", "limit": 3})
for anime in resp.json()["data"]:
    print(anime["mal_id"], anime["title"], anime["score"])
```

---

## Popular Endpoints

| Endpoint | Description |
| :--- | :--- |
| `GET /v4/anime/{id}` | Core anime metadata |
| `GET /v4/anime/{id}/full` | Full anime metadata with relations, themes & external links |
| `GET /v4/anime/{id}/episodes` | Paginated episode list |
| `GET /v4/anime/{id}/episodes/{ep}` | Individual episode details & synopsis |
| `GET /v4/anime/{id}/characters` | Characters & voice actors |
| `GET /v4/anime?q={query}` | Keyword search across anime |
| `GET /v4/manga/{id}/full` | Full manga / light novel metadata |
| `GET /v4/top/anime` | Top-ranked anime charts |
| `GET /v4/seasons/now` | Currently airing seasonal anime |
| `GET /v4/characters/{id}/full` | Character profile & appearances |

Full interactive documentation & playground: **[https://jikan.aarecords.tech](https://jikan.aarecords.tech)**

---

## Need Semantic Search, Episode/Scene Lookup, or Lore RAG?
Jikan v4 is built for structured **MyAnimeList metadata & keyword lookup**. If you need:
- **Semantic Plot & Memory Search** across **148,127** anime, manga, light novels, visual novels, manhwa, and manhua
- **Second-Exact Episode & Scene Retrieval** across **118,513 episodes** and **869,826 timestamped scenes** (`97.6%` In-Show Recall@10)
- **Vibe & Multi-Seed Recommendations** (`40% Story + 40% Vibes + 20% Strengths`)

Check out **[Anime Akashic Records (aarecords.tech)](https://aarecords.tech)**!

---

## Credits, Attribution & Data Disclaimer

**Important:** **We do not own, author, or claim ownership of the anime, manga, character, or review metadata served through Jikan-AAR.**

- **Data Source:** All anime/manga catalog data is sourced from **[MyAnimeList (myanimelist.net)](https://myanimelist.net/)**.
- **API Engine:** Powered by the open-source **[Jikan REST API (`jikan-me/jikan-rest`)](https://github.com/jikan-me/jikan-rest)** project created by the Jikan team. All credit for the Jikan parser, schema, and open-source API framework belongs to the Jikan maintainers and contributors.
- **Hosting & Edge Infrastructure:** Self-hosted, cached, and operated independently by **[Anime Akashic Records (AAR)](https://aarecords.tech)** as a free community mirror. Jikan-AAR is not officially affiliated with or endorsed by MyAnimeList or the official Jikan hosted service.

If you love Jikan, please consider starring and supporting the official **[jikan-me/jikan-rest](https://github.com/jikan-me/jikan-rest)** open-source repository!
