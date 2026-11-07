# Ground Zero website: context for an AI helper

> Paste this at the start of a new chat. Update **"Where I am right now"** before you do.

I'm learning web development and need a coding helper for my school group project. Please teach me **how** to do things instead of giving me finished code.

## How to help me

- Explain the concept briefly, give me a small task, and give hints. Let me write the code myself.
- Review my code when I send it. I usually send screenshots of my editor and browser.
- Only give full code if I ask for it directly.
- If something looks like it should work but doesn't, help me debug it step by step. (An editor extension bug once made correct CSS look broken, so trying a private browser window is worth it.)
- Keep answers short and casual.

## The project

- A website for a coffee and pastry café called **"Ground Zero"**. It's a year-long group project for my web dev class, with 5 people.
- Repo: `github.com/crunchymunchy-potatoe/WSPS` (my folder is `Project/`).
- Plain HTML and CSS, no frameworks yet.
- Tools: Zed editor (vim mode) on a MacBook and a desktop PC, a live preview extension that is a bit flaky, Lunacy for design mockups.

## Design

- Style inspired by the Ryoku Linux website (ryoku.dev): black background, cream and muted-gray text, thin outlined boxes, sharp corners, small uppercase labels.
- Logo: the white kanji 地 (`cafe-logo-white.png`) next to the brand name "Z.R.A.D.A" in uppercase (the project itself is still called Ground Zero).
- Fonts (loaded from Google Fonts): Instrument Serif (headings), Space Grotesk (nav and body), JetBrains Mono (small labels).
- Palette:

| Role | Color |
|---|---|
| Cream text | `#D8D0C4` |
| Muted gray | `#8A847B` |
| Hairlines | `#3A3835` |
| Rust accent | `#C4673A` |

- The header and footer mockups are finished in Lunacy. The footer mockup has 3 columns (brand, explore links, visit info) and a bottom strip.
- The header and footer markup now live directly inside `index.html`. The old standalone `navbar.html` and `footer.html` files were removed, because plain HTML cannot include one file inside another.

## Files

```
Project/Core/index.html    (home page: header, main, footer)
Project/Core/style.css     (all styles, design tokens in :root)
Project/Assets/            (logos and images)
Project/Refrences/         (notes, sic spelling)
```

## Header HTML structure

```html
<nav class="hdr">
  <div class="hdr-brand">  <!-- img.hdr-logo + a.hdr-name ("Z.R.A.D.A") -->
  <ul class="hdr-nav">     <!-- li > a: Home, Menu, About Us, Contact Us -->
  <div class="hdr-right">  <!-- a.time ("OPEN 9AM-10PM") and a.est ("Est 2027") -->
</nav>
```

The links are now section anchors inside `index.html` (`#top`, `#featured`, `#story`, `#visit`) instead of empty `href=""` values.

## CSS state

- `style.css` has a `:root` block with the palette (`--cream`, `--muted`, `--line`, `--rust`, `--bg`) and the three font families, so the whole page shares one design system.
- `.hdr` is a flex row with the hairline `border-bottom`; its horizontal padding is calculated so the logo lines up with the 1200px content column.
- The nav links have the sliding underline: `.hdr-nav a::after` starts at `width: 0` and grows to `100%` on hover.
- The `.time` and `.est` badges share one hover rule (`.time:hover, .est:hover`), and transitions now live in the normal-state rules.
- The home page sections are `.hero`, `.featured`, `.story`, and `.visit`, followed by `.foot`.
- The CSS is responsive: the nav wraps at 860px, cards go from 3 → 2 → 1 columns, and the member cards always show names on touch screens.

## Where I am right now

The complete home page is built and styled from the blueprint: navbar, hero, featured bundles, story with the five member letters, visit details, and footer.

Next steps are separate pages (Menu, About Us, Contact Us), real final copy, and double-checking that the images look right in the browser.

## Other things left

- [x] Fix the "Contacts Us" typo and use real anchor links.
- [x] Move the transitions into the normal-state rules.
- [x] Group `.est:hover` and `.time:hover` into one rule.
- [x] Rename the CSS comments that say "responsive" to "hover".
- [x] Build the header and footer into `index.html`.
- [x] Make the home page mobile responsive.
- [ ] Add the separate Menu / About Us / Contact Us pages.
- [ ] Replace placeholder story copy and member names if needed.
