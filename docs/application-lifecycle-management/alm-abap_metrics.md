---
layout: page
title: DORA- und DevEx-Metriken im SAP-ERP-Umfeld (ABAP)
permalink: /application-lifecycle-management/alm-abap_metrics/
parent: ALM
nav_order: 3
---

{: .no_toc}
# DORA- und DevEx-Metriken im SAP-ERP-Umfeld (ABAP)

1. TOC
{:toc}


# Der Nutzen von DORA- und DevEx-Metriken zur Optimierung von ABAP-Entwicklungsprozessen
Im Kontext der SAP-ERP-Entwicklung – insbesondere bei der Programmierung in ABAP – sind effiziente, transparente und steuerbare Entwicklungsprozesse von zentraler Bedeutung. Die Anwendung bewährter Metriken aus der DevOps-Welt, wie der DORA-Metriken ([DevOps Research and Assessment](https://dora.dev/)) und der Developer-Experience-Kennzahlen ([DevEx](https://getdx.com/research/measuring-developer-productivity-with-the-dx-core-4/)), bietet hierbei erhebliches Optimierungspotenzial. Insbesondere in traditionell prozessgesteuerten SAP-Landschaften können diese Metriken helfen, technische und organisatorische Engpässe zu identifizieren und Verbesserungsmaßnahmen zielgerichtet umzusetzen.

1. Schaffung von Transparenz im Entwicklungsprozess
Die Messung zentraler Leistungskennzahlen – wie der "Lead Time for Changes" oder der "Deployment Frequency" – erlaubt eine objektive Betrachtung des gesamten Entwicklungszyklus. Sie zeigt auf, wie lange Änderungen benötigen, um von der Anforderung in die Produktion überführt zu werden, und wie häufig produktive Auslieferungen stattfinden. Gerade in SAP-Systemen mit komplexen Freigabe- und Transportprozessen kann so sichtbar gemacht werden, an welchen Stellen im Lebenszyklus Verzögerungen auftreten.

Ein Beispiel hierfür ist die Metrik "Time in Object Lock Wait", die angibt, wie lange Entwickler durch gesperrte Objekte in ihrer Arbeit behindert werden. Diese Sperrmechanismen, die der Konsistenzsicherung dienen, können bei unzureichender Koordination zu erheblichem Produktivitätsverlust führen.

2. Identifikation technischer und organisatorischer Engpässe
Die systematische Erhebung von DORA- und DevEx-Metriken ermöglicht es, Engpässe im Prozessverlauf eindeutig zu lokalisieren. So lässt sich beispielsweise eine hohe Zahl manueller Schritte im Deployment-Prozess durch die Metrik "Manual Steps per Deployment" quantifizieren. Daraus können gezielte Automatisierungsvorhaben abgeleitet werden, etwa durch den Einsatz von gCTS (Git-enabled Change and Transport System) oder CI/CD-Lösungen für ABAP.

Darüber hinaus gibt die "Change Failure Rate" Aufschluss über die Qualität des Entwicklungsprozesses und weist auf Schwächen in den Test- oder Review-Abläufen hin. Eine hohe Änderungsfehlerrate kann Indikator für unzureichende Qualitätssicherung oder unklare Anforderungen sein.

3. Verbesserung der Planbarkeit und Steuerung
Ein weiterer zentraler Nutzen der Metrikerhebung liegt in der verbesserten Planbarkeit und Vorhersagbarkeit von Release-Zyklen. Durch kontinuierliche Erfassung und Auswertung historischer Entwicklungsdaten lassen sich Aufwandsschätzungen präzisieren und wiederkehrende Muster frühzeitig erkennen.

Darüber hinaus ermöglichen objektive Metriken eine fundierte Kommunikation zwischen Entwicklungsteams, Qualitätssicherung und Management. Diskussionen über Ressourcenzuteilung, Prozessveränderungen oder Automatisierungsmaßnahmen können auf belastbare Daten gestützt werden, wodurch Entscheidungsprozesse deutlich effizienter ablaufen.

4. Verbesserung der Developer Experience (DevEx)
Auch aus Sicht der Entwicklerinnen und Entwickler leisten DevEx-Metriken einen entscheidenden Beitrag zur Optimierung der Arbeitsbedingungen. Kennzahlen wie "Developer Waiting Time" oder "Feedback Cycle Time" geben Aufschluss darüber, inwieweit Entwickler durch Prozesse, Freigaben oder Kommunikationslücken in ihrer Produktivität eingeschränkt werden. Eine hohe Frustration durch wiederholtes Warten auf Testressourcen oder auf die Freigabe von Transportaufträgen wirkt sich nicht nur negativ auf die Performance, sondern auch auf die Mitarbeiterzufriedenheit aus.

Durch die gezielte Analyse dieser Metriken können organisatorische Maßnahmen zur Verbesserung der Zusammenarbeit und zur Erhöhung der Prozessgeschwindigkeit abgeleitet werden.

5. Grundlage für kontinuierliche Prozessverbesserung
Die Etablierung eines auf Kennzahlen basierenden Monitorings bildet die Grundlage für eine strukturierte, kontinuierliche Prozessverbesserung nach dem Prinzip des „Continuous Improvement“. Änderungen an Prozessen, Tools oder Organisationsstrukturen können hinsichtlich ihrer Wirkung transparent nachvollzogen und objektiv bewertet werden. Beispielsweise kann die Einführung automatisierter Tests oder von Review-Prozessen durch den Vergleich relevanter Metriken (z. B. Änderung der Fehlerrate oder Verkürzung der Lead Time) empirisch bewertet werden.

Fazit
Die Integration von DORA- und DevEx-Metriken in den ABAP-Entwicklungsprozess bietet auch in stark regulierten und traditionell strukturierten SAP-Landschaften eine wirkungsvolle Möglichkeit zur Prozessverbesserung. Sie ermöglicht eine datenbasierte Analyse, erhöht die Transparenz, schafft eine gemeinsame Kommunikationsbasis zwischen technischen und nicht-technischen Stakeholdern und steigert die Effizienz sowie die Zufriedenheit der Entwicklungsteams. Gerade im Kontext wachsender Anforderungen an Time-to-Market und Systemstabilität stellen diese Metriken ein unverzichtbares Werkzeug zur strategischen Weiterentwicklung des SAP-Entwicklungsprozesses dar.

---

## Relevante DORA-Metriken im SAP-ERP-Kontext

| DORA-Metrik                    | Sinnhaftigkeit im SAP-ERP-Kontext           | Besonderheiten / Einschränkungen                                                                                                                                                                                                               |
| ------------------------------ | ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Deployment Frequency**    | ✅ Sinnvoll, aber mit Einschränkungen        | SAP-Transporte sind schwergewichtig und abhängig von Freigaben, Transportaufträgen und oft sequentiell durchzuführenden Deployments. Automatisierung (z. B. mit CTS+, gCTS, oder ChaRM) kann helfen, diese Metrik überhaupt messbar zu machen. |
| **2. Lead Time for Changes**   | ✅ Sehr relevant                             | Die Zeit vom Commit (z. B. Entwicklung abgeschlossen) bis zur Produktivsetzung kann durch Objekt-Sperren, manuelle Tests und Freigabeprozesse stark verzögert werden. Diese Metrik macht Engpässe sichtbar.                                    |
| **3. Change Failure Rate**     | ⚠️ Eingeschränkt messbar                    | In ABAP fehlen häufig strukturierte Rückmeldemechanismen. Fehlerhafte Transporte, wie z.B. ein RC8 beim Import, werden selten automatisch erfasst. Integration von Monitoring- und Fehlerverfolgungstools wäre nötig (z. B. Solution Manager, Focused Build).                 |
| **4. Time to Restore Service** | ⚠️ Eher schwierig im klassischen ECC-Umfeld | Downtime des gesamten Systems durch fehlerhafte Transporte ist selten, aber wenn, dann kritisch. Die Metrik macht nur Sinn, wenn man Notfallkonzepte (z. B. Rücktransport, N+1-Systeme, Backup-Wiederherstellung) hat.                                              |

---

## Wichtige DevEx-Metriken für ABAP-Entwicklungsprozesse

| DevEx-Metrik                                    | Beschreibung                                                                             | Begründung                                                                                                                         |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Time in Object Lock Wait**                    | Zeit, die ein Entwickler wartet, weil ein Objekt gesperrt ist.                           | Im SAP sind Objektsperren ein massiver Produktivitäts- und Flow-Killer. Eine hohe Metrikzahl zeigt mangelnde Parallelisierbarkeit. Für die automatische Erfassung des Wertes ist aktuell kein bekannter Standard vorhanden. Abhilfe schafft entweder ein manueller Meldeprozess, oder eine Custom Lösung via Logging des Zugriffs auf Objektsperren.  |
| **Build & Deploy Time**                         | Zeit von „Release“ bis zur Produktivsetzung.                                             | Selbst wenn kein CI/CD existiert, kann gemessen werden, wie lange ein Transport vom Abschluss bis zur Produktion braucht.          |
| **Feedback Cycle Time (z. B. Code Review, QA)** | Zeit zwischen Commit und erstem Feedback (z. B. Review oder Test).                       | Da Reviews in SAP oft informell sind, hilft diese Metrik, manuelle Engpässe zu identifizieren.                                     |
| **Developer Waiting Time**                      | Zeit, die Entwickler mit Warten verbringen (z. B. auf Transporte, Freigaben, QA). | Besonders im Wasserfall-orientierten SAP-Change-Management (ChaRM etc.) ein Schmerzpunkt.                                          |
| **Number of Manual Steps per Deployment**       | Wie viele manuelle Aktionen sind nötig, um einen Transport zu produktivieren?            | Zeigt Reifegrad der Automatisierung. SAP hat oft hohe manuelle Aufwände – diese Metrik quantifiziert das.                          |

---

## SAP-spezifische Einschränkungen (Einfluss auf Metrik-Erhebung)

1. **Objektsperren (Locking-Mechanismus)**

   * Nur ein Entwickler pro Objekt → erschwert parallele Arbeit, reduziert Deployment-Frequenz.
   * Lang laufende Entwicklungen blockieren andere.

2. **Transportsystem & ChaRM**

   * Transporte sind sequentiell, schwer zu automatisieren.
   * Nur bedingt rollback-fähig, hohe Risikoaversion → langsame Deployment-Zyklen.

3. **Fehlende native CI/CD-Pipeline**

   * Geringe Tool-Integration, z. B. ABAPGit ist nicht überall einsatzbereit.
   * Klassische DevOps-Konzepte (Pipelines, Branching, automatische Tests) nur mit erheblichem Aufwand implementierbar.

4. **Heterogene Systemlandschaft**

   * Unterschiedliche Releases (ECC, S/4HANA), Erweiterungen (User-Exits, BADI, Z-Objekte).
   * Unterschiedliche Qualitätssicherungsmethoden.

---

## Fazit: Welche Metriken lohnen sich wirklich?

**Top-DORA-Metriken für SAP:**

* Deployment Frequency (angepasst)
* Lead Time for Changes

**Wichtige DevEx-Metriken:**

* Time in Object Lock Wait
* Developer Waiting Time
* Manual Deployment Steps

Diese Metriken machen Prozesse sichtbar und helfen dabei, **Bottlenecks zu identifizieren**, selbst wenn keine vollautomatisierten DevOps-Prozesse existieren. Sie liefern fundierte Argumente für Prozessverbesserung und Automatisierungsinitiativen im SAP-Umfeld.

---

