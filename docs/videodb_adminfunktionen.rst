Administrative Funktionen
=========================

Lade Coverbilder herunter
-------------------------
In der VideoDb sind nach dem Erstellen neuer Filme im Feld imgUrl Internetlinks auf Coverbilder
hinterlegt, die beim Aufruf angezeigt werden. Um zu verhindern, dass diese Cover jeweils aus dem
Internet heruntergeladen werden müssen und um zu gewährleisten, dass die Bilder auch in Zukunft
stets verfügbar sind, können sie mit dieser Funktion lokal auf den Server heruntergeladen und von
dort aus angezeigt werden.
Dazu müssen in der Web.config der LocalCoverPath und der HttpCoverPath konfiguriert werden.
Der LocalCoverPath gibt den absoluten, pyhsischen Pfad an, auf den die Cover heruntergeladen
werden sollen, bspw. C:\WEBROOT\videodb\localcovers. Der HttpCoverPath gibt den relativen
Webpfad aus Sich des videodb-Verzeichnisses an, im Beispiel also ./localcovers/
Die Bilder werden heruntergeladen und werden nach dem Scheman ID + JPG gespeichert, bspw.
also „53.jpg”. Die ursprüngliche Url aus dem Feld imgUrl wird ins custom3-Feld der DB geschrieben.
Im Feld imgUrl wird nun HttpCoverPath und Downloadname des Covers geschrieben, im Beispiel
„../localcovers/53.jpg”
Beim nächsten Aufruf der Funktion werden alle Einträge übersprungen, deren Eintrag im Feld
custom3 nicht leer ist.

Prüfe Vollständigkeit lokaler Bilder
------------------------------------

Es wird geprüft, ob das Coverbild für DB-Einträge, deren Custom3 Feld nicht leer ist und die somit
ein lokales Coverbild haben müssten, auch wirklich vorhanden ist. Bei Fehlern gibt es einen Eintrag
in der Logdatei

Prüfe Gültigkeit der DiskIds
----------------------------

Es wird geprüft, ob die DiskId auf der DB der Norm RxxFyDzz entsprechen. Fehler werden in die
Logdatei geschrieben.

Finde verwaiste Coverbilder
---------------------------

Werden Bilder eines Film lokal heruntergeladen, der Film aber später in der Videodatenbank gelöscht,
bleiben die lokalen JPGS zurück. Mit dieser Funktion können diese verwaisten Bilder zunächst auf