---
title: Dienstverweigerung (Denial of Service)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d5f67790abad5dcf6311de1817b4ea093e703d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="denial-of-service"></a>Dienstverweigerung (Denial of Service)
Eine Dienstverweigerung tritt auf, wenn ein System derart überlastet ist, dass Nachrichten nicht verarbeitet werden können oder extrem langsam verarbeitet werden.  
  
## <a name="excess-memory-consumption"></a>Übermäßiger Speicherverbrauch  
 Beim Lesen eines XML-Dokuments mit einer großen Anzahl von eindeutigen lokalen Namen, Namespaces oder Präfixen kann ein Problem auftreten. Wenn Sie eine von <xref:System.Xml.XmlReader> abgeleitete Klasse verwenden und für jedes Element die Eigenschaft <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> oder <xref:System.Xml.XmlReader.NamespaceURI%2A> aufrufen, wird die zurückgegebene Zeichenfolge einer <xref:System.Xml.NameTable> hinzugefügt. Die Größe der in der <xref:System.Xml.NameTable> gespeicherten Auflistung nimmt nie ab, sodass ein virtueller Speicherverlust an Zeichenfolgenhandles eintritt.  
  
 Mögliche Gegenmaßnahmen:  
  
-   Leiten Sie von der <xref:System.Xml.NameTable>-Klasse ab, und erzwingen Sie ein maximales Größenkontingent. (Die Verwendung einer <xref:System.Xml.NameTable> lässt sich nicht umgehen, und der Austausch einer vollen <xref:System.Xml.NameTable> ist nicht möglich.)  
  
-   Verwenden Sie nach Möglichkeit anstelle der genannten Eigenschaften die <xref:System.Xml.XmlReader.MoveToAttribute%2A>-Methode mit der <xref:System.Xml.XmlReader.IsStartElement%2A>-Methode. Diese Methoden geben keine Zeichenfolgen zurück und umgehen somit das Problem eines Überlaufs der <xref:System.Xml.NameTable>-Auflistung.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Ein bösartiger Client sendet übermäßig viele Lizenzanforderungen an den Dienst  
 Wenn ein bösartiger Client einen Dienst mit übermäßig vielen Lizenzanforderungen überschwemmt, kann dies eine hohe Speicherauslastung auf dem Server bewirken.  
  
 Gegenmaßnahme: Verwenden Sie die folgenden Eigenschaften der <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>-Klasse:  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: Steuert die maximale Anzahl zeitlich begrenzter `SecurityContextToken`, die der Server nach einer `SPNego`- oder `SSL`-Aushandlung zwischenspeichert.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: Steuert die Lebensdauer der `SecurityContextTokens`, die der Dienst nach der `SPNego`- oder `SSL`-Aushandlung ausstellt. Der Server speichert die `SecurityContextToken` für diesen Zeitraum zwischen.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: Steuert die maximale Anzahl sicherer Konversationen, die auf dem Server erstellt werden, für die jedoch keine Anwendungsnachrichten verarbeitet wurden. Dieses Kontingent verhindert, dass Clients sichere Konversationen auf dem Dienst erstellen, sodass der Dienst den Zustand pro Client beibehält, sie jedoch nicht verwendet.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: Steuert die maximale Zeit, die der Dienst eine sichere Konversation aufrechterhält, ohne eine Anwendungsnachricht vom Client für die Konversation zu erhalten. Dieses Kontingent verhindert, dass Clients sichere Konversationen auf dem Dienst erstellen, sodass der Dienst den Zustand pro Client beibehält, sie jedoch nicht verwendet.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding oder benutzerdefinierte Dualbindungen erfordern Clientauthentifizierung  
 Standardmäßig ist die Sicherheit für <xref:System.ServiceModel.WSDualHttpBinding> aktiviert. Es ist jedoch möglich, dass, wenn die Clientauthentifizierung durch Festlegen der <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A>-Eigenschaft auf <xref:System.ServiceModel.MessageCredentialType.None> deaktiviert ist, ein böswilliger Benutzer einen Denial-of-Service-Angriff auf einen dritten Dienst verursacht. Die Ursache dafür ist, dass ein böswilliger Benutzer den Dienst anweisen kann, einen Nachrichtenstream an einen dritten Dienst zu senden.  
  
 Legen Sie die Eigenschaft nicht auf `None` fest, um diese Gefahr zu umgehen. Bedenken Sie diese Möglichkeit auch beim Erstellen einer benutzerdefinierten Nachricht mit dualem Nachrichtenmuster.  
  
