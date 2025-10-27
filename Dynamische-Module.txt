# Dynamische Module

Ein **Modul** ist ein eigenständiger Teilprompt mit fachspezifischem Wissen, Bewertungslogik oder Anweisungen.
Ziel ist es, domänenspezifische Expertise einzubetten, ohne die Hauptlogik zu überfrachten.
Ein Modul erweitert den Basisprompt um spezialisiertes Wissen, Regeln oder Bewertungslogiken, die für den jeweiligen Kontext gelten.
Empfehle einen kurzen Dateinamen für die Moduldatei um eindeutig zu referenzieren.

## *Funktionsweise:*

→ Wenn ein Eingabeparameter ein eindeutiges Label oder Muster enthält (z. B. `Asset-Type = Aktie` oder `Asset-Type = Anleihe`), wird das dazugehörige Modul geladen und mit dem Basisprompt kombiniert.
→ Jedes Modul enthält ausschließlich rollenrelevante Informationen (z. B. Bewertungskennzahlen, Datenformat, Output-Struktur).
→ Bei Mehrdeutigkeiten oder Konflikten gelten die Regeln aus *PriorityHierarchy*.
→ Fehlt ein passendes Modul oder ist die Aktivierungsbedingung unklar, wird ausschließlich der Basisprompt verwendet und die Unsicherheit transparent kommuniziert.

## **Beispielhafte Logik:**

→ Wenn Asset-Type = „Aktie“ → Wende das Bewertungsframework aus *Aktien.txt* an.
→ Wenn Asset-Type = „Anleihe“ → Wende das Bewertungsframework aus *Anleihen.txt* an.
→ Wenn Sprache = „DE“ → Nutze deutsche Module für Stil und Fachsprache.
→ Weitere Module können hinzugefügt werden (z. B. Nachhaltigkeit, Recht, Portfolioanalyse).

## **Regeln:**

1. Module müssen eigenständig, kurz (≤ 300 Wörter) und konfliktfrei sein.
2. Aktivierungslogik und Priorität werden zentral durch *PriorityHierarchy* gesteuert.
3. Die Ausgabeformate und Sicherheitsgrenzen des Hauptprompts bleiben stets gültig.

## **Domänenwissen**

Dieses Wissen wird in **zusätzlichen Dateien** abgelegt, die im Modul mit einer **kurzen Zusammenfassung** referenziert werden. Dadurch können alle relevanten Fachinformationen modular eingebunden werden, ohne den Hauptprompt zu überladen.
Bei Bedarf kann der Generator automatisch auf diese Dateien zugreifen, um spezifische Definitionen, Rechenlogiken oder Richtlinien nachzuladen.

## **Links**

Wird externes Wissen über eine **URL** referenziert, sollen diese Links im dynamischen Modul mit einer **kurzen Zusammenfassung** hinterlegt werden. Dadurch bleibt nachvollziehbar, welche externen Quellen herangezogen wurden und zu welchem Zweck. Die Zusammenfassung enthält idealerweise Thema, Datum und Relevanz der Quelle.

## **Zusätzliche Überprüfung**

Nachdem der erste Entwurf eines Domänenmoduls generiert wurde, soll automatisch eine **Rückfrage** an den Nutzer erfolgen:

→ *„Möchtest du eine vertiefte Recherche durchführen, um Spezialfälle oder seltene Ausnahmen abzudecken?“*

Wenn der Nutzer zustimmt, wird eine **zweite, fokussierte Rechercheschleife** gestartet, die spezifische Randfälle, Ausnahmebedingungen oder seltene Anwendungsbeispiele identifiziert und integriert.
Dieser iterative Prozess wird **so oft wiederholt**, bis der Nutzer das Modul als vollständig und präzise genug bestätigt.

Ziel dieser Schleife ist es, **Domänentiefe und Robustheit** progressiv zu steigern, ohne unnötige Komplexität einzuführen.
