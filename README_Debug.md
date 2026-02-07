# 🧪 Debug-Guide: „Warum sind meine Boxen plötzlich kaputt?“

Diese README ist ein **Nachschlagewerk für dein Layout-System** (Grid / Flex / Wrapper).
Nutze sie immer dann, wenn Boxen plötzlich:
- untereinander stehen
- unterschiedlich groß sind
- über den Rand laufen
- sich beim Verkleinern „komisch“ verhalten

---

## 🔴 Symptom: Boxen stehen untereinander statt nebeneinander

**Ursache**
- `display: block` (Standard)
- Grid/Flex liegt auf dem falschen Element

**Lösung**
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 20px;
}
```

➡️ `display: grid` gehört **immer auf den Eltern-Container**, nie auf die Box selbst.

---

## 🔴 Symptom: Boxen unterschiedlich hoch

**Ursache**
- Unterschiedlich langer Text
- Keine Mindesthöhe

**Lösung**
```css
.link-box {
  min-height: 130px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
```

---

## 🔴 Symptom: Boxen werden riesig oder verzerren sich

**Ursache**
- `1fr` ohne Begrenzung
- keine `max-width`

**Lösung**
```css
.link-box {
  width: 100%;
  max-width: 180px;
}
```

Oder im Grid:
```css
grid-template-columns: repeat(auto-fill, minmax(160px, 160px));
```

---

## 🔴 Symptom: Bilder sind unterschiedlich groß

**Lösung**
```css
.link-box img {
  width: 48px;
  height: 48px;
  object-fit: contain;
}
```

➡️ `src="images/Router.png"` ist korrekt  
❌ `class="images/Router.png"` ist falsch

---

## 🔴 Symptom: Text steht neben dem Bild

**Ursache**
- falsche Flex-Richtung

**Lösung**
```css
.link-box {
  display: flex;
  flex-direction: column;
  align-items: center;
}
```

---

## 🔴 Symptom: Beim Verkleinern läuft alles aus dem Container

**Lösung**
```css
.detail-grid {
  max-width: 1100px;
  margin: 0 auto;
}
```

---

## 🧪 Debug-Trick

```css
* {
  outline: 1px solid red;
}
```

Zeigt sofort, **welches Element das Layout kaputt macht**.

---

# 🧱 Wrapper-Lexikon

## Container
Element mit `display: grid` oder `display: flex`  
➡️ regelt **Anordnung**

Beispiele:
- `.box-grid`
- `.group-grid`
- `.detail-grid`

---

## Wrapper
Strukturelles Element, kein Layout

```html
<div class="group-wrapper">
  <div class="group-title">Heimnetzwerk</div>
  <a class="link-box">…</a>
</div>
```

➡️ bündelt Inhalt logisch

---

## Grid-Parent
Element mit `display: grid`

➡️ regelt:
- Spalten
- Umbruch
- Abstände (`gap`)

---

## Grid-Item
Direktes Kind eines Grid-Parents

➡️ bekommt Größe **vom Grid**

---

## Box (`.link-box`)
Kleinste klickbare Einheit

➡️ darf **kein Layout für andere Boxen machen**

---

## 🧠 Goldene Regeln

1. Grid ordnet – Boxen stylen
2. Wrapper ≠ Container
3. Keine festen Breiten + Grid mischen
4. Wenn etwas kaputt ist → falsches Element steuert Layout
5. Responsive = `auto-fit` + `minmax()`

---

## 📌 Klassen-Übersicht

| Klasse | Aufgabe |
|------|--------|
| `.box-grid` | wichtige Links |
| `.group-grid` | Themenbereiche |
| `.group-wrapper` | Struktur |
| `.link-box` | einzelne Box |
| `.detail-grid` | Detailseiten |

---

📘 **Tipp:**  
Diese Datei ist dein persönliches CSS-Nachschlagewerk.  
Ändere Layout **immer zuerst hier im Kopf**, dann im Code.
