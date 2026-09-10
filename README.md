# ankurjaiswal-aj.github.io

Personal academic website.

- **Live:** https://ankurjaiswal-aj.github.io
- **Repo:** https://github.com/ankurjaiswal-aj/ankurjaiswal-aj.github.io
- **Local:** `/Users/aj34868/Library/CloudStorage/Box-Box/#McCombs PhD/CV & Resume/website/`
- **Built on:** [academicpages](https://github.com/academicpages/academicpages.github.io) (Jekyll, MIT)

GitHub builds the site automatically on every push. You do not need to build
anything locally to publish — local preview is only so you can see changes
before they go live.

---

## 1. Quick reference

| I want to... | Edit this |
|---|---|
| Change homepage text | `_pages/about.md` |
| Add / edit a paper | a file in `_publications/` |
| Add / edit a talk | a file in `_talks/` |
| Add / edit a course | a file in `_teaching/` |
| Rename or reorder nav tabs | `_data/navigation.yml` |
| Change email, sidebar links, section headings | `_config.yml` |
| Post a PDF | drop it in `files/` |
| Change the look | `_sass/_custom.scss` |

**Do not edit:** `_includes/`, `_layouts/`, `_sass/` (except `_custom.scss`),
`assets/`, `Gemfile`. That is theme machinery.

---

## 2. Publishing

```bash
cd "/Users/aj34868/Library/CloudStorage/Box-Box/#McCombs PhD/CV & Resume/website"
git add -A
git commit -m "describe what changed"
git push
```

Live in roughly 40 seconds. Check the build:

```bash
gh api repos/ankurjaiswal-aj/ankurjaiswal-aj.github.io/pages/builds/latest --jq '{status, error: .error.message}'
```

`"status": "built"` means it worked. `"errored"` means it did not, and the
`error` field says why. GitHub also emails you on failure.

---

## 3. Previewing locally

Ruby lives in a conda environment called `jekyll` (Ruby 3.3.6, the same
version GitHub Pages uses).

```bash
conda activate jekyll
export SDKROOT="$(xcrun --show-sdk-path)"
cd "/Users/aj34868/Library/CloudStorage/Box-Box/#McCombs PhD/CV & Resume/website"
bundle exec jekyll serve
```

Open http://localhost:4000. Stop with Ctrl-C.

**Content edits refresh automatically when you save.**
**`_config.yml` edits do NOT.** Jekyll never reloads that file. Stop the
server and start it again, or your change will appear to do nothing.

If a gem ever fails to build, it is because `SDKROOT` was not set. Set it and
run `bundle install` again.

---

## 4. Adding a paper

Copy an existing file in `_publications/`, rename it, and edit. Filename
format is `YYYY-MM-DD-short-name.md` (the date in the filename is only for
your own sorting; the `date:` field inside is what the site uses).

```yaml
---
title: "Full paper title"
collection: publications
category: workingpapers
permalink: /publication/short-name
date: 2026-12-02
venue: "Target: Information Systems Research"
excerpt: ""
citation: "Jaiswal, A. and Coauthor, B. &quot;Title.&quot;"
authors: "With Coauthor Name"
---

The abstract goes here. Everything below the closing --- is the abstract.
```

### `category:` decides which tab it appears on

| Value | Tab | Section heading |
|---|---|---|
| `workingpapers` | Research | Working Papers |
| `readytosubmit` | Research | Manuscripts Ready to Submit |
| `workinprogress` | Research | Work in Progress |
| `conferences` | Publications | Refereed Conference Proceedings |
| `bookchapters` | Publications | Book Chapters |

Section names and their order are set in `_config.yml` under
`publication_category`.

### The other fields

- **`date:`** controls ordering only and is never displayed. Within a section,
  later dates appear first. To move a paper to the top of its section, give it
  a later date than its neighbours.
- **`venue:`** on Research shows the target journal. On Publications it shows
  the venue and year. Leave it `""` to hide the line.
- **`status:`** optional, appends to the venue line, e.g. `"Conditionally accepted"`.
- **`award:`** optional, renders a gold badge, e.g. `"Best Paper Nominee"`.
- **`link:`** optional. Adds a link on the title to the publisher record.
  Research titles are deliberately never linked.
- **`authors:`** the coauthor line. HTML links are allowed here — use single
  quotes around the value if it contains double quotes.
- **`excerpt: ""`** — **keep this.** See the gotcha in section 8.

---

## 5. Adding a talk

```yaml
---
title: "Talk title"
collection: talks
type: "Conference presentation"
permalink: /talks/2026-08-venue-city
venue: "Full conference name"
date: 2026-08-01
location: "City, State"
---
```

Newest first, by `date:`. Leave `location:` empty and it is omitted.

---

## 6. Adding a course

```yaml
---
title: "MIS 000: Course Name"
collection: teaching
type: "Undergraduate course"
permalink: /teaching/mis-000
venue: "The University of Texas at Austin, McCombs School of Business"
school: "The University of Texas at Austin"
role: "Teaching Assistant &middot; Fall 2026"
date: 2026-09-01
location: "Austin, Texas"
---
Enrollment note goes here.
```

`school:` groups the entry. The group order is hardcoded in
`_pages/teaching.html` — add a new school there.

---

## 7. Posting a PDF

Drop the file into `files/`. It is served verbatim at
`https://ankurjaiswal-aj.github.io/files/<filename>`.

**Job market paper.** The homepage already links to
`files/Jaiswal_JMP.pdf`. That link is live and returns 404 until the file
exists. Name the PDF exactly that and it starts working.

**CV.** `_pages/cv.md` has the download line commented out. Put the PDF in
`files/`, uncomment the line, update the filename.

Note: git does not track empty folders, so `files/` will not exist in the
repo until you put something in it.

---

## 8. Gotchas that already cost time

**`_config.yml` needs a server restart.** Jekyll deliberately does not reload
it. Symptom: you change a section heading, refresh, nothing happens.

**Never delete `excerpt: ""` from a paper that has an abstract.** Without an
explicit excerpt, Jekyll auto-generates one from the first paragraph of the
body — which is the abstract — and it renders twice on the page.

**Section headings must be direct children.** The burnt-orange bands are
styled as `.archive > h2` and `.archive .compact > h2`. If you wrap a heading
in another `<div>`, it silently loses its band. It cannot be `.archive h2`,
because paper titles are `h2` too and would all get bands.

**Raw HTML in a Markdown file needs `markdown="1"`** on the wrapping div, or
Markdown inside it stops being processed and `**bold**` renders literally.

**Hard-refresh after CSS changes.** Cmd-Shift-R. The browser caches the
stylesheet aggressively.

---

## 9. Styling

Everything custom is in `_sass/_custom.scss`, in labelled blocks:

- **UT palette** — burnt orange `#BF5700`. Dark mode uses a lighter `#FFA05C`
  because `#BF5700` on the dark background fails the accessibility contrast
  floor (2.03:1 against a 4.5:1 requirement).
- **Base type scale** — two numbers, `15px` / `16px`. The theme's defaults
  were 16/18. Everything else is sized in `em`, so these two scale the whole
  site.
- **Masthead** — white ground, orange links, 3px orange rule beneath.
- **Avatar** — 240px, 16px corner radius.
- Timelines, award badges, listing layouts.

---

## 10. SEO

Verified in Google Search Console via a meta tag in `_config.yml`
(`google_site_verification`). Do not remove it.

Sitemap is generated automatically at `/sitemap.xml`.

To check indexing, search Google for:

```
site:ankurjaiswal-aj.github.io
```

The site is linked from Google Scholar and ORCID, which is how Google finds it.
