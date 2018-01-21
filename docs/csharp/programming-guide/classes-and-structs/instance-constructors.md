---
title: Instanzkonstruktoren (C#-Programmierhandbuch)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: efb82128ffc27a7c065d2ba12bfc08396d3b5cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="instance-constructors-c-programming-guide"></a>Instanzkonstruktoren (C#-Programmierhandbuch)
Instanzkonstruktoren werden zum Erstellen und Initialisieren von Instanzmembervariablen verwendet, wenn Sie den Ausdruck [new](../../../csharp/language-reference/keywords/new.md) verwenden, um ein Objekt einer [Klasse](../../../csharp/language-reference/keywords/class.md) zu erstellen. Sie müssen einen statischen Konstruktor definieren um eine [statische](../../../csharp/language-reference/keywords/static.md) Klasse oder eine statische Variable in einer nicht statischen Klasse zu initialisieren. Weitere Informationen finden Sie unter [Statische Konstruktoren](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Im folgenden Beispiel wird die Verwendung eines Instanzkonstruktors veranschaulicht:  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Der Deutlichkeit halber enthält diese Klasse öffentliche Felder. Das Verwenden von öffentlichen Felder wird beim Programmieren nicht empfohlen, da so jede Methode im Programm uneingeschränkten und ungeprüften Zugriff auf das Innenleben eines Objekts erhält. Datenmember sollten im Allgemeinen privat sein. Außerdem sollte auf sie nur über Klassenmethoden und Eigenschaften zugegriffen werden.  
  
 Dieser Instanzkonstruktor wird aufgerufen, wenn ein Objekt basierend auf der `CoOrds`-Klasse erstellt wird. Ein derartiger Konstruktor, der keine Argumente akzeptiert, wird als *Standardkonstruktor* bezeichnet. Es kann jedoch oft hilfreich sein, weitere Konstruktoren bereitzustellen. Sie können beispielsweise einen Konstruktor in die `CoOrds`-Klasse einfügen, mit dem Sie die Anfangswerte der Datenmember angeben können:  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Damit können `CoOrd`-Objekte mit Standard- oder spezifischen Anfangswerten erstellt werden. Dies geschieht wie folgt:  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Wenn eine Klasse über keinen Konstruktor verfügt, wird automatisch ein Standardkonstruktor generiert, und die Objektfelder werden mit Standardwerten initialisiert. Ein [int](../../../csharp/language-reference/keywords/int.md)-Objekt wird beispielsweise auf 0 (null) initialisiert. Weitere Informationen zu Standardwerten finden Sie unter [Tabelle für Standardwerte](../../../csharp/language-reference/keywords/default-values-table.md). Da der Standardkonstruktor der `CoOrds`-Klasse alle Datenmember auf 0 (null) initialisiert, kann er komplett entfernt werden, ohne dass die Arbeitsweise der Klasse geändert wird. Unter Beispiel 1 weiter unten in diesem Thema finden Sie ein vollständiges Beispiel mit mehreren Konstruktoren. Unter Beispiel 2 finden Sie ein Beispiel für einen automatisch generierten Konstruktor.  
  
 Instanzkonstruktoren können ebenfalls dazu verwendet werden, die Instanzkonstruktoren von Basisklassen aufzurufen. Der Klassenkonstruktor kann den Konstruktor der Basisklasse mit dem Initialisierer wie folgt aufrufen:  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 In diesem Beispiel übergibt die `Circle`-Klasse die Werte des Radius und der Höhe an den Konstruktor, der von `Shape` bereitgestellt wird, von dem `Circle` abgeleitet wird. Unter Beispiel 3 in diesem Thema finden Sie ein vollständiges Beispiel mit `Shape` und `Circle`.  
  
## <a name="example-1"></a>Beispiel 1  
 Das folgende Beispiel veranschaulicht eine Klasse mit zwei Klassenkonstruktoren. Einer der Konstruktoren hat kein Argument und der andere verfügt über zwei.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Beispiel 2  
 In diesem Beispiel hat die `Person`-Klasse keine Konstruktoren. In einem solchen Fall wird automatisch ein Standardkonstruktor bereitgestellt, und die Felder werden auf ihre Standardwerte initialisiert.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Beachten Sie, dass der Standardwert von `age` `0` ist, und der Standardwert von `name` ist `null`. Weitere Informationen zu Standardwerten finden Sie unter [Tabelle für Standardwerte](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Beispiel 3  
 Im folgenden Beispiel wird die Verwendung vom Basisklasseninitialisierer veranschaulicht. Die `Circle`-Klasse wird von der allgemeinen Klasse `Shape` abgeleitet, und die `Cylinder`-Klasse wird von der `Circle`-Klasse abgeleitet. Der Konstruktor von jeder abgeleiteten Klasse verwendet deren Basisklasseninitialisierer.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Weitere Beispiele für das Aufrufen des Basisklassenkonstruktors finden Sie unter [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md) und [base](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Klassen und Strukturen](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktoren](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizer](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [static](../../../csharp/language-reference/keywords/static.md)
