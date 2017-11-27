---
title: CorGCReferenceType-Enumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGCReferenceType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorGCReferenceType
helpviewer_keywords: CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45ca1e9c6123a4b22a1645d151e49a0dd65addbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="c3b35-102">CorGCReferenceType-Enumeration</span><span class="sxs-lookup"><span data-stu-id="c3b35-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="c3b35-103">Identifiziert die Quelle eines Objekts, das speicherbereinigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c3b35-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b35-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3b35-104">Syntax</span></span>  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="c3b35-105">Member</span><span class="sxs-lookup"><span data-stu-id="c3b35-105">Members</span></span>  
  
|<span data-ttu-id="c3b35-106">Membername</span><span class="sxs-lookup"><span data-stu-id="c3b35-106">Member name</span></span>|<span data-ttu-id="c3b35-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c3b35-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="c3b35-108">Ein Handle für einen starken Verweis von der Objekthandletabelle.</span><span class="sxs-lookup"><span data-stu-id="c3b35-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="c3b35-109">Ein Handle auf ein angehefteter starker Verweis von der objekthandletabelle.</span><span class="sxs-lookup"><span data-stu-id="c3b35-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="c3b35-110">Ein Handle auf einen schwachen Verweis von der objekthandletabelle.</span><span class="sxs-lookup"><span data-stu-id="c3b35-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="c3b35-111">Ein Handle zu einem schwachen Verweis gezähltes Objekt von der objekthandletabelle.</span><span class="sxs-lookup"><span data-stu-id="c3b35-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="c3b35-112">Ein Handle auf ein Objekt mit verweiszählung von der objekthandletabelle.</span><span class="sxs-lookup"><span data-stu-id="c3b35-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="c3b35-113">Ein Handle für ein abhängiges Objekt von der objekthandletabelle werden soll.</span><span class="sxs-lookup"><span data-stu-id="c3b35-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="c3b35-114">Ein asynchrones angeheftetes Objekt von der Objekthandletabelle.</span><span class="sxs-lookup"><span data-stu-id="c3b35-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="c3b35-115">Ein starkes Handle, das eine ungefähre Größe des kollektiven Abschlusses aller Objekte und Objektstämme zur Garbage Collection-Zeit enthält.</span><span class="sxs-lookup"><span data-stu-id="c3b35-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="c3b35-116">Ein Verweis vom verwalteten Stapel.</span><span class="sxs-lookup"><span data-stu-id="c3b35-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="c3b35-117">Ein Verweis von der Finalizerwarteschlange.</span><span class="sxs-lookup"><span data-stu-id="c3b35-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="c3b35-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="c3b35-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="c3b35-119">Geben Sie nur starke Verweise aus der Handletabelle zurück.</span><span class="sxs-lookup"><span data-stu-id="c3b35-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="c3b35-120">Dieser Wert wird verwendet, durch die [icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) nur Methode.</span><span class="sxs-lookup"><span data-stu-id="c3b35-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="c3b35-121">Geben Sie nur schwache Verweise aus der Handletabelle zurück.</span><span class="sxs-lookup"><span data-stu-id="c3b35-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="c3b35-122">Dieser Wert wird verwendet, durch die [icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) nur Methode.</span><span class="sxs-lookup"><span data-stu-id="c3b35-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="c3b35-123">Geben Sie alle Verweise aus der Handletabelle zurück.</span><span class="sxs-lookup"><span data-stu-id="c3b35-123">Return all references from the handle table.</span></span> <span data-ttu-id="c3b35-124">Dieser Wert wird verwendet, durch die [icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) nur Methode.</span><span class="sxs-lookup"><span data-stu-id="c3b35-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3b35-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c3b35-125">Remarks</span></span>  
 <span data-ttu-id="c3b35-126">Die `CorGCReferenceType` Enumeration wird wie folgt verwendet:</span><span class="sxs-lookup"><span data-stu-id="c3b35-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="c3b35-127">Als Wert des der `type` Feld der [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) -Struktur, es gibt die Datenquelle ein Verweis oder ein Handle.</span><span class="sxs-lookup"><span data-stu-id="c3b35-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="c3b35-128">Als die `types` Argument an die [icordebugprocess5:: Enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) -Methode, gibt die Arten von Handles in der Enumeration einschließen an.</span><span class="sxs-lookup"><span data-stu-id="c3b35-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b35-129">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c3b35-129">Requirements</span></span>  
 <span data-ttu-id="c3b35-130">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b35-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b35-131">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3b35-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3b35-132">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3b35-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3b35-133">**.NET Framework-Versionen:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b35-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b35-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c3b35-134">See Also</span></span>  
 [<span data-ttu-id="c3b35-135">Debuggen von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c3b35-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)