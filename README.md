# Mood Diary

A small daily check-in page: 10 mood tick-boxes plus cycle tracking. Each entry is
committed straight into this repo as a JSON file under `data/entries/`.

## One-time setup

### 1. Put the page in the repo
Add `index.html` to the **Fluoxetine** repo (drag-and-drop on github.com, or commit it).

### 2. Make the repo Private
Settings → General → Danger Zone → **Change visibility → Private**.
This keeps your mood and cycle data readable only by you.

### 3. Turn on GitHub Pages
Settings → **Pages** → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.
After a minute your diary is live at:
`https://nicolaslekai.github.io/Fluoxetine/`

### 4. Create a token (so the page can save entries)
GitHub → your avatar → **Settings → Developer settings → Personal access tokens →
Fine-grained tokens → Generate new token**.
- **Repository access:** *Only select repositories* → choose **Fluoxetine**
- **Permissions → Repository permissions → Contents:** *Read and write*
- Set an expiry you're comfortable with, then **Generate** and copy it.

### 5. Add the token to the page
Open the diary, click the **⚙ gear**, paste the token, Save.
The token lives only in your browser (localStorage) — it is never written into the
page or the repo.

## Daily use
Open the page, tick what's true, add a note if you like, press **Save today's entry**.
A confirmation and a quick mood score appear. Entries land in `data/entries/`.

## How the data looks
Each save is its own file, e.g. `data/entries/2026-06-19_084500.json`:

```json
{
  "date": "2026-06-19",
  "savedAt": "2026-06-19T08:45:00.000Z",
  "answers": { "slept_well": true, "felt_low": false, "on_period": true, "period_day1": true, "...": false },
  "moodScore": 3,
  "note": ""
}
```

`moodScore` is a rough number: +1 for each positive box (slept well, energy, calm,
connected, moved/outside, good day), −1 for each tough one (low, anxious, irritable,
overwhelmed). It's just a quick signal, not a diagnosis.

## Notes
- Works on your phone too — open the Pages URL and add it to your home screen.
- To change the questions, edit the `QUESTIONS` / `PERIOD_QS` arrays in `index.html`.
