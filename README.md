# auto-generating tailwind css

This is a small sample repo to demo how auto css generation works with `tailwindcss`.

The idea is that you have `html` and `js` that has embedded `tailwind` class tags. `tailwindcss` will find those classes, e.g. `"flex-none w-48 relative"`, then add tailwind css classes with those names to the output css file, e.g.:

```html
<!-- index.html -->
<div class="flex-none w-48 relative"></div>
```

```css
/* output.css */
.flex-none {
  flex: none;
}

.relative {
  position: relative;
}

.w-48 {
  width: 12rem;
}
```

## Usage

Assuming `npm` is installed, first run:

    npm install

To run once:

    npx tailwindcss -i ./src/input.css -o ./src/output.css

To run in watch mode:

    npx tailwindcss -i ./src/input.css -o ./src/output.css --watch

This will:

- read config from `tailwind.config.js`
- read css classes from `./src/input.css`
- parse all the types of files specified in `content`, e.g. `.html`, `.js` files, etc. looking for `tailwind` class tags
- generate a minimize stylesheet needed to properly render all of the classes encountered, then save to `./src/output.css`

To view the generated page, run:

    npx http-server ./src
