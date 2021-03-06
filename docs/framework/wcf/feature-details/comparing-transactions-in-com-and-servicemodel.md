---
title: Vergleichen von Transaktionen in COM+ und ServiceModel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Vergleichen von Transaktionen in COM+ und ServiceModel
In diesem Thema wird das Simulieren des Verhaltens eines COM+-Transaktionsdienstes mithilfe der [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]-Attribute, die der <xref:System.ServiceModel>-Namespace bereitstellt, beschrieben.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulieren von COM+ mit ServiceModel-Attributen  
 In der folgenden Tabelle wird die <xref:System.EnterpriseServices.TransactionOption>-Enumeration, die zum Erstellen einer `EnterpriseServices`-Transaktion verwendet wird, und die Beziehung zu den [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Attributen, die der <xref:System.ServiceModel>-Namespace bereitstellt, verglichen.  
  
|COM+-Attribut|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Attribute|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|Für <xref:System.ServiceModel.TransactionFlowAttribute> ist <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> festgelegt.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ist `true`.<br /><br /> Das `TransactionFlow`-Attribut im Bindungselement ist `false`.|  
|Erforderlich|Für <xref:System.ServiceModel.TransactionFlowAttribute> ist <xref:System.ServiceModel.TransactionFlowOption.Allowed> festgelegt.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ist `true`.<br /><br /> Das `TransactionFlow`-Attribut im Bindungselement ist `true`.|  
|Unterstützt|Es gibt keine direkte Entsprechung. Übernehmen Sie stattdessen im Allgemeinen das für `Required` angegebene Verhalten.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ist `false`.<br /><br /> Das `TransactionFlow`-Attribut im Bindungselement ist `false`.|  
|Deaktiviert|Es gibt keine direkte Entsprechung. Übernehmen Sie stattdessen im Allgemeinen das für `NotSupported` angegebene Verhalten.|
