# Post Mortem

## Zusammenfassung
In dieser Übung ging es um Entscheidungsbäumen, insbesondere Algorithmen CAL3 und ID3. Dabei habe ich zunächst im Rahmen von Aufgabe 1 beide Verfahren in Python umgesetzt und auf den gegebenen 
Datensatz (sieben Wählern mit Sozioökonimischen Attributen und Wahlpreferenz) angewendet, um entsprechende Entscheidungsregeln für zwei Kandidaten zu bestimmen. Danach habe ich den angegebenen
Entscheidungsbaum vereinfacht mit den besprochenen Pruning-Regeln. Bei der letzten Aufgabe wurde dann das Machine-Learning-Tool *Weka* ausprobiert. Dort habe ich zunächst mit dem Entscheidungsbaum-
Algorithmus *J48* auf Basis der referenzierten Datensätzen entsprechende Entscheidungsbäume trainiert und die resultierenden Metriken bzw. die Confusion Matrix analysiert. Darüber hinaus dann
mit dem Dateiformat *ARFF* auseinandergesetzt, und die als *.csv* vorliegenden Datensätzen konvertiert. Abschließend wurden die Algorithmen *J48* und *ID3* eneut angewandt und vergleichend analysiert.

## Details
Für die erste Aufgabe habe ich zunächst einige Klassen / Datenstrukturen für den allgemeinen Entscheidungsbaum erstellt, dazu eine gemeinsame Oberklasse *DTLNode* erstellt, die als Entscheidungsknoten
*DTLTree* oder als Klassen-Endknoten *DTLClassLeaf* ausgeprägt sein kann. Zur Klassifirzierung betrachtet ein *DTLTree*-Knoten ein definiertes Attribut der Eingabe, ruft dann das dem Wert zugewisene
*DTLNode* auf (entweder Endknoten *DTLClassLeaf* oder wieder *DTLTree*). Für die Implementierung des *CAL2* habe ich darber hinaus noch eine Klasse *DTLUnionLeaf* für Vereinigungsklassen als Endknoten
bzw. Unwissen-Knoten (= \*) erstellt. Beim Durchlauf des Algorithmus wird ein *DTLUnionLeaf* dann durch einen Entscheidungs-Knoten *DTLTree* ersetzt, der wiederum auf leere *DTLUnionLeaf*-Vereinigungsklassen
verweist. Für den *ID3*-Algorithmus ist diese natürlich nicht nötig, hier wird der Baum einfach rekursiv aus *DTLTree*-Knoten aufgebaut bzw. *DTLClassLeaf* bei Erreichen der Abbruchbedingung eines Pfads.

Bei Aufgabe 2 habe ich zunächst die Transformationsregel auf den linken Teil angewandt. In Verbindung mit der Pruning-Regeln für bedingt redundante Attribute hat sich für beide Seiten (ab $x_3$) der selbe
Sub-Baum ergeben. Dh. man konnte erneut Pruning für bedingt redundante Attribute einsetzten um den Test auf $x_3$ vollständig zu verwerfen.

Bei Aufgabe 3 sollten uA. auch die *CSV*-Dateien als *ARFF* konvertiert werden. Da die *ID3*-Implementierung nur Nominale Datentypen erwartet, habe ich für das Attribut *name* in der `zoo.csv` alle einzelnen
Tierarten aufgelistet.

## Reflexion
Herausfordern war zunächst, das die Ausgabe-Attribute / Klassen (*Yes* / *No*) in der ursprünglichen `restaurant.csv` Leerzeichen enthielten, daher verschiedene Klassen interpretiert wurden von *Weka*.
Als ich das Problem erkannt habe, konnte ich die Leerzeichen in der Datei entfernen, sodass nur noch die korrekten Klassen *Yes* und *No* erkannt wurden - damit haben sich die Metriken natürlich sofort
deutlich verbessert. Mit den Dateien im *ARFF*-Format besteht dieses Problem aber ebenfalls nicht. 

Bei Aufgabe 3 habe ich für das Attribut *name* in der `zoo.csv` die einzelen Tierarten als einzelne Klassen aufgelistet, daher hat der *ID3*-Algorithmus natürlich einen sehr trivialen Entscheidungsbaum
erstellt, bei der auf die entsprechende Tierart geprüft und die zugehörige Klasse (*mammals* / *fish* / etc.) geliefert wird. Das konnte ich dadurch unterbinden, indem im Menü von *Weka* das Attribut
*name* entfernt wurde, sodass ein vernünftiges Ergebniss zustande kommt.

Beim Anwenden der Algorithmen (in Aufgabe 3) habe ich neben dem vollen Training-Datensatz immer k-Fold-Cross-Valdiation verwendet (bei einem einfachen Train/Test-Split wirkt sich die zufällige Auswahl des
Test-Datensatztes ja zT. stark auf die Metriken aus, darum Cross-Validation). Bei *ID3* mit `restaurant.csv` kam es aber zu sehr schlechten Ergebnissen, darum habe ich hier stattdessen Train/Test-Split mit 75%/25% benutzt.

## Erkenntnnisse

Ich habe durch die Aufgabe ein viel tieferes Verständnis dafür bekommen, wie Entscheidungsbäume tatsächlich lernen indem der Feature-Raum schrittweise an den einzelnen Attributen aufgeteilt wird,
basierend auf Informationsgewinn. Außerdem habe ich besser verstanden, warum Pruning notwendig ist, um Überanpassung zu vermeiden. Gerade der Umgang mit *Weka* war wertvoll, um die Auswertung von 
Metriken bei Machine Learning zu üben.

## Link zur Lösung / Repo

- Direktlink zur Lösung (Jupyter Notebook): [Lösung öffnen](https://github.com/Cpp-dino/hsbi_ki_portfolio/blob/d72701eb834c81c39cd6441ec568f1ea863cd36f/aufgaben/ki_4.ipynb)
