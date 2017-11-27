---
title: Authenticode (Referenz zur nicht verwalteten API)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e90a13ebf46f1891061c78435b7ba47d68de001d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="a8d05-102">Authenticode (Referenz zur nicht verwalteten API)</span><span class="sxs-lookup"><span data-stu-id="a8d05-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="a8d05-103">Unterstützt das Authenticode-Modul zu XrML-Lizenzerstellung und Verifizierung.</span><span class="sxs-lookup"><span data-stu-id="a8d05-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8d05-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="a8d05-104">In This Section</span></span>  
 [<span data-ttu-id="a8d05-105">_AxlGetIssuerPublicKeyHash-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8d05-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="a8d05-106">Ruft den SHA-1-Hash des öffentlichen Schlüssels ab, der dem privaten Schlüssel zugeordnet wurde, der beim Signieren des festgelegten Zertifikats zur Verwendung kam.</span><span class="sxs-lookup"><span data-stu-id="a8d05-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="a8d05-107">_AxlPublicKeyBlobToPublicKeyToken-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8d05-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="a8d05-108">Berechnet den starken Namen des öffentlichen Schlüsseltokens aus einem CSP PUBLICKEYBLOB-Format.</span><span class="sxs-lookup"><span data-stu-id="a8d05-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="a8d05-109">_AxlRSAKeyValueToPublicKeyToken-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8d05-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="a8d05-110">Konvertiert ein Modulo und einen Exponenten in ein Token für den öffentlichen Schlüssel für einen starken Namen.</span><span class="sxs-lookup"><span data-stu-id="a8d05-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="a8d05-111">CertFreeAuthenticodeSignerInfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8d05-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="a8d05-112">Macht Ressourcen frei, die der AXL_AUTHENTICODE_SIGNER_INFO-Struktur zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="a8d05-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="a8d05-113">CertFreeAuthenticodeTimestamperInfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8d05-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="a8d05-114">Macht Ressourcen frei, die der AXL_AUTHENTICODE_TIMESTAMPER_INFO-Struktur zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="a8d05-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="a8d05-115">CertTimestampAuthenticodeLicense-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8d05-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="a8d05-116">Fügt einer von CertCreateAuthenticodeLicense erstellten Authenticode XrML-Lizenz einen Zeitstempel hinzu.</span><span class="sxs-lookup"><span data-stu-id="a8d05-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="a8d05-117">CertVerifyAuthenticodeLicense-Funktion</span><span class="sxs-lookup"><span data-stu-id="a8d05-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="a8d05-118">Überprüft die Gültigkeit einer Authenticode XrML-Lizenz.</span><span class="sxs-lookup"><span data-stu-id="a8d05-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="a8d05-119">AXL_AUTHENTICODE_SIGNER_INFO-Struktur</span><span class="sxs-lookup"><span data-stu-id="a8d05-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="a8d05-120">Definiert Informationen zum Signaturgeber für Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a8d05-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="a8d05-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO-Struktur</span><span class="sxs-lookup"><span data-stu-id="a8d05-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="a8d05-122">Definiert Informationen zum Ersteller des Zeitstempels für Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a8d05-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d05-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a8d05-123">See Also</span></span>  
 [<span data-ttu-id="a8d05-124">Referenz zur nicht verwalteten API</span><span class="sxs-lookup"><span data-stu-id="a8d05-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)