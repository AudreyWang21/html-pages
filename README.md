# html-pages

[English](README.md) | [中文](README.zh-CN.md)

A [Claude Code](https://docs.claude.com/en/docs/claude-code) skill with a point of view on making HTML pages with Claude: concept explainers, planning pages, quizzes, little tools.

What it pushes Claude toward:

- **Design from the content.** Each page is designed from its own information outward, not from a house template or from other pages. Creative risks are welcome; a safe, generic page is the failure mode.
- **Navigation, not an endless scroll.** Several topics get their own tabs or spaces, and a reload returns you to where you were. No width cap on the text, and landscape screens first.
- **Interactive explainers.** Interactions shaped like the idea, quizzes with an "I don't know" option, answers that persist, and an export you can paste straight back into a Claude session.
- **Reviewers.** Every page gets checked in a real browser, including by one "outsider" reviewer that knows nothing about it.

## Try the samples

Open them in your browser, no download needed:

- [Mock exam](https://audreywang21.github.io/html-pages/html-pages/references/Mock%20Exam%20Sample.html): a practice exam with a question rail, saved answers and reshuffle.
- [Tree building](https://audreywang21.github.io/html-pages/html-pages/references/Tree%20Building%20Sample.html): drag animal groups together into a tree, then name the clades.
- [Spelling test](https://audreywang21.github.io/html-pages/html-pages/references/Spelling%20Test%20Sample.html): a spelling drill that re-asks only your misses.

## Install

Copy the `html-pages/` folder into your Claude Code skills folder:

```
~/.claude/skills/html-pages/
```

(On Windows, `~` is your user folder.) To use it in one project only, put it in that project's `.claude/skills/` instead. Start a new Claude Code session and ask Claude which skills it has; `html-pages` should be listed. From then on it loads whenever Claude is about to write an HTML page, and you can also ask for it by name.

It mentions a few other skills (`artifact-design`, `artifact-diagramming`, `dataviz`, `frontend-design`). They're optional: Claude loads whichever you have. The review step works best when Claude can run subagents and drive a headless Chrome (for example through Playwright).

A Chinese translation of the skill, for reading, is in `html-pages/SKILL.zh-CN.md`. Claude loads the English `SKILL.md`; to have it use the Chinese one instead, rename it to `SKILL.md`.

## Make it yours

Near the top of `html-pages/SKILL.md` is a short **Personal preferences** section with the author's own language habits: Canadian spelling, and special terms given in English with Simplified Chinese beside them, plus IPA. Replace those with yours or delete them. The rest of the skill is opinion too (no width cap, landscape first, opening every finished page in your browser, always running an outsider reviewer). Those opinions are the point, but it's your copy, so change whatever doesn't suit.

## The samples

`html-pages/references/` holds three working pages that Claude can borrow behaviour from (and is told to restyle, not copy). All open by double-click in any modern browser.

- **Spelling Test Sample.html**: a spelling drill over ten English words, prompted by their Chinese meanings: type the English word and press Enter. Each round re-asks only the words you missed, and a results table shows how often each was wrong. Swap the word list for your own.
- **Tree Building Sample.html**: a drag-and-drop game where you build an intro-biology animal tree from twelve loose groups, then name its clades. A green tick means a grouping fits the target tree so far, not that it's finished. It's the bar the skill sets for "a quiz that is really a game".
- **Mock Exam Sample.html**: an intro-biology multiple-choice mock exam with a question rail down the side. It shows the skill's quiz rules in action: an "I don't know" option, answers saved across reloads, shuffle, a reset with Undo, and an export of your misses.

`html-pages/references/image-sources/` also holds a dated list of free image sites an agent can use for real photos (and the ones that block agents), with a recipe per site. Start with [Image Sources](html-pages/references/image-sources/Image%20Sources.md).

## Licence

MIT. See [LICENSE](LICENSE).
