---
title: '&lt;ServicePointManager&gt; -Element (Netzwerkeinstellungen)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 38ffe6728ca05022caca8f5973b546f2b17412d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicepointmanagergt-element-network-settings"></a>&lt;ServicePointManager&gt; -Element (Netzwerkeinstellungen)
Konfiguriert die Verbindungen mit Netzwerkressourcen.  
  
 \<configuration>  
\<System.NET >  
\<Einstellungen >  
\<ServicePointManager >  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|**Attribut**|**Beschreibung**|  
|-------------------|---------------------|  
|`checkCertificateName`|Gibt an, ob das System überprüft, ob der Name für das Zertifikat den Hostnamen entspricht, bevor Sie mit dem Zertifikat. Der Standardwert ist `true`.|  
|`checkCertificateRevocationList`|Gibt an, ob das System, ob das Zertifikat widerrufen wurde, bevor Sie mithilfe des Zertifikats überprüft werden soll. Der Standardwert ist `false`.|  
|`dnsRefreshTimeout`|Gibt an, wie lange Dienst DNS (Domain Name) Lösungen zwischengespeichert werden in Verbindung mit der DNS-Round-Robin-Option in Millisekunden. Der Standardwert ist 120.000 Millisekunden (zwei Minuten).|  
|`enableDnsRoundRobin`|Gibt an, ob die DNS-Auflösung des Hosts benennt mit mehreren IP (Internet Protocol)-Adressen zurückgegeben, alle Adressen oder nur die erste Aktivität. Der Standardwert ist `false`.|  
|`encryptionPolicy`|Gibt an, die Verschlüsselungsrichtlinie für eine SSL/TLS-Sitzung angewendet wird, auf eine <xref:System.Net.ServicePointManager> Instanz. Die möglichen Werte sind entsprechen den Werten für die <xref:System.Net.Security.EncryptionPolicy> Enumeration. Die Verwendung von <xref:System.Security.Authentication.CipherAlgorithmType.Null> ist erforderlich, wenn die Verschlüsselungsrichtlinie, um festgelegt ist `NoEncryption`. Der Standardwert ist `RequireEncryption`.|  
|`expect100Continue`|Gibt an, ob die POST-Methoden erwarten soll eine `100-continue` Antwort vom Server. Der Standardwert ist `true`.|  
|`useNagleAlgorithm`|Gibt an, ob den Nagle-Algorithmus, Verbindungen, die von der Point-Dienst-Manager gesteuert verwenden. Der Standardwert ist `true`.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|**Element**|**Beschreibung**|  
|-----------------|---------------------|  
|[Einstellungen](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Konfiguriert grundlegende Netzwerkoptionen für den <xref:System.Net>-Namespace.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="configuration-files"></a>Konfigurationsdateien  
 Dieses Element kann in der Anwendungskonfigurationsdatei oder in der Computerkonfigurationsdatei ("Machine.config") verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [Network Settings Schema (Schema für Netzwerkeinstellungen)](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
