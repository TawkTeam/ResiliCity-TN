# ResiliCity-TN — Flood Risk Early-Warning PoC

**Arab Youth Space Hackathon 2026 — Challenge 813**
Track: Climate Adaptation & Disaster Recovery · Data path: Hyperspectral (813 / EnMAP)

## What this is

ResiliCity-TN is an AI-powered early-warning platform for Tunisian cities, built on Space42's **GIQ**
geospatial platform. It fuses hyperspectral imagery (material classification of informal/tin-roof
construction), SAR (soil permeability and runoff), terrain data (DEM slope and drainage paths), and
rainfall timing to compute a composite flood-risk index per zone, and to flag where excess stormwater
could be redirected toward dams and aquifers instead of flooding neighborhoods.

Pilot area: **Zahrouni, Greater Tunis**, window **30 Aug – 1 Oct 2026**, which contains a documented real
flood event (16–18 September 2026; up to 80 mm of rain in a few hours on 17 September, per Tunisian civil
protection reporting).

## What's in this repo

| File | Purpose |
| --- | --- |
| `resilicity_tn_poc.ipynb` | End-to-end, already-executed notebook: rainfall data → per-zone composite risk index → alert logic → illustrative hyperspectral classification concept |
| `requirements.txt` | Pinned dependencies to re-run the notebook |
| `README.md` | This file |

## Running it

```bash
pip install -r requirements.txt
jupyter notebook resilicity_tn_poc.ipynb
```

The notebook runs top to bottom with no external network calls or credentials required — every input is
either a sourced, cited figure or a clearly labeled illustrative placeholder (see "Data honesty" below).

## Example input → output

**Input**: `2026-09-17`, rainfall = 80 mm (sourced), 5 pilot zones with static terrain/settlement scores.
**Output**: a per-zone risk table; in this example run, the **Riverside lowland** and **Central wadi
corridor** zones cross the High-risk threshold (index ≥ 65), triggering the alert condition the platform
would push to civil protection.

## Data honesty

- **Sourced**: the 17 September 2026 rainfall figure (up to 80 mm locally) and the flood event itself,
  from Tunisian civil-protection statements and news reporting (sources listed inside the notebook).
- **Illustrative placeholders**: daily rainfall on other days, the five zones' terrain/settlement scores,
  and the hyperspectral reflectance curves. These stand in for live GIQ feeds — IMERG/CHIRPS rainfall,
  Copernicus DEM slope analysis, and classified 813/EnMAP scenes — which were not accessible from this
  development environment. The **pipeline, formula, and code are fully real and reproducible**; only the
  inputs are placeholders where live data access was unavailable. Swapping in live data requires no change
  to the logic shown here.

## No credentials or restricted imagery

This repository contains no API keys, credentials, or restricted/licensed imagery. All data referenced is
either public reporting (cited in the notebook) or synthetic placeholder values clearly labeled as such.
