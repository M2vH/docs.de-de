---
title: ICorDebugFunction::GetNativeCode-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15383198da740f536061f1568fb06f042117b19c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode-Methode
Ruft den systemeigenen Code für die Funktion, die von dieser Instanz ICorDebugFunction dargestellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppCode`  
 [out] Ein Zeiger auf die ICorDebugCode-Instanz, die den systemeigenen Code für diese Funktion oder Null, darstellt, wenn diese Funktion Microsoft intermediate Language (MSIL)-Code, die nicht mit just ist-in-Time (JIT) kompiliert wurde.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Funktion, die von diesem dargestellt wird `ICorDebugFunction` Instanz wurde mit JIT kompiliert wurden mehr als einmal als im Fall von generischen Typen `GetNativeCode` eine zufällige systemeigenem Code zurück.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
