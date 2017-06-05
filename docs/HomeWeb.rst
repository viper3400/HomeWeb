Konfiguration
=============

Einleitung
----------

Die Konfigurationsdatei in der XML-Datei *HomeWebSettings.xml*. Dies
Datei muss sich im Root-Verzeichnis der Webanwendung HomeWeb befinden.
Diese Datei wird von HomeWeb selbst nicht erzeugt und muss vor
Inbetriebnahme mit dem Tool *HomeWeb Configuratior* erstellt werden und
manuell ins Root-Verzeichnis kopiert werden. Die Bedeutung der einzelnen
Einstellungen sind im Tool erläutert.

HomeWeb Configurator
--------------------

File/Open
    Liest die Datei *HomeWebSettings.xml* im Arbeitsverzeichnis des
    Konfigurationsprogramms oder erstellt eine neue Konfiguration aus
    Standardwerten

File/Save
    Speichert vorgenommene Änderungen zurück in Datei bzw. erstellt eine
    neue Konfigurationsdatei

Benutzerverwaltung
------------------

| HomeWeb benutzt die im IIS /ASP.NET integrierte FormsAuthentification.
  Benutzer können einzeln erstellt werden. Den Benutzern können dann
  bestimmte Rollen zugeordnet werden. Zugriffe auf HomeWeb-Funktionen
  werden dann über diese Rollen gesteuert.
| Es stehen die folgenden Rollen zur Verfügung:

+------------------+--------------------------------------------------+----+
| **Rollenname**   | **Beschreibung**                                 |    |
+==================+==================================================+====+
| UseVideoDb       | Berechtigt zur Verwendung der VideoDb            |    |
+------------------+--------------------------------------------------+----+
| UseGallery       | Berechtigt zur Benutzung der Galeriefunktionen   |    |
+------------------+--------------------------------------------------+----+
| Administrate     | Berechtigt zur Benutzerverwaltung                |    |
+------------------+--------------------------------------------------+----+

Erstellen eine neuen Benutzers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Um einen neuen Benutzer erstellen zu können muss der Benutzer in der
   Benutzerrolle ,,Administrate” sein.

-  Im HomeWeb-Hauptmenü ist dann der Menüpunkt ,,Administration”
   auswählbar.

-  Auf der Administrationsseite muss dann der Menüpunkt ,,Manage Users”
   ausgewählt werden.

-  Über ,,Create new user” kann ein neuer Benutzer erstellt werden.

-  Ein Benutzer muss einen eindeutigen Namen, eine E-Mail und ein
   Passwort haben.

Zuteilen vorn Benutzerrollen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Um einem Benutzer Rollen zuteilen zu können muss der Benutzer in der
   Benutzerrolle ,,Administrate” sein.

-  Im HomeWeb-Hauptmenü ist dann der Menüpunkt ,,Administration”
   auswählbar.

-  Auf der Administrationsseite muss dann der Menüpunkt ,,Manage Roles”
   ausgewählt werden.

-  Es werden aller verfügbaren Rollen, sowie die Benutzer angezeigt, die
   bereits in diese Rollen sind.

-  Ein Benutzer kann per ,,Delete from role” aus einer Roller entfernt
   werden.

-  Ein Benutzer kann über die Auswahl ,,Add User to role” und in der
   darauffolgenden Auswahlseite zu einer Rolle hinzugefügt werden.

VideoDb
=======

Filmsuche
---------

Standardsuche
~~~~~~~~~~~~~

Die Standardansicht der VideoDb im HomeWeb zeigt in einer Liste aller
Filme mit DiskIds (Regalnummer) und Titel an, die auf Basis des
Suchkriteriums gefunden wurden. Wenn ein Untertitel vorhanden ist, dann
wird dieser in Klammern hinter dem Titel angezeigt. Die Anzahl der Filme
in der Liste kann durch die Suche nach Titel oder DiskId eingeschränkt
werden. Bleiben nach der Suche weniger als 15 Filme in der Auswahl, so
wird in der Liste auch das Cover und Handlungstext des Films angezeigt.
Die Suche über den Titel deckt auch die Suche über den Untertitel mit
ab. Zusätzlich kann im Suchfeld auch der Name eines Schauspielers
eingegeben werden. Im Ergebnis ist allerdings nicht mehr sichtbar, an
welcher Stelle der Treffer für den Suchbegriff gefunden wurde. Dass
heisst, im Ergebnis ist nicht unterscheidbar, ob der Treffer aufgrund
eien Übereinstimmung im Titel oder aufgrund einer Übereinstimmung des
Schauspielers angezeigt wird. Hinter jedem Film in der Liste gibt es die
Menüpunkte Details, Verschieben und Tauschen.

