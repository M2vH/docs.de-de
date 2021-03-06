---
title: "Permanente Verzögerung in XAMLX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff5eb09acea16ac125fac5d9e3ed875c9095e1c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="durable-delay-in-xamlx"></a>Permanente Verzögerung in XAMLX
In diesem Beispiel wird veranschaulicht, wie eine permanente Verzögerung verwendet wird, eine Verzögerung, die den Workflow während der Verzögerung auf einem permanenten Gerät beibehält.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Diskussion  
 Der Beispielworkflow enthält zwei Meldungen zu einer lokalen Datei, die durch eine Verzögerung getrennt sind. Wenn die Verzögerung ausgelöst wird, wird der Workflow entladen und verbleibt 5 Sekunden im Workflowinstanzspeicher, bevor er erneut in den Speicher geladen wird.  
  
 Die XAMLX-Datei ist ein Workflowdienst, der in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] gehostet wird. [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] verwendet Cassini, das einen Workflowdiensthost zum Hosten des Workflows nutzt.  
  
 Neben dem Hosten des Workflows verwaltet der Workflowdiensthost die Workflowinstanzen durch Laden und Entladen. Um eine Instanz der [!INCLUDE[wf](../../../../includes/wf-md.md)]-Definition (auf dem Workflowdiensthost) zu starten, legen Sie einen Client fest, der eine Nachricht an die <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow sendet. Die <xref:System.ServiceModel.Activities.Receive>-Eigenschaft von <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> ist auf `true` festgelegt, sodass eine neue Instanz des Workflows erstellt werden kann, sobald eine Nachricht empfangen wird.  
  
 Während der Initialisierung wird der Konfigurationsdatei, die den Workflowdiensthost angibt, unter dem eine Instanz in den Persistenzspeicher (Datenbank) entladen werden soll, ein Verhalten zum Entladen von Instanzen hinzugefügt. Für dieses Beispiel wird die Instanz entladen, unmittelbar nachdem der Workflow in den Leerlauf eintritt (wenn die Verzögerung ausgelöst wird).  
  
#### <a name="to-use-this-sample"></a>So verwenden Sie dieses Beispiel  
  
1.  Öffnen Sie eine [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]-Eingabeaufforderung.  
  
2.  Navigieren Sie zum Ordner "DurableDelayXamlx\CS".  
  
3.  Führen Sie Setup.cmd aus.  
  
4.  Führen Sie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] als Administrator aus.  
  
5.  Öffnen Sie die Projektmappendatei "DurableDelayXamlx.sln".  
  
6.  In **Projektmappen-Explorer**mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Eigenschaften**.  
  
7.  Wählen Sie **mehrere Startprojekte** , und legen Sie beide Projekte auf **starten**.  
  
8.  Drücken Sie STRG+UMSCHALT+B, um die Projektmappe zu erstellen.  
  
9. Drücken Sie STRG+F5, um die Projektmappe auszuführen.  
  
#### <a name="to-uninstall-this-sample"></a>So deinstallieren Sie das Beispiel  
  
1.  Öffnen Sie eine [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]-Eingabeaufforderung.  
  
2.  Navigieren Sie zum Ordner "DurableDelayXamlx\CS".  
  
3.  Führen Sie die Datei "Cleanup.cmd" aus.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
