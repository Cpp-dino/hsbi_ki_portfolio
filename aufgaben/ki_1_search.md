# Post Mortem

## Zusammenfassung

In der Übung ging es um Problemformalisierung, verschiedene Suchverfahren implementieren und analysieren, die Rolle bzw. Dominanz von Heuristiken sowie die Optimalität von A*. Zunächst wurde ein vorgegebenes Problem (das mir in ähnlicher Form als "Schaf-Ziege-Wolf"-Problem bekannt war) formalisiert: Zustände, Aktionen sowie Start- und Zielzustand wurden definiert, und anschließend die Zustände mit möglichen Übergängen als Problemgraph skizziert.  

Danach wurden die Suchalgorithmen **Tiefensuche**, **Breitensuche** und **A*** in Python umgesetzt und die Ergebnisse hinsichtlich Effizienz (Zeit- und Speicherbedarf) grob bewertet. Für A* habe ich zusätzlich geprüft, ob die vorgegebene Heuristik zulässig ist, diese angepasst, erneut ausgeführt und die Ergebnisse verglichen.  

Außerdem wurde die Bedeutung **dominierender Heuristiken** behandelt, z. B. mit \(h_1(n)=0\) (entspricht Dijkstra / Uniform-Cost-Search) und \(h_2(n)=\) Luftlinie, um zu zeigen, dass A* effizienter oder gleich effizienter als Dijkstra ist. Zuletzt habe ich die kosten-optimale Eigenschaft von A* unter der Annahme einer zulässigen Heuristik als Widerspruchsbeweis formal hergeleitet.

---

## Details

Am interessantesten war wahrscheinlich **A***. Aber auch die anderen Suchalgorithmen waren im Vergleich spannend, da man sehen konnte, dass sich das Verhalten hauptsächlich durch die Wahl der **Datenstruktur** und der Kostenfunktion \(f\) ändert; ansonsten funktionieren alle als Best-First-Search.  

Besonders lehrreich war der Vergleich zwischen einer zulässigen und einer unzulässigen Heuristik: Obwohl beide im konkreten Fall den optimalen Pfad lieferten, zeigte sich bei der unzulässigen Heuristik, dass sie deutlich ineffizienter arbeitet und mehr Zustände expandiert – die Hauptschleife wurde hier 8-mal statt 3-mal (wie mit korrigierter Heuristik) durchlaufen. Testweise habe ich die unzulässige Heuristik noch weiter erhöht, um zu beobachten, dass bei noch größeren Überschätzungen irgendwann nicht mehr der optimale Pfad, sondern ein Umweg gewählt wird.

---

## Reflexion

Der schwierigste Teil war wohl die **Problemformalisierung**. Anfangs war es gar nicht so eindeutig, die reale Beschreibung des Elben-Orks-Problems in eine formale Zustandsdarstellung zu überführen, die sowohl vollständig als auch konsistent ist. Ich musste genau festlegen, welche Informationen einen Zustand eindeutig beschreiben und wie sich gültige Aktionen davon ableiten lassen.  

Besonders hilfreich war die Erkenntnis, dass man die **Symmetrie des Zustandsraums** nutzen kann, um den Graphen zu reduzieren: Für die Problemstellung ist es gleich, ob 3 Elben und 2 Orks auf einer Seite mit dem Pferd sind oder auf der anderen Seite.

---

## Erkenntnisse

Ich habe aus der Übung mitgenommen, dass eine saubere **Problemformalisierung** sehr wichtig ist – wenn die Zustände und Aktionen klar definiert sind, wird auch die Implementierung logisch und übersichtlich. Außerdem habe ich ein gutes Gefühl dafür bekommen, wie stark sich eine passende Heuristik auf **Effizienz** und **Korrektheit** von Suchverfahren auswirkt.

---

## Link zur Lösung / Repo

- Direktlink zur Lösung (Jupyter Notebook): [Lösung öffnen](Link_zum_Notebook_einfügen)  
- Link zum Repository (Lösung im Repo: `/aufgaben/ki_1_search.ipynb`): [Repo öffnen](Link_zum_Repo_einfügen)
