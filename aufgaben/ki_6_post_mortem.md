# Post Mortem

## Zusammenfassung
In dieser Übung ging es um das Perzeptron (als Einzeles, zunächst außerhalb des Zusammenhangs Neuronaler Netzte).
Dabei habe ich zunächst im Rahmen von Aufgabe 1 auf Grundlage eines Gewichtsvektors die zugehörige Trennebene / Entscheidungsgrenze
grafisch dargstellt. In diesem Kontext wurden dann bei der Folgeaufgabe weiterführend 4 andere Gewichtsvektoren vergleichend analysiert,
dh. ich habe entschieden, ob sowohl die Trennebene identisch ist als auch darüber hinaus noch die Klasssifikation die selbe bleibt.
Bei Aufgabe 2 wurde dann logische Funktionen (hier: *AND*, *OR*, *NOT*) als Perzeptron umgesetzt.
Schließlich wurde bei der letzten Aufgabe ein Perzeptron anhand von zufälligen Beispielen traininert, dabei wurde zunächst die reale Funktion
(bzw. der zugheörige Gewichtsvektor) anhand einer zufälligen Trennlinie festgelegt. auf dieser Grundlage wurde mit der Delta-Regel bzw. dem
Algorithmus für das Training eines Perzeptrons das Modell trainiert. Hierbei wurde auch mit Variantionen in Learning-Rate und Umfang des Modells
in vergleichender Analyse die Konvergenz untersucht.

## Details
Bei der ersten Aufgabe habe ich einfach aus der Beziehung $w^T = w_0 \ +\ w_1 \cdot x_1 \ +\ w_1 \cdot x_1 = 0$ die entsprechenden $x_1$/ $x_2$-Beziehung
(Gleichung umgstellt nach $x_2$) als Trennlinie ermittelt, diese Gleichung sowie den Gewichtsvektor selbst habe ich mit *matplotlib* dargstellt.
Bei der nachfolden Aufgabe konnte man ja für die ersten beiden Vektoren feststellen, dass sie gegenüber dem Referenz-Vektor aus der vorigen Aufgabe nur 
skaliert sind (mit positivem Faktor), sodass auch die Trennlinie identisch ist, die Klassifikation entsprechend auch. Beim 3. Vektor wird nicht gleichmäßig
skaliert und beim letzten Vektor wird mit negativem Faktor skaliert - hier ist die Trennlinie wie für Vektor 1 und 2 identisch, aber Klassifikation wegene
der Spiegelung des Gewichtsvektors nun genau umgekehrt.
Bei Aufgabe 2 habe wegen Unklarheiten bei der Aufgabenstellung das Ganze zuerst selbst definiert (Gewichtsvektor durch eigene Überlegung festgelegt), danach
mit dem Algorithmus und den Wahrheitstabellen - als Datensatz - traininert.

## Reflexion
Unklar war zunächst, inwieweit sich beim Vergleich der Gewichtsvektoren im Rahmen von Aufgabe 1.2 unterscheidet, ob eine Trennebene identisch ist, und die
Klassifikation ebenfalls die selbe ist. Durch den 4. Vektor wurde aber klar, dass die selbe Trennlinie natürlich 2 umgekehrte Klassifikationen haben kann.

## Erkenntnnisse

Durch die erste Aufgabe konnte man etwas mehr Verständnis über die Beziehung von Gewichtsvektor und zugehöriger Trenneben bzw. die Aufteilung des Merkmalsraums
in Klassen durch diese gewinnen - insbesondere war hierbei auch die zweite der beiden Teilaufgaben (von Aufgabe 1) hilfreich. 
Bei der Beschäftigung mit Aufgabe 2 habe ich dann eine andere Perspetive auf das Perzeptron gewinnen können, da hier nun ein Modell explizit anhand einer
Problemstellung festegelget wurde, statt direkt trainiert.
Und natürlich konnte man durch die dritte Aufgabe etwas Übung im Umgang mit dem Training eines Perzeptrons sammeln. Außerdem hat man hier ein besserers Gefühl
für den Umfang / Dauer von Trainingsepochen des Perzeptrons bekommen, diesbezüglich ist sicherlich auch das Gefühl für den Trainingsumfang von MLPS bzw. Machine
Learning im Allgemeinen besser geworden.

## Link zur Lösung / Repo

- Direktlink zur Lösung (Jupyter Notebook): [Lösung öffnen](https://github.com/Cpp-dino/hsbi_ki_portfolio/blob/3d11a6b88b6423d0901de41556c8dd56a7f7384e/aufgaben/ki_6.ipynb)
