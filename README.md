# AI Use-Case Prioritizer

A free, single-file tool that helps a team decide **which AI and automation ideas to fund first, and which to kill early.**

**Live demo:** <https://stephen-carras.github.io/ai-usecase-prioritizer/>

![Ranking and impact-vs-effort matrix](docs/screenshot.png)

## The problem

Most ops and IT teams have a long list of "we should use AI for X" ideas and no defensible way to choose between them. In practice:

- The loudest voice or the shiniest demo wins.
- Ideas are ranked on potential payoff while effort, data readiness and risk are ignored.
- Projects start with no definition of failure, so zombie pilots drag on for months.
- The reasoning lives in someone's head or a messy spreadsheet, so nobody can defend the decision later.

## What it does

1. **Score** each idea from 1 to 5 on impact, effort, risk, data readiness and strategic fit.
2. **Weight** what matters to your team with live sliders and watch the ranking change.
3. **Write down the two things most scorecards skip:** how the idea could fail, and the result that would make you stop (kill criteria).
4. **See** a ranked list and an impact-vs-effort matrix (quick wins, big bets, fill-ins, money pits).
5. **Export** a one-page summary of the top ideas as a PDF (print) or Markdown, a JSON backup, or a shareable link.

Ideas with no kill criteria, no failure mode, high impact resting on weak data, heavy effort for modest impact, or high risk are flagged automatically.

## How to use it

- **Online:** open the live demo.
- **Offline:** download `index.html` (or a release zip) and double-click it. No install, no server, no network.
- **Your own copy:** fork this repo and enable GitHub Pages (Settings, Pages, deploy from the `main` branch root).

## How scoring works

Each criterion is normalized to 0 to 1. For impact, data readiness and strategic fit a higher score is better; for effort and risk a lower score is better.

```
score = 100 x sum(weight_c x normalized_c) / sum(weight_c)
```

Ties are broken by higher impact, then lower effort. This is a decision aid, not an oracle: use it to structure the conversation and make the reasoning visible.

## Privacy

Everything runs in your browser. No analytics, no accounts, no uploads. Ideas are saved in your browser's local storage on your device. If you create a share link, your list is encoded into the URL itself, so anyone with the link can read it. Do not put confidential information in a list you plan to share.

## Limits

- Share links hold your whole list in the URL, so they work best for lists up to about 20 ideas. Use Export JSON for larger lists.
- Local storage is per browser and per device and can be cleared. Export JSON if you want a backup.
- Maximum 40 ideas per list.
- All example data is invented.

## Tech

One HTML file with vanilla JavaScript and inline SVG. No dependencies, no build step, no CDN. User text is rendered with `textContent`, never `innerHTML`, so shared links cannot inject markup.

## License

MIT. See [LICENSE](LICENSE).
