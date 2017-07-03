---
title: "WCF-Leistungsindikatoren | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungsindikatoren [WCF]"
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
caps.latest.revision: 37
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 37
---
# WCF-Leistungsindikatoren
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] beinhaltet einen umfangreichen Satz von Leistungsindikatoren zur Messung der Anwendungsleistung.  
  
## Aktivieren von Leistungsindikatoren  
 Leistungsindikatoren für einen [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Dienst können folgendermaßen über die Konfigurationsdatei app.config des [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Diensts aktiviert werden:  
  
```  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 Das `performanceCounters`\-Attribut kann dafür festgelegt werden, dass ein bestimmter Typ von Leistungsindikatoren aktiviert wird.  Folgende Werte sind gültig:  
  
-   All: Alle Kategorieindikatoren \(ServiceModelService, ServiceModelEndpoint und ServiceModelOperation\) werden aktiviert.  
  
-   ServiceOnly: Nur ServiceModelService\-Kategorieindikatoren werden aktiviert.  Dies ist der Standardwert.  
  
-   Off: ServiceModel\*\-Leistungsindikatoren werden deaktiviert.  
  
 Sollen Leistungsindikatoren für alle [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Anwendungen aktiviert werden, können die Konfigurationseinstellungen in die Datei Machine.config eingefügt werden.  Im nachfolgenden Abschnitt **Erhöhen der Arbeitsspeichergröße für Leistungsindikatoren** erhalten Sie weitere Informationen zum Konfigurieren ausreichenden Arbeitsspeichers für Leistungsindikatoren auf dem Computer.  
  
 Wenn Sie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Erweiterungspunkte \(z. B. aufrufende Instanzen für benutzerdefinierte Vorgänge\) verwenden, müssen Sie auch eigene Leistungsindikatoren ausgeben.  Dies liegt daran, dass [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bei Implementierung eines Erweiterungspunkts die Standardleistungsindikatoren nicht mehr im Standardpfad ausgeben kann.  Wenn Sie keine Unterstützung für manuelle Leistungsindikatoren implementieren, werden die erwarteten Leistungsindikatordaten möglicherweise nicht angezeigt.  
  
 Leistungsindikatoren können auch folgendermaßen im Code aktiviert werden:  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## Anzeigen von Leistungsdaten  
 Wenn Sie von den Leistungsindikatoren erfasste Daten anzeigen möchten, verwenden Sie den in Windows integrierten Leistungsmonitor \(Perfmon.exe\).  Dieses Tool wird durch Wechseln zu **Start** und Klicken auf **Ausführen** sowie durch anschließendes Eingeben von `perfmon.exe` im Dialogfeld gestartet.  
  
> [!NOTE]
>  Leistungsindikatorinstanzen werden möglicherweise freigegeben, bevor die letzten Nachrichten vom Endpunktverteiler verarbeitet wurden.  Dies kann dazu führen, dass Leistungsdaten für einige Nachrichten nicht erfasst werden.  
  
## Erhöhen der Arbeitsspeichergröße für Leistungsindikatoren  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] verwendet für die Leistungsindikatorkategorien einen separaten freigegebenen Arbeitsspeicher.  
  
 Standardmäßig wird separater freigegebener Arbeitsspeicher auf ein Viertel der Größe des globalen Leistungsindikator\-Arbeitsspeichers festgelegt.  Der standardmäßige globale Leistungsindikator\-Arbeitsspeicher besitzt eine Größe von 524.288 Byte.  Daher besitzen die drei [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Leistungsindikatorkategorien eine Standardgröße von jeweils ungefähr 128 KB.  Abhängig von den Laufzeitmerkmalen der [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Anwendungen auf einem Computer ist der Leistungsindikator\-Arbeitsspeicher möglicherweise erschöpft.  In diesem Fall schreibt [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] einen Fehler in das Anwendungsereignisprotokoll.  Der Inhaltsfehler gibt an, dass ein Leistungsindikator nicht geladen wurde, und der Eintrag beinhaltet die Ausnahme "System.InvalidOperationException: Nicht genügend Arbeitsspeicher zum Anzeigen der benutzerdefinierten Indikatordatei." Wird die Ablaufverfolgung auf Fehlerebene aktiviert, wird dieser Fehler ebenfalls nachverfolgt.  Ist der Arbeitsspeicher des Leistungsindikators erschöpft, kann das Fortsetzen der Ausführung der [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Anwendungen mit aktivierten Leistungsindikatoren zu einem Nachlassen der Leistung führen.  Der zuständige Administrator sollte den Computer für das Zuordnen von ausreichendem Arbeitsspeicher konfigurieren, damit die maximale Anzahl der Leistungsindikatoren, die jederzeit vorhanden sein können, unterstützt wird.  
  
 Sie können die Menge des Leistungsindikator\-Arbeitsspeichers für [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Kategorien in der Registrierung ändern.  Dazu muss den drei folgenden Speicherorten ein neuer DWORD\-Wert mit der Bezeichnung `FileMappingSize` hinzugefügt und auf den gewünschten Wert in Byte festgelegt werden.  Starten Sie den Computer neu, damit diese Änderungen wirksam werden.  
  
-   HKLM\\System\\CurrentControlSet\\Services\\ServiceModelEndpoint 4.0.0.0\\Performance  
  
-   HKLM\\System\\CurrentControlSet\\Services\\ServiceModelOperation 4.0.0.0\\Performance  
  
-   HKLM\\System\\CurrentControlSet\\Services\\ServiceModelService 4.0.0.0\\Performance  
  
 Wenn eine große Anzahl von Objekten \(z. B. ServiceHost\) verworfen wird, die automatische Speicherbereinigung jedoch noch aussteht, registriert der `PrivateBytes`\-Leistungsindikator eine ungewöhnlich hohe Anzahl.  Zum Beheben dieses Problems können Sie entweder eigene anwendungsspezifische Indikatoren hinzufügen oder mithilfe des `performanceCounters`\-Attributs nur Indikatoren auf Dienstebene aktivieren.  
  
## Leistungsindikatortypen  
 Leistungsindikatoren werden für drei verschiedene Ebenen festgelegt: Dienst, Endpunkt und Vorgang.  
  
 Sie können WMI verwenden, um den Namen einer Leistungsindikatorinstanz abzurufen.  Beispiel:  
  
-   Der Instanzenname des Dienstindikators kann über die "CounterInstanceName"\-Eigenschaft der WMI\-[Dienst](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)\-Instanz abgerufen werden.  
  
-   Der Instanzenname des Endpunktindikators kann über die "CounterInstanceName"\-Eigenschaft der WMI\-[Endpunkt](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)\-Instanz abgerufen werden.  
  
-   Der Instanzenname des Vorgangsindikators kann über die "GetOperationCounterInstanceName"\-Methode der WMI\-[Endpunkt](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)\-Instanz abgerufen werden.  
  
 Weitere Informationen zu WMI finden Sie unter [Verwenden der Windows\-Verwaltungsinstrumentation für die Diagnose](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### Dienstleistungsindikatoren  
 Mit Dienst\-Leistungsindikatoren wird das Dienstverhalten insgesamt gemessen und die Leistung des gesamten Diensts geprüft.  Sie sind beim Anzeigen mit dem Leistungsmonitor unter dem `ServiceModelService 4.0.0.0`\-Leistungsobjekt zu finden.  Die Instanzen werden nach dem folgenden Schema benannt:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Ein Indikator in einem Dienstbereich wird vom Indikator in einer Auflistung von Endpunkten aggregiert.  
  
 Leistungsindikatoren zur Dienstinstanzerstellung werden inkrementiert, wenn ein neuer InstanceContext erstellt wird.  Beachten Sie, dass auch dann ein neuer InstanceContext erstellt wird, wenn eine nicht aktivierende Nachricht empfangen wird \(mit einem vorhandenen Dienst\), oder wenn Sie von einer Sitzung aus eine Verbindung zu einer Instanz herstellen, die Sitzung beenden und dann von einer anderen Sitzung aus die Verbindung wieder herstellen.  
  
### Endpunktleistungsindikatoren  
 Endpunktleistungsindikatoren ermöglichen das Anzeigen von Daten, die das Akzeptieren von Nachrichten durch einen Endpunkt widerspiegeln.  Sie sind beim Anzeigen mit dem Leistungsmonitor unter dem `ServiceModelEndpoint 4.0.0.0`\-Leistungsobjekt zu finden.  Die Instanzen werden nach dem folgenden Schema benannt:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Die Daten ähneln den Daten, die für einzelne Vorgänge erfasst werden, sie werden jedoch nur über den Endpunkt aggregiert.  
  
 Ein Indikator in einem Endpunktbereich wird von den Indikatoren in einer Auflistung von Vorgängen aggregiert.  
  
> [!NOTE]
>  Wenn zwei Endpunkte identische Vertragsnamen und Adressen besitzen, werden sie derselben Indikatorinstanz zugeordnet.  
  
### Vorgangsleistungsindikatoren  
 Vorgangsleistungsindikatoren befinden sich unter dem `ServiceModelOperation 4.0.0.0`\-Leistungsobjekt, wenn sie mit dem Leistungsmonitor angezeigt werden.  Jeder Vorgang hat eine einzelne Instanz.  Das heißt, wenn ein bestimmter Vertrag 10 Vorgänge enthält, werden mit diesem Vertrag 10 Vorgangsleistungsindikatoren verbunden.  Die Objektinstanzen werden nach dem folgenden Muster benannt:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Mit diesem Indikator können Sie messen, wie der Aufruf verwendet wird und wie gut der Vorgang funktioniert.  
  
 Wenn Indikatoren in mehreren Bereichen angezeigt werden können, werden von einem höheren Bereich gesammelte Daten mit Daten aus niedrigeren Bereichen aggregiert.  Beispielsweise ist `Calls` an einem Endpunkt die Summe aller Vorgangsaufrufe innerhalb des Endpunkts; bei einem Dienst ist `Calls` die Summe aller Aufrufe von Endpunkten innerhalb des Diensts.  
  
> [!NOTE]
>  Sind in einem Vertrag Vorgangsnamen doppelt vorhanden, wird nur eine Indikatorinstanz für beide Vorgänge ausgegeben.  
  
## Programmieren der WCF\-Leistungsindikatoren  
 Im SDK\-Installationsordner werden mehrere Dateien installiert, sodass ein programmgesteuerter Zugriff auf die [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]\-Leistungsindikatoren möglich ist.  Diese Dateien werden wie folgt aufgelistet.  
  
-   \_ServiceModelEndpointPerfCounters.vrg  
  
-   \_ServiceModelOperationPerfCounters.vrg  
  
-   \_ServiceModelServicePerfCounters.vrg  
  
-   \_SMSvcHostPerfCounters.vrg  
  
-   \_TransactionBridgePerfCounters.vrg  
  
 Weitere Informationen zum programmgesteuerten Zugriff auf die Indikatoren finden Sie unter [Architektur der Leistungsindikatorprogrammierung](http://go.microsoft.com/fwlink/?LinkId=95179).  
  
## Siehe auch  
 [Verwaltung und Diagnose](../../../../../docs/framework/wcf/diagnostics/index.md)