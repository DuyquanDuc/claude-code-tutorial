# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Japanese study tracker - a single-page web app that mimics GitHub's contribution heatmap to track study consistency. No build system or dependencies.

## Development

Open `index.html` directly in a browser. No server required.

## Architecture

Single `index.html` file containing:
- Inline CSS (GitHub dark theme styling)
- Inline JavaScript (vanilla, no frameworks)
- localStorage persistence under key `japanese-study-commits`

Data structure for commits:
```javascript
{ id: timestamp, message: string, date: ISO8601 }
```

## Key Functions

- `addCommit(message)` - saves a new study entry
- `getCommitsByDate()` - aggregates commits by date for heatmap
- `calculateStreak()` - computes current consecutive day streak
- `renderHeatmap()` - generates the 53-week contribution grid
- `render()` - main render function that updates all UI components
