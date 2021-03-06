---
title: Exception-Klasse und Exception-Eigenschaften
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a>Ausnahmeklasse und -eigenschaften

Die <xref:System.Exception>-Klasse ist die Basisklasse, von der Ausnahmen erben. Die Hierarchie der <xref:System.InvalidCastException>-Klasse sieht beispielsweise wie folgt aus:

```
Object
  Exception
    SystemException
       InvalidCastException
```

Die <xref:System.Exception>-Klasse verfügt über die folgenden Eigenschaften, die das Verständnis einer Ausnahme erleichtern.

| Eigenschaftenname | Beschreibung |
| ------------- | ----------- |
| <xref:System.Exception.Data> | Ein <xref:System.Collections.IDictionary>, das beliebige Daten in Schlüssel-Wert-Paaren enthält. |
| <xref:System.Exception.HelpLink> | Kann einen URL (oder URN) zu einer Hilfedatei enthalten, die ausführliche Informationen zur Ursache einer Ausnahme bereitstellt. |
| <xref:System.Exception.InnerException> | Diese Eigenschaft kann verwendet werden, um während der Ausnahmebehandlung eine Reihe von Ausnahmen zu erstellen und beizubehalten. Sie können sie verwenden, um eine neue Ausnahme zu erstellen, die zuvor bereits abgefangene Ausnahmen enthält. Die ursprüngliche Ausnahme kann durch die zweite Ausnahme in der <xref:System.Exception.InnerException>-Eigenschaft abgefangen werden. So kann der Code, der die zweite Ausnahme verarbeitet, die zusätzlichen Informationen untersuchen. Ein Beispiel: Sie verfügen über eine Methode, die ein unzureichend formatiertes Argument erhält.  Der Code versucht, das Argument zu lesen, es wird aber eine Ausnahme ausgelöst. Die Methode fängt die Ausnahme ab und löst eine <xref:System.FormatException> aus. Um die Fähigkeit des Aufrufers zu erhöhen, den Grund für eine Ausnahme zu ermitteln, ist es manchmal wünschenswert, dass eine Methode eine von einer Hilfsroutine ausgelöste Ausnahme abfängt und dann eine Ausnahme auslöst, die bessere Hinweise auf den aufgetretenen Fehler bietet. Es kann eine neue, aussagekräftigere Ausnahme erstellt werden, in der der Verweis auf die innere Ausnahme auf die ursprüngliche Ausnahme festgelegt werden kann. Diese aussagekräftigere Ausnahme kann für den Aufrufer ausgelöst werden. Beachten Sie, dass Sie mit dieser Funktionalität eine Reihe von verknüpften Ausnahmen erstellen können, die mit der Ausnahme endet, die zuerst ausgelöst wurde. |
| <xref:System.Exception.Message> | Bietet Informationen zur Ursache einer Ausnahme.
| <xref:System.Exception.Source> | Gibt den Namen der Anwendung oder des Objekts zurück, die bzw. das den Fehler verursacht hat, oder legt diesen fest. |
| <xref:System.Exception.StackTrace>| Enthält eine Stapelüberwachung, die verwendet kann, um zu ermitteln, wo ein Fehler aufgetreten ist. Die Stapelüberwachung beinhaltet den Quelldateinamen und die Programmzeilennummer, falls Debuginformationen verfügbar sind. |

Die meisten der Klassen, die von <xref:System.Exception> erben, implementieren keine weiteren Member und stellen keine weitere Funktionalität bereit. Sie erben einfach von <xref:System.Exception>. Daher finden sich die wichtigsten Informationen für eine Ausnahme in der Hierarchie der Ausnahmeklassen, dem Namen der Ausnahme und den in der Ausnahme enthaltenen Details.

Es wird empfohlen, dass Sie auslösen und nur Abfangen von abgeleiteten Objekte <xref:System.Exception>, aber Sie können jedes Objekt, das von abgeleitet ist Auslösen der <xref:System.Object> Klasse als eine Ausnahme. Beachten Sie, dass einige Sprachen nur das Auslösen und Abfangen von Objekten unterstützen, die nicht von <xref:System.Exception> abgeleitet sind.
  
## <a name="see-also"></a>Siehe auch  
[Ausnahmen](index.md)
