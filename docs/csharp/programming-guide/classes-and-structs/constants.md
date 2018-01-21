---
title: Konstanten (C#-Programmierhandbuch)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81a085ff016fb9ee8f8a13167728c37ca799920a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="constants-c-programming-guide"></a>Konstanten (C#-Programmierhandbuch)
Konstanten sind unveränderliche Werte, die zur Kompilierzeit bekannt sind und sich während der Lebensdauer des Programms nicht ändern. Konstanten werden mit dem [const](../../../csharp/language-reference/keywords/const.md)-Modifizierer deklariert. Nur die in C# integrierten Typen (außer <xref:System.Object?displayProperty=nameWithType>) können als `const` deklariert werden. Eine Liste der integrierten Typen finden Sie unter [Tabelle integrierter Typen](../../../csharp/language-reference/keywords/built-in-types-table.md). Benutzerdefinierte Typen einschließlich Klassen, Strukturen und Arrays können nicht `const` sein. Verwenden Sie den [readonly](../../../csharp/language-reference/keywords/readonly.md)-Modifizierer zum Erstellen einer Klasse, einer Struktur oder eines Arrays, die/das zur Laufzeit einmal initialisiert wird (z.B. in einem Konstruktor) und danach nicht geändert werden kann.  
  
 C# unterstützt keine `const`-Methoden, -Eigenschaften oder -Ereignisse.  
  
 Der Enumerationstyp ermöglicht Ihnen das Definieren benannter Konstanten für ganzzahlige integrierte Typen (z.B. `int`, `uint`, `long` usw.). Weitere Informationen finden Sie unter [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Konstanten müssen initialisiert werden, wenn sie deklariert werden. Zum Beispiel:  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 In diesem Beispiel ist die Konstante `months` immer 12 und kann nicht einmal durch die Klasse selbst geändert werden. Wenn der Compiler einen konstanten Bezeichner im C#-Quellcode erkennt (z.B. `months`), ersetzt er den Literalwert direkt durch Code der Zwischensprache (Intermediate Language, IL), den er produziert. Da zur Laufzeit keine Variablenadresse einer Konstanten zugeordnet ist, können `const`-Felder nicht durch Verweis übergeben werden und können nicht als l-Wert in einem Ausdruck stehen.  
  
> [!NOTE]
>  Seien Sie vorsichtig beim Verweisen auf konstante Werte, die in anderem Code wie z.B. DLLs definiert sind. Wenn eine neue Version der DLL einen neuen Wert für die Konstante definiert, enthält das Programm weiterhin den alten Literalwert, bis es mit der neuen Version erneut kompiliert wird.  
  
 Mehrere Konstanten desselben Typs können zur gleichen Zeit deklariert werden wie zum Beispiel:  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 Der Ausdruck, mit dem eine Konstante initialisiert wird, kann auf eine andere Konstante verweisen, wenn dadurch kein Zirkelverweis entsteht. Zum Beispiel:  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Konstanten können als [öffentlich](../../../csharp/language-reference/keywords/public.md), [privat](../../../csharp/language-reference/keywords/private.md), [geschützt](../../../csharp/language-reference/keywords/protected.md), [intern](../../../csharp/language-reference/keywords/internal.md), [geschützt intern](../../../csharp/language-reference/keywords/protected-internal.md)oder [privat geschützt](../../../csharp/language-reference/keywords/private-protected.md) gekennzeichnet werden. Diese Zugriffsmodifizierer definieren, wie Benutzer der Klasse auf die Konstante zugreifen können. Weitere Informationen finden Sie unter [Zugriffsmodifizierer](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Auf Konstanten wird zugegriffen, als wären sie [statische](../../../csharp/language-reference/keywords/static.md) Felder, da der Wert der Konstante für alle Instanzen des Typs identisch ist. Sie verwenden nicht das `static`-Schlüsselwort, um sie zu deklarieren. Ausdrücke, die nicht in der Klasse enthalten sind, die die Konstante definiert, müssen den Klassennamen, einen Punkt und den Namen der Konstante verwenden, um auf die Konstante zuzugreifen. Zum Beispiel:  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a>C#-Programmiersprachenspezifikation  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Klassen und Strukturen](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Eigenschaften](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Typen](../../../csharp/programming-guide/types/index.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)  
 [Immutability in C# Part One: Kinds of Immutability (Unveränderlichkeit in C# Teil eins: Arten von Unveränderlichkeit)](http://go.microsoft.com/fwlink/?LinkId=112379)
