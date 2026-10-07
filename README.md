# HitGoals — marketing site

The HitGoals landing page, implemented as a plain static site. No build step, no
framework, no runtime dependencies — open `index.html` and it works.

Implemented from the Claude Design project
[Hitgoals App Website](https://claude.ai/design/p/044131fb-74c9-414a-8764-570489c37a8f)
(design file `HitGoals Site.dc.html`). The design prototype and its runtime are
deliberately not kept here — see "Re-syncing" below.

## Open it

**Double-click `index.html`.** That works — no server needed. The Onest/Nunito
brand fonts pop in a beat after the rest of the page, because the design
system's `typography.css` pulls them from Google Fonts through a nested
`@import`.

To serve it the way it will be deployed:

```bash
python -m http.server 8000
# then open http://127.0.0.1:8000/
```

## Layout

```
index.html                 The whole page: header, hero, problem, how it works,
                           FAQ, CTA, footer.
assets/css/site.css        All page styling. Every value resolves to a design
                           system token.
assets/mascot/*.png        Arrow mascot poses used by the page.
_ds/hitgoals-the-real-main-8b4e00c6-6f70-4fc8-bd92-96c5d314cf09/
                           The HitGoals design system, copied verbatim from the
                           design project. `tokens/` holds the six token files
                           the page links; `styles.css` is the design system's
                           own entry point, which just imports those six.
                           `readme.md` documents the brand (voice, colour,
                           type, the "chunky edge" button look, motion).
uploads/, scraps/,         Source material from the design project: raw
assets/cut/, assets/*.png  character art, frame grabs, working files. Nothing
                           in the site links to these — safe to delete if you
                           want the folder lean.
```

## How the design was translated

The `.dc.html` source is a Claude Design document: it carries `<x-dc>` /
`<helmet>` wrappers, a `support.js` editor runtime, `<x-import>` component
references resolved from a JS bundle at runtime, and every style written inline
on the element. None of that belongs in a shipped site, so:

- **Editor scaffolding dropped.** The prototype's `support.js` runtime, its
  `<x-dc>` wrappers and `data-comment-anchor` attributes are all gone. The page
  is ordinary HTML.
- **Design tokens kept as-is.** The six token files are linked straight from
  `_ds/.../tokens/`, so colours, type, spacing, radii, shadows and easings still
  come from the design system rather than from hard-coded values. (They are
  linked individually rather than through the design system's `styles.css`,
  which only `@import`s those same six — one less serialized round-trip.)
- **The one `<x-import>` Button reimplemented in CSS.** The header CTA used the
  design system `Button` component (`primary`, `size="sm"`), which needed React
  and a 98 KB component bundle just to render one button. `.btn--sm
  .btn--primary` reproduces it exactly — same padding, 38px min-height,
  `--fs-body-sm`, and the 3px solid red-700 bottom edge that the button
  translates down onto when pressed. Hover and press are plain CSS instead of
  React state.
- **Inline styles lifted into classes.** Same values, now named and reusable —
  the six App Store / Google Play badges are one `.store-btn` rule, and the two
  badge glyphs are an SVG sprite (`#i-apple`, `#i-play`) used six times instead
  of six copies of the path data.
- **Semantics added.** Real `<header>` / `<main>` / `<footer>`, the comparison
  bullets as `<ul>`, decorative images given empty `alt`, decorative icons
  marked `aria-hidden`, `<title>`, meta description and Open Graph tags.

Rendered at 1440px, the result was **pixel-identical** to the design preview —
verified by screenshot diff (0 differing pixels, both 1440×3346). One requested
change has since been made on top of that baseline: the FAQ mascot is 99px
instead of the design's 76px (+30%). Everything around it — the "Fair
questions." heading at 42px, the 18px gap — is untouched.

## Deliberate departures from the design

Three things the design file did not handle, fixed here because a shipped site
has to cope with them:

1. **Narrow phones clipped the headline.** The `<h1>` sets `white-space: nowrap`
   on both lines with a 42px clamp floor, so at 360px (a very common Android
   width) roughly 30px of "a plan you'll stick to." was cut off the right edge.
   Below 430px the headline now scales down instead
   (`clamp(28px, 8.6vw, 42px)`), keeping the intended two-line composition.
2. **`auto-fit` grid minimums exceeded narrow viewports.** `minmax(340px, 1fr)`
   and friends demand more width than a 320px screen has. They are now
   `minmax(min(340px, 100%), 1fr)`, which behaves identically at every width
   where the track fits and simply stops overflowing below that.
3. **The comparison card's divider.** Its vertical rule became a horizontal one
   once the two columns stack, instead of a right border on a full-width block.

Horizontal overflow is 0 at 320, 360, 390, 430, 768, 1024, 1280, 1440 and
1920px. There are no console errors and no failed requests.

Smaller additions: the header CTA links to `#cta` (the design system `Button`
rendered a `<button>` with no handler); store badges and footer links get a
press-down state consistent with the brand's chunky-button language; and a
`prefers-reduced-motion` block neutralises transitions.

## Fonts and icons

Type loads from Google Fonts via `tokens/typography.css` — **Onest** for
display, **Nunito** for body, **DM Mono** for the step numerals. The design
system flags these as substitutions; if HitGoals has official brand fonts, drop
the files in and self-host them by editing that token file.

## Assets

The page itself uses four mascot poses: `hero-trim`, `wave`, `confused`,
`proud`. The full set is here too — roughly thirty stills in `assets/mascot/`
and thirteen MP4 loops in `assets/mascot/anim/` (wave, jump, running, typing,
studying, sad, stressed…) for future pages, empty states and loading moments.

## Re-syncing after edits in Claude Design

Changes made in the Claude Design canvas do not flow here automatically, and the
prototype is not kept locally to diff against. To pull an update, re-export the
handoff (or read the file from the project above), compare it to this page, and
port the change into `index.html` / `assets/css/site.css`.

If the design system itself changes, re-copy `_ds/.../tokens/` — it is used
verbatim, so it can be replaced wholesale.
