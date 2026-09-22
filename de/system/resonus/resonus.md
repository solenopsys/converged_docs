# Resonus-Medien- und KI-Gateway

Resonus verbindet Echtzeitgespräche mit der Converged-Plattform. Es verarbeitet
Browser-Audio, Telefonanrufe, Transkription und KI-Sitzungen und hält die daraus
resultierenden Geschäftsaktionen innerhalb desselben Berechtigungs- und
Workflow-Modells, das auch für den Rest des Systems verwendet wird.

## Eine Sitzungsgrenze

Medientransport und KI-Interaktion teilen sich den Anrufstatus, das Timing und den
Kontext. Wenn beides in einem nativen Prozess zusammengehalten wird, muss ein
laufendes Gespräch nicht mehrere unabhängige Gateways durchlaufen, bevor es ein
Modell oder einen menschlichen Operator erreichen kann.

```text
Browser oder Telefon
       |
       v
    Resonus ---- KI-Sitzung
       |
       +-------- Weiterleitung an einen Menschen
       |
       +-------- Plattformdienste und Workflows
```

Eine Bereitstellungsrichtlinie legt fest, wie ein eingehender Anruf behandelt
wird: durch eine KI-Sitzung, durch ein menschliches Ziel, durch einen
Weiterleitungspfad oder durch Ablehnung. Transport und Medienausführung bleiben
nativ, während die Richtlinie eine kleine, austauschbare Entscheidungsschicht
bleibt.

## Plattformintegration

Resonus verwendet Plattformdienste für Anrufkontext und Geschäftsdaten. Audio-
fragmente können den Laufzeit-Cache durchlaufen, bevor der zuständige Dienst sie
speichert. Anrufe können Workflows oder Dienstoperationen auslösen, ohne dass
das Gateway die Verantwortung für diese Bereiche übernimmt.

Die Transkription wandelt Sprache in dieselbe Art strukturierter Eingabe um, die
auch für andere Schnittstellen verfügbar ist. So können Operatoren oder Kunden
auf natürliche Weise interagieren, während die daraus resultierende Aktion
weiterhin den üblichen Dienstverträgen und Prüfpfaden folgt.

## Vertrauenswürdiger Mandantenkontext

Für Datenverkehr, der über Fujin eintrifft, akzeptiert Resonus den Mandanten-
bereich aus dem vertrauenswürdigen Nachrichtenumschlag. Es leitet keinen
Bereich aus einer Telefonnummer, einer Benutzerbezeichnung oder einer
Modell-Payload ab. Der Bereich wird für die Sitzung beibehalten und an die von
dieser Sitzung verwendeten Plattformdienste weitergeleitet.

Eingangspfade, die keinen vertrauenswürdigen Bereich herstellen können, müssen
isoliert werden, bis die Bereitstellung sie an einen solchen bindet. Dadurch
wird verhindert, dass eine praktische Medienkennung stillschweigend zu einer
Autorisierungsentscheidung wird.

## Anbietergrenze

KI-Anbieter befinden sich hinter einer gemeinsamen Sitzungs- und Richtlinien-
grenze. Die Wahl des Anbieters, die Modellauswahl sowie Sprach- und
Weiterleitungsverhalten sind Entscheidungen der Bereitstellung und keine
Annahmen, die in Geschäftsmodule eingebettet sind. Das Gateway kann seine
Anbieteradapter weiterentwickeln, ohne die Art und Weise zu ändern, wie der
Rest von Converged einen KI-gestützten Anruf adressiert.

## Rolle im System

Resonus ist für die Ausführung von Echtzeitmedien und KI-Sitzungen zuständig. Es
besitzt keine Kundenakten, keine Anrufhistorie, keine Workflowdefinitionen,
keine Mandantenauswahl und kein allgemeines Nachrichtenrouting. Diese
Verantwortlichkeiten verbleiben bei den Domänendiensten, Centimanus, dem
vertrauenswürdigen Edge und Fujin.
