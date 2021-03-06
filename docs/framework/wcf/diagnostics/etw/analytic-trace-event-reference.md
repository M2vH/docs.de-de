---
title: Ereignisverweis der analytischen Ablaufverfolgung
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
caps.latest.revision: "50"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a07aed6ade7d5eb806b666711a49c0b9507d3ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-trace-event-reference"></a>Ereignisverweis der analytischen Ablaufverfolgung
In der folgenden Tabelle werden die Ereignisebenen, Bezeichner und Nachrichten definiert, die der analytischen Ablaufverfolgung von [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zugeordnet sind.  
  
## <a name="event-reference"></a>Ereignisverweis  
  
|Ereignis-ID|Ereignisgrad|Ereignismeldung|Stichwörter|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Ausführlich|Poolreservierung %1 Bytes.|Infrastruktur|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Ausführlich|BufferPool der Größe %1, Kontingent wird um %2 geändert.|Infrastruktur|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Ausführlich|Der E/A-Threadplanungsrückruf wurde aufgerufen.|Infrastruktur|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Ausführlich|Der E/A-Threadplanungsrückruf wurde aufgerufen.|Infrastruktur|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Information|Der Verteiler hat 'AfterReceiveReply' auf einem ClientMessageInspector vom Typ '%1' aufgerufen.|Troubleshooting, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Information|Der Verteiler hat 'BeforeSendRequest' auf einem ClientMessageInspector des Typs '%1' aufgerufen.|Troubleshooting, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Information|Der Verteiler hat 'AfterCall' auf einem ClientParameterInspector aufgerufen. vom Typ '%1'.|Troubleshooting, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Information|Der Verteiler hat 'BeforeCall' auf einem ClientParameterInspector vom Typ '%1' aufgerufen.|Troubleshooting, ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Information|Ein OperationInvoker hat die '%1'-Methode aufgerufen.|EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Information|Der Verteiler hat einen ErrorHandler vom Typ '%1' mit einer Ausnahme vom Typ '%3' aufgerufen.  ErrorHandled == '%2'.|Troubleshooting, ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Information|Der Verteiler hat einen FaultProvider vom Typ '%1' mit einer Ausnahme vom Typ '%2' aufgerufen.|Troubleshooting, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Information|Der Verteiler hat 'AfterReceiveReply' auf einem MessageInspector vom Typ '%1' aufgerufen.|Troubleshooting, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Information|Der Verteiler hat 'BeforeSendRequest' auf einem MessageInspector vom Typ '%1' aufgerufen.|Troubleshooting, ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Warnung|Die '% 1'-Drosselungsgrenze von '%2' wurde erreicht.|HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Information|Der Verteiler hat 'AfterCall' auf einem ParameterInspector vom Typ '%1' aufgerufen.|Troubleshooting, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Information|Der Verteiler hat 'BeforeCall' auf einem ParameterInspector vom Typ '%1' aufgerufen.|Troubleshooting, ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|ServiceHost wurde gestartet: '%1'.|HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Information|Ein OperationInvoker hat den Aufruf der '%1'-Methode abgeschlossen.  Die Methodenaufrufdauer betrug '%2' ms.|HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Information|Der Transport hat eine Nachricht von '%1' empfangen.|Troubleshooting, ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Information|Der Transport hat eine Nachricht an '%1' gesendet.|Troubleshooting, ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Information|Der Client führt den Vorgang '%1' aus, der im Vertrag '%2' definiert ist. Die Nachricht wird an '%3' gesendet.|Troubleshooting, ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Information|Der Client hat die Ausführung des Vorgangs '%1' abgeschlossen, der im Vertrag '%2' definiert ist. Die Nachricht wurde an '%3' gesendet.|Troubleshooting, ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Fehler|Während der Meldungsverarbeitung ist eine nicht behandelte Ausnahme vom Typ '%2' aufgetreten.  Vollständige Ausnahme ToString: %1.|HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Information|Der Verteiler hat eine Nachricht an den Transport gesendet. Korrelations-ID == '%1'.|EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Information|Der Verteiler hat eine Nachricht vom Transport empfangen. Korrelations-ID == '%1'.|EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Warnung|Die '%1'-Methode hat beim Aufrufen durch den OperationInvoker eine nicht behandelte Ausnahme ausgelöst. Die Methodenaufrufdauer betrug '%2' ms.|HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Warnung|Die '%1'-Methode hat beim Aufrufen von OperationInvoker eine FaultException ausgelöst. Die Methodenaufrufdauer betrug '%2' ms.|HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Warnung|Die '%1'-Drosselungsgrenze von '%2' liegt bei 70%.|HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|%1 Dienste im Leerlauf von insgesamt %2 aktivierten Diensten wurden geschlossen.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Fehler|Name: '%1', Verweis: '%2', Nutzlast: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Warnung|Name: '%1', Verweis: '%2', Nutzlast: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Information|Name: '%1', Verweis: '%2', Nutzlast: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel|  
|[401- StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Information|Aktivitätsgrenze.|Problembehandlung|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Information|Aktivitätsgrenze.|Problembehandlung|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Information|Aktivitätsgrenze.|Problembehandlung|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Information|Aktivitätsgrenze.|Problembehandlung|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Information|%1|Troubleshooting, WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Warnung|%1|Troubleshooting, WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Übertragungsereignis ausgegeben.|Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Information|Kompilierung starten.|WebHost|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Information|Kompilierung beenden.|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Information|ServiceHostFactory-Erstellung starten.|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Information|ServiceHostFactory-Erstellung beenden.|WebHost|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Information|CreateServiceHost starten.|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Information|CreateServiceHost beenden.|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Information|HostedTransportConfigurationManager-Konfigurationsinitialisierung starten.|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Information|HostedTransportConfigurationManager-Konfigurationsinitialisierung beenden.|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Information|HostedTransportConfigurationManager-Konfigurationsinitialisierung beenden.|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Information|Öffnen von ServiceHost wurde abgeschlossen.|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Information|Anforderung mit virtuellem Pfad "%2" von AppDomain "%1" empfangen.|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Information|WebHostRequest anhalten.|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Ausführlich|Das ServiceActivation-Element mit der relativen Adresse '%1' und der normalisierten relativen Adresse '%2' wurde verarbeitet.||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Ausführlich|Die eingehende Anforderung stimmt mit einem ServiceActivation-Element mit der Adresse '%1' überein.||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Ausführlich|Die eingehende Anforderung stimmt mit einem WCF-Dienst überein, der in der Asp.Net-Route mit der Adresse %1 definiert wird.|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Ausführlich|Eine neue Asp.Net-Route '%1' mit serviceType '%2' und serviceHostFactoryType '%3' wird hinzugefügt.|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Ausführlich|IncrementBusyCount aufgerufen. Quelle: %1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Ausführlich|DecrementBusyCount aufgerufen. Quelle: %1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Ausführlich|ServiceChannelOpen wurde gestartet.|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Information|ServiceChannelOpen wurde abgeschlossen.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Information|ServiceChannelCall wurde gestartet.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Information|Asynchrone Aufrufe von ServiceChannel wurden gestartet.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Ausführlich|HTTP-Sendeanforderung starten.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Ausführlich|HTTP-Sendeanforderung anhalten.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Ausführlich|Vom HTTP-Transport wurde eine Nachricht empfangen.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Information|Die Nachrichtenverteilung wurde gestartet.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Ausführlich|Authentifizierung für die Nachrichtenverteilung starten.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Ausführlich|Autorisierung für die Nachrichtenverteilung starten.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Information|Die Nachrichtenverteilung wurde abgeschlossen.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Information|Öffnen von ServiceChannel starten.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Information|Öffnen von ServiceChannel anhalten.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Information|HTTP-Sendevorgang für die gestreamte Nachricht wurde gestartet.|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Fehler|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Fehler|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Fehler|%1 Verbindungspoolschlüssel: %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Information|%1 Verbindungspoolschlüssel: %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Fehler|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Fehler|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Fehler|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Information|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Fehler|%1|Kontingent|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Fehler|%1|Kontingent|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Information|%1|Kontingent|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Information|%1|Kontingent|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Fehler|%1|Kontingent|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Fehler|%1|Kontingent|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Ausführlich|Verhältnis von Aushandlungen für Tokenauthentifizierungs-Zustandscache: %1%2|Kontingent|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Ausführlich|Verhältnis Sicherheitssitzungen: %1%2|Kontingent|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Ausführlich|Verhältnis ausstehende Verbindungen: %1%2|Kontingent|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Ausführlich|Verhältnis gleichzeitige Sitzungen: %1/%2|Kontingent|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Ausführlich|Verhältnis gleichzeitige Sitzungen: %1/%2|Kontingent|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Ausführlich|Verhältnis ausgehende Verbindungen/Endpunkte: %1/%2|Kontingent|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Ausführlich|Verhältnis ausgehende Verbindungen/Endpunkte: %1/%2|Kontingent|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Ausführlich|Verhältnis ausstehende Nachrichten pro Kanal: %1/%2|Kontingent|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Ausführlich|Verhältnis gleichzeitige Instanzen: %1%2|Kontingent|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Information|Null ausstehende Annahmevorgänge übrig|Kontingent|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Warnung|1%|Kontingent|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Warnung|Die Anzahl von Empfangswiederholungen für die MSMQ-Nachricht mit der ID '%1' wurde erreicht.|Kontingent|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Fehler|Die maximale Anzahl von Wiederholungszyklen für die MSMQ-Nachricht mit der ID "%1" wurde überschritten.|Kontingent|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Ausführlich|"%1" neu erstellt|Kontingent|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Ausführlich|"%1" neu erstellt|Kontingent|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Fehler|1%|Kontingent|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Warnung|%1 konnte nicht abgeschlossen werden.|Kanal|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Warnung|%1 konnte nicht aufgegeben werden.|Kanal|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Warnung|Der Empfangskontext ist fehlerhaft.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Information|%1 wurde mit der Ausnahme %2 aufgegeben.|Kanal|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Information|Anzahl der zwischengespeicherten Kanalfactorys: "%1".  Maximal können "%2" Kanalfactorys zwischengespeichert werden.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Information|Eine Kanalfactory wurde aufgrund des Alters aus dem Cache entfernt, da der Cache die Einschränkung von "%1" erreicht hat.|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Information|Es wurde eine übereinstimmende Kanalfactory aus dem Cache verwendet.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Information|Die Kanalfactory aus dem Cache wird nicht verwendet, d. h., Zwischenspeichern ist für die Instanz deaktiviert.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Information|Abfragekomposition mit "%1" wurde für den Anforderungs-URI "%2" ausgeführt.|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Fehler|Der Vorgang "%1" wurde mit Fehlern verteilt.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Information|Der Vorgang "%1" wurde erfolgreich verteilt.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Information|Vom Encoder wurde eine Nachricht mit einer Größe von '%1' Bytes gelesen.|Kanal|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Information|Vom Encoder wurde eine Nachricht mit einer Größe von '%1' Bytes geschrieben.|Kanal|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Fehler|Sitzungsabbruch für im Leerlauf befindlichen Kanal zum URI: "%1".|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Ausführlich|Die Verbindungsannahme wurde gestartet.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Ausführlich|ListenerId: hat folgende SocketId akzeptiert: %2|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Ausführlich|Der Pool für "%1" besitzt keine verfügbaren Verbindungen und %2 ausgelastete Verbindungen.|Kanal|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Ausführlich|Die Deserialisierung der Anforderungsnachricht wurde vom Verteiler gestartet.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Ausführlich|Die Deserialisierung der Anforderungsnachricht wurde vom Verteiler abgeschlossen.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Ausführlich|Die Serialisierung der Antwortnachricht wurde vom Verteiler gestartet.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Ausführlich|Die Serialisierung der Antwortnachricht wurde vom Verteiler abgeschlossen.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Ausführlich|Die Serialisierung der Clientanforderung wurde gestartet.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Ausführlich|Die Serialisierung der Anforderungsnachricht wurde vom Client abgeschlossen.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Ausführlich|Die Deserialisierung der Antwortnachricht wurde vom Client gestartet.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Ausführlich|Die Deserialisierung der Antwortnachricht wurde vom Client abgeschlossen.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Ausführlich|Die Sicherheitsaushandlung wurde gestartet.|Sicherheit|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Ausführlich|Die Sicherheitsaushandlung wurde abgeschlossen.|Sicherheit|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Ausführlich|Öffnen von SecurityTokenProvider wurde abgeschlossen.|Sicherheit|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Ausführlich|Die ausgehende Nachricht wurde geschützt.|Sicherheit|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Ausführlich|Die eingehende Nachricht wurde überprüft.|Sicherheits-ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Ausführlich|Das Abrufen der Dienstinstanz wurde gestartet.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Ausführlich|Die Dienstinstanz wurde abgerufen.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Ausführlich|ChannelHandlerId:%1 - Nachrichtenempfangsschleife wurde gestartet.|Kanal|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Ausführlich|ChannelHandlerId:%1 - Nachrichtenempfangsschleife wurde angehalten.|Kanal|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Ausführlich|Die ChannelFactory wurde erstellt.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Ausführlich|Die Pipeverbindungsannahme für "%1" wurde gestartet.|Kanal|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Ausführlich|Die Pipeverbindung wurde akzeptiert.|Kanal|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Ausführlich|Die Verbindungseinrichtung für "%1" wurde gestartet.|Kanal|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Ausführlich|Die Verbindung wurde eingerichtet.|Kanal|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Ausführlich|Die Sitzungspräambel für "%1" wurde verstanden.|Kanal|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Fehler|Der Verbindungsleser sendet Fehler "%1".|Kanal|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Ausführlich|Die Socketannahme wurde geschlossen.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Kritisch|Fehler beim Diensthost.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Ausführlich|Der Listener für "%1" wird geöffnet.|Kanal|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Ausführlich|Öffnen des Listeners wurde abgeschlossen.|Kanal|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Ausführlich|Das Kontingent für die maximale Anzahl von Verbindungen im Serverpool wurde erreicht.|Kontingent|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Fehler|Zeitüberschreitung für SocketId:%1 für Remoteadresse %2.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Warnung|Fehler beim Zurücksetzen der Verbindung für SocketId:%1 für Remoteadresse %2.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Ausführlich|Die Dienstsicherheitsaushandlung wurde abgeschlossen.|Sicherheit|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Fehler|Fehler beim Verarbeiten der Sicherheitsaushandlung.|Sicherheit|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Ausführlich|Die Sicherheitsüberprüfung war erfolgreich.|Sicherheit|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Fehler|Fehler bei der Sicherheitsüberprüfung.|Sicherheit|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Ausführlich|Socket für %1 wurde dupliziert.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Ausführlich|Der Sicherheitsidentitätswechsel war erfolgreich.|Sicherheit|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Warnung|Fehler beim Sicherheitsidentitätswechsel.|Sicherheit|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Warnung|Die HTTP-Kanalanforderung wurde abgebrochen.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Warnung|Die HTTP-Kanalantwort wurde abgebrochen.|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Warnung|Fehler bei der HTTP-Authentifizierung.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Ausführlich|Die SharedListenerProxy-Registrierung für URI "%1" wurde gestartet.|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Ausführlich|SharedListenerProxy-Registrierung anhalten.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Fehler|Fehler beim Registrieren von SharedListenerProxy mit Status "%1".|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Fehler|ConnectionPoolPreambleFailed.|Kanal|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Ausführlich|SslOnAcceptUpgradeStart|Sicherheit|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Ausführlich|SslOnAcceptUpgradeStop|Sicherheit|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Ausführlich|Das Codieren der Nachricht wurde von BinaryMessageEncoder gestartet.|Kanal|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Ausführlich|Das Codieren der Nachricht wurde von MtomMessageEncoder gestartet.|Kanal|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Ausführlich|Das Codieren der Nachricht wurde von TextMessageEncoder gestartet.|Kanal|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Ausführlich|Das Decodieren der Nachricht wurde von BinaryMessageEncoder gestartet.|Kanal|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Ausführlich|Der MtomMessageEncoder hat das Decodieren der Nachricht gestartet.|Kanal|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Ausführlich|Das Decodieren der Nachricht wurde von TextMessageEncoder gestartet.|Kanal|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Information|HTTP-Transport hat mit dem Empfang einer Nachricht begonnen.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Ausführlich|SocketId:%1 hat '%2' Bytes aus '%3' gelesen.|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Ausführlich|SocketId:%1 hat '%2' Bytes aus '%3' gelesen.|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Ausführlich|SocketId:%1 schreibt %2 Bytes in "%3".|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Ausführlich|SocketId:%1 schreibt %2 Bytes in "%3".|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Ausführlich|Bestätigung für SessionId: %1 wurde gesendet.|Kanal|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Information|Verbindung für SessionId:%1 wird wiederhergestellt.|Kanal|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Information|Fehler bei SessionId:%1.|Kanal|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Ausführlich|WindowsStreamSecurity initiiert Sicherheitsupgrade.|Sicherheit|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Ausführlich|Windows-Streamingsicherheit akzeptiert Upgrade.|Sicherheit|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Warnung|SocketId:%1 wird abgebrochen.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Ausführlich|HttpGetContext starten.|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Ausführlich|Senden der Präambel durch den Client beginnt.|Kanal|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Ausführlich|Senden der Präambel durch den Client wird beendet.|Kanal|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Warnung|Fehler beim Empfang der HTTP-Nachricht.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Information|TransactionScope wird mit LocalIdentifier:'%1' und DistributedIdentifier:'%2' erstellt.|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Information|Vom Encoder wurde eine gestreamte Nachricht gelesen.|Kanal|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Information|Vom Encoder wurde eine gestreamte Nachricht geschrieben.|Kanal|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Information|Vom Encoder wurde eine Nachricht asynchron geschrieben.|Kanal|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Information|BufferId:%1 hat das Schreiben von '%2' Bytes in den zugrunde liegenden Datenstrom abgeschlossen.|Kanal|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Information|Vom Encoder wurde eine Nachricht asynchron geschrieben.|Kanal|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Ausführlich|Gemeinsam genutzter Speicher für Pipe wurde erstellt bei "%1".|Kanal|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Ausführlich|NamedPipe "%1" wurde erstellt.|Kanal|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Ausführlich|Signaturüberprüfung gestartet.|Sicherheit|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Ausführlich|Signaturüberprüfung erfolgreich.|Sicherheit|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Ausführlich|Entschlüsselung des Wrapperschlüssels gestartet.|Sicherheit|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Ausführlich|Entschlüsselung des Wrapperschlüssels erfolgreich.|Sicherheit|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Ausführlich|Verarbeitung verschlüsselter Daten gestartet.|Sicherheit|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Ausführlich|Verarbeitung verschlüsselter Daten erfolgreich.|Sicherheit|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Ausführlich|Der HTTP-Nachrichtenhandler hat das Verarbeiten der eingehenden Anforderung gestartet.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Ausführlich|Der HTTP-Nachrichtenhandler hat das asynchrone Verarbeiten der eingehenden Anforderung gestartet.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Ausführlich|Der HTTP-Nachrichtenhandler hat das Verarbeiten einer eingehenden Anforderung abgeschlossen.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Warnung|Fehler beim HTTP-Nachrichtenhandler.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Fehler|WebSocket-Verbindungstimeout.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Ausführlich|Der HTTP-Nachrichtenhandler hat das Verarbeiten der Antwort gestartet.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Ausführlich|Der HTTP-Nachrichtenhandler hat das asynchrone Verarbeiten der Antwort gestartet.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Ausführlich|Der HTTP-Nachrichtenhandler hat das Verarbeiten der Antwort abgeschlossen.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Ausführlich|Das Senden der WebSocket-Verbindungsanforderung an "%1" wurde gestartet.|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Ausführlich|Die Verbindungsanforderung für WebSocketId:%1 wurde gesendet.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Ausführlich|Das Akzeptieren der WebSocket-Verbindung wurde gestartet.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Ausführlich|Die Verbindung mit WebSocketId:%1 wurde akzeptiert.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Fehler|Die WebSocket-Verbindung wurde mit dem Statuscode "%1" abgelehnt.|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Fehler|Fehler bei der WebSocket-Verbindungsanforderung: '%1'|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Fehler|Die Verbindung mit WebSocketId: %1 wurde abgebrochen.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Ausführlich|WebSocketId: %1 schreibt %2 Bytes in "%3".|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Ausführlich|WebSocketId: %1 hat den asynchronen Schreibvorgang beendet.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Ausführlich|WebSocketId: %1 hat den Lesevorgang gestartet.|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Ausführlich|WebSocketId: %1 hat %2 Bytes aus "%3" gelesen.|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Ausführlich|WebSocketId: %1 sendet Schließen-Nachricht mit dem Schließstatus "%3" an "%2".|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Ausführlich|WebSocketId: %1 sendet Nachricht zum Schließen der Ausgabe mit dem Schließstatus "%2" an "%3".|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Ausführlich|Die Verbindung mit WebSocketId: %1 wurde geschlossen.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Ausführlich|Nachricht zum Schließen der Verbindung mit WebSocketId: %1 mit dem Status "%2" empfangen.|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Ausführlich|Es wird die WebSocketVersion aus einer Client-WebSocket-Factory vom Typ '%1' verwendet.|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Ausführlich|Der Client-WebSocket mit einer Factory vom Typ '%1' wird erstellt.|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Information|XamlServicesLoad starten|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Information|XamlServicesLoad beenden|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Information|CreateWorkflowServiceHost starten|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Information|CreateWorkflowServiceHost beenden|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Information|Dienstaktivierung starten|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Information|Dienstaktivierung anhalten|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Ausführlich|Verfügbarer Speicher (Bytes): %1|Kontingent|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Information|Der Routingdienst schließt den Client '%1'.|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Warnung|Der Routingdienstclient '%1' hat einen Fehler ausgelöst.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Information|Eine unidirektionale Nachricht vom Routingdienst wird abgeschlossen.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Fehler|Fehler bei der Verarbeitung einer Nachricht auf dem Endpunkt mit der Adresse '%1'.|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Information|Der Routingdienst erstellt einen Client für folgenden Endpunkt: '%1'|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Ausführlich|Der Routingdienst wurde wie folgt konfiguriert: RouteOnHeadersOnly: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Information|Eine Routingdienst-Anforderungsantwortnachricht wird abgeschlossen.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Ausführlich|Die Nachricht mit der ID '%1' wurde an %2 Endpunktlisten weitergeleitet.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Information|Eine neue RoutingConfiguration wurde auf den Routingdienst angewendet.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Information|Der Routingdienst verarbeitet eine Nachricht mit ID: '%1', Aktion: '%2', eingehende URL: '%3' empfangen in Transaktion: %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Information|Der Routingdienst sendet die Nachricht mit der ID: "%1" [Vorgang %2] an "%3 ".|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Information|Der Routingdienst führt einen Commit für die Transaktion mit der ID '%1' aus.|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Fehler|Routingdienstkomponente %1 hat eine Duplexrückrufausnahme festgestellt.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Information|Die Routingdienstnachricht mit der ID '%1' [Vorgang %2] wurde auf den Sicherungsendpunkt '%3' verschoben.|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Information|Der Routingdienst hat eine neue Transaktion mit der ID '%1' zur Verarbeitung von Nachrichten erstellt.|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Warnung|Der Routingdienst hat beim Schließen des Ausgangs-Clients '%1' einen Fehler ausgelöst.|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Information|Der Routingdienst sendet eine Antwortnachricht mit Aktion '%1' zurück.|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Warnung|Der Routingdienst sendet eine Antwortnachricht vom Typ 'Fault' mit Aktion '%1' zurück.|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Ausführlich|Der Routingdienst ruft ReceiveContext.Complete für die Nachricht mit der ID '%1' auf.|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Warnung|Der Routingdienst ruft ReceiveContext.Abandon für die Nachricht mit der ID "%1" auf.|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Ausführlich|Nachrichten werden mit der vorhandenen Transaktion '%1' gesendet.|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Warnung|Der Routingdienst hat beim Senden an '%1' einen Fehler ausgelöst.|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Information|Der Routingdienst startet den MessageFilterTable-Abgleich.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Information|Der Routingdienst beendet den MessageFilterTable-Abgleich.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Ausführlich|Der Routingdienst ruft einen Abbruch auf folgendem Kanal auf: '%1'|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Ausführlich|Vom Routingdienst wurde eine Ausnahme behandelt.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Information|Der Routingdienst hat die Nachricht mit der ID '%1 [Vorgang %2] erfolgreich an '%3' übermittelt.|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Ausführlich|Transportlistenersitzung wurde über "%1" empfangen.|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Kritisch|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Fehler|Pipefehler beim Starten des Diensts.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Ausführlich|Die Sitzungsverteilung wurde gestartet.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Warnung|Fehler bei der Sitzungsverteilung für "%1", da die Sitzungswarteschlange mit '%2' ausstehenden Elementen voll ist.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Ausführlich|Registrierung der Nachrichtenwarteschlange starten.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Fehler|Die Registrierung der Nachrichtenwarteschlange für URI "%2" wurde mit Status "%1" abgebrochen.|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Ausführlich|Die Aufhebung der Registrierung der Nachrichtenwarteschlange für URI "%1" war erfolgreich.|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Fehler|Fehler bei der Registrierung der Nachrichtenwarteschlange für URI "%1", Status: "%2".|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Information|Die Registrierung der Nachrichtenwarteschlange für URI "%1" wurde abgeschlossen.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Fehler|Fehler beim Duplizieren des Sockets durch die Nachrichtenwarteschlange.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Ausführlich|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Ausführlich|Der TCP-Transportlistener beginnt mit dem Lauschen für den URI "%1".|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Ausführlich|Der TCP-Transportlistener ist empfangsbereit.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Fehler|Fehlercode: %1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Information|Schließen aller Listenerkanalinstanzen mithilfe von WAS abgeschlossen.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Fehler|Fehlercode: %1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Fehler|Fehlercode: %1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Ausführlich|Die WAS-Verbindung wurde hergestellt.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Ausführlich|Die WAS-Verbindung wurde getrennt.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Ausführlich|Der Pipe-Transportlistener beginnt, den URI "%1" zu überwachen.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Ausführlich|Der Pipe-Transportlistener ist nicht mehr empfangsbereit.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Information|Die Sitzungsverteilung war erfolgreich.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Fehler|Fehler bei der Sitzungsverteilung.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Kritisch|WAS-Verbindungstimeout.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Ausführlich|Das Lookup in der Routingtabelle wurde gestartet.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Ausführlich|Die Routingtabellensuche wurde abgeschlossen.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Ausführlich|Verhältnis Sitzungswarteschlange: %1%2|Kontingent|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Warnung|Nachricht konnte nicht protokolliert werden, da sie die zulässige ETW-Ereignisgröße überschreitet.|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Warnung|Der in DiscoveryClientChannel erstellte DiscoveryClient konnte nicht geschlossen werden und wurde daher abgebrochen.|Suche|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Information|Eine ProtocolException wurde beim Schließen von DiscoveryClient unterdrückt. Dies kann darauf zurückzuführen sein, dass von einem DiscoveryService nach wie vor versucht wird, eine Antwort an den DiscoveryClient zu senden.|Suche|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Information|Vom DiscoveryClient wurde eine Multicastunterdrückungsmeldung von einem DiscoveryProxy empfangen.|Suche|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Information|Eine %1-Meldung mit messageId='%2' wurde vom DiscoveryClient gelöscht, da der entsprechende %3-Vorgang abgeschlossen wurde.|Suche|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Warnung|Eine %1-Meldung mit messageId='%2' wurde gelöscht, da sie ungültigen Inhalt aufwies.|Suche|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Warnung|Eine %1-Meldung mit messageId='%2' und relatesTo='%3' wurde vom DiscoveryClient gelöscht, da entweder der entsprechende %4-Vorgang abgeschlossen wurde oder der relatesTo-Wert ungültig ist.|Suche|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Warnung|Eine Erkennungsanforderungsmeldung mit messageId='%1' wurde gelöscht, da sie eine ungültige ReplyTo-Adresse enthielt.|Suche|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Warnung|Eine %1-Meldung wurde gelöscht, da kein Inhalt vorhanden war.|Suche|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Warnung|Eine %1-Meldung wurde gelöscht, da der Meldungsheader nicht die erforderliche MessageId-Eigenschaft enthielt.|Suche|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Warnung|Eine %1-Meldung mit messageId='%2' wurde vom DiscoveryClient gelöscht, da sie nicht über die DiscoveryMessageSequence-Eigenschaft verfügte.|Suche|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Warnung|Eine %1-Meldung mit messageId='%2' wurde vom DiscoveryClient gelöscht, da der Meldungsheader nicht die erforderliche RelatesTo-Eigenschaft enthielt.|Suche|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Warnung|Eine Erkennungsanforderungsmeldung mit messageId='%1' wurde gelöscht, da sie keine ReplyTo-Adresse enthielt.|Suche|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Warnung|Eine %1-Meldung mit messageId='%2' wurde gelöscht, da es sich um ein Duplikat handelte.|Suche|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Information|Die Erkennbarkeit des Endpunkts mit EndpointAddress='%1' und ListenUri='%2' wurde deaktiviert.|Suche|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Information|Die Erkennbarkeit des Endpunkts mit EndpointAddress='%1' und ListenUri='%2' wurde aktiviert.|Suche|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Ausführlich|Ein Suchvorgang wurde im DiscoveryClientChannel initiiert, um Endpunkte zu suchen.|Suche|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Warnung|Fehler beim Erstellen des Channels mit einem gefundenen Endpunkt mit EndpointAddress='%1' und Via='%2'. Vom DiscoveryClientChannel wird nun versucht, den nächsten verfügbaren gefundenen Endpunkt zu verwenden.|Suche|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Warnung|Fehler beim Öffnen des Channels mit einem gefundenen Endpunkt mit EndpointAddress= '%1' und Via= '%2'. Vom DiscoveryClientChannel wird nun versucht, den nächsten verfügbaren gefundenen Endpunkt zu verwenden.|Suche|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Information|Der DiscoveryClientChannel hat erfolgreich einen Endpunkt erkannt und über diesen den Kanal geöffnet. Der Client ist über EndpointAddress='%1' und Via='%2' mit einem Dienst verbunden.|Suche|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Information|Der SynchronizationContext wurde von DiscoveryClientChannel auf den ursprünglichen Wert "%1" zurückgesetzt.|Suche|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Information|Der SynchronizationContext wurde von DiscoveryClientChannel auf NULL festgelegt, bevor der Suchvorgang initiiert wurde.|Suche|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Ausführlich|DataContract-Serialisierung von "%1" mit Surrogates starten.|Serialisierung|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Ausführlich|DataContract-Serialisierung mit Surrogates anhalten.|Serialisierung|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Ausführlich|DataContract-Deserialisierung von "%1" mit Surrogates starten.|Serialisierung|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Ausführlich|Die DataContract-Deserialisierung mit Surrogates wird beendet.|Serialisierung|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Ausführlich|ImportKnownTypes starten.|Serialisierung|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Ausführlich|ImportKnownTypes wird beendet.|Serialisierung|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Ausführlich|DataContract-Resolver für "%1" starten.|Serialisierung|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Ausführlich|DataContract-Generierung von %1-Writer für %2 starten.|Serialisierung|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Ausführlich|DataContract-Generierung von Writer anhalten.|Serialisierung|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Ausführlich|DataContract-Generierung von %1-Reader für %2 starten.|Serialisierung|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Ausführlich|DataContract-Generierung anhalten.|Serialisierung|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Ausführlich|Json-Generierung von %1 Reader für "%2" starten.|Serialisierung|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Ausführlich|Json-Readergenerierung anhalten.|Serialisierung|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Ausführlich|Json-Generierung von %1-Writer für %2 starten.|Serialisierung|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Ausführlich|Json-Generierung von Writer anhalten.|Serialisierung|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Ausführlich|Generierung von serialisierbarem XML-Element für "%1" starten.|Serialisierung|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Ausführlich|Generierung von serialisierbarem XML-Element anhalten.|Serialisierung|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Ausführlich|JsonMessageEncoder hat mit dem Dekodieren der Nachricht begonnen.|Kanal|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Ausführlich|JsonMessageEncoder hat mit dem Codieren der Nachricht begonnen.|Kanal|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Ausführlich|Überprüfung des SecurityToken (Typ "%1" und ID "%2") gestartet.|Sicherheit|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Ausführlich|SecurityToken (Typ "%1" und ID "%2") erfolgreich überprüft.|Sicherheit|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Fehler|Fehler bei der Überprüfung des SecurityToken (Typ "%1" und ID "%2"). %3|Sicherheit|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Ausführlich|Ausstellernamen %1 erfolgreich von der tokenId: %2 abgerufen.|Sicherheit|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Fehler|Fehler beim Abrufen des Ausstellernamens von der tokenId: %1.|Sicherheit|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Ausführlich|Verbundnachrichtenverarbeitung gestartet.|Sicherheit|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Ausführlich|Verbundnachrichtenverarbeitung erfolgreich.|Sicherheit|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Ausführlich|Erstellung der Verbundnachricht aus der Formularbereitstellung gestartet.|Sicherheit|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Ausführlich|Erstellung der Verbundnachricht aus der Formularbereitstellung erfolgreich.|Sicherheit|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Ausführlich|Lesen des Sitzungstokens aus dem Sitzungscookie gestartet.|Sicherheit|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Ausführlich|Lesen des Sitzungstokens aus dem Sitzungscookie erfolgreich.|Sicherheit|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Ausführlich|Prinzipaleinstellung aus dem Sitzungstoken gestartet.|Sicherheit|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Ausführlich|Prinzipaleinstellung aus dem Sitzungstoken erfolgreich.|Sicherheit|  
|[57393 - AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Information|AppDomain wird entladen. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infrastruktur|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Information|Eine Ausnahme wird verarbeitet.|Infrastruktur|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Fehler|Unerwarteter Fehler. Anwendungen sollten diesen Fehler nicht behandeln. Zu Diagnosezwecken ist diesem Fehler die folgende englischsprachige Meldung zugewiesen: %1.|Infrastruktur|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Warnung|Eine Ausnahme wird ausgelöst. Quelle: %1.|Infrastruktur|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Kritisch|Ausnahmefehler.|Infrastruktur|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Kritisch|Wurde in EventLog geschrieben.|Infrastruktur|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Fehler|Wurde in EventLog geschrieben.|Infrastruktur|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Information|Wurde in EventLog geschrieben.|Infrastruktur|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Ausführlich|Wurde in EventLog geschrieben.|Infrastruktur|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Warnung|Wurde in EventLog geschrieben.|Infrastruktur|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Warnung|Eine Ausnahme wird verarbeitet.|Infrastruktur|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Information|Die URL '%1' hostet ein XAML-Dokument mit Stammelementtyp '%2'. Der HTTP-Handlertyp '%3' wurde zum Verarbeiten aller Anforderungen an diese URL ausgewählt.|WebHost|
