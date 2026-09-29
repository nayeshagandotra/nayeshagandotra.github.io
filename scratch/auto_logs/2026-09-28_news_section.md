# News section + BCTMP rename (2026-09-28)

- `_config.yml`: uncommented `announcements` (enabled, scrollable, limit 5).
- `_pages/about.md`: `news: true`, so the about layout renders the news block.
- `_news/`: deleted the three al-folio template announcements; added `bctmp_best_paper.md` (inline item, arXiv link to 2512.00939).
- `_projects/bctmp.md`: title "Behavioral CTMP" -> "Constant-Time Planning for Chaining Collision-Free Motion to Manipulation Behaviors" (new title; arXiv listing still shows the old one until updated); description -> Best Paper Award @ SARL workshop, IROS'26.
- `_includes/news.liquid`: replaced the `<table>` with a `<ul class="news-list">`; date shown as "Mon YYYY".
- `_sass/_layout.scss`: timeline styling (left rule, theme-colored dot, pill-shaped date badge), all using theme CSS variables so dark mode works.

Not verified with a local Jekyll build (no jekyll/bundle installed).
