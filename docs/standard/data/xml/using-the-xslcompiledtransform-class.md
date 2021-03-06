---
title: Verwenden der XslCompiledTransform-Klasse
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a5c71a7796790343bf39de5bbfd03997c25d5f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-xslcompiledtransform-class"></a>Verwenden der XslCompiledTransform-Klasse
Die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse ist der XSLT-Prozessor in .NET Framework. Diese Klasse wird zum Kompilieren von Stylesheets und zum Ausführen von XSLT-Transformationen verwendet.  
  
> [!NOTE]
>  Obwohl die Gesamtleistung der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse besser ist als die der <xref:System.Xml.Xsl.XslTransform>-Klasse, ist die Leistung der <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>-Methode der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse möglicherweise langsamer als die <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methode der <xref:System.Xml.Xsl.XslTransform>-Klasse, wenn sie zum ersten Mal für eine Transformation aufgerufen wird. Dies liegt daran, dass die XSLT-Datei zunächst kompiliert werden muss, bevor sie geladen wird. Weitere Informationen finden Sie im folgenden Blogbeitrag: [XslCompiledTransform Slower than XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Eingaben für die XslCompiledTransform-Klasse](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Beschreibt die verfügbaren XSLT-Eingabeoptionen.  
  
 [Ausgabeoptionen für die XslCompiledTransform-Klasse](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Beschreibt die verfügbaren XSLT-Ausgabeoptionen.  
  
 [Auflösen von externen Ressourcen während der XSLT-Verarbeitung](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Erläutert die Verwendung der <xref:System.Xml.XmlResolver>-Klasse beim Auflösen externer Ressourcen.  
  
 [Erweitern von XSLT-Stylesheets](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Erläutert die Unterstützung von XSLT-Erweiterungen.  
  
|||  
|-|-|  
|[Wiederherstellbare XSLT-Fehler](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Listet die freigegebenen Verhaltensweisen auf, die gemäß der W3C-Empfehlung zu XSL-Transformationen (XSLT), Version 1.0, zugelassen sind, und beschreibt, wie diese Verhaltensweisen von der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse behandelt werden.|  
|[Vorgehensweise: Transformieren eines Knotenfragments](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Beschreibt, wie ein Knotenfragment transformiert wird.|  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Migrieren von der XslTransform-Klasse](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Erläutert die Migration von Code von der <xref:System.Xml.Xsl.XslTransform>-Klasse.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
