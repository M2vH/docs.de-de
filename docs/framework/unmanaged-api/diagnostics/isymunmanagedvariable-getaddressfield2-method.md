---
title: ISymUnmanagedVariable::GetAddressField2-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d3e9124cb800416c44596d7b6f21a21c416e0e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="c9f68-102">ISymUnmanagedVariable::GetAddressField2-Methode</span><span class="sxs-lookup"><span data-stu-id="c9f68-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="c9f68-103">Ruft das zweite Adressfeld für diese Variable ab.</span><span class="sxs-lookup"><span data-stu-id="c9f68-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="c9f68-104">Seiner Bedeutung hängt von der Art der Adresse ab.</span><span class="sxs-lookup"><span data-stu-id="c9f68-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f68-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9f68-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9f68-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="c9f68-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c9f68-107">[out] Ein Zeiger auf eine `ULONG32` , die Feld für die zweite Adresse empfängt.</span><span class="sxs-lookup"><span data-stu-id="c9f68-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9f68-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c9f68-108">Return Value</span></span>  
 <span data-ttu-id="c9f68-109">S_OK, wenn die Methode erfolgreich ist; andernfalls E_FAIL oder einen anderen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="c9f68-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f68-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c9f68-110">Requirements</span></span>  
 <span data-ttu-id="c9f68-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9f68-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f68-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c9f68-112">See Also</span></span>  
 [<span data-ttu-id="c9f68-113">ISymUnmanagedVariable-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="c9f68-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="c9f68-114">GetAddressField1-Methode</span><span class="sxs-lookup"><span data-stu-id="c9f68-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="c9f68-115">GetAddressField3-Methode</span><span class="sxs-lookup"><span data-stu-id="c9f68-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="c9f68-116">GetAddressKind-Methode</span><span class="sxs-lookup"><span data-stu-id="c9f68-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)