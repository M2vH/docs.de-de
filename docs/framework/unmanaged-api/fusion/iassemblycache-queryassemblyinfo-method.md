---
title: IAssemblyCache::QueryAssemblyInfo-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.QueryAssemblyInfo
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66e09f805b120239eef764b8cd61835e713e236c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycachequeryassemblyinfo-method"></a>IAssemblyCache::QueryAssemblyInfo-Methode
Ruft die angeforderten Daten über die angegebene Assembly ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFlags`  
 [in] Flags, die in Fusion.idl definiert sind. Die folgenden Werte werden unterstützt:  
  
-   QUERYASMINFO_FLAG_VALIDATE (0 X 00000001)  
  
-   QUERYASMINFO_FLAG_GETSIZE (0 X 00000002)  
  
 `pszAssemblyName`  
 [in] Der Name der Assembly, die für die Daten abgerufen werden sollen.  
  
 `pAsmInfo`  
 [in, out] Ein [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) -Struktur, die Daten über die Assembly enthält.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Fusion.h  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [IAssemblyCache-Schnittstelle](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
