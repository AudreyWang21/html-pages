---
name: html-pages
description: Standing preferences for HTML pages. Read whenever writing or planning any .html page — most often concept explainers for learning and project-planning pages, but equally reports, prototypes, dashboards, one-off editors and tools. Also read when a concept is proving hard to explain in prose (consider offering an interactive HTML explainer), or when several Markdown notes orbit one subject (consider offering to fold them into a single tabbed HTML page).
---

中文版：[SKILL.zh-CN.md](SKILL.zh-CN.md)

# HTML Pages

Definition of done: an `.html` page that presents its specific content the best way that content can be presented — designed from the information outward. Each page stands alone, but a larger effort can be a web of linked pages rather than one file straining to hold everything.

## Personal preferences (the author's; edit to taste)

- Canadian English spelling.
- Special terms are appreciated bilingual — English with the Simplified Chinese beside it — on first appearance and in term lists; ordinary prose stays English. Where they help, add the IPA for a term that's hard to pronounce (Latin names, for instance) and the roots of a difficult compound, briefly, in the same spot.

## Design approach

Don't use other HTML files as style references unless told otherwise. Nearly every HTML page lying around was written by an agent, so "learning from examples" is agents imitating agents — each borrowed pattern nudges every page toward one converged house style, and the examples were never authoritative to begin with. Instead, let this page's own information decide its creative design. The user prefers every page independently designed, even if the collection never looks uniform. For the same reason this skill rarely gives examples: working out the best and most creative presentation is your job, page by page.

The same principle at widget scale: match the interaction to the shape of the idea. This matching — not interactivity for its own sake — is what has made pages land.

**Creativity over stability.** These pages are one-offs and cheap to regenerate, so this is the place to take real design risks. A page that tries something structural and misses beats a safe template that could have been any AI's output.

**Sibling skills worth loading, if available.** Several skills that ship with Claude Code or come from Anthropic apply to any HTML page, not only to published artifacts. Load whichever of these you have:

- `artifact-design` — craft fundamentals: type pairing, token-based colour, layout spacing, "show the page at rest", and the catalogue of AI-default looks to avoid. Load it for every page.
- `artifact-diagramming` — hand-authored inline SVG for a diagram that shows a mechanism (what changes between two options, where data flows).
- `dataviz` — governs any chart.
- `frontend-design` — may co-load; owns visual-identity craft (palette, type, generic-look calibration).

This skill owns purpose, interaction, and the rules in this file, and wins wherever they disagree: one theme is fine when the content decides it, the reading column has no width cap, and a finished page opens in the browser rather than publishing.

## Layout

**Theme:** the content decides. Commit to the single look — light or dark — that serves this page best; no need to style both or follow the system setting.

**No width cap on the reading column.** Text fills the pane or window it lives in; don't put a `max-width` on the content, its wrapper or the article body. The user prefers these off. Where line length matters, give the reader a way to resize rather than a fixed cap. Small components (dropdowns, pills, captions, dialogs) can still have their own widths.

**Landscape first, portrait and phone considered.** Design for a landscape laptop or desktop screen first; that's where the user mostly reads. But the user sometimes reads on a monitor rotated to portrait (about 1000–1450 px wide and very tall), and in a Claude artifact on a phone or iPad, so give those a little thought too. Nothing should be clipped, overlapping or unreadable there, and a split layout that cramps a diagram may read better stacked. Put portrait-only changes behind `@media (orientation: portrait)` so they never cost the landscape design.

**Clear navigation, never an endless scroll.** The user dislikes pages that are one long scroll to the end with no way to see or jump to what's there. When a page covers several topics, give each its own space and let the reader switch between them, and a reload returns to the topic that was open. A single topic that runs past a screen or two still lets the reader see where they are and jump anywhere.

## Content

