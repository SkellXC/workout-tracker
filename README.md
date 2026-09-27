# Workout Tracker

A Tkinter desktop app for logging weight training sets and viewing progress over time, backed by a local SQLite database.

## Requirements

- Python 3
- tkinter (included with most Python installs; on Linux, install separately, e.g. `sudo apt install python3-tk`)
- matplotlib
- numpy

## Setup

```
git clone https://github.com/SkellXC/My-NEA.git
cd My-NEA
pip install matplotlib numpy
python gui.py
```

`workout.db` is created automatically in the working directory on first run if it doesn't already exist.

## Usage

- **Home** — shows the last 4 sets logged today, and a button to open the progress graph.
- **+ (bottom bar)** — opens the exercise picker, grouped by muscle group (Chest, Back, Legs). Selecting an exercise opens its logging page.
- **Exercise page** — set weight and reps with the +/- controls (weight in steps of 5, reps in steps of 1), then Save to log the set with today's date.
- **Graph page** — pick an exercise from the dropdown and plot its logged weight over time (opens in a separate matplotlib window).
- **Settings** — KG/LBS toggle buttons are present but not yet wired to any functionality.

## Data

All sets are stored in a single SQLite table:

```sql
CREATE TABLE exercises (
    id INTEGER PRIMARY KEY,
    exerciseName TEXT NOT NULL,
    weight INTEGER NOT NULL,
    repetitions INTEGER NOT NULL,
    date TEXT NOT NULL
)
```

## Project structure

| Path | Purpose |
|---|---|
| `gui.py` | Entire application — UI, navigation, and database logic |
| `workout.db` | SQLite database, created/used at runtime |
| `.devdbrc` | Config for the DevDb editor extension, for inspecting `workout.db` directly |
| `Old/` | Earlier versions of the project kept for reference |

## Known limitations

- KG/LBS toggle in Settings doesn't change anything yet
- No way to edit or delete a logged set once saved
- Graph opens in a separate window rather than embedded in the app
