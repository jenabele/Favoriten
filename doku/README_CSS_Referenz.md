# 🎨 CSS-Referenz – verständlich erklärt

## display
- `block` → untereinander
- `flex` → Inhalt ausrichten
- `grid` → Boxen anordnen

## grid-template-columns
```css
repeat(auto-fit, minmax(160px, 1fr))
```
✔ passt sich Bildschirm an  
✔ verhindert Quetschen  

## gap
Abstand zwischen Grid-Items (besser als margin)

## min-height
Sorgt für **gleich hohe Boxen**

## object-fit: contain
Skaliert Bilder ohne Verzerrung

## justify-content / align-items
Nur für **Flex**, nicht Grid

## max-width
Verhindert riesige Boxen im Fullscreen

---

Merksatz:  
👉 Grid = Außen, Flex = Innen