Der Titel von Filmen, die verliehen wurden wird kann in einer anderen
Farbe angezeigt werden (Standard rot). Der Name Ausleihers steht dann in
Klammern hinter dem Titel.

Suche nach Film anhand des Bacodes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Über den Aufruf *./Videodb/DetailsByBarcode/?barcode=xyz* wird das
*custom2* Feld der DB nach dem Barcode xyz durchsucht. Bei einer
Übereinstimmung wird die Detailseite für den gefundenen Film angezeigt,
bei mehreren Ergebnissen wird eine Übersicht über diese Filme angezeigt,
auch wenn dieser Fall theoretisch nur dann vorkommen sollte, wenn auf
der DB der selbe Film mehrfach vorhanden ist.

Wird kein Ergebnis gefunden, wird die Barcodeabfrage auch an OFDB
weitergeleitet. Kommt von dort ein Titel als Ergebnis zurück und lässt
sich dieser Titel auch auf der VideoDB finden, dann wird dieser Titel
angezeigt und der Barcode für zukünftige Anfragen im *custom2* Feld
gespeichert. Ansonsten wird die komplette Indexseite zurückgegeben.
Diese Funktion ist für den Aufruf aus dem Android-Barcodescanner
gedacht.

Details
~~~~~~~

Die Detailansicht zeigt genauere Informationen zu einem Film.

ExtendendCommands
~~~~~~~~~~~~~~~~~

Mit *ExtendendCommands* können per Suchanfrage komplexere, im Code
definierte Abfragen gestartet werden. ExtendedCommands unterscheiden
sich von normalen Abfragen durch die vorangestellten 2-fachen
Doppelpunkte (::). ExtendedCommands können aus dem Suchfeld der
Webanwendung heraus oder über die JSON API angerufen werden.

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

Standortwechsel von Filmen
--------------------------

Verschieben
~~~~~~~~~~~

Ein Film kann an einen neuen, bisher leeren Standort verschoben werden.
Dazu kann eine neue DiskId eingegeben werden. Ist die eingebene DiskId
bereits vergeben, d.h. der Standort bereits belegt, erfolgt eine
entsprechende Benachrichtigung und der Standortwechsel findet nicht
statt

Tauschen
~~~~~~~~

Der Standort eines Films kann mit dem Standort eines anderen getauscht
werden. Mit dem Menüpunkt ,,Tauschen” der Hauptauswahlliste kann
zunächst der erste Filme ausgewählt werden, dieser wird dann im oberen
Bereich in der Detailansicht dargestellt. Im unteren Bereich kann nun
der zweite, zu tauschende Film ausgewählt werden (“Mit o.g. Titel
tauschen). Die Auswahl kann ebenfalls mit einer Suche eingeschränkt
werden. Im nächsten Schritt werden die beiden zu tauschenden Filme
nebeneinander dargestellt. Der Tauschvorgang muss per Button ”Tauschen"
bestätigt werden. Es erfolgt keine weitere Abfrage. Suche nach freiem
Standort

Es kann im Format RxxFy (xx = Regalnummer, y = Fachnummer) nach dem
nächsfreien Standort, bzw. der nächstfreien DiskId gesucht werden.

Löschen von Filmen aus der Sammlung
-----------------------------------

| Filme dürfen nicht komplett von der DB gelöscht werden, da so bspw.
  Referenzen verloren gehen, wenn Filme gelöscht werden, die schon
  einmal angesehen wurden (Historisierung). Film werden dadurch als
  gelöscht markiert, dass der Besitzer des Films (OwnerId) auf einen
  bestimmten dafür vorgesehnen Benutzer gesetzt wird (Konfiguration über
  DeletedOwnerId).
| Als gelöscht markierte Filme werden in der Suche noch immer gefunden
  und auch die der Liste der gesehenen Filme angezeigt. Der Titel wird
  allerdings in roter Schrift angezeigt und der Hinweis “Gelöscht” in
  Klammern angezeigt.

