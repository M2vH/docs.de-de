---
title: '&lt;workflowRuntime&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2860c7ddd5f3d2f0ce2749c36afebcf9abfeac3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowruntimegt"></a>&lt;workflowRuntime&gt;
Legt Einstellungen für eine Instanz von <xref:System.Workflow.Runtime.WorkflowRuntime> zum Hosten workflowbasierter [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]-Dienste fest.  
  
 \<System. ServiceModel >  
\<Verhalten >  
\<ServiceBehaviors >  
\<Verhalten >  
\<WorkflowRuntime >  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|cachedInstanceExpiration|Ein optionaler <xref:System.TimeSpan>-Wert, der die maximale Dauer angibt, die eine Workflowinstanz im Arbeitsspeicher im Leerlaufzustand verbleiben kann, bevor ihre Entladung oder ihr Abbruch erzwungen wird. Wenn die Workflow-Laufzeit über `PersistenceService` verfügt, der unloadOnIdle ausführt, wird dieses Attribut ignoriert.|  
|enablePerformanceCounters|Ein optionaler boolescher Wert, der angibt, ob Leistungsindikatoren aktiviert sind. Leistungsindikatoren liefern Informationen zu verschiedenen workflowbezogenen Statistiken, verursachen jedoch eine Leistungseinbuße, wenn das Workflow-Laufzeitmodul gestartet wird und Workflowinstanzen ausgeführt werden. Der Standardwert ist `true`.|  
|Name|Eine Zeichenfolge, die den Namen der Workflow-Laufzeitengine enthält. Der Name wird in der Ausgabe verwendet, um diese Laufzeit von anderen Laufzeiten zu unterscheiden, die unter Umständen im System ausgeführt werden, beispielsweise in Leistungsindikatoren.<br /><br /> Der Standardwert ist eine leere Zeichenfolge.|  
|validateOnCreate|Ein optionaler boolescher Wert, der angibt, ob eine Überprüfung der Workflowdefinition auftritt, wenn WorkflowServiceHost geöffnet wird.  Wenn dieses Attribut auf `true` festgelegt ist, wird die Workflowüberprüfung jedes Mal ausgeführt, wenn `WorkflowServiceHost.Open` aufgerufen wird. Wenn Überprüfungsfehler gefunden werden, wird ein <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException>-Fehler ausgelöst.<br /><br /> Wenn diese Eigenschaft auf `false` festgelegt wird, findet keine Workflow-Definitionsüberprüfung statt.<br /><br /> Der Standardwert für diese Eigenschaft ist `true`.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|commonParameters|Eine Auflistung der allgemeinen, von Diensten verwendeten Parameter. Diese Auflistung schließt in der Regel die Datenbankverbindungszeichenfolge ein, die ggf. von permanenten Diensten gemeinsam genutzt wird.|  
|Dienste|Eine Auflistung von Diensten, die dem <xref:System.Workflow.Runtime.WorkflowRuntime>-Modul hinzugefügt werden. Die Elemente sind vom Typ <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Die in der Auflistung angegebenen Dienste werden vom Workflow-Laufzeitmodul initialisiert und den Diensten hinzugefügt, wenn der entsprechende <xref:System.Workflow.Runtime.WorkflowRuntime>-Konstruktor aufgerufen wird. Aus diesem Grund müssen die in der Auflistung angegebenen Dienste bestimmte Regeln bezüglich der Signaturen ihrer Konstruktoren erfüllen. Weitere Informationen finden Sie unter <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<Verhalten >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Gibt ein Verhaltenselement an.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Verwendung einer Konfigurationsdatei zum Steuern des Verhaltens von einer <xref:System.Workflow.Runtime.WorkflowRuntime> Objekt einer Windows Workflow Foundation-Host-Anwendung finden Sie unter [Workflow-Konfigurationsdateien](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
## <a name="example"></a>Beispiel  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <commonParameters>  
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
            <add name="EnableRetries" value="True" />  
         </commonParameters>  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [Workflow-Konfigurationsdateien](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
