---
title: "Vorgehensweise: Konfigurieren eines WCF-Clients für die Zusammenarbeit mit WSE3.0-Diensten"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 214e0de13ba362bf4f101a665e943a424c56363c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Vorgehensweise: Konfigurieren eines WCF-Clients für die Zusammenarbeit mit WSE3.0-Diensten
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]-Clients sind auf niedriger Ebene mit Diensten von Web Services Enhancements 3.0 für Microsoft .NET (WSE) kompatibel, wenn [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Clients für die Verwendung der Version der WS-Addressing-Spezifikation vom August 2004 konfiguriert sind.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>So konfigurieren Sie einen WCF-Client für die Zusammenarbeit mit einem WSE3.0-Webdienst  
  
1.  Führen Sie die [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zum Erstellen einer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client für den WSE 3.0-Webdienst.  
  
     Für einen WSE-Webdienst wird eine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Clientklasse erstellt.  
  
     Ausführliche Informationen zum Erstellen einer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client finden Sie unter der [Vorgehensweise: Erstellen eines Clients](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Erstellen Sie eine Klasse, die eine Bindung darstellt, die mit WSE 3.0-Webdiensten kommunizieren kann.  
  
     Die folgende Klasse ist Teil der [Zusammenarbeit mit WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41) Beispiel.  
  
    1.  Erstellen Sie eine von der <xref:System.ServiceModel.Channels.Binding>-Klasse abgeleitete Klasse.  
  
         Der folgende Code erstellt eine Klasse mit dem Namen `WseHttpBinding`, die von der <xref:System.ServiceModel.Channels.Binding>-Klasse abgeleitet wird.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Fügen Sie der Klasse Eigenschaften hinzu, die die sofort verwendbare WSE-Assertion festlegen. Hierzu gehört, ob abgeleitete Schlüssel erforderlich sind, ob Sicherheitssitzungen zum Einsatz kommen, ob Signaturbestätigungen erforderlich sind sowie die Einstellungen für den Nachrichtenschutz.  
  
         Das folgende Codebeispiel definiert `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` Eigenschaften, die angeben, die sofort verwendbare WSE-Assertion, gibt an, ob abgeleitete Schlüssel erforderlich sind, gibt an, ob sicherheitssitzungen zum Einsatz kommen, ob signaturbestätigungen erforderlich sind und Einstellungen für den Nachrichtenschutz, bzw.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Überschreiben Sie die <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>-Methode, um die Bindungseigenschaften einzurichten.  
  
         Das folgende Codebeispiel legt die Einstellungen für Transport, Nachrichtencodierung und Nachrichtenschutz fest, indem die Werte für `SecurityAssertion` und die `MessageProtectionOrder`-Eigenschaften abgerufen werden.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  Fügen Sie im Clientanwendungscode Code hinzu, um die Bindungseigenschaften festzulegen.  
  
     Das folgende Codebeispiel legt fest, dass der [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Client Nachrichtenschutz und -authentifizierung, wie von der sofort verwendbaren WSE 3.0-`AnonymousForCertificate`-Sicherheitsassertion definiert, verwenden muss. Darüber hinaus sind Sicherheitssitzungen und abgeleitete Schlüssel erforderlich.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel definiert eine benutzerdefinierte Bindung, die Eigenschaften offenlegt, die mit den Eigenschaften der sofort verwendbaren WSE 3.0-Sicherheitsassertion übereinstimmen. Die benutzerdefinierte Bindung mit dem Namen `WseHttpBinding` wird dann verwendet, um die Bindungseigenschaften für einen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Client festzulegen.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Channels.Binding>  
 [Zusammenarbeit mit WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
