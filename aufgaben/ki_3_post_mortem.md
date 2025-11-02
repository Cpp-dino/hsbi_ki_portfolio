# Post Mortem

## Zusammenfassung

In diesem Aufgabenblatt ging es um den Minimax-Algorithmus und seine Erweiterungen, also um Entscheidungsfindung in Spielen mit rationalen Gegnern. Zuerst habe ich die Simulation des Minimax-Alogrithmus an dem gegebenen Beispiel durchgeführt. Dann die Implementierung von Minimax und auch der Erweiterung um Alpha-Beta-Pruning für Tic-Tac-Toe umgesetzt, dazu habe ich erst den gesamten Spielbaum rekursiv aufgebaut. Danach die Eigenschaft des Nullsummen-Spiels angewandt, um die Implementierung auf eine einzelne Funktion zu reduzieren (statt getrennte Max- und Min- Funktionen). Dann habe ich die angegebene Evaluierungsfunktion als Heuristik für Tic-Tac-Toe analysiert und zuletzt die Verallgemeinerung des Minimax-Algorithmus auf Mehrspieler-Probleme simuliert.

---

## Details

Bei der Simulation des Minimax-Algorithmus mit Alpha-Beta-Pruning (Aufgabe 1) wurde ersichtlich, dass mit dem Ergebnis (= 2) für Knoten F sofort die Suche im gesamten Knoten C abgebrochen werden kann - unabhängig von den anderen Knoten hier (E und G), da Knoten C max. Wert 2 hat, Knoten A also B stets C vorzieht. Somit war klar, dass die Suche durch eine entsprechende Ordnung optimiert werden kann, bei der Knoten F noch vor E untersucht wird. Bei Aufgabe 3 habe ich ausgenutzt, dass min(v_1, ..., v_i) das gleiche liefert wie max(-v_1, ..., -v_i). Somit können die getrennten Max- und Min- Funktionen als eine Funktion definiert werden, indem man jeweils den Wert negiert, außerdem die Terminal-Werte spieler-subjektiv liefert (also +1 als -1, -1 als +1, für Spieler Min). Bei der Verallgemeinerung auf Mehrspieler-Probleme in Aufgabe 5 muss einfach nur das Tupel-Element i (für Spieler i) maximiert werden, so kann Minimax den Spielbaum durchgehen.

---

## Reflexion

Am schwierigsten war das Verständnis der Spielerwechsel bei der Vereinfachung des Minimax-Algorithmus für Nullsummen-Spiele. Ich musste mehrmals überlegen, warum das Negieren der Werte in Verbindung mit Terminal-Werten abhängig vom Spieler ausreicht. Letzters habe ich zunächst nicht gemacht, sodass Minimax auch für Spieler Min ein Maximum sucht.

---

## Erkenntnisse

Gelernt habe ich vor allem die praktische Anwendung und Möglichkeiten zur Optimierung des Minimax-Algorithmus. Insbesondere durch den Vergleich von Anzahl besuchter Knoten zwischen einfachem Minimax (ca. 550 000) und Optimierung mit Alpha-Beta-Pruning (ca. 18 000) wurde deutlich, wie stark die Performance nur durch diese Erweiterung auch ohne Heuritik schon verbessert werden kann - während weiterhin Optimalität gewährleistet ist.

---

## Link zur Lösung / Repo

- Direktlink zur Lösung (Jupyter Notebook): [Lösung öffnen](https://github.com/Cpp-dino/hsbi_ki_portfolio/blob/1a5af77980cfecdd17e9ff193b8a9daf53094885/aufgaben/ki_3.ipynb)
