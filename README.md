# Marjan Chavdarov

I build data pipelines — pulling data out of websites and documents that don't
want to give it up, and turning it into something structured, queryable, and
trustworthy.

**Python · Playwright · PostgreSQL / pgvector · LLM extraction**

Most of the interesting work is in the parts nobody demos: making a job safe to
re-run, refusing to write a bad row, and knowing *why* a result ranked where it
did.

---

## What I've built

### [resilient-scraper](https://github.com/marjanchavdarov/resilient-scraper)

A crawler that is safe to interrupt and safe to re-run, built around a real bug:
a scrape that logged only successes, so it silently redid roughly **80% of its
work on every run** while reporting healthy progress the entire time. The fix is
one table — and an entire module exists to make the mistake impossible again.

`21 tests · runs offline · no network required`

### [document-extract](https://github.com/marjanchavdarov/document-extract)

LLM extraction from documents, with validation and a bounded repair loop.

The premise: **structured outputs guarantee the shape of a response, not its
content.** A model constrained to a schema will always return the right keys and
the right types — and will still return `0` for a number it couldn't find and
`"N/A"` for a date it never read. Both validate perfectly. Both are wrong.

`23 tests · runs offline · no API key required`

### [semantic-match](https://github.com/marjanchavdarov/semantic-match)

Ranking by embedding similarity **and** explicit domain signals, with every
score explaining its own components.

Similarity measures topical closeness, not fitness — two candidates can sit on
top of each other in embedding space and differ completely in whether they're a
good match. A bare `0.72` is unarguable; `0.72, mostly prior history` can be
checked, disputed, and fixed.

`25 tests · runs offline · no database required`

### [links-pricewatch](https://github.com/marjanchavdarov/links-pricewatch)

A price monitor for a retail catalogue whose product grid **is not in the served
HTML at all** — so it drives a real browser, waits for the grid, and parses the
rendered DOM. Checks `robots.txt` before every request and fails closed; paces
requests; identifies itself honestly.

`12 tests · respects robots.txt`

---

Every repository runs its demo with a single command, offline, with no
credentials. That's deliberate — if a reviewer has to configure something to see
whether the code works, they won't.

**Get in touch:** marjanchavdarov@gmail.com
