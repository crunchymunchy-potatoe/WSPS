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

- Style inspired by the Ryoku Linux website (ryoku.dev): black background, white and slate-gray text, thin outlined boxes, sharp corners, small uppercase labels.
- Logo: the white kanji 地 (`cafe-logo-white.png`) next to the name "GROUND ZERO" in uppercase.
- Planned fonts: Instrument Serif (headings), Space Grotesk (nav and body), JetBrains Mono (small labels).
- Planned palette (approximate):

| Role | Color |
|---|---|
| Cream text | `#D8D0C4` |
| Muted gray | `#8A847B` |
| Hairlines | `#3A3835` |
| Rust accent | `#C4673A` |

- The navbar and footer mockups are finished in Lunacy. The footer mockup has 3 columns (brand, explore links, visit info) and a bottom strip.

## Files

```
Project/Core/navbar.html
Project/Core/style.css
Project/Assets/        (logos and images)
Project/Refrences/     (notes, sic spelling)
```

## Navbar HTML structure

```html
<nav class="hdr">
  <div class="hdr-brand">  <!-- img.hdr-logo + a.hdr-name ("Ground Zero") -->
  <ul class="hdr-nav">     <!-- li > a: Menu, Shop, About Us, Contacts Us (typo, should be "Contact Us"), Visit Us -->
  <div class="hdr-right">  <!-- a.time ("OPEN 9AM-10PM") and a.est ("Est 2027") -->
</nav>
```

All links currently have `href=""`. I'm going to change them to `#`.

## CSS state

- `.hdr` is a flex row with `align-items: center`, padding, and a hairline `border-bottom`.
- `.hdr-brand` is a flex container with a gap, items centered.
- `.hdr-nav` is a flex row with a gap and no list bullets, with `margin-left: auto` and `margin-right: 5rem`.
- Nav links are `slategray`, and white on hover (`.hdr-nav a:hover`).
- `.hdr-nav a` already has `position: relative`.
- `.hdr-right` is a flex container with a gap.
- The badges (`.time` and `.est`) have a `1px solid slategray` border and padding, and turn white on hover.
- The `transition` is currently inside the hover rule, and I plan to move it into the normal-state rules.

## Where I am right now

I'm making the **sliding underline** for the nav links: it should grow from left to right on hover, slightly slower than the text turns white. My plan:

1. `.hdr-nav a` gets `position: relative` (done).
2. `.hdr-nav a::after` gets:
   - `content: ""` (an empty string, I'm stuck here)
   - `position: absolute`, `left: 0`, a small negative `bottom`
   - `height: 1px`, `width: 0`, a white `background`
   - `transition: width 0.5s`
3. `.hdr-nav a:hover::after` sets `width: 100%`.
4. Remove `text-decoration: underline` from the hover rule, so the instant browser underline doesn't show.

## Other things left

- [ ] Fix the "Contacts Us" typo and change the `href=""` values to `#`.
- [ ] Move the transitions into the normal-state rules.
- [ ] Group `.est:hover` and `.time:hover` into one rule with a comma.
- [ ] Rename the CSS comments that say "responsive" to "hover".
- [ ] Commit the navbar to Git.
- [ ] Build the footer from the Lunacy mockup.
- [ ] Add more pages.
- [ ] Later: make it mobile responsive.
