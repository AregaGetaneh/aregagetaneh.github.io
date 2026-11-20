# aregagetaneh.github.io

Personal academic website for Arega Getaneh Abate, served at
<https://aregagetaneh.github.io>.

Single static page, no build step, no dependencies. Everything lives in
`index.html`: markup, styles, and a small script for the dark-mode toggle and
the section highlight in the left rail.

## Layout of the repo

```
index.html             the whole site
assets/
  portrait.jpg         your photo
  journals/*.jpg       journal cover thumbnails, 168x224
.nojekyll              tells GitHub Pages to serve the files as-is
README.md
```

## Photo

`assets/portrait.jpg` is a 362x362 square crop of your original photo.
Replace it with a larger square image whenever you have one, same filename and
no other change needed. If the file is ever missing the page falls back to a
monogram tile instead of showing a broken image.

## Journal covers

Each journal article shows its cover in the left gutter. Covers live in
`assets/journals/` at 168x224 (a 3:4 crop, 3x the display size). Preprints get
a dashed `arXiv` tile drawn in CSS instead, so there is no file for those.

To add a journal, save a 3:4 cover as `assets/journals/<name>.jpg` and point the
new entry's `<img>` at it.

## Editing

Everything you will want to change is plain HTML in `index.html`, marked with
comments:

| Section | What to edit |
| --- | --- |
| `<!-- IDENTITY RAIL -->` | name, title, affiliation, contact, profile links |
| `01 About` | bio paragraphs and the citation metrics strip |
| `02 Research` | method and application tags |
| `03 Publications` | one `<li class="pub">` per paper |
| `04 Code` | one `<a class="repo">` per repository |
| `05 Supervision` | one `<li class="sup-item">` per student |

### Adding a publication

Copy an existing block and edit it. Use `class="pub"` for published work and
`class="pub is-draft"` for preprints, which renders a dashed rather than a
solid rule in the gutter.

```html
<li class="pub">
  <span class="id">J7</span>
  <div class="body">
    <span class="title">Title of the paper</span>
    <span class="authors"><span class="me">A. G. Abate</span>, Co Author</span>
    <span class="meta">
      <span class="venue">Journal Name</span><span class="sep">/</span>
      <span>123 (2027) 456789</span><span class="sep">/</span>
      <a href="https://doi.org/10..." title="doi:10...">Link</a>
    </span>
  </div>
</li>
```

Wrapping your own name in `<span class="me">` is what makes it stand out in
the author list.

### Colors and type

All colors are CSS custom properties in the `:root` block at the top of the
`<style>` element, with a matching dark set further down. Changing
`--accent` recolors links, markers, and highlights across the page. The
`--signal` token is reserved for the award flag.

## Publishing

```
git add -A
git commit -m "New site"
git push
```

GitHub Pages serves the `main` branch root. Check
Settings > Pages if the site does not refresh within a minute.
