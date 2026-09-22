# CASE

CASE interpretiert die Anfrage eines Benutzers als Plattformbefehl. Es erhält die Menge der
Befehle, die die Plattform ausführen kann, sowie Beispiele für die Formulierungen, die jeden
Befehl ausdrücken. Aus „show equipment“ wählt es den Befehl aus, der die Ausrüstungsliste
öffnet. Aus „show order 4815“ wählt es den Befehl aus, der eine Bestellung öffnet.

Der Dienst vergleicht die Anfrage mit den Befehlsbeispielen und gibt den
gewählten Befehl mit einer Bewertung zurück. `EXECUTE` bedeutet, dass ein Befehl
eindeutig genug erkannt wurde, um ihn auszuführen. `AMBIGUOUS` bedeutet, dass mehrere
Befehle zu ähnlich sind, um zwischen ihnen zu wählen. `UNKNOWN` bedeutet, dass die Anfrage
nicht zur Befehlsmenge passt.

CASE entscheidet, was der Benutzer tun möchte. Es extrahiert nicht die Details dieser
Anfrage. Wenn ein Befehl diese benötigt, liest PARAMS denselben Text und gibt die zum Öffnen
oder Filtern des Ergebnisses erforderlichen Werte zurück: In „show order 4815“
wählt CASE den Bestellbefehl aus, und PARAMS extrahiert `4815`.
