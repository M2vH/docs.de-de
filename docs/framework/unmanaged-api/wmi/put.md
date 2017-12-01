---
title: Put-Funktion (Referenz zur nicht verwalteten API)
description: Die Put-Funktion weist einen neuen Wert an eine benannte Eigenschaft an.
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c4ad979a3a662618ab62b52d63bda3dbb1e71b9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="put-function"></a><span data-ttu-id="d7d43-103">Put-Funktion</span><span class="sxs-lookup"><span data-stu-id="d7d43-103">Put function</span></span>
<span data-ttu-id="d7d43-104">Legt eine benannte Eigenschaft auf einen neuen Wert fest.</span><span class="sxs-lookup"><span data-stu-id="d7d43-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d7d43-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7d43-105">Syntax</span></span>  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a><span data-ttu-id="d7d43-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="d7d43-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d7d43-107">[in] Dieser Parameter wird nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="d7d43-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d7d43-108">[in] Ein Zeiger auf ein [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) Instanz.</span><span class="sxs-lookup"><span data-stu-id="d7d43-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="d7d43-109">[in] Der Name der Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d7d43-109">[in] The name of the property.</span></span> <span data-ttu-id="d7d43-110">Dieser Parameter darf nicht sein `null`.</span><span class="sxs-lookup"><span data-stu-id="d7d43-110">This parameter cannot be `null`.</span></span>

`lFlags`  
<span data-ttu-id="d7d43-111">[in] Reserviert.</span><span class="sxs-lookup"><span data-stu-id="d7d43-111">[in] Reserved.</span></span> <span data-ttu-id="d7d43-112">Dieser Parameter muss 0 sein.</span><span class="sxs-lookup"><span data-stu-id="d7d43-112">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="d7d43-113">[in] Ein Zeiger auf eine gültige `VARIANT` , wird der neue Eigenschaftswert.</span><span class="sxs-lookup"><span data-stu-id="d7d43-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="d7d43-114">Wenn `pVal` ist `null` oder verweist auf eine `VARIANT` des Typs `VT_NULL`, die Eigenschaft wird festgelegt, um `null`.</span><span class="sxs-lookup"><span data-stu-id="d7d43-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span> 

`vtType`  
<span data-ttu-id="d7d43-115">[in] Der Typ des `VARIANT` verweist `pVal`.</span><span class="sxs-lookup"><span data-stu-id="d7d43-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="d7d43-116">Finden Sie unter der ["Hinweise"](#remarks) Abschnitt, um weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="d7d43-116">See the [Remarks](#remarks) section for more information.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="d7d43-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d7d43-117">Return value</span></span>

<span data-ttu-id="d7d43-118">Die folgenden Werte, die von dieser Funktion zurückgegebenen werden definiert, der *WbemCli.h* Header-Datei, oder Sie können diese definieren als Konstanten in Ihrem Code:</span><span class="sxs-lookup"><span data-stu-id="d7d43-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d7d43-119">Konstante</span><span class="sxs-lookup"><span data-stu-id="d7d43-119">Constant</span></span>  |<span data-ttu-id="d7d43-120">Wert</span><span class="sxs-lookup"><span data-stu-id="d7d43-120">Value</span></span>  |<span data-ttu-id="d7d43-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7d43-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="d7d43-122">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="d7d43-122">0x80041001</span></span> | <span data-ttu-id="d7d43-123">Ein allgemeiner Fehler ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="d7d43-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d7d43-124">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="d7d43-124">0x80041008</span></span> | <span data-ttu-id="d7d43-125">Einen oder mehrere Parameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="d7d43-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="d7d43-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="d7d43-126">0x8004102a</span></span> | <span data-ttu-id="d7d43-127">Der Eigenschaftentyp wird nicht erkannt.</span><span class="sxs-lookup"><span data-stu-id="d7d43-127">The property type is not recognized.</span></span> <span data-ttu-id="d7d43-128">Dieser Wert wird zurückgegeben, wenn Klasseninstanzen zu erstellen, wenn die Klasse bereits besteht.</span><span class="sxs-lookup"><span data-stu-id="d7d43-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d7d43-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d7d43-129">0x80041006</span></span> | <span data-ttu-id="d7d43-130">Es ist nicht genügend Arbeitsspeicher verfügbar, um den Vorgang abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="d7d43-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="d7d43-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="d7d43-131">0x80041005</span></span> | <span data-ttu-id="d7d43-132">Für Instanzen: Gibt an, dass `pVal` verweist auf eine `VARIANT` mit einem falschen Typ für die Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d7d43-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="d7d43-133">Für Klassendefinitionen: die Eigenschaft bereits vorhanden ist, in der übergeordneten Klasse und der neue COM-Typ unterscheidet sich von der alten COM-Typ.</span><span class="sxs-lookup"><span data-stu-id="d7d43-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d7d43-134">0</span><span class="sxs-lookup"><span data-stu-id="d7d43-134">0</span></span> | <span data-ttu-id="d7d43-135">Der Funktionsaufruf war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="d7d43-135">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d7d43-136">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d7d43-136">Remarks</span></span>

