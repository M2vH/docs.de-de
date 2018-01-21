---
title: Verwenden von Strukturen (C#-Programmierhandbuch)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94181c42ce913dc76c9a074e4bcbb8240764c896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="using-structs-c-programming-guide"></a>Verwenden von Strukturen (C#-Programmierhandbuch)
Der `struct` -Typ eignet sich für die Darstellung von kompakten Objekten, z. B. `Point`, `Rectangle`und `Color`. Obwohl es ebenso einfach ist, einen Punkt als [Klasse](../../../csharp/language-reference/keywords/class.md) mit [automatisch implementierten Eigenschaften](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) darzustellen, kann eine [Struktur](../../../csharp/language-reference/keywords/struct.md) in verschiedenen Szenarien effizienter sein. Bei der Deklaration eines Arrays mit 1.000 `Point` -Objekten belegen Sie z. B. zusätzlichen Arbeitsspeicher, damit auf jedes Objekt verwiesen werden kann. In diesem Fall wäre eine Struktur weniger speicherintensiv. Da das [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ein Objekt mit dem Namen <xref:System.Drawing.Point> enthält, wird die Struktur in diesem Beispiel stattdessen „CoOrds“ genannt.  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Die Definition eines (parameterlosen) Standardkonstruktors für eine Struktur verursacht einen Fehler. Auch durch die Initialisierung eines Instanzenfelds in einem Strukturtext wird ein Fehler generiert. Sie können extern zugängliche Strukturmember nur mithilfe eines parametrisierten Konstruktors,  mit dem impliziten Standardkonstruktor, oder mit einem [Objektinitialisierer](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  initialisieren, oder durch Zugriff auf einzelne Member, nachdem die Struktur deklariert ist. Alle privaten oder auf andere Weise gesperrten Member erfordern ausschließlich die Verwendung von Konstruktoren.
  
 Beim Instanziieren einer Struktur mit dem [new](../../../csharp/language-reference/keywords/new.md) Operator wird eine Struktur erstellt und der entsprechende Konstruktor wird,  gemäß der [Signatur des Konstruktors](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax), aufgerufen. Strukturen können im Gegensatz zu Klassen ohne den Operator `new` instanziiert werden. In einem solchen Fall gibt es keinen Konstruktoraufruf, sodass die Zuordnung effizienter ausgeführt werden kann. Die Felder werden jedoch nicht zugewiesen, und das Objekt kann erst verwendet werden, nachdem alle Felder initialisiert wurden. Dies schließt die Unfähigkeit in Bezug auf Abrufen oder Festlegen von Werten über automatisch implementierte Eigenschaften mit ein.
 
 Wenn Sie ein Struktur-Objekt mit dem standardmäßigen, parameterlosen Konstruktor instanziiert haben, werden allen Membern ihre  [Standardwerte](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) zugewiesen.
  
 Wenn Sie für eine Struktur einen Konstruktor mit Parametern schreiben, müssen Sie alle Elemente explizit initialisieren; andernfalls sind ein oder mehrere Member nicht zugewiesen, und die Struktur kann nicht verwendet werden, was einen Compilerfehler CS0171 erzeugt.  
  
 Bei Strukturen findet keine Vererbung wie bei Klassen statt. Eine Struktur kann nicht von einer anderen Struktur oder Klasse erben, und sie kann auch nicht die Basis einer Klasse sein. Stattdessen erben Strukturen von der <xref:System.Object>-Basisklasse. Eine Struktur kann Schnittstellen implementieren. Dies geschieht auf dieselbe Weise wie bei Klassen.  
  
 Sie können keine Klasse mit dem `struct`-Schlüsselwort deklarieren. Klassen und Strukturen weisen in C# semantische Unterschiede auf. Eine Struktur ist ein Werttyp, während eine Klasse ein Verweistyp ist. Weitere Informationen finden Sie unter [Verweistypen](../../../csharp/language-reference/keywords/reference-types.md) und [Werttypen](../../../csharp/language-reference/keywords/value-types.md).  
  
 Sofern keine Semantik für Verweistypen benötigt wird, kann das System kleine Klassen effizienter verarbeiten, wenn diese als Struktur definiert werden.  
  
## <a name="example-1"></a>Beispiel 1  
  
### <a name="description"></a>Beschreibung  
 In diesem Beispiel wird die `struct` -Initialisierung sowohl unter Verwendung von Standardkonstruktoren als auch unter Verwendung von parametrisierten Konstruktoren veranschaulicht.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Beispiel 2  
  
### <a name="description"></a>Beschreibung  
 Dieses Beispiel veranschaulicht ein Feature, das ausschließlich auf Strukturen anwendbar ist. Es wird ein CoOrds-Objekt ohne Verwendung des Operators `new` erstellt. Wenn Sie den Begriff `struct` durch `class`ersetzen, wird das Programm nicht kompiliert.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Klassen und Strukturen](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Strukturen](../../../csharp/programming-guide/classes-and-structs/structs.md)
