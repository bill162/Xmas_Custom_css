# 🎄 Jellyfin Xmas Theme

After months of testing, breaking my server, fixing it, breaking it again,  
and questioning my life choices — this theme is finally done.

I survived. Barely.

---

## 🛠 Installation (Yes, This Matters)

There are **two ways** to load things in Jellyfin.

One is correct.  
One is cursed.

Choose wisely.

---

## ✅ Recommended Way (Admin Dashboard)

This is the **ONLY method I actually recommend**.

### CSS (Theme)

1. Go to **Jellyfin Admin Dashboard**
2. Navigate to:
   - **Dashboard → Branding → Custom CSS**
3. Copy **ALL** the CSS from this repository and paste it there
4. Save
5. Reload Jellyfin

### 👍 Why this is good
- Stable
- Jellyfin updates won’t nuke it
- Less pain
- Less crying

This is how normal people do it.

---

# ☠️ Alternative Way (index.html) — NOT RECOMMENDED 

Yes, you *can* inject things via `index.html`.

No, you **should not** (especially CSS).

Still, here is the truth.

---

## ❌ CSS in `index.html` (DON’T)

Loading **CSS** via `index.html` is a **bad idea**.

```html
<link rel="stylesheet" href="xmas.css">
```

Yes, it works.  
Yes, it will break later.

### Why this is stupid:
- Jellyfin updates overwrite it
- CSS load order becomes unpredictable
- One typo = silent UI break
- You will forget you added it
- You will blame the theme (it’s not the theme)

**Do NOT load `xmas.css` via `index.html`.**

---

## ✅ JavaScript in `index.html` (ACCEPTABLE)

Loading **JavaScript** via `index.html` is **acceptable**  
*if you know what you’re doing*.

This applies to:
- `pausescreen.js`
- `snowstorm.js`
- `qualitytags.js`

---

## 📦 REQUIRED JAVASCRIPT FILES (NO EXCEPTIONS)

You **MUST** download these manually:

- `pausescreen.js`
- `snowstorm.js`
- `qualitytags.js`

All scripts are created by **BobHasNoSoul**.

👉 https://github.com/bobhasnosoul

These files are **NOT included** in this repository  
(**except `qualitytags`, which is modified and Xmas-themed by me**).

No JS = nothing works.

---

## ❄️ VERY IMPORTANT — Snowstorm vs Pause Screen

There is a **known conflict**.

### ❌ If Snowstorm is ENABLED
- Pause screen **WILL NOT WORK**
- This is expected
- This is NOT a bug (I think)

### ✅ If Snowstorm is DISABLED
- Pause screen **WILL WORK**

You **cannot have both** at the same time.

Pick one and move on with your life.

---

## ⚙️ REQUIRED CSS FIX (CRITICAL FOR SNOWSTORM)

If you want **Snowstorm** to work correctly,  
you **MUST** include this CSS **somewhere** (Admin Dashboard preferred):

```css
/* fix snowstorm */
.content-primary,
.padded-bottom-page,
.page,
.pageWithAbsoluteTabs .pageTabContent {
    z-index: 4;
}

.videoPlayerContainer {
    z-index: 3;
}

.skinHeader.osdHeader {
    z-index: 5 !important;
}

.backgroundContainer {
    z-index: 0 !important;
}

.htmlvideoplayer {
    z-index: 3;
}
```

### ❌ Without this
- Snow renders behind everything
- UI layering breaks
- Visual chaos

### ✅ With this
- Snowstorm works
- UI behaves
- You sleep better

---

## 📍 How to Inject Custom JS in `index.html` (READ SLOWLY)

If you **choose** the `index.html` path:

### 1️⃣ Create the folder

In your **Jellyfin web root**, create a folder called:

```
seasonal
```

Copy **all contents** of the `seasonal` folder from this repository  
into that folder.

---

### 2️⃣ Edit `index.html`

Open Jellyfin’s `index.html`.

Scroll **ALL THE WAY DOWN**.

You must inject scripts **RIGHT BEFORE** the final closing tags:

```html
</body>
</html>
```

---

### 3️⃣ Inject the scripts (EXAMPLE)

```html
    <!-- Seasonal / Xmas scripts -->
    <script src="seasonal/snowstorm.js"></script>
    <script src="seasonal/pausescreen.js"></script>
    <script src="seasonal/qualitytags.js"></script>
</body>
</html>
```

### ⚠️ RULES (DO NOT IGNORE)
- ❌ Do NOT put scripts in `<head>`
- ❌ Do NOT put them randomly
- ❌ Do NOT load CSS here
- ✅ Always load JS **at the very bottom**

---

### 🧠 Internal Dialogue

me: this should work  
code: interesting theory  

---


## 🎞️ Optional: Quality Tags

This theme **expects quality tags**.

If you don’t use them:
- Cards may look empty or unbalanced
- UI feels less complete
- It’s not fatal, just sad

Examples:
- `4K`
- `HDR`
- `HDR10+`
- `Dolby Vision`
- `Dolby Atmos`
- `BluRay`
- `WEB-DL`
- `HEVC`


---

## 🪦 FINAL WARNING

```
CSS in index.html
= pain

JS in index.html
= ok-ish

Admin Dashboard
= peace

Snowstorm ON
= pause screen OFF

Snowstorm OFF
= pause screen ON
```

You were warned.
