---
title: Objekte (C#-Programmierhandbuch)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f8a8e283b42b27a40780068be42c03fc5047a511
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="objects-c-programming-guide"></a>Objekte (C#-Programmierhandbuch)
Die Definition einer Klasse oder Struktur ist mit einem Entwurf vergleichbar, der angibt, was der Typ machen kann. Ein Objekt ist im Grunde ein Speicherblock, der nach Plan zugewiesen und konfiguriert wurde. Ein Programm kann viele Objekte der selben Klasse erstellen. Objekte werden auch Instanzen genannt, und sie können entweder in einer benannten Variable, einem Array oder in einer Auflistung gespeichert werden. Der Client-Code ist der Code, der diese Variablen verwendet, um die Methoden aufzurufen und um auf die öffentlichen Eigenschaften des Objekts zuzugreifen. In einer objektorientierten Programmiersprache wie C# besteht ein typisches Programm aus mehreren Objekten, die dynamisch interagieren.  
  
> [!NOTE]
>  Statische Typen verhalten sich anders, als die hier beschriebenen. Weitere Informationen finden Sie unter [Statische Klassen und statische Klassenmember](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Strukturinstanzen im Vergleich zu Klasseninstanzen  
 Da Klassen Verweistypen sind, enthält eine Variable eines Klassenobjekts einen Verweis auf die Adresse des Objekts auf dem verwalteten Heap. Wenn dem ersten Objekt ein zweites Objekt desselben Typs zugewiesen wird, verweisen beide Variablen auf das Objekt in dieser Adresse. Dieser Punkt wird in diesem Thema an späterer Stelle ausführlicher behandelt.  
  
 Instanzen von Klassen werden mit dem [new-Operator](../../../csharp/language-reference/keywords/new-operator.md) erstellt. Im folgenden Beispiel ist `Person` der Typ und `person1` und `person2` sind Instanzen oder Objekte des Typs.  
  
 [!code-csharp[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Da Strukturen Werttypen sind, enthält eine Variable eines Strukturobjekts eine Kopie des gesamten Objekts. Instanzen von Strukturen können auch mithilfe des `new`-Operators erstellt werden; dies ist jedoch nicht erforderlich, wie im folgenden Beispiel gezeigt wird:  
  
 [!code-csharp[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 Der Speicher für `p1` und `p2` ist dem Stapel des Threads zugeordnet. Der Speicher wird zusammen mit dem Typ oder der Methode freigegeben, in dem bzw. in der er deklariert wird. Dies ist ein Grund, weshalb Strukturen bei Zuweisung kopiert werden. Im Gegensatz dazu wird der Speicher, der für eine Klasseninstanz zugeordnet ist, automatisch von der Common Language Runtime freigegeben (von Garbage Collection bereinigt), wenn alle Verweise auf das Objekt außerhalb des Gültigkeitsbereichs liegen. Es ist nicht möglich, ein Klassenobjekt deterministisch wie in C++ zu zerstören. Weitere Informationen zur Garbage Collection im [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] finden Sie unter [Garbage Collection](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Die Belegung und Freigabe von Arbeitsspeicher auf dem verwalteten Heap ist in der Common Language Runtime stark optimiert. In den meisten Fällen besteht kein wesentlicher Unterschied zwischen den Leistungskosten beim Zuweisen einer Klasseninstanz auf dem Heap im Vergleich zum Zuweisen einer Strukturinstanz im Stapel.  
  
## <a name="object-identity-vs-value-equality"></a>Objektidentität im Vergleich zur Wertgleichheit  
 Wenn Sie zwei Objekte auf Gleichheit vergleichen, müssen Sie zuerst unterscheiden, ob Sie wissen möchten, ob die zwei Variablen das gleiche Objekt im Speicher darstellen, oder ob die Werte von einem oder mehreren Feldern gleich sind. Wenn Sie planen, Werte zu vergleichen, müssen Sie berücksichtigen, ob die Objekte Instanzen von Werttypen (Strukturen) oder Referenztypen (Klassen, Delegate, Arrays) sind.  
  
-   Verwenden Sie die statische Methode <xref:System.Object.Equals%2A>, um zu bestimmen, ob zwei Klasseninstanzen auf den gleichen Speicherort im Arbeitsspeicher verweisen (d.h., sie haben die gleiche *Identität*). (<xref:System.Object?displayProperty=nameWithType> ist die implizite Basisklasse für alle Wert- und Referenztypen, einschließlich benutzerdefinierter Strukturen und Klassen.)  
  
-   Verwenden Sie die Methode <xref:System.ValueType.Equals%2A?displayProperty=nameWithType>, um zu bestimmen, ob die Instanzfelder in zwei Strukturinstanzen die gleichen Werte haben. Da alle Strukturen implizit von <xref:System.ValueType?displayProperty=nameWithType> erben, rufen Sie die Methode direkt an Ihrem Objekt auf, wie im folgenden Beispiel gezeigt wird:  
  
 [!code-csharp[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 Die Implementierung <xref:System.ValueType?displayProperty=nameWithType> von `Equals` verwendet Reflektion, da sie bestimmen muss, was die Felder in jeder Struktur sind. Wenn Sie eigene Strukturen erstellen, überschreiben Sie die Methode `Equals`, um einen effizienten Gleichheitsalgorithmus bereitzustellen, der spezifisch für Ihren Typ ist.  
  
-   Sie können möglicherweise die Methode <xref:System.Object.Equals%2A> oder den [==-Operator](../../../csharp/language-reference/operators/equality-comparison-operator.md) verwenden, um zu bestimmen, ob die Werte des Felds in zwei Klasseninstanzen gleich sind. Verwenden Sie sie jedoch nur, wenn die Klasse die Werte überschrieben oder überladen hat, um eine benutzerdefinierte Definition von „Gleichheit“ für Objekte dieses Typs bereitzustellen. Die Klasse kann auch die Schnittstelle <xref:System.IEquatable%601> oder die Schnittstelle <xref:System.Collections.Generic.IEqualityComparer%601> implementieren. Beide Schnittstellen bieten Methoden, die zum Testen der Wertgleichheit verwendet werden können. Wenn Sie Ihre eigenen Klassen entwickeln, die `Equals` überschreiben, achten Sie darauf, die Richtlinien zu befolgen, die in [Vorgehensweise: Definieren von Wertgleichheit für einen Typ](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) und <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> aufgeführt sind.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 Weitere Informationen finden Sie unter:   
  
-   [Klassen](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Strukturen](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Konstruktoren](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Finalizer](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Ereignisse](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [object](../../../csharp/language-reference/keywords/object.md)  
 [Vererbung](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [new-Operator](../../../csharp/language-reference/keywords/new-operator.md)  
 [Allgemeines Typsystem](../../../standard/base-types/common-type-system.md)