- Content-complete, using the course material. When the page follows slides or a textbook, bring the reference material it uses into the page, so the reader can follow it on the page alone without opening the course PDF, deck or note, and use their photos, images and diagrams wherever they help, alongside public ones. Render a figure straight from the source at high resolution and crop tightly to it rather than reusing a screenshot or a low-res export. Redraw instead when the page needs to label, animate or interact with the figure.
- Packaging: the page opens by double-click, but you're welcome to load external libraries from a CDN to typeset LaTeX math, build interactive geometry and function plots, draw diagrams or chart data, wherever one genuinely serves the page — better effect beats purity.
- Spelling and special terms follow *Personal preferences* above.
- Maps (Leaflet and the like) need a tile server that accepts `file://` pages. OpenStreetMap answers 403 "Access blocked" because the page sends no Referer, and CARTO came up blank; a headless screenshot can still show OSM tiles, so check in a real browser. Esri works with no key: `https://server.arcgisonline.com/ArcGIS/rest/services/World_Topo_Map/MapServer/tile/{z}/{y}/{x}` (y before x), credited "Tiles © Esri — Esri, HERE, Garmin, FAO, NOAA, USGS, © OpenStreetMap contributors".
- Real photos: choose the ones that best convey information or deepen understanding, and find them before fixing the layout; a primary image can carry a whole opening. Metadata can be wrong, so check a caption's what, where and when against a second source. Free image sites (museums, archives, nature and biology databases) are a good place to look; some need a login or key or refuse automated downloads, so test one before relying on it. Tested free image sites that work without a login or key, with recipes, are in `references/image-sources/Image Sources.md`; the ones that refuse agents are in `references/image-sources/Image Sources (Blocked).md`.

## Interaction

A page exists so the user can read, react, tune, and feed the result back — not as a decoration. When the interaction produces a result worth capturing — a choice, a config, an ordering, tuned parameters — close the loop with an export that turns what the user did into something pasteable straight back into a Claude session or a file. Put the page's absolute file path at the top of the copied text (read from `location` at runtime, so it stays right if the file moves), so a pasted export tells the receiving session which page it came from.

**Multiple-choice always offers "I don't know."** Every multiple-choice question gets an "I don't know" option after the real choices, counted as a miss but recorded as *didn't know* rather than *guessed wrong*, so the misses export separates the two. Shuffle the real options so position gives nothing away; keep "I don't know" last.

**Answers persist, and can be cleared.** Every page with questions (quizzes, fill-ins, games, ratings) saves the reader's last answers in localStorage, so a reload, or closing the page and coming back days later, shows them as they were left. Store answers by question and option identity, not by screen position, so a shuffle or a content edit can't misattribute them. All `file://` pages share one localStorage in Chrome, so prefix keys with the page's path. Give the page a "clear all answers" control that asks first, inline (no browser `confirm()`), and offers Undo for a few seconds afterwards. Copy-and-paste export stays as well.

**Shuffle on demand for drill pages.** Pages built for practice (mock exams, quiz banks, vocabulary pages) get a Shuffle control for the order of questions and options, remembered across reloads. An explainer with a handful of questions doesn't need one.

### Reference samples

`references/` holds working samples of interactions the author has refined in use. Reuse their behaviour when a page needs it, and change their design: a new look, or a reworked layout where the page calls for one, is encouraged for variety and creativity, the same as for any page designed from its content.

- `Spelling Test Sample.html`: a spelling test over a fixed word list. The meaning is the prompt, a miss shows the word to retype, each round re-asks only the previous round's misses, and a results table counts how often each word was wrong. Self-contained; its `SPELLING DRILL` script block states its own contract.
- `Tree Building Sample.html`: a recall game the author commissioned and loves. Twelve loose animal groups are dragged together into the lecture's tree: a drop on a piece pairs them into a fork, a drop on a fork's dot adds a branch, and a click cuts a branch or flips a fork. Then the clades get named. Reuse the game wherever building a tree helps (a cladogram, a classification), with a new design each time. Beyond that, treat it as the bar for creative interactions: a test that is a real game whose moves are the idea itself (building a tree *is* joining branches), so recall feels like play rather than a quiz.
- `Mock Exam Sample.html`: a multiple-choice mock exam, and the worked example of this file's question rules. A rail down the left holds one cell per question, coloured by result, so the whole exam is visible at a glance and any question is one click away; the sheets on the right are grouped by part and section, with scopes for Everything, Missed, Marked and Not yet answered. Every question has "I don't know" last after shuffled options; answers and marks are saved; In order / Random with a seeded Reshuffle survives reloads; Reset asks inline which answers to clear (missed, marked or all) and offers Undo; "Copy misses & marks" exports for a Claude session. Reuse the rail-and-sheets layout and the whole question machinery for any quiz bank, with a new look.

