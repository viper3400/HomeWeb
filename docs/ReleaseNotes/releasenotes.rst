Versionsgeschichte
==================

2.30.0
------

VideoDb
~~~~~~~

- `GH 9 <https://github.com/viper3400/HomeWeb/issues/9>`_: VideoDbNetStandard Bibilothek integriert.
    - Die Titelsuche (via WebUI und via JSON API laufen nun über diese Bibilothek
    - In diesem Zusammenhang wurde das neue ExtendedCommand ::GENRE eingeführt
    - :ref:`Extendend Command Genre`
- `GH 10 <https://github.com/viper3400/HomeWeb/issues/10>`_: Abhängigkeit zu LibJVideoDB entfernt.

2.29.0
------

Konfiguration
~~~~~~~~~~~~~

- `GH #5 <https://github.com/viper3400/HomeWeb/issues/5>`_: Update diverser NuGet Pakete auf aktuelle Versionen

2.28.0
------

Konfiguration
~~~~~~~~~~~~~
- MovieMetaEngine
    - `GH #3 <https://github.com/viper3400/HomeWeb/issues/3>`_, `GH #2 <https://github.com/viper3400/HomeWeb/issues/2>`_:
    - MovieMetaEngine wird nun als NuGet Package via nuget.org eingebunden (V1.1.0)
    - Dadurch wird aber der *OfdbWebGateWayParser* nicht mehr unterstützt und wurde somit aus den Settings entfernt.

2.27.0
------

Konfiguration
~~~~~~~~~~~~~

- `GH #1 <https://github.com/viper3400/HomeWeb/issues/1>`_: Die Einstellung *DocumentationLink* wurde so angepasst, dass sie nun auch absolute URL unterstützt. Bisher war hier nur die Angabe eine Adress relative zum aktuellen Kontext möglich. Der Standardwert wurde auf `https://homeweb.readthedocs.io <https://homeweb.readthedocs.io>`_ festgelegt.

2.26.0
------

VideoDb
~~~~~~~

- Durch die Umstellung von ofdb.de auf SSL wurden Filme über die OFDB Filmsuche  nicht mehr gefunden bzw. Metadaten unvollständig heruntergeladen.
- Wenn das letzte "Gesehen"-Datum eines Films länger als 365 Tage zurückliegt, wird dies nicht mehr in Tagen sondern in Jahren und Tagen angezeigt.

2.25.0
------

VideoDb
~~~~~~~

-  Experimentelle Integration einer überarbeiteten Suchseite

Gallery
~~~~~~~

-  Implementation einer neuen JavaScript Galerie (auf bluemimp-bootstrap
   Basis)

2.24.0
------

VideoDb
~~~~~~~

-  Die Favoriten-Liste und die Nochmal-Sehen-Liste sind nur über einen
   Link im Menü aufrufbar.

-  Die Icons für Favoriten-Liste und die Nochmal-Sehen-Liste haben einen
   Tooltip erhalten.

2.23.0
------

Gallery
~~~~~~~

-  HOWEB-3: Wenn ein Album kein definiertes Preview Thumbnail hat so
   wird das erste Bild des Albums als Vorschaubild angezeigt.

-  HOWEB-2: Die Vergabe und der Entzug von Benutzerberechtigungen
   erfolgt jetzt über eine Webseite.

2.22.0
------

VideoDb
~~~~~~~

-  Der Download der Filmmetadaten kann nur direkt über das Parsing der
   Ofdb Webseite vollzogen werden (OfdbParser)

-  Über das Setting VideoDbMetaDataParser kann eingestellt werden, ob
   das Parsing über den OfdbParser oder über den OfdbWebGateway erfolgen
   soll.

2.21.1
------

VideoDb
~~~~~~~

-  Das DVR-R Icon wurde hinterlegt.

-  Beim Speichern bestehender Filme wird nicht nochmals versucht das
   Genre aus der Metadaten-Engine zu holen.

-  Der Standardwert für den OFDB Webgateway ist nun http://ofdbgw.org

2.21.0
------

VideoDb
~~~~~~~

-  Beim Erstellen neuer Filme werden die Genre mit in die DB
   geschrieben.

-  Per /VideoDbEdit/UpdateGenres/**id** können die Genres eines
   bestehenden Filmes vervollständigt werden.

-  Per /VideoDbEdit/UpdateVideosWithoutGenres können die Genres aller
   Filme geupdated werden, die nicht mindestens ein Genre haben.

2.20.0.
-------

VideoDb
~~~~~~~

-  HW-17: Möglichkeit für Benutzer Filme als Favoriten zu markieren und
   Filme auf eine Liste zum Wiederansehen zu setzen.

2.19.0
------

Gallery
~~~~~~~

-  HW-25: Beim Löschen eines Albums werden auch die darin enthaltenen
   Bilder entfernt.

-  HW-26: Ein Album kann nachträglich upgedatet werden.

-  Kleine Layoutanpassung in Albumübersicht um mehr Platz für die
   Vorschaubilder zu bekommen.

-  HW-27: Für einen User wird nun nur einmal das Nutzungsrecht pro Album
   auf die DB geschrieben.

2.18.0
------

Gallery
~~~~~~~

-  HW-21: Das Layout der Albumübersicht wurde optimiert, da die
   Thumbnails nicht wie gewünscht umgebrochen wurden.

-  HW-23: Beim Löschen eines Albums werden auch etwaige vergebene Rechte
   darauf entzogen.

-  HW-24: Auf der Seite des JavaScript-Album-Karusells wurde ein
   einfacher Link implementiert, der zurück auf die Albumseite führt.

2.17.0
------

Gallery
~~~~~~~

-  Die Gallerie wurde komplett überarbeitet.

2.16.0
------

VideoDb
~~~~~~~

-  Sucht man nach einem Barcode, so wird dieser auch gleich mit in das
   Ergebnis übernommen und muss nicht nachgetragen werden.

-  Das Produktionsland wird aus der Metadatensuche übernommen.

-  Beim Speichern eines Films nach dem Bearbeiten bzw. beim Erstellen
   wird nun unter anderem die DiskId auf Gültigkeit überprüft.

2.15.0
------

VideoDb
~~~~~~~

-  Nach den grundsätzlichen Test in 2.14.0 wurde das Erstellen neuer
   Filme über ofdbgw stabilisiert. Ein neuer Parameter in der
   Konfiguration ist hinzugekommen (OfdbGwUrlBase).

2.14.0
------

VideoDb
~~~~~~~

-  Ein Film kann ,,gelöscht” werden, in dem die OwnerId auf die in der
   Konfiguration festgelegte DeletedOwnerId gesetzt wird.

2.13.0
------

VideoDb
~~~~~~~

-  Neue Konfigurationseinstellung HomeLanServerConfigFilePath und erste
   Einbindung des HomeLanServerHomeWebConnectors.

-  Bugfix: Bei der Übergabe eines Barcodes im Index/GET wurde immer eine
   ::SURPRISE Suche ausgeführt.

-  Bei dem Aufruf ,,Tauschen” werden keine Filme mehr in die Liste
   geladen, da ja erst der Film gesucht werden muss, mit dem getauscht
   wird.

-  Erste Implementation /VideoDbEdit zu Erfassen und Editieren von
   Videos

-  Implementation der MovieMetaEngine.dll zur Auslesen von Videos über
   OFDB (ofdbgw.org)

2.12.0
------

VideoDb
~~~~~~~

-  HW-5: Neue ExtendedCommand ::SURPRISE x / ::SURPRISE x;SEEN /
   SURPRISE x;NOT SEEN

-  Der Zufallsgenerator wurde optimiert.

2.11.0
------

VideoDb
~~~~~~~

-  HW-13: Die Detailsansicht eines Films baut nun im Hintergrund immer
   auf der selben Ansicht auf. Bisher wurde die Detailansicht je nach
   Webpage neu aufgebaut.

-  HW-14: Im Header der Übersicht über die gesehenen Filme sind ein paar
   statistische Angaben eingefügt wurden. (Anzahl gesehener Filme).

2.10.0
------

VideoDb
~~~~~~~

-  HW-12: Die in 2.9.0 implementierte Schauspielersuche liefert zu viele
   unerwünschte Ergebnisse. Um nach Schauspieler zu suchen muss nun das
   ExtendedCommand ::ACTOR gefolgt vom gesuchten Schauspieler benutzt
   werden.

2.9.0
-----

VideoDb
~~~~~~~

-  HW-10:Es kann nun auf über die Namen der Schauspieler gesucht werden.
   Es findet dabei jedoch keine Unterscheidung statt, wo ein Text
   gefunden wird. Es ist somit nicht ersichtlich, ob ein Film aufgrund
   einer Übereinstimmung bei einem Titel oder bei einem Schauspieler
   angezeigt wird.

-  HW-9: Die Berechnung der Tage seitdem ein Film das Letzte mal gesehen
   wurde, berücksichtigt nun nur noch den Tag. Die Berechnung bisher hat
   auch die Zeit berücksichtigt, sodass ein falscher Wert angezeigt
   wurde.

-  HE-11: Die Informationen, wann ein Film zuletzt gesehen wurde stehen
   nun auch als formulierter Satz im GUI und per JSON zur Verfügung. Das
   erspart das Zusammensetzen des String auf der View-Ebene und
   verlagert die Logik auf die Seite des Servers.

2.8.0
-----

VideoDb
~~~~~~~

-  In der Liste der Ergebnisse der Filmsuche wird nun, wenn die
   Detailansicht verfügbar ist, jeweils angezeigt, wie oft ein Film
   bereits gesehen wurde, das letzte Datum und wie viele Tage dies
   bereits zurückliegt.

2.7.0
-----

Allgemein
~~~~~~~~~

-  Der Link “About” wurde in “Dokumentation” umbenannt. Über die
   Konfiguration (Home Web Configurator) kann nun der Documentation Link
   gesetzt werden. Dies ist ein relativer Pfad zur Domain der Webseite,
   Standardwert ist /HomeWeb/Doc/HomeWeb.pdf.

VideoDb
~~~~~~~

-  Wenn ein Film als gesehen markiert wird, wird die Detailansicht des
   Films neu geladen. Hierbei verschwand das Medienicon.

2.6.2
-----

VideoDb
~~~~~~~

-  Wenn im Suchformular ein Text eingegeben wurde, für den die
   Schnellsuche (Dropdown) kein Ergebnis lieferte, wurde die Suche
   sofort ausgeführt, als wenn man ENTER oder den Suchbutton bereits
   geklickt hätte. Der Suchbegriff verschwand komplett aus dem
   Eingabefeld. Dies wurde korrigiert. Liefert die Schnellsuche keine
   Ergebnisse wird dies nun entsprechend im DropDown angezeigt. Der
   Suchbegriff kann anschliessend angepasst werden.

-  Delay von 500ms für das Auslösen der Schnellsuche eingestellt

2.6.1
-----

VideoDb
~~~~~~~

-  In der View *./VideoDbViewHistory* konnte nicht korrekt nach Datum
   sortiert werden.

2.6.0
-----

Allgemein
~~~~~~~~~

-  Es wurden diverse NuGetPackages auf die aktuelle Version
   aktualisiert.

VideoDb
~~~~~~~

-  In Version 2.5.0 wurde die Rückmeldung von Filmen eingeführt, diese
   können nun über die View *./VideoDbViewHistory* angesehen und wenn
   notwendig wieder entfernt werden.

2.5.0
-----

Allgemein
~~~~~~~~~

-  Ein Grossteil der Benutzer-Konfiguration wurde aus der web.config in
   die HomeWebSettings.config ausgelagert. Diese ist nicht
   standardmässig Bestandteil von HomeWeb2, sondern muss zunächst mit
   dem separaten HomeWebConfigurator erstellt und ins HomeWeb
   Root-Verzeichnis kopiert werden.

VideoDb
~~~~~~~

-  Es wurde eine neue Funktion eingeführt, mit der Filme als gesehen
   gemeldet werden können.

2.4.0
-----

VideoDb
~~~~~~~

-  Neues ExtendedCommand ::DURATION100 liefert alle Filme bis 100
   Minuten Dauer.

-  GetJson: ExtendendCommands werden im Default-Modus durchgelassen,
   damit die Kommandos als Zwischenlösung auf von der Android-App

-  genutzt werden können. Nur beim Aufruf
   GetVideoListByTitleOrDiskIdFilterExtendendCommands wird geprüft, ob
   es sich um ein ExtendedCommand handelt, da es hier anderfalls zu
   Performanceproblemen aufgrund der per JavaScript gesteuerten
   Vorschlagsliste im Webinterface kommt.

2.3.0
-----

VideoDb
~~~~~~~

-  Neues ExtendedCommand ::3D liefert eine Liste aller 3D Filme zurück.

-  Titel der Webseite wir nund in der web.config als AppSetting
   ,,WebSiteTitle” hinterlegt.

-  Wenn in der Filmsuche nur ein oder zwei Zeichen eingeben wurden, kam
   es zu einem Fehler.

2.2.0
-----

VideoDb
~~~~~~~

-  Die Filmliste enthält nun im Initialzustand nicht mehr alle Filme,
   sondern nur noch einen zufällig ausgewählten Titel.

-  Die Zufallssuche wird bei jedem Reload der Seite neu ausgeführt,
   solange das Suchefeld keinen Wert enthält.

-  Extended Command: Ins Suchfeld können Extendend Commands eingegeben
   werden. Diese beginnen mit einem Doppelpunkt.

-  “::SURPRISE” liefert einen Zufallsfilm zurück.

-  Die Titelvorschläge im Suchfeld gelten nicht für Extendend Commands

-  Es wird nun auch ein Icon für das benutzte Medium eingeblendet.

2.1.0
-----

VideoDb
~~~~~~~

-  Das Suchfeld macht nun nach der Eingabe von mindestens drei
   Buchstaben erste Titel-Vorschläge.

2.0.0
-----

Allgemein
~~~~~~~~~

-  Bibliotheken: libjfunx 2.2.0

-  .NET 4.5, MVC 4.0

-  neues Layout (Default Layout MVC 4.0)

-  Im Rahmen der Layoutanpassung wurden im Kopfbereich der Seiten
   erklärende Hinweise zum Kontext hinzugefügt.

1.13.0
------

VideoDb
~~~~~~~

-  VideoDb/GetJson: Es wird nun eine API unterstüzt

   -  NotAvailable

   -  GetVideoListByTitleOrDiskId

   -  GetVideoListByBarcode

   Dazu muss die Post-Variable apiCall ausgefüllt werden, wird diese
   leer gelassen, wird automatisch NotAvailable gesetzt und das
   ursprüngliche Verhalten tritt ein.

-  Benötigt libjfunx 2.1.0

-  Auf neues Logformat umgestellt

1.12.0
------

VideoDb
~~~~~~~

-  VideoDb: In der Suchmaske gibt es nur noch ein Feld, in welches
   entweder Filmtitel oder DiskId eingeben werden kann. Fängt die
   Eingabe nach dem Muster R00 an, dann geht das System automatisch
   davon aus, dass es sich um die Suche nach einem Standort handelt.
   Andernfalls wird nach einem Titel gesucht.

-  VideoDb: Nach dem Laden der Seiten positioniert sich der Cursor nun
   automatisch im jeweiligen Eingabefeld.

1.11.1
------

VideoDb
~~~~~~~

-  Bei der Abfrage des JsonObjekts muss beim Umlauten URL encodiert
   abgefragt werden und .NET seitig wieder decodiert werden.(Android
   Schnittstelle)

1.11.0
------

VideoDb
~~~~~~~

-  Unter Account/AutomatedLogOn kann sich per HTTP Post und den
   Variablen User, Password, returnUrl und searchString angemeldet
   werden um ein JsonObjekt einer Filmliste aus der VideoDB zurück zu
   bekommen (Android Schnittstelle)

1.10.0
------

VideoDb
~~~~~~~

-  VideoDb: Verliehende Videos werden im Suchresultat farblich und mit
   dem Namen des Ausleihers gekennzeichnet.

1.9.0
-----

Allgemein
~~~~~~~~~

-  AccountAdministration: Benutzer können gelöscht werden,
   Gruppenberechtigungen können den Benutzer wieder entzogen werden.

VideoDb
~~~~~~~

-  VideoDb: Es wurde ein direkter Link auf die originale VideoDb
   hinzugefügt

-  VideoDb: (FS#84) Beim Standorttausch wurde in der Suche des 2. Films
   der Untertitel nicht mit berücksichtigt und auch nicht mit angezeigt.

1.8.0
-----

Allgemein
~~~~~~~~~

-  Bibliotheken: libjfunx.dll (2.0.0), LibJOfdb.dll (1.0.0),
   LibJVideoDB.dll (1.2.0)

VideoDb
~~~~~~~

-  VideoDb: Es wurde eine Funktion zum Auffinden verwaister Coverbilder
   hinzugefügt.

1.7.0
-----

VideoDb
~~~~~~~

-  VideoDb: Die Suche nach einem Titel wird nun auch über das
   Tabellenfeld für den Untertitel durchgeführt.

-  VideoDb: Hat ein Film einen Untertitel, so wird dieser in der
   Filmliste in Klammern hinter dem Titel angezeigt.

1.6.0
-----

Allgemein
~~~~~~~~~

-  Die Untermenüs wurden angepasst und mit einem Icon versehen. Dabei
   können unterschiedliche Iconsets verwendet werden.

1.5.0
-----

VideoDb
~~~~~~~

-  VideoDb: Die Barcodesuche findet nun in einem 2. Schritt auch auf der
   OFDB statt"

1.4.0
-----

VideoDb
~~~~~~~

-  VideoDb: Funktion “Prüfe Gültigkeit der DiskIds” hinzugefügt"

-  VideoDb: Funktion “Prüfe Vollständigkeit lokaler Bilder” hinzugefügt"

-  VideoDb: Barcodeabfrage hinzugefügt (GET)

1.3.0
-----

VideoDb
~~~~~~~

-  VideoDb: Funktion “Lade Coverbilder lokal herunter” hinzugefügt"

1.2.0
-----

VideoDb
~~~~~~~

-  VideoDb: “Suche nach freim Standort” hinzugefügt.

-  Den Menüpunkt VideoDb nach Videodatenbank umbenannt

1.1.0
-----

VideoDb
~~~~~~~

-  VideoDb: Suche, Details, Tauschen, Verschieben (mit Prüfung auf
   gültige DiskId)