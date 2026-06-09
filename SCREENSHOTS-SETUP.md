# Screenshots Sectie — Setup Instructies

## 📁 Repository Structuur

Zorg dat de volgende structuur aanwezig is in je GitHub Pages repository:

```
safeguardodin-del.github.io/
├── index.html
├── README.md
├── SCREENSHOTS-SETUP.md (dit bestand)
├── assets/
│   ├── styles.css
│   ├── script.js
│   └── screenshots/
│       ├── 01-dashboard.jpg
│       ├── 02-fraud-inbox.jpg
│       ├── 03-source-status.jpg
│       ├── 04-settings.jpg
│       ├── 05-sms-protection.jpg
│       └── 06-ai-model.jpg
```

## 🖼️ Screenshots Toevoegen

### Stap 1: Maak de screenshots-map aan

```bash
mkdir -p assets/screenshots
```

### Stap 2: Screenshots Van De App Exporteren

**Optie A: Van Je Telefoon (Aanbevolen)**
- Neem screenshots van je SafeGuard Senior app
- Geef ze deze namen:
  - `01-dashboard.jpg` — Home screen met Odin-AI status
  - `02-fraud-inbox.jpg` — Fraude Inbox (threats)
  - `03-source-status.jpg` — Source synchronisatie status
  - `04-settings.jpg` — Settings/Instellingen
  - `05-sms-protection.jpg` — SMS Protection actief
  - `06-ai-model.jpg` — AI Model info (leer curve)

**Optie B: Placeholder Images (Voor Nu)**

Als je nog geen screenshots hebt, kun je placeholder images maken:

```bash
# macOS/Linux: Maak placeholder images (300x600px, blauw)
for i in {1..6}; do
  convert -size 300x600 xc:"#4f46e5" "assets/screenshots/0$i-placeholder.jpg"
done

# OF gebruik een online tool: https://placeholder.com/300x600
```

### Stap 3: Images Uploaden Naar Repository

**Methode A: Via GitHub Web UI**
1. Ga naar je repo: `https://github.com/safeguardodin-del/safeguardodin-del.github.io`
2. Klik op `assets` → `screenshots` (maak deze map aan als deze niet bestaat)
3. Klik op "Add file" → "Upload files"
4. Sleep de 6 screenshot files er in
5. Commit met message: "Add app screenshots"

**Methode B: Via Git CLI**
```bash
cd safeguardodin-del.github.io

# Copy screenshots naar assets/screenshots/
cp ~/Downloads/01-dashboard.jpg assets/screenshots/
cp ~/Downloads/02-fraud-inbox.jpg assets/screenshots/
# ... etc

# Commit
git add assets/screenshots/
git commit -m "Add app screenshots"
git push origin main
```

## 🎨 Afbeeldingsvereisten

| Eigenschap | Aanbeveling |
|---|---|
| **Formaat** | JPG of PNG |
| **Afmetingen** | Min. 300×600px (telefoon aspect ratio) |
| **Grootte** | Max. 500KB per image (om snel te laden) |
| **Aspect Ratio** | 9:16 (portrait/staand) |

### Afbeeldingen Optimaliseren

```bash
# macOS: Compress images met ImageOptim
open -a ImageOptim assets/screenshots/

# Linux: Gebruik ImageMagick
convert input.jpg -quality 85 -resize 300x600 output.jpg

# Online: https://tinypng.com/ of https://imagecompressor.com/
```

## 📝 HTML Structuur Aangepast

De Screenshots sectie is al toegevoegd in `index.html`. De structuur is:

```html
<!-- Screenshots Section -->
<section id="screenshots" class="screenshots">
  <div class="container">
    <h2>Hoe ziet de app eruit?</h2>
    <p class="screenshots-intro">Een blik op SafeGuard Senior's schone en intuïtieve interface.</p>
    <div class="screenshots-grid">
      <!-- Screenshot cards -->
      <div class="screenshot-card">
        <img src="assets/screenshots/01-dashboard.jpg" alt="Beschrijving">
        <div class="screenshot-label">🏠 Home Dashboard</div>
        <button class="lightbox-btn" data-image="assets/screenshots/01-dashboard.jpg">+</button>
      </div>
      <!-- ... meer cards -->
    </div>
  </div>
</section>
```