Die Diskid, also im Prinzip der ehemalige Standort bleibt erhalten. Bei
der Überprüfung der DiskIds sowie bei der Prüfung der nächstfreien
Diskid werden diese Filme in der derzeitigen Implementierung weiterhin
berücksichtigt. Auch bei sonstigen Prüfaktionen werden diese Filme wie
normale Filme behandelt.

Ausgenommen sind die als gelöscht markierten Filme bei dem Zugriff über
die ExtendedCommands.

Administrative Funktionen
-------------------------

Lade Coverbilder herunter
~~~~~~~~~~~~~~~~~~~~~~~~~

In der VideoDb sind nach dem Erstellen neuer Filme im Feld imgUrl
Internetlinks auf Coverbilder hinterlegt, die beim Aufruf angezeigt
werden. Um zu verhindern, dass diese Cover jeweils aus dem Internet
heruntergeladen werden müssen und um zu gewährleisten, dass die Bilder
auch in Zukunft stets verfügbar sind, können sie mit dieser Funktion
lokal auf den Server heruntergeladen und von dort aus angezeigt werden.

Dazu müssen in der Web.config der LocalCoverPath und der HttpCoverPath
konfiguriert werden. Der LocalCoverPath gibt den absoluten, pyhsischen
Pfad an, auf den die Cover heruntergeladen werden sollen, bspw.
C:WEBROOTvideodblocalcovers. Der HttpCoverPath gibt den relativen
Webpfad aus Sich des videodb-Verzeichnisses an, im Beispiel also
./localcovers/

Die Bilder werden heruntergeladen und werden nach dem Scheman ID + JPG
gespeichert, bspw. also ,,53.jpg”. Die ursprüngliche Url aus dem Feld
imgUrl wird ins custom3-Feld der DB geschrieben. Im Feld imgUrl wird nun
HttpCoverPath und Downloadname des Covers geschrieben, im Beispiel
,,../localcovers/53.jpg”

Beim nächsten Aufruf der Funktion werden alle Einträge übersprungen,
deren Eintrag im Feld custom3 nicht leer ist.

Prüfe Vollständigkeit lokaler Bilder
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Es wird geprüft, ob das Coverbild für DB-Einträge, deren Custom3 Feld
nicht leer ist und die somit ein lokales Coverbild haben müssten, auch
wirklich vorhanden ist. Bei Fehlern gibt es einen Eintrag in der
Logdatei

Prüfe Gültigkeit der DiskIds
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Es wird geprüft, ob die DiskId auf der DB der Norm RxxFyDzz entsprechen.
Fehler werden in die Logdatei geschrieben.

Finde verwaiste Coverbilder
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Werden Bilder eines Film lokal heruntergeladen, der Film aber später in
der Videodatenbank gelöscht, bleiben die lokalen JPGS zurück. Mit dieser
Funktion können diese verwaisten Bilder zunächst aufgelistet werden und
auf Wunsch mit der Endung “.orphaned” versehen werden. Anhand der Endung
können die Bilder dann manuell vom Server gelöscht werden.

Benutzerbezogene Merkmale eines Films
-------------------------------------

Favoriten
~~~~~~~~~

Ein Film kann per Klick auf das Sternsymbol zu den Favoriten des
angemeldeten Benutzer hinzugefügt werden. Ein gelber Stern bedeutet, der
Film ist ein Favorit, ein grauer Stern bedeutet, der Film ist kein
Favorit.

Filme zur erneuten Ansicht
~~~~~~~~~~~~~~~~~~~~~~~~~~

Ein Film kann unabhängig vom Favoritenstatus kann ein Film zu erneuten
Ansicht markiert werden. Dies geschieht über das Disksymbol. Ist das
Symbol mit einem *i* gekennzeichnet, so ist der Film zur erneuten
Ansicht markiert.

DB Strukur
~~~~~~~~~~

::

    CREATE TABLE `homewebbridge_usermoviesettings` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `vdb_movieid` int(11) NOT NULL,
      `asp_username` varchar(45) NOT NULL,
      `is_favorite` int(11) DEFAULT NULL,
      `watchagain` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=12 DEFAULT CHARSET=utf8;

gesehene Filme
--------------

Einleitung
~~~~~~~~~~