## <a name="auditing-event-log-can-be-filled"></a>Überwachungsereignisprotokoll kann ausgefüllt werden  
 Wenn ein böswilliger Benutzer erkennt, dass die Überwachung aktiviert ist, kann dieser Angreifer ungültige Nachrichten senden, die dazu führen, dass Überwachungseinträge geschrieben werden. Wenn das Überwachungsprotokoll auf diese Weise ausgefüllt wird, schlägt das Überwachungssystem fehl.  
  
 Legen Sie die <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>-Eigenschaft auf `true` fest, und verwenden Sie die Eigenschaften der Ereignisanzeige zum Steuern des Überwachungsverhaltens, um diese Gefahr zu umgehen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Mithilfe der Ereignisanzeige anzeigen und Verwalten von Ereignisprotokollen finden Sie unter [Ereignisanzeige](http://go.microsoft.com/fwlink/?LinkId=186123). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Überwachung](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Ungültige Implementierungen von IAuthorizationPolicy können zu Dienstfehlern führen  
 Das Aufrufen der <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>-Methode für eine fehlerhafte Implementierung der <xref:System.IdentityModel.Policy.IAuthorizationPolicy>-Schnittstelle kann Dienstfehler verursachen.  
  
 Gegenmaßnahme: Verwenden Sie ausschließlich vertrauenswürdigen Code. Verwenden Sie also nur selbst geschriebenen und getesteten Code oder Code von einem vertrauenswürdigen Anbieter. Lassen Sie nicht ohne gründliche Prüfung zu, dass nicht vertrauenswürdige Erweiterungen der <xref:System.IdentityModel.Policy.IAuthorizationPolicy> in Ihren Code geladen werden. Dies gilt für alle in einer Dienstimplementierung verwendeten Erweiterungen. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] unterscheidet nicht zwischen Anwendungscode und Fremdcode, der über Erweiterungspunkte geladen wird.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Maximale Größe des Kerberos-Tokens muss möglicherweise geändert werden  
 Gehört ein Client zu vielen Gruppen (ungefähr 900, obwohl die tatsächliche Anzahl je nach den Gruppen variiert), kann ein Problem auftreten, wenn ein Nachrichtenheaderblock größer als 64 Kilobyte ist. In diesem Fall können Sie die maximale Kerberos-Tokengröße erhöhen, wie in den Microsoft Support-Artikel beschrieben "[Internet Explorer Kerberos-Authentifizierung funktioniert nicht wegen nicht ausreichenden Puffers Herstellen einer Verbindung mit IIS](http://go.microsoft.com/fwlink/?LinkId=89176)." Sie müssen unter Umständen auch die maximale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Nachrichtengröße erhöhen, um sie an den größeren Kerberos-Token anzupassen.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Automatische Registrierung führt zu mehreren Zertifikaten mit gleichem Antragstellernamen für den Computer  
 *Automatische Registrierung* ist die Fähigkeit von [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] -Benutzer und-Computer für Zertifikate automatisch registrieren. Befindet sich ein Computer in einer Domäne mit aktivierter Funktion, wird ein X.509-Zertifikat mit dem beabsichtigten Zweck der Clientauthentifizierung automatisch erstellt und in den persönlichen Zertifikatspeicher des lokalen Computers eingefügt, wenn ein neuer Computer mit dem Netzwerk verbunden wird. Die automatische Registrierung verwendet jedoch den gleichen Antragstellernamen für alle Zertifikate, die sie im Cache erstellt.  
  
 Dies kann zu Fehlern beim Öffnen von [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Diensten in Domänen mit automatischer Registrierung führen. Die Ursache ist, dass die standardmäßigen Suchkriterien des Dienstes für X.509-Anmeldeinformationen mehrdeutig sein können, da mehrere Zertifikate mit dem vollqualifizierten DNS (Domain Name System) des Computers vorhanden sind. Ein Zertifikat stammt aus der automatischen Registrierung, das andere kann ein selbst ausgestelltes Zertifikat sein.  
  
 Um dies abzuschwächen, verweisen Sie Zertifikat zu verwenden, indem Sie eine feiner abgestimmte Suchkriterium auf die [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Verwenden Sie z. B. die <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>-Option, und geben Sie das Zertifikat anhand seines eindeutigen Fingerabdrucks an (Hash).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Registrierungsfunktion finden Sie unter [automatischen Registrierung von Zertifikaten in Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Der letzte von mehreren für die Autorisierung verwendeten alternativen Antragstellernamen  
 In dem seltenen Fall, dass ein X.509-Zertifikat mehrere alternative Antragstellernamen enthält und Sie die Verwendung des alternativen Antragstellernamens autorisieren, kann die Autorisierung fehlschlagen.  
  
## <a name="protect-configuration-files-with-acls"></a>Schutz von Konfigurationsdateien mit Zugriffssteuerungslisten  
 Sie können erforderliche und optionale Ansprüche im Code und in Konfigurationsdateien für von [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ausgestellten Token angeben. Dies führt dazu, dass entsprechende Elemente in `RequestSecurityToken`-Nachrichten ausgegeben werden, die an den Sicherheitstokendienst gesendet werden. Ein Angreifer kann den Code oder die Konfiguration ändern, um erforderliche oder optionale Ansprüche zu entfernen, sodass der Sicherheitstokendienst möglicherweise einen Token ausstellt, der keinen Zugriff auf den Zieldienst gewährt.  
  
 Erfordern Sie zum Ändern der Konfigurationsdatei den Zugriff auf den Computer, um diese Gefahr zu umgehen. Verwenden Sie Zugriffssteuerungslisten zum Sichern von Konfigurationsdateien. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] erfordert, dass sich Code im Anwendungsverzeichnis oder im globalen Assemblycache befindet, bevor er aus der Konfiguration geladen werden kann. Verwenden Sie Verzeichnis-Zugriffssteuerungslisten zum Sichern von Verzeichnissen.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Maximale Anzahl von sicheren Sitzungen für einen Dienst wurde erreicht  
 Wenn ein Client erfolgreich durch einen Dienst authentifiziert wird und eine sichere Verbindung mit dem Dienst eingerichtet wird, verfolgt der Dienst die Sitzung, bis sie vom Client abgebrochen wird oder abläuft. Jede eingerichtete Sitzung wird auf den Grenzwert für die maximale Anzahl gleichzeitiger aktiver Sitzungen mit dem Dienst angerechnet. Wenn dieser Grenzwert erreicht wird, werden Clients abgelehnt, die versuchen, eine neue Sitzung mit diesem Dienst zu erstellen, bis eine oder mehrere aktive Sitzungen ablaufen oder vom Client abgebrochen werden. Ein Client kann über mehrere Sitzungen mit einem Dienst verfügen, und jede dieser Sitzungen wird auf den Grenzwert angerechnet.  
  
> [!NOTE]
>  Wenn Sie zustandsbehaftete Sitzungen verwenden, trifft der vorhergehende Absatz nicht zu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zustandsbehaftete Sitzungen finden Sie unter [Vorgehensweise: Erstellen Sie ein Sicherheitskontexttoken für eine Sicherheitssitzung](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Legen Sie den Grenzwert für die maximale Anzahl aktiver Sitzungen und die maximale Lebensdauer für eine Sitzung über die <xref:System.ServiceModel.Channels.SecurityBindingElement>-Eigenschaft der <xref:System.ServiceModel.Channels.SecurityBindingElement>-Klasse fest, wenn Sie dieses Sicherheitsproblem vermeiden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberlegungen](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Offenlegung vertraulicher Informationen](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Erhöhen der Berechtigungen](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Denial-of-Service-Angriffe](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Replayangriffe](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Manipulation](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nicht unterstützte Szenarien](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
