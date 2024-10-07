# Fehlersuche

!!! example "In Arbeit: Dieser Abschnitt kann unvollständig sein, da er auf Kundenrückmeldungen und Vertriebsunterstützungsfällen basiert"

## :material-chat-question: Allgemeine Probleme

!!! question "Das Live-Diagramm zeigt Null an, obwohl ein Durchfluss vorhanden und der M12-Stecker eingesteckt ist"
    1. Prüfen Sie, ob die Anschlusskonfiguration für beide Durchflussmesser richtig eingestellt ist (1/2-Kanal).

    2. Prüfen Sie, ob der Sensor mit Strom versorgt wird.

    3. Wenn alles andere fehlschlägt, versuchen Sie, das Datenerfassungsgerät erneut anzuschließen.

!!! question "Hilfe: Ich kann den Schieberegler nicht benutzen, er zeigt immer den Eingangswert an"
    ![Fehler](img/bug.png)
    
    Dies ist ein Fehler, der auftritt, wenn Sie die `CTRL`-Taste benutzen. Sie können diesen Fehler beheben, indem Sie die "STRG"-Taste auf Ihrer Tastatur gedrückt halten und mit der linken Maustaste auf den fehlerhaften Schieberegler klicken. Lassen Sie nun die `CTRL`-Taste los, drücken Sie irgendwo anders in EasyGraph und versuchen Sie es dann erneut. Der Fehler sollte behoben sein!

## :fontawesome-brands-usb: Über log.flow

!!! question "Was bedeutet "interner Boost-Konverter"?"
    Der interne Hochsetzsteller ermöglicht es dem Benutzer, eine stabile 24V-Ausgangsspannung für die Versorgung der Durchflussmesser zu erzeugen, indem er nur den USB-Anschluss verwendet (und keine DC-Buchse!). Es handelt sich um eine Schaltung, die die 5V-Busspannung auf 24V transformiert, allerdings mit einer geringen Stromstärke (aufgrund der begrenzten USB-Leistungsaufnahme). Daher ist es ratsam, nur Low-Power-Durchflussmesser mit einer Gesamtstromaufnahme $I<50 \textrm{ mA}$ an den log.flow anzuschließen, wenn man den Konverter verwendet. Andernfalls wird die interne Schaltung überhitzt und kann keine konstante Stromversorgung erzeugen.

    Der interne Aufwärtswandler ist praktisch für mobile Geräte/Notebooks, bei denen keine externe Stromversorgung verfügbar ist.

    Als Referenz: Ein TB2-Impulsgenerator von Testbox verbraucht $30 \textrm{ mA}$, während ein VSI+-Vorverstärker etwa $36 \textrm{ mA}$ verbraucht.