Die Einstiegsseite für die Funktion ist *./VideoDbViewHistory*. Auf
dieser Seite ist ersichtlich, *welcher* Film, *wann* und *wie oft* von
*einer Person* oder von *Gruppen* von Personen gesehen wurde. Für eine
bestimme Benutzergruppe oder einen bestimmten Benutzer wird eine Liste
von Filmen zurückgegeben, die

-  bereits als gesehen markierte Filme,

-  nebst dem Datum der letzten Sichtung,

-  nebst der Anzahl der Sichtungen insgesamt

enthält. Die Sortierung ist nach letzter Sichtung und nach Anzahl
möglich, jeweils auf- und absteigend. Die Standardsortierung ist nach
letzter Sichtung absteigend. Filme, die in der Videodatenbank gelöscht
wurden, werden nicht angezeigt. Per Standard wird immer für den aktuell
angemeldeten Benutzer und die angemeldete Viewgroup zurückgemeldet.

-  Benutzer können zu Nutzergruppen zusammengefasst werden
   (,,Seher-Gemeinschaften”).

-  Gesehene Filme werden zurückgemeldet mit dem Datum.

-  Jedes mal, wenn der Film gesehen wird, wird ein neuer Eintrag
   erstellt.

-  Die Daten eines Films müssen auf Benutzerebene abgespeichert werden.

-  Die Rückmeldung muss pro Benutzer und pro Benutzergruppe möglich
   sein.

-  Aufgrund der Rückmeldungen muss der ,,Gruppenzusammenzug” stattfinden

UseCases Rückmeldung im GUI
~~~~~~~~~~~~~~~~~~~~~~~~~~~

In der Übersicht zu einem Film kann per direktem Link ein Film
zurückgemeldet werden, der

-  **heute** gesehen wurde,

-  **gestern** gesehen wurde oder

-  **vorgestern** gesehen wurde.

Filme können ebenfalls **per Datum** zurückgemeldet werden, hier ist
allerdings eine zusätzliche Abfrage eines Datum notwendig. Das mehrfache
Rückmelden eines Filmes für einen Benutzer am selben Tag ist nicht
möglich.

UseCases Löschen eines ,,Gesehen”-Eintrages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In einer Übersicht, die nach Datum oder Film sortierbar ist, besteht die
Möglichkeit, einen ,,Gesehen”-Eintrag wieder zu löschen.

Benutzer und Benutzergruppen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

HomeNet bietet bereits eine integrierte Benutzerverwaltung, welche im
Moment die Zugriffsberechtigungen abbildet. In dieser Struktur gibt es
*users* und *roles*, die Zuordnung findet über *users-in-roles* statt.

ViewGroups
^^^^^^^^^^

Die ,,Sehergemeinschaften” - die ViewGroups - werden als *role*
abgebildet und können über das Administrationsmenü angelegt werden.
Somit können die Benutzer einer *role* zugeordnet werden. Zur
Unterscheidung von den anderen Rollen, beginnen die Namen der ViewGroups
mit dem Präfix VG\_ .

Abbildung auf der Datenbank
^^^^^^^^^^^^^^^^^^^^^^^^^^^

+------------------+---------------+----------------------------------------------------------------------------------+
| **Spalte**       | **Typ**       | **Verwendung**                                                                   |
+==================+===============+==================================================================================+
| id               | int           | Primärschlüssel der Tabelle                                                      |
+------------------+---------------+----------------------------------------------------------------------------------+
| vdb\_videoid     | int           | Fremdschlüssel auf videodb\_videodata (id)                                       |
+------------------+---------------+----------------------------------------------------------------------------------+
| viewdate         | datetime      | Das Datum, wann der Film gesehen wurde. Der Zeitanteil sollte ignoriert werde.   |
+------------------+---------------+----------------------------------------------------------------------------------+
| asp\_viewgroup   | varchar(45)   | Name der ASP-Rolle als Viewgroup                                                 |
+------------------+---------------+----------------------------------------------------------------------------------+
| asp\_username    | varchar(45)   | Name des ASP-Benutzers                                                           |
+------------------+---------------+----------------------------------------------------------------------------------+

Das Create-Statement für MySQL lautet:

