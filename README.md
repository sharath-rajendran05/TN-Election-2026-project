# Tamil Nadu Assembly Elections 2026 — Constituency Explorer

An interactive, fully offline single-file web app for exploring Tamil Nadu's 234 assembly constituencies across 38 districts, managing candidate profiles, and editing map labels.

## Features

- 🗺️ **Interactive Map** — click any district to zoom in; click any constituency to view candidates
- 🏷️ **Editable Labels** — drag district/constituency labels to reposition; control font, size, color, halo
- 👤 **Candidate Profiles** — detailed popup with education, party history, social contributions, potential
- ✏️ **Full Edit Mode** — add/edit/delete candidates, upload photos, edit constituency info
- 📱 **Mobile Ready** — works on phones via touch; no server needed
- 🔌 **Fully Offline** — single HTML file, no internet dependency after first load (fonts use Google Fonts CDN)

## Project Structure

```
tn_election_project/
├── index.html              ← Main application (self-contained)
├── data/
│   ├── constituencies.geojson   ← 234 constituency polygons (38 districts, corrected)
│   └── candidates.json          ← Candidate data keyed by AC number
├── .gitignore
└── README.md
```

> **Note:** `index.html` embeds both data files inline for offline use. The `data/` folder contains the source files for editing/updating data separately.

## Quick Start

### Run locally
Just open `index.html` in any modern browser — no server needed.

### Deploy to GitHub Pages
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/tn-election-2026.git
git push -u origin main
```
Then: GitHub repo → Settings → Pages → Branch: main → Save.
Your site will be live at `https://YOUR_USERNAME.github.io/tn-election-2026`

### Deploy to Netlify (drag & drop)
1. Go to https://app.netlify.com/drop
2. Drag the entire `tn_election_project/` folder onto the page
3. Get a public URL instantly

### Connect your own domain
On Netlify/Cloudflare Pages/GitHub Pages, go to the domain settings and add a CNAME record pointing to your host's URL.

## Data Format

### candidates.json
Keyed by AC number (integer as string):
```json
{
  "1": {
    "ac_name": "Gummidipoondi",
    "dist_name": "Thiruvallur",
    "candidates": [
      {
        "name": "Candidate Name",
        "age": 45,
        "party": "DMK",
        "partySymbol": "🌅",
        "partyColor": "#E31837",
        "alliance": "INDIA",
        "description": "Short bio",
        "photoUrl": "",
        "education": "",
        "previousParty": "",
        "socialContribution": "",
        "potentialContribution": ""
      }
    ]
  }
}
```

### constituencies.geojson
Standard GeoJSON FeatureCollection. Each feature has:
```json
{
  "properties": {
    "dist_name": "Thiruvallur",
    "ac_name": "Gummidipoondi",
    "ac_no": 1,
    "dt_code": "01"
  },
  "geometry": { "type": "Polygon", "coordinates": [...] }
}
```

## Updating Candidate Data
Edit `data/candidates.json` with real candidate information, then paste the updated JSON into `index.html` replacing the `const BASE_CANDS={...}` block. Or rebuild with the Python script below.

## Districts (38)
Ariyalur, Chengalpattu, Chennai, Coimbatore, Cuddalore, Dharmapuri, Dindigul, Erode, Kallakurichi, Kancheepuram, Kanniyakumari, Karur, Krishnagiri, Madurai, Mayiladuthurai, Nagapattinam, Namakkal, Nilgiris, Perambalur, Pudukkottai, Ramanathapuram, Ranipet, Salem, Sivaganga, Tenkasi, Thanjavur, Theni, Thiruvallur, Thiruvarur, Thoothukudi, Tiruchirappalli, Tirunelveli, Tirupattur, Tiruppur, Tiruvannamalai, Vellore, Viluppuram, Virudhunagar

## License
MIT — free to use, modify, and distribute.
