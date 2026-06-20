# Rumchester Website

This is a small Jekyll website for Rumchester. It is designed so non-developers can edit the common content without touching complicated code.

## The Main Files To Edit

- `_config.yml` controls the site title, tagline, description, Instagram link, and default logo.
- `index.md` controls the main homepage text.
- `_data/events.yml` controls the events list.
- `_data/gallery.yml` controls the photo gallery.
- `assets/css/variables.css` controls the colors, fonts, sizing, and theme values.
- `assets/images/` stores logos, gallery images, and section artwork.

## Editing Events

Open `_data/events.yml` and copy one of the existing event blocks:

```yaml
- title: "Event title"
  description: "Short public description."
  start_time: "2026-08-14T19:00:00-04:00"
  image: "assets/images/gallery-map.svg"
  location: "Rochester, NY"
```

Keep the spacing exactly like the example. The `image` field can point to any file in `assets/images/`.

## Editing The Gallery

Open `_data/gallery.yml` and add or remove image blocks:

```yaml
- title: "Tasting Notes"
  image: "assets/images/gallery-tasting.svg"
  alt: "Describe the image for screen readers."
```

Put new image files in `assets/images/`, then reference the filename from the YAML.

## Editing Colors

Open `assets/css/variables.css`. Most theme values are grouped at the top:

```css
--color-rum: #c6792c;
--color-bottle: #173d32;
--color-cane: #f6e4bb;
```

Changing a variable updates the site everywhere that color is used.

## Local Preview

If Ruby and Bundler are installed:

```bash
bundle install
bundle exec jekyll serve
```

Then open the local URL shown in the terminal.

## Deployment

GitHub Pages deploys the site from `main` using `.github/workflows/deploy.yml`.
