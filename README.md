# Asymmetric Bet Calculator

A single-file web app for sizing up the payoff profile of a trade. No build step, no dependencies, no network calls — everything runs in your browser.

## Running it

Open `index.html` in any modern browser (double-click it, or serve the folder with something like `python3 -m http.server` and visit `http://localhost:8000`).

## Using it

1. Fill in the inputs:
   - **Ticker** — symbol for the position (required to save).
   - **Entry price** — what you pay per share.
   - **Position size** — total dollars you're putting in.
   - **Bull-case target** — price you expect if the thesis plays out (must be above entry).
   - **Bear-case stop** — price where you're wrong and exit (must be below entry).
   - **Probability of bull case** — your estimate, 0–100%.
2. Results update as you type:
   - **Upside to target** — `(target − entry) / entry`
   - **Downside to stop** — `(entry − stop) / entry`
   - **Reward : risk** — upside % ÷ downside %
   - **Bull / bear-case P/L** — position size × upside %, and position size × −downside %
   - **Expected value** — `p × bull P/L + (1 − p) × bear P/L`, shown in dollars and as a % of position size
   - **Flag** — red if upside is under 150%, green otherwise.
3. Click **Save position** to add it to the table below. Click **Delete** on a row to remove it, or **Delete all** to clear the table.

Saved positions are stored in your browser's `localStorage`, so they persist across reloads on the same browser and device but aren't synced anywhere else. Clearing site data removes them.

The model is a simple two-outcome bet: it assumes the price ends at either the target or the stop. It ignores fees, slippage, taxes, and time.
