---
title: "Gewusst wie: Hinzufügen und Entfernen von Elementen aus einem ConcurrentDictionary"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c034b656cf7a953ae532c12640b5916001764c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Gewusst wie: Hinzufügen und Entfernen von Elementen aus einem ConcurrentDictionary
Dieses Beispiel zeigt, wie Elemente hinzugefügt, abgerufen, aktualisiert und von einer <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> entfernt werden. Diese Auflistungsklasse ist eine threadsichere Implementierung. Es empfiehlt sich, diese Klasse immer dann zu verwenden, wenn möglicherweise mehrere Threads gleichzeitig versuchen, auf Elemente zuzugreifen.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> bietet verschiedene praktische Methoden, mit denen der Code nicht mehr zuerst prüfen muss, ob ein Schlüssel vorhanden ist, bevor versucht wird, Daten hinzuzufügen oder zu entfernen. Die folgende Tabelle führt diese praktischen Methoden auf und beschreibt ihre Verwendung.  
  
|Methode|Wenn folgende Bedingungen vorliegen|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Sie möchten einen neuen Wert für einen angegebenen Schlüssel hinzufügen und, wenn der Schlüssel bereits vorhanden ist, den Wert ersetzen.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Sie möchten den vorhandenen Wert für einen angegebenen Schlüssel abrufen und, wenn der Schlüssel nicht vorhanden ist, ein Schlüssel-Wert-Paar angeben.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Sie möchten ein Schlüssel-Wert-Paar hinzufügen, abrufen, aktualisieren oder entfernen und, wenn der Schlüssel bereits vorhanden ist oder der Versuch aus einem anderen Grund fehlschlägt, eine alternative Aktion durchführen.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden zwei Instanzen von <xref:System.Threading.Tasks.Task> verwendet, um <xref:System.Collections.Concurrent.ConcurrentDictionary%602> parallel einige Elemente hinzuzufügen und dann den gesamten Inhalt auszugeben, um zu zeigen, dass die Elemente erfolgreich hinzugefügt wurden. Das Beispiel zeigt auch, wie die Methoden <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> und <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> zum Hinzufügen, Aktualisieren und Abrufen von Elementen aus der Auflistung verwendet werden.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> wurde für Multithread-Szenarios entworfen. Sie müssen keine Sperren in Ihrem Code verwenden, um Elemente zur Auflistung hinzuzufügen oder daraus zu entfernen. Es ist jedoch immer möglich, dass ein Thread einen Wert abruft und ein anderer Thread durch Zuweisen eines neuen Werts zum gleichen Schlüssel die Auflistung unmittelbar danach aktualisiert.  
  
 Darüber hinaus sind zwar alle Methoden von <xref:System.Collections.Concurrent.ConcurrentDictionary%602> threadsicher, aber nicht alle Methoden sind atomisch – insbesondere <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> und <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Der an diese Methoden übergebene Benutzerdelegat wird außerhalb der internen Sperre des Wörterbuchs aufgerufen. (Dies erfolgt, um zu verhindern, dass unbekannter Code alle Threads blockiert.) Daher ist es möglich, dass die folgende Ereignissequenz eintritt:  
  
 1\) threadA ruft <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> auf, findet kein Element und erstellt ein neues hinzuzufügendes Element durch Aufrufen des valueFactory-Delegaten.  
  
 2\) threadB ruft <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> gleichzeitig auf, der zugehörige valueFactory-Delegat wird aufgerufen und erreicht die interne Sperre vor threadA. Daher wird das neue Schlüssel-Wert-Paar dieses Threads zum Wörterbuch hinzugefügt.  
  
 3\) Der Benutzerdelegat von threadA wird fertiggestellt, und der Thread erreicht die Sperre, stellt jetzt aber fest, dass das Element bereits vorhanden ist.  
  
 4\) threadA führt einen „Get“ aus und gibt die Daten zurück, die zuvor von threadB hinzugefügt worden waren.  
  
 Daher ist nicht garantiert, dass die von <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> zurückgegebenen Daten die gleichen Daten sind, die von der valueFactory des Threads erstellt wurden. Eine ähnliche Abfolge von Ereignissen kann eintreten, wenn <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [threadsichere Auflistungen](../../../../docs/standard/collections/thread-safe/index.md)
