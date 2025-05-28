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


# DORA- und DevEx-Metriken im SAP-ERP-Umfeld (ABAP)

Bei der Entwicklung mit ABAP gelten besondere Rahmenbedingungen, die sich deutlich von modernen, Cloud-nativen Entwicklungsszenarien unterscheiden. Dennoch können ausgewählte **DORA-DevOps-Metriken** und **Developer Experience (DevEx) Metriken** auch hier sinnvoll genutzt werden – jedoch angepasst an die SAP-spezifische Realität.

---

## Relevante DORA-Metriken im SAP-ERP-Kontext

| DORA-Metrik                    | Sinnhaftigkeit im SAP-ERP-Kontext           | Besonderheiten / Einschränkungen                                                                                                                                                                                                               |
| ------------------------------ | ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Deployment Frequency**    | ✅ Sinnvoll, aber mit Einschränkungen        | SAP-Transporte sind schwergewichtig und abhängig von Freigaben, Transportaufträgen und oft sequentiell durchzuführenden Deployments. Automatisierung (z. B. mit CTS+, gCTS, oder ChaRM) kann helfen, diese Metrik überhaupt messbar zu machen. |
| **2. Lead Time for Changes**   | ✅ Sehr relevant                             | Die Zeit vom Commit (z. B. Entwicklung abgeschlossen) bis zur Produktivsetzung kann durch Objekt-Sperren, manuelle Tests und Freigabeprozesse stark verzögert werden. Diese Metrik macht Engpässe sichtbar.                                    |
| **3. Change Failure Rate**     | ⚠️ Eingeschränkt messbar                    | In ABAP fehlen häufig strukturierte Rückmeldemechanismen. Fehlerhafte Transporte, wie z.B. ein RC8 beim Import, werden selten automatisch erfasst. Integration von Monitoring- und Fehlerverfolgungstools wäre nötig (z. B. Solution Manager, Focused Build).                 |
| **4. Time to Restore Service** | ⚠️ Eher schwierig im klassischen ECC-Umfeld | Downtime durch fehlerhafte Transporte ist selten, aber wenn, dann kritisch. Die Metrik macht nur Sinn, wenn man Notfallkonzepte (z. B. Rücktransport, N+1-Systeme, Backup-Wiederherstellung) hat.                                              |

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

