# School Clubs and Activities

A lightweight, Greek-language information page for the clubs and activities of
the Public Onassis Lyceum of Rhodes (ΔΗΜ.Ω.Σ. ΓΕΛ Ρόδου). Visitors can browse
club cards, filter them by day and school year, and open a detail view with a
full description, image, and optional video.

## Features

- Responsive layout for desktop and mobile screens.
- Club cards populated from `clubs.json`.
- Filters generated from the days and classes present in the data.
- Detail modal with club information and optional video playback.
- No framework, package manager, build step, or external runtime dependency.

## Run locally

The page loads `clubs.json` with the browser Fetch API, so serve the project
through a local web server rather than opening `index.html` directly.

For example, with Python installed:

```sh
py -m http.server 8000
```

Then open <http://localhost:8000> in a browser. Alternatively, use a static
file server such as the VS Code Live Server extension.

## Project files

| File or folder | Purpose |
| --- | --- |
| `index.html` | Complete single-page application, including styles and JavaScript. |
| `clubs.json` | The club data displayed by the page. |
| `clubs-sample.json` | Example of the expected club data structure. |
| `images/` | School branding and images used by club cards and details. |
| `video/` | Video files referenced by club entries. |

## Club data

Edit `clubs.json` to add or update clubs. It must contain a JSON array. Each
entry uses these properties:

| Property | Type | Purpose |
| --- | --- | --- |
| `title` | string | Club name. |
| `teacher` | string | Responsible teacher. |
| `days` | array of strings | Meeting days; used to create the day filters. |
| `classes` | array of strings | Eligible school years; used to create the class filters. |
| `shortDescription` | string | Summary shown on the club card. |
| `description` | string | Full text shown in the detail modal. |
| `image` | string | Optional path to an image, relative to the project root. |
| `video` | string | Optional path to a video, relative to the project root; use `""` when there is none. |

Example:

```json
{
  "title": "Όμιλος Φωτογραφίας",
  "teacher": "Ονοματεπώνυμο εκπαιδευτικού",
  "days": ["Τρίτη"],
  "classes": ["Α΄ Λυκείου", "Β΄ Λυκείου"],
  "shortDescription": "Μια σύντομη παρουσίαση του ομίλου.",
  "description": "Περισσότερες πληροφορίες για τις δραστηριότητες του ομίλου.",
  "image": "images/photography.jpg",
  "video": ""
}
```

Use valid JSON (including double quotes and commas between properties). Keep
asset paths relative to the project root and ensure their spelling and
capitalization match the actual filenames. Days and class names are displayed
as written, so use consistent labels across entries.

## Updating and publishing

1. Update `clubs.json` and add or replace any referenced files under `images/`
   or `video/`.
2. Preview the page using a local web server.
3. Publish the project directory to any static web host. Keep `index.html`,
   `clubs.json`, and the asset folders together; the site does not require a
   server-side application.
