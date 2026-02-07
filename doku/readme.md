# 📘 Favoriten-Projekt – Layout & Know-how

Dieses Dokument erklärt:
- wie das Layout funktioniert
- was Wrapper sind
- wann Grid / Flex benutzt wird
- wo man gezielt Änderungen vornimmt

---

## 🧱 Grundprinzip

### 🔹 Grid = Umbruch & Verteilung
### 🔹 Flex = Ausrichtung von Inhalten

> **Nie beides gleichzeitig für dasselbe Problem verwenden**

---

## 📦 Was ist ein Wrapper?

Ein **Wrapper** ist ein Container, der **nicht sichtbar ist**, sondern nur Layout steuert.

Beispiel:

```html
<div class="detail-grid">
    <a class="link-box">…</a>
</div>
```

➡️ `.detail-grid` ist ein **Layout-Wrapper**

---

## ❌ Schlechter Wrapper (Altlast)

```html
<div id="content" class="content">
    <a class="link-box">…</a>
</div>
```

```css
.content {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### Warum problematisch?
- erzwingt Zentrierung
- verhindert Umbruch
- überlagert Überschriften
- kollidiert mit Grid

➡️ **Für Detailseiten NICHT verwenden**

---

## 🔄 Umbruch (wichtig!)

### Das passiert beim Verkleinern des Browsers:

| Richtig | Falsch |
|------|------|
| Boxen umbrechen | Boxen werden größer |
| mehrere Zeilen | Überlappung |
| gleiche Größe | verzogenes Layout |

### Der Schlüssel:

```css
grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
```

**Bedeutung**
- `auto-fit` → passt Anzahl automatisch an
- `minmax(160px, 1fr)` → nie kleiner, nie gequetscht

---

## 🧭 Wo ändere ich was?

| Ziel | Ort |
|----|----|
| Boxen nebeneinander | `.detail-grid` |
| Abstand | `gap` |
| Icon-Größe | `.link-box img` |
| Text unter Bild | `.link-box { flex-direction: column }` |
| gleicher Box-Look | `.link-box` |
| neuer Tab | HTML (`target="_blank"`) |

---

## 🧪 Typische Symptome

### ❌ Alles verrutscht
➡️ alter Wrapper aktiv

### ❌ Icons wachsen
➡️ keine feste Größe

### ❌ Boxen stehen untereinander
➡️ kein Grid

---

## 🧠 Denkmodell (merken!)

```
Seite
 └─ Grid (Layout)
     └─ Box
         └─ Flex (Inhalt)
```

---

## ✅ Goldene Regeln

1. Eine Aufgabe = eine Technik
2. Grid NIE durch Flex ersetzen
3. Wrapper nur, wenn nötig
4. Alte Wrapper löschen
5. CSS lieber klar als clever

