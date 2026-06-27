# Fortune Poker — High Hand Clock

In-room High Hand promotion display + operator control for the poker room. Counts down to the next high-hand award, shows the current qualifying hand and prize, and lets the floor run the promo.

> 🚧 **Design phase.** Repo scaffolded; app not built yet. See "Planned design" below — decisions locked, implementation next.

## Planned design

| Decision | Choice |
| --- | --- |
| Codebase | New standalone repo (separate from [PokerTournamentClock](https://github.com/to64time/PokerTournamentClock)) |
| Displays | **TV display** (public clock) **+ operator device** (phone/tablet), kept in sync |
| Promo format | **Fixed-interval drawing** — every _X_ min the highest qualifying hand of the window wins $_Y_; clock counts down, alarms, resets |
| Operation | **Floor staff control panel** — start/pause/reset, set prize & interval, record winning hand + table/seat; public display stays clean |

### Open design questions (next discussion)
- **Sync mechanism** for TV ↔ operator device (Supabase realtime, like SwingStakes? or a lighter option?)
- Qualifying hand minimum (e.g. quads minimum? full house?) and how the current high hand is entered/displayed
- Schedule: promo start/end times, what happens between windows, end-of-night behavior
- Multiple tables — does the operator log which table/seat won?
- Branding: reuse Fortune Poker logo + dark cyan/gold theme from the tournament clock

## Stack (planned)

Following the tournament clock's proven approach: aiming for a lightweight single-page web app (vanilla HTML/CSS/JS, Web Audio for alarms, Wake Lock to keep the TV awake), deployed on Vercel with auto-deploy on push to `main`. Sync layer TBD.

## Local hacking

Just open `index.html` in a browser. For LAN testing on a tablet/TV:

```bash
python -m http.server 8080
```

Then visit `http://your-laptop-ip:8080` from the device.