<span data-ttu-id="d7d43-137">Diese Funktion dient als Wrapper für einen Aufruf der [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) Methode.</span><span class="sxs-lookup"><span data-stu-id="d7d43-137">This function wraps a call to the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="d7d43-138">Diese Funktion überschreibt immer den aktuellen Eigenschaftenwert durch ein neues.</span><span class="sxs-lookup"><span data-stu-id="d7d43-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="d7d43-139">Wenn die [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) verweist auf eine Klassendefinition `Put` erstellt oder aktualisiert den Wert der Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d7d43-139">If the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="d7d43-140">Wenn [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) verweist auf eine CIM-Instanz `Put` aktualisiert den Wert der Eigenschaft nur; `Put` einen Eigenschaftswert kann nicht erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="d7d43-140">When [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="d7d43-141">Die `__CLASS` Systemeigenschaft überschreibbar nur während der klassenerstellung, wenn er nicht leer sein kann.</span><span class="sxs-lookup"><span data-stu-id="d7d43-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="d7d43-142">Alle anderen Systemeigenschaften sind schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="d7d43-142">All other system properties are read-only.</span></span>

<span data-ttu-id="d7d43-143">Ein Benutzer kann keine Eigenschaften mit Namen erstellen, die mit einem Unterstrich ("_") beginnen oder enden.</span><span class="sxs-lookup"><span data-stu-id="d7d43-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="d7d43-144">Dies ist für Systemklassen und Eigenschaften reserviert.</span><span class="sxs-lookup"><span data-stu-id="d7d43-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="d7d43-145">Wenn die Eigenschaft festgelegt wird, indem Sie die `Put` Funktion, die in der übergeordneten Klasse vorhanden ist, wird der Standardwert der Eigenschaft wird geändert, es sei denn, der Eigenschaftstyp nicht den Typ der übergeordneten Klasse übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="d7d43-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="d7d43-146">Wenn die Eigenschaft ist nicht vorhanden, und es kein Typenkonflikt ist, ist die Eigenschaft Ceated.</span><span class="sxs-lookup"><span data-stu-id="d7d43-146">If the property does not exist and it is not a type mismatch, the property is ceated.</span></span>

<span data-ttu-id="d7d43-147">Verwenden der `vtType` Parameters nur beim Erstellen von neuer Eigenschaften in einer CIM-Klassendefinition und `pVal` ist `null` oder verweist auf eine `VARIANT` vom Typ `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="d7d43-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="d7d43-148">In diesem Fall die `vType` Parameter gibt den CIM-Typ der Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d7d43-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="d7d43-149">In allen anderen Fällen `vtType` muss 0 sein.</span><span class="sxs-lookup"><span data-stu-id="d7d43-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="d7d43-150">`vtType`muss auch 0 sein, wenn das zugrunde liegende Objekt eine Instanz ist (auch wenn `Val` ist `null`), da der Typ der Eigenschaft unveränderlich ist und kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="d7d43-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>   

## <a name="example"></a><span data-ttu-id="d7d43-151">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d7d43-151">Example</span></span>

<span data-ttu-id="d7d43-152">Ein Beispiel finden Sie die [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) Methode.</span><span class="sxs-lookup"><span data-stu-id="d7d43-152">For an example, see the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7d43-153">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d7d43-153">Requirements</span></span>  
 <span data-ttu-id="d7d43-154">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7d43-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7d43-155">**Header:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d7d43-155">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d7d43-156">**.NET Framework-Versionen:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d7d43-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d43-157">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d7d43-157">See also</span></span>  
[<span data-ttu-id="d7d43-158">WMI und Leistungsindikatoren (Referenz zur nicht verwalteten API)</span><span class="sxs-lookup"><span data-stu-id="d7d43-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)