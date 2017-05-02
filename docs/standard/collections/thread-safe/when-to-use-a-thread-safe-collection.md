---
title: Verwendung einer threadsicheren Sammlung | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 87898a4a6ba3d3ef4c53fd1c6b8f94ff353f10e4
ms.lasthandoff: 04/18/2017

---
# <a name="when-to-use-a-thread-safe-collection"></a>Verwendung einer threadsicheren Auflistung
Mit [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] werden fünf neue Sammlungstypen eingeführt, die speziell für die Unterstützung von multithreaded Hinzufügen- und Entfernungsvorgängen ausgelegt sind. Zur Gewährleistung von Threadsicherheit verwenden diese neuen Typen unterschiedliche Arten effizienter sperrender und sperrfreier Synchronisierungsmechanismen. Ein Vorgang wird durch Synchronisierung aufwändiger. Das Ausmaß des Aufwands hängt von der Art der verwendeten Synchronisierung, der Art der ausgeführten Vorgänge und von anderen Faktoren ab, z.B. der Anzahl der Threads, die versuchen, gleichzeitig auf die Sammlung zuzugreifen.  
  
 In einigen Szenarien ist der Synchronisierungsaufwand unwesentlich und ermöglicht eine deutlich schnellere Ausführung und bessere Skalierbarkeit des Multithreadtyps als beim nicht threadsicheren Äquivalent, wenn ein Schutz durch eine externe Sperre besteht. In anderen Szenarien kann der Aufwand dazu führen, dass der threadsichere Typ in etwa mit der gleichen oder sogar einer geringeren Leistung und Skalierbarkeit ausgeführt wird wie die extern gesperrte, nicht threadsichere Version des Typs.  
  
 Die folgenden Abschnitte enthalten eine allgemeine Anleitung dazu, wann eine threadsichere Sammlung anstelle ihres nicht threadsicheren Äquivalents verwendet wird, das eine vom Benutzer bereitgestellte Sperre für die Lese- und Schreibvorgänge besitzt. Da die Leistung von vielen Faktoren abhängig sein kann, handelt es sich nicht um eine spezielle Anleitung, die daher nicht unter allen Umständen gültig ist. Wenn die Leistung sehr wichtig ist, ist die am besten geeignete Methode zur Bestimmung des zu verwendenden Sammlungstyps die Messung der Leistung auf Basis von repräsentativen Computerkonfigurationen und Lasten. In diesem Dokument werden die folgenden Begriffe verwendet:  
  
 *Reines Producer-Consumer-Szenario*  
 In jedem vorhandenen Thread werden Elemente entweder hinzugefügt oder entfernt, es finden jedoch nicht beide Vorgänge statt.  
  
 *Gemischtes Producer-Consumer-Szenario*  
 In jedem vorhandenen Thread werden Elemente sowohl hinzugefügt als auch entfernt.  
  
 *Geschwindigkeitszuwachs*  
 Höhere algorithmische Leistung relativ zu einem anderen Typ im gleichen Szenario.  
  
 *Skalierbarkeit*  
 Die Zunahme der Leistung, die proportional zur Anzahl der Kerne des Computers ist. Mit einem Algorithmus, der skaliert wird, werden bei acht Kernen höhere Leistungen erzielt als bei zwei Kernen.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) oder Queue(T)  
 In reinen Producer-Consumer-Szenarien, in denen die Verarbeitungszeit für jedes Element sehr kurz ist (einige Anweisungen), kann <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> geringfügige Leistungsvorteile gegenüber <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> mit einer externen Sperre bieten. In diesem Szenario erzielt <xref:System.Collections.Concurrent.ConcurrentQueue%601> die beste Leistung, wenn sich ein dedizierter Thread in der Warteschlange befindet und ein dedizierter Thread die Warteschlange verlässt. Wenn Sie diese Regel nicht erzwingen, arbeitet <xref:System.Collections.Generic.Queue%601> auf Computern mit mehreren Kernen möglicherweise sogar minimal schneller als <xref:System.Collections.Concurrent.ConcurrentQueue%601>.  
  
 Wenn die Verarbeitungszeit bei etwa 500 FLOPS (Gleitkommavorgänge) oder höher liegt, gilt die Zwei-Thread-Regel nicht für <xref:System.Collections.Concurrent.ConcurrentQueue%601>, sodass dann eine sehr gute Skalierbarkeit möglich ist. <xref:System.Collections.Generic.Queue%601> skaliert in diesem Szenario nicht gut.  
  
 In gemischten Producer-Consumer-Szenarien mit sehr kurzer Verarbeitungszeit skaliert <xref:System.Collections.Generic.Queue%601> mit einer externen Sperre besser als <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Wenn die Verarbeitungszeit jedoch um 500 FLOPS oder höher liegt, skaliert <xref:System.Collections.Concurrent.ConcurrentQueue%601> besser.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack oder Stapel  
 In reinen Producer-Consumer-Szenarien erzielen <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> und <xref:System.Collections.Generic.Stack%601?displayProperty=fullName> mit einer externen Sperre bei sehr geringer Verarbeitungszeit wahrscheinlich annähernd die gleiche Leistung mit einem dedizierten Thread für Ablegevorgänge und einem dedizierten Thread für Abholvorgänge. Bei wachsender Threadanzahl werden allerdings beide Typen aufgrund steigender Sättigung langsamer, dann ist die Leistung von <xref:System.Collections.Generic.Stack%601> möglicherweise besser als die von <xref:System.Collections.Concurrent.ConcurrentStack%601>. Wenn die Verarbeitungszeit bei rund 500 FLOPS oder darüber liegt, werden beide Typen mit der etwa gleichen Rate skaliert.  
  
 In gemischten Producer-Consumer-Szenarien ist <xref:System.Collections.Concurrent.ConcurrentStack%601> sowohl für kleine als auch für große Arbeitsauslastungen schneller.  
  
 Die Verwendung von <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> und <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> kann die Zugriffszeiten stark verkürzen.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary oder Dictionary  
 Verwenden Sie im Allgemeinen in allen Szenarien, in denen Sie Schlüssel oder Werte parallel aus mehreren Threads hinzufügen und aktualisieren, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>. In Szenarien, in denen häufige Aktualisierungen und relativ wenig Lesezugriffe vorkommen, bietet <xref:System.Collections.Concurrent.ConcurrentDictionary%602> im Allgemeinen geringfügige Vorteile. In Szenarien, die zahlreiche Lesevorgänge und Aktualisierungen umfassen, ist <xref:System.Collections.Concurrent.ConcurrentDictionary%602> im Allgemeinen auf Computern bedeutend schneller, die über eine beliebige Anzahl von Kernen verfügen.  
  
 In Szenarien, die häufige Updates umfassen, können Sie den Grad der Parallelität in <xref:System.Collections.Concurrent.ConcurrentDictionary%602> erhöhen und anschließend ermitteln, ob sich die Leistung auf Computern mit einer größeren Anzahl von Kernen verbessert. Wenn Sie die Parallelitätsebene ändern, vermeiden Sie so weit wie möglich globale Vorgänge.  
  
 Wenn Sie nur Schlüssel oder Werte lesen, ist <xref:System.Collections.Generic.Dictionary%602> schneller, da keine Synchronisierung erforderlich ist, wenn das Wörterbuch nicht von Threads geändert wird.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 In reinen Producer-Consumer-Szenarien ist <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> wahrscheinlich langsamer als die anderen gleichzeitigen Sammlungstypen.  
  
 In gemischten Producer-Consumer-Szenarien ist <xref:System.Collections.Concurrent.ConcurrentBag%601> sowohl bei großen als auch bei kleinen Arbeitsauslastungen im Allgemeinen viel schneller und besser skalierbar als ein beliebiger anderer gleichzeitiger Sammlungstyp.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Wenn Begrenzungs- und Blockierungssemantiken erforderlich sind, wird <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> wahrscheinlich schneller als jede beliebige benutzerdefinierte Implementierung ausgeführt. Zudem werden umfassende Möglichkeiten für die Abbruch-, Enumerations- und Ausnahmebehandlung unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Threadsichere Sammlungen](../../../../docs/standard/collections/thread-safe/index.md)   
 [Parallele Programmierung](../../../../docs/standard/parallel-programming/index.md)