# Nathaniel's Digital Contact Cards

NFC tap-to-save contact cards. One repo, one card per subfolder, one Netlify
site per card (each pointing at its own subfolder).

```
nathaniels-card/
  francis/       -> index.html  (Francis's card)   -> Netlify site: francis-nathaniel-co
  fkc/           -> (future fork)
  cafe-fernando/ -> (future fork)
```

Each card is a single self-contained `index.html`. All editable content lives
in the `CONFIG` block at the top of the file — name, title, phones, email,
website, logo. Nothing else needs touching.

---

## First-time setup (once ever)

Run these from the repo root in your WSL2 terminal. Replace `YOUR_GH_USERNAME`.

```bash
cd nathaniels-card
git init
git add .
git commit -m "Initial commit: Francis contact card"
git branch -M main

# create the repo on GitHub first (github.com/new, name it nathaniels-card, empty),
# then:
git remote add origin https://github.com/YOUR_GH_USERNAME/nathaniels-card.git
git push -u origin main
```

### Connect to Netlify (one browser session, then never again)

1. app.netlify.com -> the existing **francis-nathaniel-co** project -> Site
   configuration -> Build & deploy -> Link repository -> pick this repo.
2. Set **Base directory** / **Publish directory** to `francis`.
3. Save. Done.

From now on: edit `francis/index.html`, `git push`, and Netlify redeploys
automatically. No browser, no manual deploy.

---

## The logo

The card loads `logo.png` from its own folder. Drop a clean square PNG of the
Nathaniel's dove into `francis/logo.png`. Until it's there, the card shows the
"FC" initials fallback — which is fine, it won't break.

---

## Adding a new card (FKC, Cafe Fernando, etc.)

```bash
cp -r francis fkc
# edit fkc/index.html CONFIG (new name, phones, email, logo, accent color)
# drop fkc/logo.png
git add . && git commit -m "Add FKC card" && git push
```

Then create a new Netlify site pointed at the `fkc` subfolder. Same pattern.

To rebrand a fork's color, change the two `--accent` lines in `:root` near the
top of that card's `index.html`.