## ⚙️ Lightbox Functionaliteit

- **Click op "+" button** → Image opent in fullscreen
- **Click op het kruis** → Lightbox sluit
- **Click buiten image** → Lightbox sluit
- **Druk Escape** → Lightbox sluit
- **Responsive** op mobiel

## 🔄 Screenshots Bijwerken

**Existing screenshot vervangen:**

1. Ga naar `assets/screenshots/` in je repo
2. Klik op het bestand (bijv. `01-dashboard.jpg`)
3. Klik op het potlood-icoon (edit)
4. Klik op "Delete this file"
5. Upload het nieuwe bestand met dezelfde naam
6. Commit met message: "Update screenshot: 01-dashboard"

**Of via CLI:**

```bash
git rm assets/screenshots/01-dashboard.jpg
cp ~/Downloads/new-screenshot.jpg assets/screenshots/01-dashboard.jpg
git add assets/screenshots/01-dashboard.jpg
git commit -m "Update screenshot: 01-dashboard"
git push
```

## 📱 Screenshots Van Je App Maken

### Android Studio Emulator
1. Open Android Studio
2. Run je app in emulator
3. Klik op "Extended Controls" → "Screenshot"
4. Of gebruik: `adb shell screencap -p /sdcard/screenshot.png`

### Via Telefoon (Aanbevolen)
1. Open SafeGuard Senior op je telefoon
2. Navigeer naar elke scherm
3. Maak screenshot (meestal: **Volume Down + Power Button**)
4. Stuur naar computer via:
   - Email attachment
   - Cloud storage (Google Drive, OneDrive)
   - Bluetooth / USB
   - ADB: `adb pull /sdcard/DCIM/Camera/screenshot.jpg`

## ✅ Checklist

- [ ] Map `assets/screenshots/` aangemaakt
- [ ] 6 screenshots in de juiste map (.jpg of .png)
- [ ] Screenshots 300×600px (of groter)
- [ ] Bestanden geoptimaliseerd (max 500KB)
- [ ] Bestandsnamen: `01-dashboard.jpg`, `02-fraud-inbox.jpg`, etc.
- [ ] Gepushed naar main branch
- [ ] Website vernieuwd → Screenshots zichtbaar
- [ ] Lightbox werkt (click op "+")
- [ ] Responsive op mobiel

## 🆘 Troubleshooting

### Screenshots tonen niet

1. Check bestandspaden: `assets/screenshots/01-dashboard.jpg` (exact case-sensitive)
2. Check dat afbeeldingen in repo zijn: `github.com/safeguardodin-del/safeguardodin-del.github.io/tree/main/assets/screenshots`
3. Browser cache clearen: **Ctrl+Shift+Delete** (Chrome) of **Cmd+Shift+Delete** (Safari)
4. Wacht 5-10 minuten voor GitHub Pages cache refresh

### Lightbox niet werkend

1. Open browser Developer Tools: **F12**
2. Check Console voor JavaScript errors
3. Check Network tab: laden de images?
4. Zorg dat `assets/script.js` properly loaded is

### Afbeeldingen laden langzaam

1. Comprimeer images verder (max 200KB per image)
2. Gebruik WebP format (beter compression)
3. Lazy loading is al ingebouwd (`loading="lazy"`)

## 📚 Referenties

- [GitHub Pages Uploaden Files](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)
- [Image Optimization Tips](https://web.dev/image-optimization/)
- [Responsive Images Best Practices](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)

---

**Vragen?** Bekijk de eerste 6 screenshots in images 1-4 hierboven als referentie voor content types!