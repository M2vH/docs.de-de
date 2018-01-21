---
title: Polymorphismus (C#-Programmierhandbuch)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 601c8cf626c846ca6c5d6bc2338e271e6b93544a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="polymorphism-c-programming-guide"></a>Polymorphismus (C#-Programmierhandbuch)
Polymorphismus wird häufig nach der Kapselung und der Vererbung als die dritte Säule der objektorientierten Programmierung bezeichnet. Es handelt sich dabei um ein griechisches Wort, das "Vielgestaltigkeit" bedeutet und zwei verschiedene Aspekte umfasst:  
  
-   In Methodenparametern, Auflistungen und Arrays können Objekte einer abgeleiteten Klasse zur Laufzeit als Objekte einer Basisklasse behandelt werden. In diesem Fall ist der deklarierte Typ des Objekts nicht mehr mit dem Laufzeittyp identisch.  
  
-   Basisklassen können [virtuelle](../../../csharp/language-reference/keywords/virtual.md) *Methoden* definieren und implementieren und können von abgeleiteten Klassen [überschrieben](../../../csharp/language-reference/keywords/override.md) werden, was bedeutet, dass sie ihre eigene Definition und Implementierung bereitstellen. Zur Laufzeit, wenn die Methode von Clientcode aufgerufen wird, sucht die CLR den Laufzeittyp des Objekts und ruft die Überschreibung der virtuellen Methode auf. In Ihrem Quellcode können Sie daher eine Methode in einer Basisklasse aufrufen und bewirken, dass die Methodenversion der abgeleiteten Klasse ausgeführt wird.  
  
 Dank virtueller Methoden können Sie auf einheitliche Weise mit Gruppen verwandter Objekte arbeiten. Nehmen Sie beispielsweise an, Sie haben eine Zeichenanwendung, mit der ein Benutzer verschiedene Arten von Formen auf einer Zeichenoberfläche erstellen kann. Zur Kompilierzeit wissen Sie nicht, welche spezifischen Typen von Formen der Benutzer erstellen wird. Die Anwendung muss jedoch alle verschiedenen Formentypen, die erstellt werden, nachverfolgen und diese als Antwort auf die Mausaktionen des Benutzers aktualisieren. Sie können Polymorphismus verwenden, um dieses Problem mithilfe von zwei einfachen Schritten zu lösen:  
  
1.  Erstellen Sie eine Klassenhierarchie, in der jede spezifische Formenklasse von einer gemeinsamen Basisklasse abgeleitet wird.  
  
2.  Verwenden Sie eine virtuelle Methode, um die entsprechende Methode in einer abgeleiteten Klasse durch einen einzigen Aufruf der Basisklassenmethode aufzurufen.  
  
 Erstellen Sie zuerst eine Basisklasse namens `Shape` und abgeleitete Klassen, wie z. B. `Rectangle`, `Circle` und `Triangle`. Geben Sie der `Shape`-Klasse eine virtuelle Methode namens `Draw`, und überschreiben Sie sie in jeder abgeleiteten Klasse, um die jeweilige Form zu zeichnen, die die Klasse darstellt. Erstellen Sie ein `List<Shape>`-Objekt und fügen Sie einen Kreis, ein Dreieck und ein Rechteck hinzu. Um die Zeichenoberfläche zu aktualisieren, verwenden Sie eine [foreach](../../../csharp/language-reference/keywords/foreach-in.md)-Schleife, um die Liste zu durchlaufen und die `Draw`-Methode für jedes `Shape`-Objekt in der Liste aufzurufen. Obwohl jedes Objekt in der Liste einen deklarierten `Shape`-Typ aufweist, wird der Laufzeittyp (die überschriebene Version der Methode in jeder abgeleiteten Klasse) aufgerufen.  
  
 [!code-csharp[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]  
  
 In C# ist jeder Typ polymorph, da alle Typen, einschließlich benutzerdefinierten Typen, von <xref:System.Object> erben.  
  
## <a name="polymorphism-overview"></a>Übersicht über Polymorphismus  
  
### <a name="virtual-members"></a>Virtuelle Member  
 Wenn eine abgeleitete Klasse von einer Basisklasse erbt, erhält sie alle Methoden, Felder, Eigenschaften und Ereignisse der Basisklasse. Der Designer der abgeleiteten Klassen kann entscheiden, ob:  
  
-   virtuelle Member in der Basisklasse überschrieben werden sollen  
  
-   die nächste Basisklassenmethoden ohne Überschreiben vererbt werden soll,  
  
-   neue nicht virtuelle Implementierungen der Member definiert werden sollen, die die Basisklassenimplementierungen verbergen.  
  
 Eine abgeleitete Klasse kann einen Basisklassenmember nur überschreiben, wenn der Basisklassenmember als [virtuell](../../../csharp/language-reference/keywords/virtual.md) oder [abstrakt](../../../csharp/language-reference/keywords/abstract.md) deklariert ist. Der abgeleitete Member muss das [override](../../../csharp/language-reference/keywords/override.md)-Schlüsselwort verwenden, um explizit anzugeben, dass die Methode an dem virtuellen Aufruf beteiligt sein soll. Der folgende Code veranschaulicht dies:  
  
 [!code-csharp[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]  
  
 Felder können nicht virtuell sein; nur Methoden, Eigenschaften, Ereignisse und Indexer können virtuell sein. Wenn eine abgeleitete Klasse einen virtuellen Member überschreibt, wird dieser Member auch dann aufgerufen, wenn auf eine Instanz dieser Klasse als Instanz der Basisklasse zugegriffen wird. Der folgende Code veranschaulicht dies:  
  
 [!code-csharp[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]  
  
 Mithilfe virtueller Methoden und Eigenschaften können abgeleitete Klassen eine Basisklasse erweitern, ohne die Basisklassenimplementierung einer Methode verwenden zu müssen. Weitere Informationen finden Sie unter [Versionsverwaltung mit den Schlüsselwörtern „override“ und „new“](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md). Eine Schnittstelle bietet eine weitere Möglichkeit zur Definition einer Methode bzw. einer Gruppe von Methoden, deren Implementierung von abgeleiteten Klassen übernommen wird. Weitere Informationen finden Sie unter [Schnittstellen](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Ausblenden von Basisklassenmembern für neue Member  
 Wenn Sie möchten, dass der abgeleitete Member denselben Namen wie ein Member in einer Basisklasse aufweist, jedoch nicht möchten, dass dieser an dem virtuellen Aufruf beteiligt ist, können Sie das [new](../../../csharp/language-reference/keywords/new.md)-Schlüsselwort verwenden. Das `new`-Schlüsselwort wird dem Rückgabetyp eines Klassenmembers vorangestellt, der ersetzt wird. Der folgende Code veranschaulicht dies:  
  
 [!code-csharp[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]  
  
 Auf ausgeblendete Klassenmember kann vom Clientcode immer noch zugegriffen werden, indem die Instanz der abgeleiteten Klasse in eine Instanz der Basisklasse umgewandelt wird. Beispiel:  
  
 [!code-csharp[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Verhindern, dass abgeleitete Klassen virtuelle Member überschreiben  
 Virtuelle Member bleiben praktisch unendlich erhalten, unabhängig davon, wie viele Klassen zwischen dem virtuellen Member und der Klasse deklariert wurden, die diesen ursprünglich deklariert hat. Wenn Klasse A einen virtuellen Member deklariert und Klasse B von A erbt und Klasse C von B erbt, so erbt C den virtuellen Member und hat die Option, diesen zu überschreiben, unabhängig davon, ob Klasse B das Überschreibung für diesen Member deklariert hat. Der folgende Code veranschaulicht dies:  
  
 [!code-csharp[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]  
  
 Eine abgeleitete Klasse kann die virtuelle Vererbung stoppen, indem das Überschreiben als [versiegelt](../../../csharp/language-reference/keywords/sealed.md) deklariert wird. Hierfür muss das `sealed`-Schlüsselwort in der Klassenmemberdeklaration vor das `override`-Schlüsselwort gestellt werden. Der folgende Code veranschaulicht dies:  
  
 [!code-csharp[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]  
  
 Im vorherigen Beispiel ist die Methode `DoWork` für jede von C abgeleitete Klasse nicht mehr virtuell. Sie ist weiterhin virtuell für Instanzen von C, selbst wenn diese in Typ B oder Typ A umgewandelt werden. Versiegelte Methoden können, wie im folgenden Beispiel gezeigt, mithilfe des `new`-Schlüsselworts durch abgeleitete Klassen ersetzt werden:  
  
 [!code-csharp[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]  
  
 In diesem Fall wird, wenn `DoWork` für D mithilfe einer Variablen vom Typ D aufgerufen wird, das neue `DoWork` aufgerufen. Wenn eine Variable vom Typ C, B oder A zum Zugreifen auf eine Instanz von D verwendet wird, befolgt ein Aufruf von `DoWork` die Regeln der virtuellen Vererbung, und diese Aufrufe werden an die Implementierung von `DoWork` für Klasse C weitergeleitet.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Zugreifen auf virtuelle Basisklassenmember von abgeleiteten Klassen aus  
 Eine abgeleitete Klasse, die eine Methode oder Eigenschaft ersetzt oder überschrieben hat, kann immer noch auf die Methode oder Eigenschaft in der Basisklasse mithilfe des base-Schlüsselworts zugreifen. Der folgende Code veranschaulicht dies:  
  
 [!code-csharp[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]  
  
 Weitere Informationen finden Sie unter [base](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass virtuelle Member `base` verwenden, um die Basisklassenimplementierung dieses Members in seiner eigenen Implementierung aufzurufen. Durch Zulassen des Basisklassenverhaltens kann sich die abgeleitete Klasse auf die Implementierung von Verhalten konzentrieren, das spezifisch für die abgeleitete Klasse ist. Wenn die Basisklassenimplementierung nicht aufgerufen wird, liegt es an der abgeleiteten Klasse, ihr Verhalten kompatibel mit dem Verhalten der Basisklasse zu gestalten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Versionsverwaltung mit den Schlüsselwörtern "override" und "new"](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Wann müssen die Schlüsselwörter "override" und "new" verwendet werden?](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Gewusst wie: Überschreiben der ToString-Methode](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Vererbung](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Abstrakte und versiegelte Klassen und Klassenmember](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Methoden](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Ereignisse](../../../csharp/programming-guide/events/index.md)  
 [Eigenschaften](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Indexer](../../../csharp/programming-guide/indexers/index.md)  
 [Typen](../../../csharp/programming-guide/types/index.md)
