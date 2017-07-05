.. _filmsuche:
Filmsuche
=========

Standardsuche
-------------------
Die Standardansicht der VideoDb im HomeWeb zeigt in einer Liste aller Filme mit DiskIds (Re-
galnummer) und Titel an, die auf Basis des Suchkriteriums gefunden wurden. Wenn ein Untertitel
vorhanden ist, dann wird dieser in Klammern hinter dem Titel angezeigt. Die Anzahl der Filme in
der Liste kann durch die Suche nach Titel oder DiskId eingeschränkt werden. Bleiben nach der Suche
weniger als 15 Filme in der Auswahl, so wird in der Liste auch das Cover und Handlungstext des
Films angezeigt. Die Suche über den Titel deckt auch die Suche über den Untertitel mit ab. Zusätzlich
kann im Suchfeld auch der Name eines Schauspielers eingegeben werden. Im Ergebnis ist allerdings
nicht mehr sichtbar, an welcher Stelle der Treffer für den Suchbegriff gefunden wurde. Dass heisst,
im Ergebnis ist nicht unterscheidbar, ob der Treffer aufgrund eien Übereinstimmung im Titel oder
aufgrund einer Übereinstimmung des Schauspielers angezeigt wird. Hinter jedem Film in der Liste
gibt es die Menüpunkte Details, Verschieben und Tauschen.
Der Titel von Filmen, die verliehen wurden wird kann in einer anderen Farbe angezeigt werden
(Standard rot). Der Name Ausleihers steht dann in Klammern hinter dem Titel.

Suche nach Film anhand des Bacodes
----------------------------------

Über den Aufruf
./Videodb/DetailsByBarcode/?barcode=xyz
wird das
custom2
Feld der DB nach dem
Barcode xyz durchsucht. Bei einer Übereinstimmung wird die Detailseite für den gefundenen Film
angezeigt, bei mehreren Ergebnissen wird eine Übersicht über diese Filme angezeigt, auch wenn dieser
Fall theoretisch nur dann vorkommen sollte, wenn auf der DB der selbe Film mehrfach vorhanden ist.
Wird kein Ergebnis gefunden, wird die Barcodeabfrage auch an OFDB weitergeleitet. Kommt von
dort ein Titel als Ergebnis zurück und lässt sich dieser Titel auch auf der VideoDB finden, dann
wird dieser Titel angezeigt und der Barcode für zukünftige Anfragen im
custom2
Feld gespeichert.
Ansonsten wird die komplette Indexseite zurückgegeben. Diese Funktion ist für den Aufruf aus dem
Android-Barcodescanner gedacht.

Details
-------

Die Detailansicht zeigt genauere Informationen zu einem Film.

ExtendendCommands
-----------------

Mit ExtendendCommands können per Suchanfrage komplexere, im Code definierte Abfragen gestartet
werden. ExtendedCommands unterscheiden sich von normalen Abfragen durch die vorangestellten 2-
fachen Doppelpunkte (::). ExtendedCommands können aus dem Suchfeld der Webanwendung heraus
oder über die JSON API angerufen werden.

Es werden folgende Kommandos unterstützt:

SURPRISE
^^^^^^^^

*::SURPRISE X* liefert einen Anzahl X an zufälligen
,,Überraschungsfilmen” zurück. Ist der Wert für X leer oder ungültig
wird nur ein Film zurückgegeben, als ob ::SURPRISE 1 eingegeben worden
wäre. Mit *::SURPRISE x;SEEN* bzw. *::SURPRISE x;NOT SEEN* kann
zusätzlich ein Filter angegeben werden, mit dem Zufallsfilme aus bereits
gesehenen oder aber aus den noch nicht gesehenen Filmen gesetzt werden
kann.

3D
^^

*::3D* liefert eine Liste aller 3D-Filme zurück.

DURATION100
^^^^^^^^^^^

*::DURATION100* liefert eine Liste aller Filme zurück, die eine maximale
Laufzeit von 100 Minuten haben.

DURATION\_UNDER
^^^^^^^^^^^^^^^

*::DURATION\_UNDER X* liefert eine Liste aller Filme zurück, deren
Laufzeit unter X Minuten liegt (zum Beispiel ::DURATION\_UNDER 90).

ACTOR
^^^^^

*::ACTOR Name* liefert eine Liste aller Filme, in der der mit dem Namen
gesuchte Schauspieler mitwirkt (zum Beispiel ::ACTOR Justin Timberlake).

SHOW
^^^^

*::SHOW TOWATCH* liefert eine Liste aller Filme, die der aktuelle
Benutzer zur Wiederansicht markiert hat. *::SHOW FAV* liefert eine Liste
mit Filmen, die der aktuelle Benutzer als Favorit markiert hat.

.. _Extendend Command Genre:
GENRE
^^^^^

Dem ExtendedCommand *::GENRE* muss ein Leerschlag und eines (oder mehrere) der unten aufgelisteten verfügbaren Genres folgen. Mehrere Genre sind durch ein Semikolon zu trennen. Werden mehrere Genres gesucht, so besteht zwischen den einzelnen Gneres eine UND-Verknüpfung.

Beispiel ::GENRE Action
Beispiel ::GENRE Drama;Romance

Da unter Umständen eine höhere Anzahl an Ergebnissen gefunden wird, kann diese Abfrage etwas Zeit beanspruchen.

- Action
- Adventure
- Animation
- Comedy
- Crime
- Documentary
- Drama
- Family
- Fantasy
- Film-Noir
- Horror
- Musical
- Mystery
- Romance
- Sci-Fi
- Short
- Thriller
- War
- Western
- Adult
- Music
- Biography
- History
- Sport
- Gay

