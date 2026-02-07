🧪 Debug-Guide: „Warum sind meine Boxen plötzlich kaputt?“

Dieser Guide hilft dir, Layout-Fehler systematisch zu finden und zu beheben – ohne Rumprobieren.

🔴 Symptom 1: Boxen stehen untereinander, nicht nebeneinander
Ursache (fast immer eines davon):

❌ display: block (Standard)

❌ display: flex ohne flex-wrap

❌ Grid/Flex liegt auf dem falschen Element

✅ Lösung:
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 20px;
}


👉 Wichtig:
display: grid oder flex muss auf den Elternelementen liegen, nicht auf .link-box.

🔴 Symptom 2: Boxen sind unterschiedlich hoch
Ursache:

Unterschiedlich langer Text

Kein Höhen-Ausgleich

Grid/Flex darf schrumpfen

✅ Lösung:
.link-box {
  min-height: 130px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}


💡 Merksatz:

Höhe gehört in die Box, nicht ins Grid.

🔴 Symptom 3: Boxen „ziehen sich auseinander“ oder werden riesig
Ursache:

grid-template-columns: 1fr

Kein max-width

Boxen dürfen wachsen

✅ Lösung:
.link-box {
  width: 100%;
  max-width: 180px;
}


oder im Grid:

grid-template-columns: repeat(auto-fill, minmax(160px, 160px));

🔴 Symptom 4: Bilder sind plötzlich riesig
Ursache:

Kein festes width / height

CSS greift nicht (falscher Pfad!)

✅ Lösung:
.link-box img {
  width: 48px;
  height: 48px;
  object-fit: contain;
}


👉 Check:
Ist das Bild wirklich <img src="images/Router.png">
und nicht class="images/Router.png"?

🔴 Symptom 5: Text steht neben dem Bild
Ursache:

flex-direction: row (Standard)

Kein Block-Element

✅ Lösung:
.link-box {
  display: flex;
  flex-direction: column;
  align-items: center;
}

🔴 Symptom 6: Beim Verkleinern des Browsers rutschen Boxen nach links über Überschriften
Ursache:

Grid breiter als Container

Kein max-width

Zentrierung fehlt

✅ Lösung:
.detail-grid {
  max-width: 1100px;
  margin: 0 auto;
}

🔴 Symptom 7: Auf iPad / Tablet sieht alles „komisch“ aus
Ursache:

Fixe Pixelwerte

Kein responsives Grid

✅ Lösung:
grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));

🧪 Universal-Debug-Trick
* {
  outline: 1px solid red;
}


👉 Sofort sichtbar:

welches Element zu groß

welches überläuft

welches nicht im Grid ist

Danach wieder löschen 😉

🧱 Wrapper-Lexikon (das mentale Modell)

Das ist der wichtigste Teil.
Wenn du den verstehst, passieren 80 % der Fehler nicht mehr.

🧩 Container

Bedeutung:
Ein Element, das Layout macht (Grid oder Flex).

.container {
  display: grid;
}


📌 Beispiele:

.box-grid

.group-grid

.detail-grid

👉 Regel:

Container = regelt Anordnung der Kinder

🧱 Wrapper

Bedeutung:
Ein logischer Block, der Dinge zusammenhält.

<div class="group-wrapper">
  <div class="group-title">Heimnetzwerk</div>
  <a class="link-box">…</a>
</div>


📌 Aufgaben:

Struktur

Höhe ausgleichen

Überschrift + Inhalt bündeln

👉 Wrapper machen KEIN Layout, sie sind Inhaltseinheiten.

🧩 Grid-Parent

Ein Container mit display: grid.

.group-grid {
  display: grid;
}


👉 regelt:

Spalten

Umbruch

Abstand (gap)

📦 Grid-Item

Alles direkt darunter:

<div class="group-grid">
  <div class="group-wrapper"> ← Grid-Item


👉 Grid-Items:

dürfen keine eigene Breite erzwingen

bekommen Größe vom Grid

🧱 Box (.link-box)

Die kleinste Einheit:

Bild

Text

Klickbar

.link-box {
  display: flex;
  flex-direction: column;
}


👉 Boxen:

NIE Layout für andere Boxen

NIE Grid

NIE float

🧠 Goldene Regeln (bitte merken)

Grid ordnet – Boxen stylen

Nie Grid + feste Breiten mischen

Wrapper = Struktur, nicht Layout

Wenn etwas kaputt ist → falsches Element steuert das Layout

Responsive = auto-fit + minmax()

📌 Typische Klassen & ihre Aufgabe
Klasse	Aufgabe
.box-grid	wichtige Links anordnen
.group-grid	Themenbereiche nebeneinander
.group-wrapper	Überschrift + Inhalt bündeln
.link-box	einzelne klickbare Box
.detail-grid	Detailseiten responsiv