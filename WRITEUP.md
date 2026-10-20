# Building deaddates.com: A Project Writeup

## Overview

I built [deaddates.com](https://deaddates.com/), a free site where you type in a Grateful Dead show date and get every recording of that show from the Internet Archive, ranked so the likeliest best tape comes first. I'm a longtime Deadhead and a systems administrator, and I built it to teach myself to write software. It went from a single HTML file to a public site with its own domain in a couple of days.

## The problem

Finding a good tape of a show means digging through long lists. A popular show can have 20 or more recordings on the Internet Archive: soundboards, audience tapes, matrix mixes and remasters, all in no useful order.

Plenty of Dead sites already exist. I wanted one that goes straight from a date to the tapes and puts the most promising recording at the top.

## What it does

The site does one thing: it takes you from a date to the tapes.

- Search a single show by date, or browse a whole year (1965 to 1995) with one expandable card per show
- "Shows on this date" finds every show played on a calendar day across all the years the band toured
- A "Fire" score ranks each show's recordings, blending all-time views with listener ratings
- SBD (soundboard), AUD (audience) and MTX (matrix) tags, with filters that show how many of each exist
- A link to find each show on YouTube
- Shareable links to a search, a show, or one specific recording, which opens highlighted and scrolled into view

## How it works

It's a static site: plain HTML, CSS and JavaScript, with no framework and no build step. When you search, your browser asks the Internet Archive's public search API for matching recordings, scores and sorts them, and draws the results.

The code lives on GitHub, and GitHub Pages hosts it for free. The domain is registered at Porkbun, pointed at GitHub with DNS records, served over HTTPS and verified with GitHub. A second domain, deaddates.net, forwards to the main one.

Because every visitor's browser makes its own requests, there is no server of mine to run or pay for.

## Decisions and tradeoffs

Most of the interesting work was deciding how things should behave.

- **Fire score.** It multiplies a logarithm of all-time views by a smoothed rating. The logarithm keeps a few hugely popular tapes from drowning out everything else. The smoothing pulls ratings toward a neutral 3.5 until enough people have reviewed a tape, so one five-star review can't beat dozens of good ones. It's a starting point that I plan to tune by ear.
- **Source tags.** They come from naming conventions in the recording titles. When the name doesn't say, the site shows no tag rather than guess wrong.
- **YouTube.** Each show gets a search link instead of an API integration, because a key placed in a static site is visible to every visitor.
- **Cutting photos.** I dropped the photo idea. It would add clutter, and Google Images already covers it.
- **Fetching and drawing are separate.** Search results are stored once, so changing a filter re-sorts instantly without asking the Archive again.

## Problems I ran into

Most of what I learned came from things that broke.

- **Permission denied.** My terminal opened in a Windows system folder and refused to create my project. I moved to my own user folder.
- **"code" not recognized.** VS Code's PATH option was off at install. I reinstalled with it checked.
- **Fine locally, broken online.** I had forgotten to push the stylesheet. Now I run `git status` before every push.
- **Syntax errors.** A stray word and a misplaced line each stopped the whole page. The browser console named the line, and the fixes took seconds.
- **Stale styling.** The browser kept an old copy of my stylesheet. A hard reload fixed it, and a version number on the stylesheet link prevents it for visitors.

## What I learned and what's next

I learned the full loop of shipping a web project: write it, test it, commit it, push it, deploy it, and put it on a real domain. I also learned to read error messages instead of fearing them, and that deciding what not to build matters as much as what to build.

I built this with Claude as a coding partner. I chose the idea, made the design calls, tested everything and fixed the bugs I hit. Friends I shared it with said it was easier to use than the other Dead sites.

Next, I plan to tune the Fire score against shows I know well and act on what my first users ask for.
