# ADR-010: Workload-Isolation nach Kritikalität

**Status:** Accepted  
**Datum:** 2026-01-04  

## Context
Die Azure-Plattform hostet Workloads mit unterschiedlichen fachlichen, technischen und regulatorischen Anforderungen.  
Kritische Anwendungen verarbeiten sensible Daten oder unterstützen geschäftskritische Prozesse und stellen erhöhte Anforderungen an Security, Verfügbarkeit und Compliance.  
Eine gemeinsame technische Umgebung für unterschiedlich kritische Workloads erhöht Risiken und erschwert Governance.

## Decision
Workloads werden entsprechend ihrer Kritikalität klassifiziert und technisch voneinander isoliert betrieben.  
Hochkritische Workloads werden in dedizierten Subscriptions und separaten Netzwerksegmenten betrieben.  
Nicht-kritische oder interne Anwendungen können gemeinsam betrieben werden, sofern Sicherheits- und Governance-Anforderungen erfüllt sind.

## Rationale
Die Isolation nach Kritikalität reduziert das Risiko von Sicherheits- und Betriebsereignissen, erleichtert die Durchsetzung differenzierter Governance-Vorgaben und ermöglicht eine gezielte Kosten- und Verantwortungszuordnung.  
Gleichzeitig wird unnötige Komplexität für weniger kritische Workloads vermieden.

## Alternatives
- Gemeinsamer Betrieb aller Workloads in einer Subscription  
- Isolation ausschließlich auf Resource-Group-Ebene  

## Consequences
- Erhöhter Verwaltungsaufwand für hochkritische Workloads  
- Verbesserte Sicherheit, Compliance und Auditierbarkeit  
- Klare Trennung von Verantwortlichkeiten und Kosten