## Page types

### Explainer pages (learning concepts)

The user learns by building genuine mental models, not collecting facts — so they often want more than the mechanism itself: concrete everyday examples, where the thing sits in the bigger system, cross-platform or cross-case comparison. Taste information, not a section template — use what fits the concept. Engaging prose, in the user's preferred writing style if they have one.

Teach with more than prose: illustrations and diagrams, hands-on parts, and quizzes or games for recall — whichever best fits the content. Pick by what the concept needs.

### Planning pages (projects)

Lead with the decisions the user is most likely to want to change — data models, interfaces, UX flows, scope calls — and put the mechanical parts they'd trust anyway at the bottom. Mockups and key snippets inline where a decision needs them. A good planning page doubles as a reference to hand a fresh implementing session, so make it self-explanatory without this conversation.

## Review

Reviewers are subagents (in Claude Code, the Agent tool); which model each gets and where two or more of them write their reports is up to your own setup. Whoever builds the page launches its reviewers. If you delegate the build to a forked agent, tell it in the brief to launch the reviewers itself, since forks may be told by default not to start agents. What a reviewer cannot know unless told:

- **Reviewers open the page in Chrome and use it.** Reading the code finds a different class of defects from clicking through the page; both are needed. A page with many generated states (a randomized quiz, an explorer with many selections) is exercised across those states from the browser console, not judged from one screenshot.
- **How to reach the page.** The Claude in Chrome extension refuses `file://` URLs. Playwright driving Chrome (`channel="chrome"`) opens the real `file:///` path at any window size, and is the best route for width checks and console-driven state tests. For a quick look, `chrome --headless=new --screenshot=<png> --window-size=1400,1500 <url>`. If the extension itself must drive the page, serve the folder with `python -m http.server <port> --bind 127.0.0.1` on a port no other session is using. A reviewer that starts a local server stops it, and closes its tab, when done.
- **One tab per agent.** With two or three agents sharing the user's Chrome, extension screenshots time out, and low memory once killed a test server. Each agent works in a single tab and closes it when done.
- **Check a laptop width first, then a phone width (~390 px) and a wide desktop.** The user reads pages mostly on a laptop. On a phone, the page only needs to stay usable: nothing cut off or unreadable. Report phone problems, but a fix should never flatten a laptop design for the phone's sake.
- **One outsider reviewer is always required,** and Sonnet is generally enough for it. It gets no context at all: no conversation history, nothing about the page beyond its file path and "you know nothing about this page." The only practical additions are where to write its report and how to reach the page in a browser. It judges style, clarity, readability and creativity as a first-time reader, then tries to break the page in Chrome. Narrow briefs find what they name; the outsider finds what nobody thought to name.
- **Other reviewers are designed per page.** Their number and briefs follow the page's own risks (a fact check gets the source files, a correctness check gets the functions and test cases). Give test cases without expected answers, so they derive verdicts rather than confirm the builder's.

## Finishing

- A finished page's natural home is the relevant project, topic or skill folder.
- Once the page is finished, open it in the default browser for the user — Windows: `start "" "Page.html"`; macOS: `open Page.html`; Linux: `xdg-open Page.html`. Do this without being asked — the page is meant to be looked at.
- A page that needs a shareable link, comments, or state shared between viewers can additionally be published with the Artifact tool, if available; the local file stays the source of truth.
