# MOA 2026 Competition Website

This repository contains the static website served through GitHub Pages.

## Leaderboard

The competition page is `index.html`. The **Leaderboard** button opens
`leaderboard.html`, which displays the Round 1 kernel leaderboards.

The website does not connect to MongoDB directly. It fetches public leaderboard
data from the separately deployed HTTPS API:

```text
https://micro2026-api.duckdns.org/api/leaderboard
```

The API, MongoDB connection, API key, and deployment configuration are managed
on the backend server and are intentionally not included in this repository.
Do not add database credentials or API keys to this repository.

## Submitting benchmark results

External benchmark servers send results to the backend API. See
[RESULTS_API.md](RESULTS_API.md) for the required JSON format, allowed kernel
names, temporary ranking logic, and a request example.
