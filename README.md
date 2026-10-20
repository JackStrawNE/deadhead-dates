# Dead Dates

Pick a Grateful Dead show date (or a whole year) and find the available recordings on the Internet Archive, ranked by a "Fire" score.

**Live site:** https://deaddates.com

## What it does

- **Single show search:** choose a date and see every recording of that show.
- **Year browsing:** pick a year (1965 to 1995) and see its shows, each expanding to show its recordings.
- **On This Date** Search for all shows played on a specific day of the year.
- **Fire score:** recordings are ranked hottest first, using a score that blends all-time views with listener ratings.
- **Source tags:** recordings are labeled SBD (soundboard), AUD (audience), or MTX (matrix) when the naming makes that clear.
- **Source Filter** You can filter recordings by source type.
- **YouTube Links** There are now YouTube links for each show.  (This is only leading to a YouTube search, it does not mean that the show exists, or in what form it may exist.)
- **Shareable Links** There are now shareable links to specific recordings, dates and years.

## How the Fire score works

Each recording's score is the logarithm of its all-time views multiplied by a smoothed rating. The smoothing pulls ratings toward a neutral 3.5 until enough people have reviewed a recording, so a single 5-star review can't outrank a tape that dozens of people have rated highly. Using a logarithm keeps a few hugely popular recordings from drowning out everything else. The formula is a starting point and is meant to be tuned.

## Built with

Plain HTML, CSS, and JavaScript. There's no framework and no build step. Data comes from the Internet Archive's public search API, and the site is hosted on GitHub Pages.

## Run it locally

```
git clone https://github.com/jackstrawne/deadhead-dates.git
cd deadhead-dates
```

Then open `index.html` in a browser.

## Roadmap

- Tune the Fire score

## Why I Did This

I'm a longtime DeadHead in good standing, and wanted to learn how to vibe code a webpage.  This combined a lifelong passion with a new learning adventure!

## Notes

This site hosts no audio. It links to recordings on the Internet Archive, and all recordings belong to their respective sources and tapers. It's an independent fan project, not affiliated with the Grateful Dead or the Internet Archive.

This is a learning project, built with help from Claude (an AI assistant) as part of learning to code.