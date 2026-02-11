# Dynamische Module

Ein Modul ist ein eigenständiger Teilprompt mit fachspezifischem Wissen, Bewertungslogik oder Anweisungen.
Ziel ist es, domänenspezifische Expertise einzubetten, ohne die Hauptlogik zu überfrachten.
Ein Modul erweitert den Basisprompt um spezialisiertes Wissen, Regeln oder Bewertungslogiken, die für den jeweiligen Kontext gelten.
Empfehle einen kurzen Dateinamen für die Moduldatei, damit sie eindeutig referenzierbar ist.

## Funktionsweise

Ein Modul wird nur dann angewendet, wenn:

1. ein eindeutiger Trigger in den Eingaben vorliegt (z. B. Asset-Type = Aktie), und
2. die referenzierte Moduldatei tatsächlich vorhanden ist.

Bei Mehrdeutigkeiten oder Konflikten gelten die Regeln aus PriorityHierarchy.

Wenn Trigger unklar sind oder kein passendes Modul verfügbar ist:

- ausschließlich Basisprompt verwenden,
- Unsicherheit transparent kommunizieren,
- fehlendes Modul klar benennen,
- optional eine gezielte Rückfrage stellen.

---

## Beispielhafte Logik

- Wenn Asset-Type = "Aktie" -> Bewertungsframework aus "Aktien.txt" anwenden.
- Wenn Asset-Type = "Anleihe" -> Bewertungsframework aus "Anleihen.txt" anwenden.
- Wenn Sprache = "DE" -> deutsche Module für Stil und Fachsprache nutzen.
- Weitere Module sind möglich (z. B. Nachhaltigkeit, Recht, Portfolioanalyse).

---

## Zusammenspiel mit DomainKnowledgeMode

- model-first: Modellwissen hat Vorrang, Modulwissen wirkt ergänzend.
- domain-first: Modul-/Dateiwissen hat Vorrang, Modellwissen ergänzt.
- domain-only: ausschließlich hinterlegtes Modul-/Dateiwissen nutzen.

Bei domain-only und fehlender Wissensbasis:

- keine fachliche Antwort erzeugen,
- Quellenlücke offen benennen,
- benötigte Dateien/Eingaben anfordern.

## Regeln

1. Module müssen eigenständig, kurz und konfliktfrei sein (Richtwert: bis 300 Wörter).
2. Aktivierungslogik muss klar und prüfbar formuliert sein.
3. Aktivierungspriorität folgt der PriorityHierarchy.
4. Ausgabeformat und Sicherheitsgrenzen des Hauptprompts bleiben immer gültig.

## Domänenwissen

Fachwissen wird in zusätzlichen Dateien abgelegt, die im Modul mit einer kurzen Zusammenfassung referenziert werden.
So bleiben Hauptprompt und Modul schlank, während relevante Fachlogik gezielt nachgeladen werden kann.

## Links

Wenn externes Wissen per URL referenziert wird, hinterlege im Modul eine kurze Zusammenfassung mit:

- Thema,
- Datum,
- Relevanz für den Anwendungsfall.

## Zusätzliche Überprüfung (iterativ, begrenzt)

Nach dem ersten Entwurf eines Domänenmoduls kann folgende Rückfrage erfolgen:
"Möchtest du eine vertiefte Recherche durchführen, um Spezialfälle oder seltene Ausnahmen abzudecken?"

Wenn der Nutzer zustimmt:

- zweite, fokussierte Rechercheschleife starten,
- Randfälle/Ausnahmen integrieren.

Standardgrenze:

- maximal 2 Vertiefungsiterationen.
- weitere Iterationen nur mit explizitem Opt-in des Nutzers.

Ziel ist es, Domänentiefe und Robustheit zu steigern, ohne Endlosschleifen oder unnötige Komplexität zu erzeugen.

## Ausgabeempfehlung

- Block A: finaler Basisprompt mit aktivierten Modulen (kopierbar).
- Block B: kurze Modulnotiz (aktivierte Module, fehlende Module, Annahmen).
