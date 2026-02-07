# 📘 CSS‑Spickzettel & Erklärungen

> **Kurz vorweg:**
> In CSS heißen diese Dinge **keine Argumente**, sondern **CSS‑Eigenschaften (Properties)** und **Werte (Values)**.
>
> Beispiel:
> ```css
> display: grid;
> ```
> - `display` → Eigenschaft (Property)
> - `grid` → Wert (Value)

---

## 🧠 Mentales Modell (wichtig!)

CSS beantwortet immer nur 3 Fragen:

1. **Wie wird etwas angeordnet?** → `display`, `grid`, `flex`
2. **Wie groß darf es sein?** → `width`, `min-height`, `max-width`
3. **Wie viel Abstand gibt es?** → `gap`, `margin`, `padding`

---

## 🔹 Layout-Grundlagen

### `display`
Legt fest, **wie** ein Element seine Kinder anordnet.

```css
display: block;   /* untereinander */
display: flex;    /* eindimensional */
display: grid;    /* zweidimensional */
```

**Merke:**
- `block` → Standard, langweilig
- `flex` → eine Richtung (Zeile ODER Spalte)
- `grid` → Reihen **und** Spalten

---

## 🔹 Grid (dein Hauptwerkzeug für Boxen)

### `display: grid`
Aktiviert Grid‑Layout.

```css
.container {
  display: grid;
}
```

Ohne `display: grid` funktionieren **alle Grid‑Eigenschaften nicht**.

---

### `grid-template-columns`
Definiert die **Spalten**.

```css
grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
```

**Was passiert hier genau?**

- `repeat(...)` → Wiederhole Spalten automatisch
- `auto-fit` → so viele Spalten wie Platz ist
- `minmax(160px, 1fr)` →
  - mindestens 160px breit
  - maximal flexibel (`1fr`)

✅ **Ergebnis:**
- Boxen stehen nebeneinander
- umbrechen automatisch bei kleinerem Bildschirm
- KEIN Überlappen

---

### `gap`
Abstand **zwischen** Boxen (nicht außen!).

```css
gap: 24px;
```

- ersetzt `margin` zwischen Grid‑Kindern
- sauber & berechenbar

❌ Kein Chaos mehr mit Margins

---

### `justify-items`
Ausrichtung **innerhalb der Grid‑Zelle** (horizontal).

```css
justify-items: center;
```

- `start` → links
- `center` → mittig
- `stretch` → füllt Zelle

---

## 🔹 Flexbox (für Inhalte IN einer Box)

### `display: flex`

```css
display: flex;
```

Verwendest du **in `.link-box`**, nicht im äußeren Layout.

---

### `flex-direction`

```css
flex-direction: column;
```

- `row` → nebeneinander
- `column` → untereinander (Bild über Text ✅)

---

### `align-items`
Ausrichtung **quer zur Richtung**.

```css
align-items: center;
```

Bei `column` → horizontal zentrieren

---

### `justify-content`
Ausrichtung **in Haupt‑Richtung**.

```css
justify-content: center;
```

Bei `column` → vertikal zentrieren

---

## 🔹 Größenkontrolle (extrem wichtig)

### `width` / `max-width`

```css
width: 100%;
max-width: 180px;
```

➡ verhindert:
- riesige Boxen im Vollbild
- Mini‑Boxen bei wenig Platz

---

### `min-height`

```css
min-height: 130px;
```

**Wofür?**
- Alle Boxen gleich hoch
- längerer Text macht Box **nicht größer als andere**

💡 DAS war dein Speedport‑&‑mehr‑Problem

---

## 🔹 Text & Umbruch

### `word-break` + `hyphens`

```css
word-break: break-word;
hyphens: auto;
```

➡ verhindert:
- überbreite Boxen
- Text läuft über den Rand

---

## 🔹 Bildgrößen (stabil!)

```css
.link-box img {
  width: 48px;
  height: 48px;
  object-fit: contain;
}
```

➡ garantiert:
- alle Icons gleich groß
- kein Springen beim Resize

---

## 🔹 Hover & UX

```css
.link-box:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 10px rgba(0,0,0,0.2);
}
```

Nur optisch – kein Layout‑Einfluss.

---

## 🧭 „Wo ändere ich was?“ – Index

| Ziel | Property |
|----|----|
| Boxen nebeneinander | `display: grid` |
| Abstand zwischen Boxen | `gap` |
| Umbruch bei kleiner Breite | `auto-fit + minmax` |
| Bild über Text | `flex-direction: column` |
| Alle Boxen gleich hoch | `min-height` |
| Icons gleich groß | `img { width/height }` |

---

## 🧪 Typische Fehler & Lösungen

❌ Boxen werden unterschiedlich groß  
✅ `min-height` setzen

❌ Boxen rutschen untereinander  
✅ `display: grid` + `grid-template-columns`

❌ Icons wachsen beim Verkleinern  
✅ feste `width` + `height`

❌ Text sprengt Box  
✅ `word-break` + `hyphens`

---

## 🏁 Merksatz zum Mitnehmen

> **Grid ordnet Boxen.**  
> **Flex ordnet Inhalte IN der Box.**  
> **Größen begrenzen Chaos.**

---

📌 Dieses Dokument ist dein **CSS‑Nachschlagewerk**.  
📌 Du kannst es jederzeit erweitern oder kommentieren.

