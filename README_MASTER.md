# 📘 Master README – Favoriten-Projekt

Dieses Dokument ist das **zentrale Nachschlagewerk** für dein komplettes Projekt.
Es erklärt **Struktur, CSS-Logik, typische Fehler und wo du was änderst**.

---

## 1️⃣ Projekt-Struktur (mentales Modell)

```
HTML (Struktur)
└── Wrapper (logisch)
    └── Container (Grid/Flex → Layout)
        └── Boxen (Inhalt)
```

**Merksatz:**  
👉 *Container ordnen, Boxen stylen.*

---

## 2️⃣ Wann Grid, wann Flex?

| Zweck | Technik |
|-----|--------|
| Boxen nebeneinander / umbrechen | Grid |
| Inhalt in Box zentrieren | Flex |
| Gleichmäßige Spalten | Grid |
| Bild über Text | Flex (column) |

---

## 3️⃣ Wichtige CSS-Stellen – „Wo ändere ich was?“

| Ziel | CSS |
|----|----|
| Boxen nebeneinander | `display: grid` |
| Abstand zwischen Boxen | `gap` |
| Gleich große Boxen | `min-height` |
| Umbruch bei kleinerem Screen | `auto-fit + minmax()` |
| Bildgröße fix | `img { width/height }` |

---

## 4️⃣ Goldene Regeln

1. Grid **nie** auf `.link-box`
2. Kein `width` + `1fr` mischen
3. Textumbruch → `word-break`
4. Icons **immer feste Größe**
5. Wrapper = Struktur, kein Layout

---

## 5️⃣ Typische Fehler

❌ Boxen untereinander → Grid fehlt  
❌ Bilder riesig → `img` nicht begrenzt  
❌ Überschrift höher → kein `min-height`

---

Ende Master README
