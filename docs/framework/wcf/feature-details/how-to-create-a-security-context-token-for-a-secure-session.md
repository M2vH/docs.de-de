---
title: "Vorgehensweise: Erstellen eines Tokens für den Sicherheitskontext einer sicheren Sitzung"
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
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3dc0e44e7f561e39128e32d3af5fbd495316fdd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Vorgehensweise: Erstellen eines Tokens für den Sicherheitskontext einer sicheren Sitzung
Durch das Verwenden eines zustandsbehafteten Sicherheitskontexttokens (SCT) in einer sicheren Sitzung, kann die Sitzung verhindern, dass der Dienst wiederverwendet wird. Wenn beispielsweise ein zustandsloses SCT in einer sicheren Sitzung verwendet wird und die IIS (Internet Information Services) zurückgesetzt werden, gehen die Sitzungsdaten, die dem Dienst zugewiesen sind, verloren. Zu den Sitzungsdaten gehört auch ein SCT-Token-Cache. Wenn ein Client also das nächste Mal dem Dienst einen zustandsloses SCT sendet, wird ein Fehler zurückgegeben, da der diesem SCT zugewiesene Schlüssel nicht abgerufen werden kann. Wenn jedoch ein zustandsbehafteter SCT verwendet wird, enthält das SCT den diesem SCT zugewiesenen Schlüssel. Da der Schlüssel im SCT enthalten ist und somit auch in der Nachricht, wird die sichere Sitzung nicht von der Wiederverwendung des Dienstes beeinträchtigt. Standardmäßig verwendet [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zustandslose SCTs in einer sicheren Sitzung. Dieses Thema erläutert, wie Sie zustandsbehaftete SCTs in einer sicheren Sitzung verwenden können.  
  
> [!NOTE]
>  Zustandsbehaftete SCTs können nicht in einer sicheren Sitzung verwendet werden, die einen Vertrag einschließt, der vom <xref:System.ServiceModel.Channels.IDuplexChannel> abgeleitet wird.  
  
> [!NOTE]
>  Bei Anwendungen, die zustandsbehaftete SCTs in einer sicheren Sitzung verwenden, muss die Thread-Identität des Dienstes ein Benutzerkonto sein, dem ein Benutzerprofil zugewiesen ist. Wenn der Dienst unter einem Konto ausgeführt wird, für das kein Benutzerprofil festgelegt wurde, z. B. ein `Local Service`, wird möglicherweise eine Ausnahme ausgegeben.  
  
> [!NOTE]
>  Wenn ein Identitätswechsel auf Windows XP erforderlich ist, verwenden Sie eine sichere Sitzung ohne zustandsbehaftetes SCT. Wenn Token für den Sicherheitszustandskontext (SCTs) mit einem Identitätswechsel verwendet werden, wird ein <xref:System.InvalidOperationException> ausgelöst. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nicht unterstützte Szenarien](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>So verwenden Sie zustandsbehaftete SCTs in einer sicheren Sitzung  
  
-   Erstellen Sie eine benutzerdefinierte Bindung, die angibt, dass SOAP-Nachrichten durch eine sichere Sitzung mit einem zustandsbehafteten SCT geschützt sind.  
  
    1.  Definieren Sie eine benutzerdefinierte Bindung durch Hinzufügen einer [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in die Konfigurationsdatei für den Dienst.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Hinzufügen einer [ \<Bindung >](../../../../docs/framework/misc/binding.md) untergeordnetes Element der [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Geben Sie einen Bindungsnamen an, indem Sie das `name`-Attribut auf einen eindeutigen Namen in der Konfigurationsdatei festlegen.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Geben Sie den Authentifizierungsmodus für Nachrichten an und von diesem Dienst durch Hinzufügen einer [ \<Sicherheit >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) untergeordnetes Element der [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Legen Sie fest, dass eine sichere Sitzung verwendet wird, indem Sie das `authenticationMode`-Attribut auf `SecureConversation` setzen. Legen Sie fest, dass zustandsbehaftete SCTs verwendet werden, indem Sie das `requireSecurityContextCancellation`-Attribut auf `false` setzen.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Angeben, wie der Client authentifiziert wird, während die sichere Sitzung, durch Hinzufügen verwendet wird einer [ \<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) untergeordnetes Element der [ \<Sicherheit >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Geben Sie an, wie der Client authentifiziert wird, indem Sie das `authenticationMode`-Attribut setzen.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Geben Sie die nachrichtencodierung, indem Sie ein Codierungselement, z. B. hinzufügen [ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Geben Sie den Transport durch Hinzufügen von ein Transportelement, z. B. die [ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Im folgenden Codebeispiel wird die Konfiguration verwendet, um eine benutzerdefinierte Bindung anzugeben, die Nachrichten mit zustandsbehafteten SCTs in einer sicheren Sitzung verwenden können.  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel erstellt eine benutzerdefinierte Bindung, die den <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>-Authentifizierungsmodus verwendet, um eine sichere Sitzung mithilfe eines Bootstrap-Vorgangs zu starten.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Wenn die Windows-Authentifizierung zusammen mit einem zustandsbehafteten SCT verwendet wird, füllt [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nicht die <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>-Eigenschaft mit der tatsächlichen Identität des Anrufers aus, sondern legt die Eigenschaft auf den Wert Anonym fest. Da die [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Sicherheit den Inhalt des Dienstsicherheitskontextes für jede Anfrage vom eingehenden SCT neu erstellen muss, verfolgt der Server nicht die Sicherheitssitzung im Speicher. Da die <xref:System.Security.Principal.WindowsIdentity>-Instanz nicht in das SCT serialisiert werden kann, gibt die <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>-Eigenschaft eine anonyme Identität zurück.  
  
 Die folgende Konfiguration weist dieses Verhalten auf.  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
