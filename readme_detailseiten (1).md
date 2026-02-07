# 📗 Detailseiten (z. B. heimnetzwerk.html)

Dieses Dokument erklärt **nur** die Detailseiten mit vielen Icons.

---

## 🎯 Ziel

- Icons **immer gleich groß**
- sauberer Umbruch bei kleinen Bildschirmen
- kein Überlappen mit Überschrift
- kein Zentrieren über Flex

---

## ✅ Richtige HTML-Struktur

```html
<h2>Heimnetzwerk</h2>

<div class="detail-grid">
    <a class="link-box" href="http://192.168.2.1/" target="_blank">
        <img src="images/Router.png" alt="Router" />
        <span>Speedport IP</span>
    </a>
</div>
```

❌ **Kein `#content`, kein `.content`**

---

## ✅ Richtiges CSS

```css
.detail-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 24px;
    max-width: 1100px;
    margin: 0 auto;
}
```

```css
.link-box {
    display: flex;
    flex-direction: column;
    align-items: center;

    min-height: 130px;
    padding: 14px;
    text-align: center;

    background: #f5f5f5;
    border: 2px solid #888;
    border-radius: 8px;
}
```

```css
.link-box img {
    width: 48px;
    height: 48px;
    object-fit: contain;
}
```

---

## 🔍 Häufige Fehler

### ❌ Icons werden größer
➡️ `width: 100%` im Grid

### ❌ Boxen überdecken Überschrift
➡️ alter Flex-Wrapper aktiv

### ❌ Nur eine Spalte
➡️ kein Grid oder `display:flex`

---

## 🧠 Merksatz

> **Detailseiten brauchen NUR ein Grid + Boxen – sonst nichts**

---

## ✅ Checkliste

- [ ] kein `.content`
- [ ] Grid direkt nach Überschrift
- [ ] feste Icongröße
- [ ] `auto-fit + minmax`

---

## 🔚 Fertig

Wenn etwas kaputt wirkt → **erst Wrapper prüfen**

