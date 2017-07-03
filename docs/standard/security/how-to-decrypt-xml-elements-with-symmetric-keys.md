---
title: "How to: Decrypt XML Elements with Symmetric Keys | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "symmetric keys"
  - "System.Security.Cryptography.EncryptedXml class"
  - "System.Security.Cryptography.RijndaelManaged class"
  - "XML encryption"
  - "Rijndael"
  - "decryption"
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Decrypt XML Elements with Symmetric Keys
Sie können die Klassen im <xref:System.Security.Cryptography.Xml>\-Namespace verwenden, um ein Element in einem XML\-Dokument zu verschlüsseln.  Die XML\-Verschlüsselung ermöglicht Ihnen das Speichern oder Transportieren von vertraulichen XML\-Dokumenten, ohne befürchten zu müssen, dass die Daten einfach gelesen werden können.  In diesem Codebeispiel wird ein XML\-Element mithilfe des AES\-Algorithmus \(Advanced Encryption Standard\) entschlüsselt, der auch unter dem Namen Rijndael bekannt ist.  
  
 Informationen dazu, wie ein XML\-Element mit dieser Prozedur verschlüsselt wird, finden Sie unter [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Wenn Sie einen symmetrischen Algorithmus wie AES verwenden, um XML\-Daten zu verschlüsseln, müssen Sie für das Verschlüsseln und Entschlüsseln der XML\-Daten denselben Schlüssel verwenden.  Für das Beispiel in dieser Prozedur wird angenommen, dass das verschlüsselte XML\-Element mit demselben Schlüssel verschlüsselt wurde und dass sich die verschlüsselnden und die entschlüsselnden Beteiligten über den zu verwendenden Algorithmus und Schlüssel verständigt haben.  In diesem Beispiel wird der AES\-Schlüssel weder im verschlüsselten XML\-Element gespeichert noch dort verschlüsselt.  
  
 Dieses Beispiel ist für Situationen geeignet, in denen eine einzelne Anwendung Daten auf Basis eines Sitzungsschlüssels, der sich im Arbeitsspeicher befindet, oder auf Basis eines starken kryptografischen Schlüssels verschlüsseln muss, der aus einem Kennwort abgeleitet wurde.  Für Situationen, in denen zwei oder mehr Anwendungen verschlüsselte XML\-Daten gemeinsam verwenden müssen, empfiehlt sich die Verwendung eines Verschlüsselungsschemas, dem ein asymmetrischer Algorithmus oder ein X.509\-Zertifikat zugrunde liegt.  
  
### So entschlüsseln Sie ein XML\-Element mit einem symmetrischen Schlüssel  
  
1.  Verschlüsseln Sie ein XML\-Element mit dem zuvor generierten Schlüssel. Verwenden Sie dazu die Verfahren, die unter [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md) beschrieben sind.  
  
2.  Suchen Sie das `EncryptedData`\-Element \(definiert im Standard für XML\-Verschlüsselung\) in einem <xref:System.Xml.XmlDocument>\-Objekt, das das verschlüsselte XML\-Element enthält, und erstellen Sie ein neues <xref:System.Xml.XmlElement>\-Objekt, das dieses Element darstellt.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  Erstellen Sie ein <xref:System.Security.Cryptography.Xml.EncryptedData>\-Objekt, indem Sie die unformatierten XML\-Daten aus dem zuvor erstellten <xref:System.Xml.XmlElement>\-Objekt laden.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  Erstellen Sie ein neues <xref:System.Security.Cryptography.Xml.EncryptedXml>\-Objekt, und verwenden Sie dieses Objekt, um die XML\-Daten zu entschlüsseln. Verwenden Sie dazu den Schlüssel, der für die Verschlüsselung verwendet wurde.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  Ersetzen Sie das verschlüsselte Element durch das neu entschlüsselte Nur\-Text Element innerhalb des XML\-Dokuments.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## Beispiel  
 Für dieses Beispiel wird angenommen, dass eine Datei namens `"test.xml"` im selben Verzeichnis wie das kompilierte Programm vorhanden ist.  Außerdem wird angenommen, dass `"test.xml"` ein `"creditcard"`\-Element enthält.  Sie können den folgenden XML\-Code in eine Datei namens `test.xml` einfügen und mit diesem Beispiel verwenden.  
  
```  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## Kompilieren des Codes  
  
-   Um dieses Beispiel zu kompilieren, müssen Sie einen Verweis auf `System.Security.dll` einfügen.  
  
-   Fügen Sie die folgenden Namespaces hinzu: <xref:System.Xml>, <xref:System.Security.Cryptography> und <xref:System.Security.Cryptography.Xml>.  
  
## .NET Framework-Sicherheit  
 Speichern Sie einen kryptografischen Schlüssel nie im Klartextformat, und übertragen Sie einen Schlüssel nie im Klartextformat zwischen Computern.  
  
 Wenn Sie einen symmetrischen kryptografischen Schlüssel nicht mehr benötigen, entfernen Sie ihn aus dem Arbeitsspeicher, indem Sie jedes Byte auf 0 \(null\) festlegen oder indem Sie die <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A>\-Methode der verwalteten Kryptografieklasse aufrufen.  
  
## Siehe auch  
 <xref:System.Security.Cryptography.Xml>   
 [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)