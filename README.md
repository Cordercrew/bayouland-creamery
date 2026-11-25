# Bayouland Creamery — bayoulanddairy.com

The standalone website for **Bayouland Creamery**, a Bayouland Ag Enterprises farm in Crowley, LA.
Sister site: [Bayou Bees](https://bayoubees.com).

```
index.html    → the whole site (story, shop, follow along, order form)
styles.css    → design
site.js       → menu, order cart, order form, share button, social links
404.html      → "page not found" page
CNAME         → tells GitHub Pages to serve this repo at bayoulanddairy.com
robots.txt / sitemap.xml → help Google find the site
assets/       → logos, photos, social preview image (og-image.jpg), icons
```

No build step: edit the files on GitHub (pencil icon) and commit, and the site updates within a minute or two.

---

## 1. Turn on GitHub Pages
**Settings → Pages →** *Build and deployment*: **Source = Deploy from a branch**, **Branch = main / (root)** → Save.
The site goes live at `https://cordercrew.github.io/bayouland-creamery/` first.

## 2. Connect bayoulanddairy.com
1. **Verify the domain first** (protects it from being hijacked): your GitHub profile picture → **Settings → Pages → Add a domain**, enter `bayoulanddairy.com`, and add the TXT record GitHub shows you at your domain registrar.
2. In this repo: **Settings → Pages → Custom domain** → `bayoulanddairy.com` → Save. (The `CNAME` file is already here.)
3. At your domain registrar, add these DNS records (delete any old A/CNAME records for `@` and `www` first):

```
A      @    185.199.108.153
A      @    185.199.109.153
A      @    185.199.110.153
A      @    185.199.111.153
CNAME  www  cordercrew.github.io
```
4. Wait (can take up to 24 hours), then tick **Enforce HTTPS** in Settings → Pages.

## 3. Turn on the order form
Until this is set up, **Send order request** opens the customer's email app with the order filled in, so nothing is broken in the meantime.
1. Sign up at **formspree.io** (free tier is fine) and create a form named "Bayouland Creamery orders". You'll get an address like `https://formspree.io/f/abcdwxyz`.
2. In `index.html`, find `data-endpoint="https://formspree.io/f/YOUR_FORM_ID"` and paste your address in.
3. On the same line, make sure `data-fallback-email="orders@bayoulanddairy.com"` is an inbox you actually check.

## 4. Social media
- **Your page links:** in `index.html`, search for `YOUR_` and replace with your real Facebook / Instagram / TikTok addresses. Any link left as `YOUR_…` stays hidden automatically, so fill in only the ones you use.
- **Link previews:** when someone posts bayoulanddairy.com on Facebook or texts it, it shows `assets/og-image.jpg` with your logo and tagline. After the domain is live, paste the URL into Facebook's **Sharing Debugger** (developers.facebook.com/tools/debug) and click *Scrape Again* to make Facebook pick it up.
- **Share buttons:** the "Follow along" section has a *Share this page* button (opens the phone's share sheet or copies the link) and a *Share on Facebook* button.
- **Google:** add the site to **Google Search Console** and submit `https://bayoulanddairy.com/sitemap.xml`. Setting up a free **Google Business Profile** for Bayouland Creamery is the biggest single boost for "fresh milk near Crowley" searches.

## 5. Everyday edits
- **Prices:** search `index.html` for `price on request` and replace the whole `<span class="ph">…</span>` with the number, e.g. `$<span>14</span>`.
- **Products:** copy an `<article class="prod">…</article>` block. Give its quantity picker a new, unique `data-product="..."` and a `data-name="..."` (that's what shows in the order). Use the same name in the button's `data-add="..."`.
- **Photos:** drop new photos into `assets/` and change the `<img src="assets/...">`. The milk, butter, and cheese cards are using calf photos and the logo as stand-ins; real product photos will sell better.

> **Before you go live:** dairy sales (especially raw milk) are regulated by the state. Make sure the product list and any labeling follow Louisiana rules.

## 6. Taking payment later
The form sends an order *request*; you confirm and collect payment your way. When you're ready for real checkout, **Square Online**, **Stripe Payment Links**, or **Shopify Buy Buttons** each give you a link or snippet that can go right on the product cards.
