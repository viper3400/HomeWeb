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