::

    CREATE TABLE `homewebbridge_userseen` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `vdb_videoid` int(11) NOT NULL,
      `viewdate` datetime NOT NULL,
      `asp_viewgroup` varchar(45) NOT NULL,
      `asp_username` varchar(45) NOT NULL,
      PRIMARY KEY (`id`),
      UNIQUE KEY `id_UNIQUE` (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

JSON-API
========

Einleitung
----------

Der VideoDb-Teil des HomeWeb implementiert eine JSON-API, die unter der
Adresse

::

        http://www.webserver.net/HomeWeb/VideoDb/GetJson
        

für autorisierte Benutzer erreichbar ist. Diese JSON-API wird unter
anderem für die Autovervollständigung bei Suchanfragen per JavaScript
angesteuert.

Aus Gründen der Sicherheit ist die API für nicht autorisierte Benutzer
nicht verfügbar. Die Abfrage aus Drittapplikationen ist jedoch per
HTTP-Post (siehe ) über die Adresse

::

        http://www.webserver.net/HomeWeb/Account/AutomatedLogOn
        

möglich.

Autorisierter Aufruf
--------------------

Der Aufruf ist der Regel dann bereits autorisiert, wenn er aus der
Webanwendung selbst erfolgt, nachdem sich ein Benutzer angemeldet hat.

GetJson
~~~~~~~

Liefert grundsätzlich den kompletten Inhalt ohne Einschränkungen zurück.

::

        http://www.webserver.net/HomeWeb/VideoDb/GetJson
        

Parameter *search*
~~~~~~~~~~~~~~~~~~

In diesem Parameter wird der Suchbegriff für die JSON-Abfrage übergeben.
Er kann aus Kompatibilitätsgründen allein genutzt werden, es wird
allerdings empfohlen, ihn stets in Verbindung mit einem *apiCall* zu
benutzen.

::

        http://www.webserver.net/HomeWeb/VideoDb/GetJson?search=batman
        

Parameter *apiCall*
~~~~~~~~~~~~~~~~~~~

Der Parameter *apiCall* bestimmt, auf welche Art und Weise der in
*search* übergebene Weise interpretiert wird und beeinflusst so direkt
das mögliche Suchergebnis.

NotAvailable
^^^^^^^^^^^^

Standardaufruf, wenn keine apiCall-Wert übergeben wurde. Liefert
prinzipiell die selben Werte wie der Aufruf per
*GetVideoListByTitleOrDiskId*.

::

        http://www.webserver.net/HomeWeb/VideoDb/GetJson?search=batman&apiCall=NotAvailable
        

GetVideoListByTitleOrDiskId
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Interpretiert den in *search* übergebenen Wert als Titel oder DiskId und
durchsucht die entsprechenden Felder.

::

        http://www.webserver.net/HomeWeb/VideoDb/GetJson?search=batman&apiCall=GetVideoListByTitleOrDiskId}
        

GetVideoListByBarcode
^^^^^^^^^^^^^^^^^^^^^

Interpretiert den in *search* übergebenen Wert als Barcode und
durchsucht die entsprechenden Felder.

::

        http://www.webserver.net/HomeWeb/VideoDb/GetJson?search=88563412&apiCall=GetVideoListByBarcode
        

GetVideoListByTitleOrDiskIdFilterExtendendCommands
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Liefert grundsätzlich das selbe Ergebnis wie
*GetVideoListByTitleOrDiskId*. Zur Steigerung der Peformanz werden
ExtendedCommands hier jedoch nicht verarbeitet. Dieser Wert ist vor
allem für Eingabefelder gedacht, die per JavaScript-Hook bereits während
der Eingabe erste Suchergebnisse filtern und liefern sollen
(Suchvorschlag). Bei der Eingabe von ExtendendCommands wird aber in der
Regel kein Suchvorschlag vor Ende des ExtendendCommands erwartet.

::

        http://www.webserver.net/HomeWeb/VideoDb/GetJson?search=batman&apiCall=GetVideoListByTitleOrDiskIdFilterExtendendCommands
        

Aufruf aus Drittapplikationen
-----------------------------

Der Aufruf aus Drittapplikationen ist über einen HTTP-POST an die
Adresse

::

        http://www.webserver.net/HomeWeb/Account/AutomatedLogOn
        

möglich. Dabei müssen die folgenden POST-Variablen mit Werten befüllt
und übergeben werden:

User
    Gültiger HomeWeb Benutzername

Password
    Passwort des Benutzers im Klartext

returnUrl
    Im Moment *offensichtlich* nicht genutzt

searchString
    UTF-8 codierter Suchstring

ApiCall
    Art des API Aufrufs (siehe )

Fotoverwaltung und Ansicht in einer Webgalerie
==============================================

-  Über den Menüpunkt Galerie steht dem Benutzer ein Webgallerie zur
   Verfügung.

-  In einer Übersicht werden die für den Benuzer verfügbaren Webalben
   mit einem representativen Vorschaubild sowie mit dem Titel des Albums
   angezeigt (siehe Abbildung [fig:gallery\_choosealbum], Seite .

-  Durch die Auswahl eines Albums öffnet sich das Album in einem
   touchfähigen Fotokarusell (JavaScript basiert, siehe Abbildung
   [fig:gallery\_albumview], Seite ).

-  Ein Link unter dem Foto-Karusell führt zurück zur Übersichtsseite.

.. figure:: choose-album.png
   :alt: Gallerie Übersicht

   Gallerie Übersicht

.. figure:: image-carrousel.png
   :alt: JavaScript Fotokarusell

   JavaScript Fotokarusell

Administration der Galerie und der Alben
----------------------------------------

Diese Kapitel beschreibt

-  wie ein neues Album erstellt wird,

-  wie Benutzer für die Ansicht eines Albums berechtigt werden,

-  wie Benutzern das Recht zur Ansicht eines Albums entzogen wird,

-  wie einem bestehenden Album neue Fotos hinzugefügt werden,

-  wie Fotos aus einem bestehendem Album gelöscht werden und

-  ein bestehende Album gelöscht wird.

Zusammenstellen der gewünschten Fotos
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Vor Erstellen eines Webalbum müssen die gewünschten Fotos für das
   neue Album zusammengestellt werden.

-  Die Fotos müssen in einem Verzeichnis abgelegt werden, auf welches
   der Webserver, bzw. der Windowsaccount unter dem der Webserver läuft,
   Leserechte besitzt.

-  Die Galerie nimmt keine Veränderungen an Dateien in diesem
   Verzeichnis vor.

-  Die Fotos werden lediglich gelesen und die Metadaten in einer
   Datenbank abgelegt.

Achtung: Die Bilder werden später direkt aus diesem Verzeichnis in der
dort vorhanden Auflösung angezeigt. Je nach Grösse der abgelegten
Bilddateien kann es auf Seite des Galeriebesuchers bei Ansicht eines
Albums zu längeren Ladezeiten kommen.

*Es empfiehlt sich, die Bilder entsprechend herunterzurechnen und in
einer zweckdienlichen Auflösung und Grösse zu präsentieren*

.. figure:: HomeWebGallery_FileSystem.png
   :alt: Ablage von Bildern im Dateisystem

   Ablage von Bildern im Dateisystem

.. figure:: HomeWebGallery_FileSystemRights.png
   :alt: Berechtigungen für den Webserver im Dateisystem

   Berechtigungen für den Webserver im Dateisystem

Hinzufügen eines neuen Albums im HomeWeb
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Um eine neues Album erstellen zu können, muss der Benutzer Mitglieder
   der Benutzerrolle Administrate des HomeWeb sein.

-  Im HomeWeb-Hauptmenü ist dann der Menüpunkt Administration
   auswählbar.

-  Auf der Administrationseite wird der Menüpunkt Manage
   Gallerysausgewählt.

-  Über Create new wird eine neue Galerie erstellt.

-  Es werden nur Bilder vom Typ jpg eingelesen.

-  Es müssen ein Name für die Galerie und der lokale Pfad angegeben
   werden, auf dem die Bilder abgelegt sind (siehe
   [subsec:fotos\_zusammenstellen])

-  Damit ein Benutzer die Galerie anzeigen kann muss er in der Rolle
   UseGallery sein und Berechtigungen auf das jeweilige Album besitzen.

Hinweise zu Berechtigungen
~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Damit ein Benutzer den Menüpunkt Galerie im HomeWeb-Menü angezeigt
   bekommt, muss er Mitglied der Benutzerrolle UseGallery sein (siehe
   Kapitel [sec:benutzerverwaltung] auf Seite ).

-  Es können nur Berechtigungen für ganze Fotoalben, nicht aber für
   einzelne Bilder gesetzt werden.

-  Berechtigungen werden pro Benutzer gesetzt.

-  Die Berechtigung wird bei jedem Zugriff auf eine Album und auch beim
   Zugriff auf das Einzelbild geprüft.

-  Die Berechtigungen werden in der Tabelle *gallerypermission*
   gespeichert.

Vergabe von Berechtigungen
~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Die Administrationseite über den Menüpunkt Administration öffnen.

-  Dort die Galerieadministration über Manage Galleriesöffnen.

-  Den Menüpunkt Grant and remove access for users wählen.

-  Auf der Folgeseite werden alle vorhanden Alben aufgelistet.

-  Für jedes Album kann nun hier jedem HomeWeb Benutzer das Recht zu
   Ansicht gewährt bzw. je nach aktuellem Status auch wieder entzogen
   werden.

.. figure:: HomeWebGallery_Grant_1.png
   :alt: Galerie Management

   Galerie Management

Hinzufügen / Entfernen von Bildern aus einem Album
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Zum Hinzufügen bzw. Entfernen von Bilder aus einem Album müssen die
Bilder zunächst wie unter [subsec:fotos\_zusammenstellen] beschrieben im
Dateisystem hinzugefügt werden. Auf der Galerie Management-Seite im
HomeWeb muss für das entsprechende Album dann die Funktion Update
ausgeführt werden.

Die Update-Funktion eines Albums bewirkt, dass das physische
Bildverzeichnis des Albums neu eingelesen wird.

-  Neu gefundene Bilder werden zur DB hinzugefügt.

-  Im Dateisystem nicht mehr auffindbare Dateien werden von der DB
   gelöscht.

HomeWeb selbst nimmt keine Änderungen von Dateien im Dateisystem vor.

Löschen eines Albums
~~~~~~~~~~~~~~~~~~~~

Ein Album kann über die Delete-Funktion komplett gelöscht werden.

-  Die vergebenen Berechtigungen auf das Album werden gelöscht.

-  Die Bilder im Album werden gelöscht (jedoch nur auf der Datenbank und
   nicht im Dateisystem).

DB Datenstruktur/ Tabellenbeschreibung
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Die notwendige Datenbankstruktur kann mit den folgenden Statements
erstellt werden.

::

    CREATE DATABASE `content` /*!40100 DEFAULT CHARACTER SET utf8 */;

    CREATE TABLE `galleryalbums` (
      `Id` int(11) NOT NULL AUTO_INCREMENT,
      `Name` varchar(256) DEFAULT NULL,
      `LocalPath` varchar(256) DEFAULT NULL,
      `FirstDate` varchar(22) DEFAULT NULL,
      `LastDate` varchar(22) DEFAULT NULL,
      `Description` varchar(256) DEFAULT NULL,
      `ThumbPath` varchar(256) DEFAULT NULL,
      PRIMARY KEY (`Id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;

    CREATE TABLE `galleryimages` (
      `Id` int(11) NOT NULL AUTO_INCREMENT,
      `AlbumId` int(11) DEFAULT NULL,
      `Name` varchar(256) DEFAULT NULL,
      `LocalPath` varchar(256) DEFAULT NULL,
      `RemotePath` varchar(256) DEFAULT NULL,
      `Date` varchar(22) DEFAULT NULL,
      `Description` varchar(256) DEFAULT NULL,
      `Permissions` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`Id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=95 DEFAULT CHARSET=utf8;

    CREATE TABLE `gallerypermissions` (
      `Id` int(11) NOT NULL AUTO_INCREMENT,
      `User` varchar(45) DEFAULT NULL,
      `PermissionReference` int(11) DEFAULT NULL,
      PRIMARY KEY (`Id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;

galleryalbums
~~~~~~~~~~~~~

+----------------+----------------+-----------------------------------------------+
| **Feldname**   | **Datentyp**   | **Beschreibung**                              |
+================+================+===============================================+
| Id             | int            | Primary Key (eindeutiger Tabellenschlüssel)   |
+----------------+----------------+-----------------------------------------------+
| Name           | text           | Name des Albums                               |
+----------------+----------------+-----------------------------------------------+
| LocalPath      | text           | Lokaler Ablagepfad der Fotos auf dem Server   |
+----------------+----------------+-----------------------------------------------+
| FirstDate      | varchar(22)    | •                                             |
+----------------+----------------+-----------------------------------------------+
| LastDate       | varcahr(22)    | •                                             |
+----------------+----------------+-----------------------------------------------+
| Description    | text           | Beschreibung des Albums                       |
+----------------+----------------+-----------------------------------------------+

galleryimages
~~~~~~~~~~~~~

+----------------+----------------+--------------------------------------------------------+
| **Feldname**   | **Datentyp**   | **Beschreibung**                                       |
+================+================+========================================================+
| Id             | int            | Primary Key (eindeutiger Tabellenschlüssel)            |
+----------------+----------------+--------------------------------------------------------+
| AlbumId        | int            | Fremdschlüssel auf das Album, zu dem das Foto gehört   |
+----------------+----------------+--------------------------------------------------------+
| Name           | text           | Name des aktuellen Fotos                               |
+----------------+----------------+--------------------------------------------------------+
| LocalPath      | text           | Pfad zur lokalen Bildatei auf dem Server               |
+----------------+----------------+--------------------------------------------------------+
| RemotePath     | text           | Pfad zum Thumbnail des Fotos auf dem Webserver         |
+----------------+----------------+--------------------------------------------------------+
| Date           | varchar(22)    | Aufnahmedatum des Fotos                                |
+----------------+----------------+--------------------------------------------------------+
| Description    | text           | Beschreibung des Fotos                                 |
+----------------+----------------+--------------------------------------------------------+
| Permission     | text           | obsolet                                                |
+----------------+----------------+--------------------------------------------------------+

gallerypermissions
~~~~~~~~~~~~~~~~~~

| l\|l\|p9cm\ **Feldname** & **Datentyp** & **Beschreibung**

--------------

| Id & int & Primary Key (eindeutiger Tabellenschlüssel)

--------------

| UserId & int & Fremdschlüssel auf den Benutzer, für den diese
  Berechtigung gilt

--------------

| PermissionReference & int & Fremdschlüssel auf das Berechtigungsobjekt

HomeWeb-Update
==============

Für ein Update können und müssen prinzipiell alle Dateien im
entsprechenden Verzeichnis auf dem WebServer ausgetauscht werden. Im
Prinzip sollte das Update durch " Umwandlung" eines Testsystems
erfolgen, welches bereits auf der Version des Zielreleases läuft. Das
Testsystem ist identisch mit dem Hauptsystem, unterscheidet sich jedoch
in der Konfiguration (web.config / HomeWebSettings.config).

Im Deployment sind im Verzeichnis /AppData jeweils auch die aktuellen
Konfigurationsdateien des Hauptsystems enthalten und stehen dort unter
Versionskontrolle (web.config.main, HomeWebSettings.config.main. Vor
einem Update müssen diese Dateien mit den aktuellen Konfigurationen des
Testsystems abgeglichen werden und vor dem Build und dem Deployment des
gewünschten Ziel-Release im Versionskontrollsystem commited werden. Zum
Zeitpunkt des Update vom Testsystem auf das Hauptsystem müssen diese
Dateien in angepasster Form im Deployment bereit stehen.

Konzeption
==========

Aufruf aus Drittapplikationen mit verschlüsseltem Benutzerdaten
---------------------------------------------------------------

Aus Sicherheitsüberlegungen heraus, sollte der Aufruf aus
Drittapplikationen auch mit verschlüsselten Benutzerinformationen
erfolgen können.

Abhängigkeiten
--------------

+-------------------------------+--------------------------------------------------------------------------------------------------------+
| **Abhängigkeit**              | **Beschreibung**                                                                                       |
+===============================+========================================================================================================+
| Libjfunx.dll                  | Eigene Bibliothek mit häufig benötigten Grundfunktionen                                                |
+-------------------------------+--------------------------------------------------------------------------------------------------------+
| MovieSearchEngine.dll         | Bibliothek zur Anbindun von ODFB                                                                       |
+-------------------------------+--------------------------------------------------------------------------------------------------------+
| HomeLanHomeWebConnector.dll   | Eigende Bibliothek zur Anbindung des HomeLanServer für den verteilten Aufruf von VLC (experimentell)   |
+-------------------------------+--------------------------------------------------------------------------------------------------------+