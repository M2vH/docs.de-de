---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f920ceb802231112ef1b855fd0a78d3a0e6ca4c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a>ICLRErrorReportingManager::GetBucketParametersForCurrentException-Methode
Ruft die Dr. Watson-Bucket für die aktuelle Ausnahme im aufrufenden Thread ab.  
  
 Ein *Bucket* ist eine Auflistung von Fehlerdaten, die auf den gleichen Codefehler beziehen. *Watson* bezieht sich auf eine Reihe von Technologien zum Sammeln und Analysieren von Daten, die eine Ausnahme zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pParams`  
 [out] Ein Zeiger auf eine [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) Struktur, die Fehlerdaten für die Ausnahme enthält.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** MSCorEE.h  
  
 **Bibliothek:** als Ressource in MSCorEE.dll enthalten  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ICLRErrorReportingManager-Schnittstelle](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
