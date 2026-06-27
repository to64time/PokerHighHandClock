# Fortune Casino — High Hand Clock

In-room High Hand promotion display + operator control. One tablet runs everything and **mirrors to the TV** (AirPlay / Chromecast / HDMI). No accounts, no server, no build step — a single `index.html`, just like the tournament clock.

## 🟢 Live site

**https://to64time.github.io/PokerHighHandClock/**

Hosted free on GitHub Pages — **auto-deploys on every push to `main`**. Open it on the tablet, Add to Home Screen for a chromeless launcher, then mirror to the TV.

## How it works

The whole app lives on one tablet. What's on the tablet screen is what shows on the TV. Three views:

1. **Clock view** (default — the TV display)
   - Fortune Casinos branding + `$100 – $250 HIGH HAND / Every 30 Minutes` banner
   - Big countdown **linked to the real wall clock** — awards always land on **:00 and :30** of the hour, never drift, and survive the tablet sleeping or the page reloading
   - `[ Table N ]` of the current high hand
   - 5 cards: face-down (crown backs) when idle, face-up when a hand is in
   - **Last 30 seconds flash red** for excitement
   - At **0:00** the alarm sounds, the winning hand + table holds on screen for **10 seconds**, then it clears to face-down and the next period is already counting down
2. **Enter Hand** — tap a table (1–15), tap exactly 5 cards, Submit. No player names. Replaces the displayed high hand.
3. **History** — log of past winners (time, table, the hand).

## Operator quickstart

1. Open the page on the tablet, **Add to Home Screen** for a chromeless launcher
2. Start mirroring the tablet to the TV
3. Tap **⛶** for fullscreen on the tablet
4. When a player hits a high hand: tap **＋ Enter Hand** → table → 5 cards → **Submit**
5. That's it — the clock runs itself off the real time. At :00/:30 it buzzes, shows the winner 10s, then resets.

The control bar sits at the bottom, dimmed so it stays subtle on the TV; tap the screen to brighten it.

## Settings (⚙)

Prize text · period length (minutes, aligned to the clock — 30 = top & bottom of the hour) · number of tables · sound on/off · end-of-period sound (pick from 10, ~1–2s each, tap to preview) · clear current hand.

## Stack

Single `index.html` + `fortune-casino-logo.png`. Vanilla HTML/CSS/JS, no frameworks. Web Audio for the alarm, Screen Wake Lock to keep the tablet awake, state saved to `localStorage`. Real Fortune Casino logo sits top-left; card-back crown is a small inline SVG. Add `?demo` to the URL to preview a sample winning hand without affecting saved state.

## Local hacking

Open `index.html` in a browser. For LAN testing on the tablet:

```bash
python -m http.server 8080
```

Then visit `http://your-laptop-ip:8080` from the tablet.
