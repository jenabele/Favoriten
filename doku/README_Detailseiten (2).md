# 📄 Detailseiten – Aufbau & Regeln

## Ziel
- Viele Boxen
- Sauberer Umbruch
- Gleichbleibende Größe

## HTML
```html
<div class="detail-grid">
  <a class="link-box">...</a>
</div>
```

## CSS
```css
.detail-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 24px;
  max-width: 1100px;
  margin: 0 auto;
}
```

## Wichtig
❌ Kein `.content` nötig  
❌ Kein Flex um Grid herum  

---

Ende Detailseiten README
