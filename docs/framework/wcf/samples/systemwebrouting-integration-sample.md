---
title: SystemWebRouting-Integrationsbeispiel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1718ea9c6ea1e029b66955e88fd54e20db1a3527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting-Integrationsbeispiel
In diesem Beispiel wird die Integration der Hostebene in die Klassen im <xref:System.Web.Routing>-Namespace veranschaulicht. Mit den Klassen im <xref:System.Web.Routing>-Namespace können Anwendungen URLs verwenden, die einer physischen Ressource nicht direkt entsprechen. Webrouting ermöglicht es dem Entwickler, virtuelle Adressen für HTTP zu erstellen, die danach erneut tatsächlichen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Diensten zugeordnet werden. Dies ist nützlich, wenn ein WCF-Dienst gehostet werden muss, ohne dass eine physische Datei oder Ressource erforderlich ist, oder wenn auf Dienste mit URLs zugegriffen werden muss, die keine Dateierweiterung wie .html oder .aspx enthalten. In diesem Beispiel wird veranschaulicht, wie mithilfe der <xref:System.Web.Routing.RouteTable>-Klasse virtuelle URIs erstellt werden können, die in global.asax definierten, ausgeführten Diensten zugeordnet werden. Für dieses Beispiel gibt es zwei mit WCF erstellte RSS-Feeds: ein `movies`-Feed und ein `channels`-Feed. Die URLs zur Aktivierung der Dienste enthalten keine Erweiterung und registriert sind, der `Application_Start` Methode der `Global` abgeleitete Klasse die <xref:System.Web.HttpApplication.Application_Start> Klasse.  
  
> [!NOTE]
>  Die Klassen im <xref:System.Web.Routing>-Namespace können nur für Dienste verwendet werden, die über HTTP gehostet werden.  
  
> [!NOTE]
>  Dieses Beispiel funktioniert nur in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], da [!INCLUDE[iis60](../../../../includes/iis60-md.md)] eine andere Methode für die Unterstützung von URLs ohne Erweiterung verwendet.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>So verwenden Sie dieses Beispiel  
  
1.  Öffnen Sie die Datei WebRoutingIntegration.sln in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Drücken Sie F5, um die Projektmappe auszuführen und den Webentwicklungsserver zu starten.  
  
     Eine Verzeichnisliste für das Beispiel wird angezeigt. Beachten Sie, dass es keine Dateien mit der Dateierweiterung SVC gibt.  
  
3.  Fügen Sie der URL in der Adressleiste `movies` hinzu, sodass die Adresse nun http://localhost:[Port]/movies lautet, und drücken Sie die EINGABETASTE.  
  
     Der Filmfeed (movies) wird im Browser angezeigt.  
  
4.  Fügen Sie der URL in der Adressleiste `channels` hinzu, sodass die Adresse nun http://localhost:[Port]/channels lautet, und drücken Sie die EINGABETASTE.  
  
     Der Channelfeed wird im Browser angezeigt.  
  
5.  Schließen Sie den Webbrowser, indem Sie ALT+F4 drücken.  
  
     Wenn der Entwicklungsserver nicht beendet wurde, mit der rechten Maustaste das Symbol im Infobereich, und wählen Sie **beenden**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>So verwenden Sie dieses Beispiel, wenn es in IIS gehostet wird  
  
1.  Öffnen Sie die Datei WebRoutingIntegration.sln in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Erstellen Sie das Projekt, indem Sie STRG+UMSCHALT+B drücken.  
  
3.  Erstellen Sie eine Webanwendung im Internetinformationsdienste-Manager.  
  
    1.  Mit der rechten Maustaste im IIS-Manager, klicken Sie auf die **Default Web Site** , und wählen Sie **Hinzufügen einer Anwendung**.  
  
    2.  Für die **Alias**, geben Sie in `WebRoutingIntegration`.  
  
    3.  Für die **physischen Pfad**, wählen Sie den Dienstordner im Projekt.  
  
    4.  Press **OK**.  
  
4.  Starten Sie die Anwendung, indem Sie die Web-Anwendung mit der rechten Maustaste und auswählen **-Anwendung verwalten** und dann **Durchsuchen**.  
  
5.  Fügen Sie der URL in der Adressleiste `movies` hinzu, sodass die Adresse nun http://localhost:[Port]/movies lautet, und drücken Sie die EINGABETASTE.  
  
     Der Filmfeed (movies) wird im Browser angezeigt.  
  
6.  Fügen Sie der URL in der Adressleiste `channels` hinzu, sodass die Adresse nun http://localhost:[Port]/channels lautet, und drücken Sie die EINGABETASTE.  
  
     Der Channelfeed wird im Browser angezeigt.  
  
7.  Schließen Sie den Webbrowser, indem Sie ALT+F4 drücken.  
  
 In diesem Beispiel wird gezeigt, dass die Hostebene mit den Klassen im <xref:System.Web.Routing>-Namespace eingesetzt werden kann, um die Anforderungen von Diensten zu routen, die über HTTP gehostet werden.  
  
> [!NOTE]
>  Aktualisieren Sie die Version des Standardanwendungspools auf [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], wenn sie auf Version 2 festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [AppFabric-Hosting und Persistenzbeispiele](http://go.microsoft.com/fwlink/?LinkId=193961)
