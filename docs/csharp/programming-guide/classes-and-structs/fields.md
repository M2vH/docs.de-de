---
title: Felder (C#-Programmierhandbuch)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: acf4ade68235a196fd6d2f3c6c71279748f3dd71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="fields-c-programming-guide"></a>Felder (C#-Programmierhandbuch)
Ein *Feld* ist eine Variable eines beliebigen Typs, die direkt in einer [class](../../../csharp/language-reference/keywords/class.md) oder [struct](../../../csharp/language-reference/keywords/struct.md) deklariert ist. Felder sind *Member* Ihres enthaltenden Typs.  
  
 Eine Klasse oder Struktur kann möglicherweise über Instanzenfelder, statische Felder oder beides verfügen. Instanzfelder sind für eine Instanz eines Typs spezifisch. Wenn Sie eine Klasse T mit einem Instanzfeld F haben, können Sie zwei Objekte vom Typ T erstellen und den Wert von F in jedem Objekt ändern, ohne dabei den Wert in dem anderen Objekt zu beeinflussen. Im Gegensatz dazu gehört ein statisches Feld zur Klasse selbst und wird in allen Instanzen dieser Klasse gemeinsam verwendet. Änderungen, die von der Instanz A vorgenommen wurden, werden für die Instanzen B und C direkt sichtbar, sobald sie auf das Feld zugreifen.  
  
 Im Allgemeinen sollten Sie Felder nur für Variablen verwenden, die private oder geschützte Zugriffsmöglichkeiten haben. Daten, die Ihre Klasse für Clientcode verfügbar macht, sollten über [Methoden](../../../csharp/programming-guide/classes-and-structs/methods.md), [Eigenschaften](../../../csharp/programming-guide/classes-and-structs/properties.md) und [Indexer](../../../csharp/programming-guide/indexers/index.md) bereitgestellt werden. Sie können sich mit diesen Konstrukten für indirekten Zugriff auf interne Felder vor ungültigen Eingabewerten schützen. Ein privates Feld, das über eine öffentliche Eigenschaft bereitgestellte Daten speichert, wird als *Sicherungsspeicher* oder *Unterstützungsfeld* bezeichnet.  
  
 Felder speichern in der Regel die Daten, die über Zugriff auf mehr als eine Klassenmethode verfügen müssen und länger als die Lebensdauer einer einzelnen Methode gespeichert werden müssen. Z.B. verfügt eine Klasse, die ein Kalenderdatum darstellt, möglicherweise über drei Felder: Jeweils eines für Monat, Tag und Jahr. Variablen, die außerhalb des Bereichs einer einzelnen Methode nicht verwendet werden, sollten als *lokale Variablen* innerhalb des Methodentexts selbst deklariert werden.  
  
 Felder werden innerhalb des Class-Blocks deklariert, indem Sie die Zugriffsebene des Felds, gefolgt vom Typ des Felds, gefolgt vom Namen des Felds angeben. Zum Beispiel:  
  
 [!code-csharp[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Um auf ein Feld in einem Objekt zuzugreifen, fügen Sie einen Punkt hinter dem Objektnamen ein, gefolgt vom Namen des Felds, wie in `objectname.fieldname`. Zum Beispiel:  
  
 [!code-csharp[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Einem Feld kann ein Anfangswert durch Verwendung des Zuweisungsoperators zugewiesen werden, wenn das Feld deklariert wird. Sie würden z.B. `day` wie im folgenden Beispiel deklarieren, um das `day`-Feld automatisch `"Monday"` zuzuweisen:  
  
 [!code-csharp[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Felder werden umgehend initialisiert, bevor der Konstruktor für die Objektinstanz aufgerufen wird. Wenn der Konstruktor den Wert eines Felds zuweist, überschreibt er jeden während der Felddeklaration angegebenen Wert. Weitere Informationen finden Sie unter [Verwenden von Konstruktoren](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Ein Feldinitialisierer kann nicht auf andere Instanzfelder verweisen.  
  
 Felder können als [öffentlich](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [geschützt](../../../csharp/language-reference/keywords/protected.md), [intern](../../../csharp/language-reference/keywords/internal.md), [geschützt intern](../../../csharp/language-reference/keywords/protected-internal.md) oder [privat geschützt](../../../csharp/language-reference/keywords/private-protected.md) deklariert werden. Diese Zugriffsmodifizierer definieren, wie Benutzer der Klasse auf die Felder zugreifen können. Weitere Informationen finden Sie unter [Zugriffsmodifizierer](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Ein Feld kann optional als [static](../../../csharp/language-reference/keywords/static.md) deklariert werden. Dadurch steht das Feld Aufrufern jederzeit zur Verfügung, auch wenn keine Instanz der Klasse vorhanden ist. Weitere Informationen finden Sie unter [Statische Klassen und statische Klassenmember](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Ein Feld kann als [readonly](../../../csharp/language-reference/keywords/readonly.md) deklariert werden. Einem schreibgeschützten Feld kann nur ein Wert während der Initialisierung oder in einem Konstruktor zugewiesen werden. Ein `static``readonly`-Feld ist einer Konstanten sehr ähnlich, außer dass der C#-Compiler nicht auf den Wert eines statischen schreibgeschützten Felds zur Kompilierzeit, sondern nur zur Laufzeit zugreifen kann. Weitere Informationen finden Sie unter [Konstanten](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>C#-Programmiersprachenspezifikation  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Klassen und Strukturen](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Verwenden von Konstruktoren](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Vererbung](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Zugriffsmodifizierer](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Abstrakte und versiegelte Klassen und Klassenmember](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
