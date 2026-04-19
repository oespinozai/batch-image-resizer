# Batch Image Resizer

A free, privacy-first batch image resizer that runs 100% in your browser.
No uploads. No signup. No watermark. No server.

Resize multiple photos at once by pixel width or compress images to a target
file size (KB). All processing happens via the Canvas API on your device.
Results download as individual files or a single ZIP.

## Features

- Drag-and-drop or click-to-select multiple images (JPG, PNG, WebP)
- Two modes: resize by width (px) or compress to max KB
- Shows before/after file size for every image
- Thumbnail grid with individual download buttons
- Download all results as a ZIP in one click
- Free up to 20 images per batch
- Mobile-friendly dark UI
- Zero dependencies except JSZip (loaded from CDN)

---

## Deploy to GitHub Pages in 3 steps

1. **Create a new GitHub repository** (e.g. `batch-image-resizer`).
   Push the files:
   ```
   git init
   git add index.html README.md _config.yml
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/batch-image-resizer.git
   git push -u origin main
   ```

2. **Enable GitHub Pages** in your repo settings:
   Settings → Pages → Source: Deploy from a branch → Branch: `main` → folder: `/ (root)` → Save.

3. **Visit your live site** at:
   `https://YOUR_USERNAME.github.io/batch-image-resizer/`

That's it. No build step, no CI, no config needed.

---

## Wiring in Lemon Squeezy (paid unlock)

The paywall is already built into the app. Here is how to activate it:

### 1. Create a Lemon Squeezy product

- Sign up at https://lemonsqueezy.com
- Create a Store → New Product → One-time purchase, price $1.99
- Copy the checkout URL (looks like `https://yourstore.lemonsqueezy.com/checkout/buy/PRODUCT_ID`)

### 2. Update the Buy button URL

In `index.html`, find the buy button:
```html
<a href="#" class="modal-buy-btn" id="buy-btn">Buy Unlimited Access — $1.99</a>
```
Replace `href="#"` with your Lemon Squeezy checkout URL.

### 3. Verify purchase and set `isPurchased`

The simplest approach for a static site is a license-key flow:

- In Lemon Squeezy, enable License Keys for your product.
- After purchase the customer gets an email with a license key.
- Add a small "Enter license key" input in the UI.
- On submit, call the Lemon Squeezy Licenses API to validate:
  ```
  POST https://api.lemonsqueezy.com/v1/licenses/validate
  Body: { "license_key": "USER_KEY" }
  ```
- If valid, set `isPurchased = true` and persist to `localStorage`:
  ```js
  localStorage.setItem('ls_unlocked', '1');
  ```
- On page load, read it back:
  ```js
  const isPurchased = localStorage.getItem('ls_unlocked') === '1';
  ```

This requires no backend — the Lemon Squeezy API supports CORS for license
validation from the browser.

---

## File structure

```
batch-image-resizer/
├── index.html      # The entire app — HTML, CSS, JS in one file
├── README.md       # This file
└── _config.yml     # Minimal GitHub Pages config
```

## License

MIT — do whatever you want with it.
