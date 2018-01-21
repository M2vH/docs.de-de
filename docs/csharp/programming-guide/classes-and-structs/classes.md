---
title: Klassen (C#-Programmierhandbuch)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: "40"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e810fc5a5397a6b9240346ac28505b11b1e817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="classes-c-programming-guide"></a>Klassen (C#-Programmierhandbuch)
Eine *Klasse* ist ein Konstrukt, das Ihnen ermöglicht, Ihre eigenen benutzerdefinierten Typen zu erstellen, indem Variablen anderer Typen, Methoden und Ereignisse zusammengefasst werden. Eine Klasse ist mit einem Entwurf vergleichbar. Sie definiert die Daten und das Verhalten eines Typs. Wenn die Klasse nicht als statisch deklariert ist, kann der Clientcode diese durch Erstellen von *Objekten* oder *Instanzen* verwenden, die einer Variable zugeordnet sind. Die Variable verbleibt im Arbeitsspeicher, bis alle Verweise darauf ihre Gültigkeit verlieren. Zu diesem Zeitpunkt markiert die CLR sie als geeignet für die Garbage Collection. Wenn die Klasse als [statisch](../../../csharp/language-reference/keywords/static.md) deklariert wird, existiert die einzige Kopie im Arbeitsspeicher, und der Clientcode kann nur über die Klasse selbst auf diesen zugreifen und nicht über eine *Instanzvariable*. Weitere Informationen finden Sie unter [Statische Klassen und statische Klassenmember](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Im Gegensatz zu Strukturen unterstützen Klassen die *Vererbung*, ein wesentliches Merkmal der objektorientierten Programmierung. Weitere Informationen finden Sie unter [Vererbung](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="declaring-classes"></a>Deklarieren von Klassen  
 Klassen werden mithilfe des Schlüsselworts [class](../../../csharp/language-reference/keywords/class.md) deklariert, so wie im folgenden Beispiel dargestellt:  
  
 [!code-csharp[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 Das `class`-Schlüsselwort wird der Zugriffsebene vorangestellt. Da [public](../../../csharp/language-reference/keywords/public.md) in diesem Fall verwendet wird, kann jede Person Objekte aus dieser Klasse erstellen. Der Name der Klasse folgt dem `class`-Schlüsselwort. Der Rest der Definition ist der Text einer Klasse, in dem das Verhalten und die Daten definiert sind. Felder, Eigenschaften, Methoden und Ereignisse für eine Klasse werden zusammen als *Klassenmember* bezeichnet.  
  
## <a name="creating-objects"></a>Erstellen von Objekten  
 Obwohl sie manchmal synonym werden, sind eine Klasse und ein Objekt unterschiedliche Dinge. Eine Klasse definiert einen Typ eines Objekts, aber es ist kein Objekt selbst. Ein Objekt ist eine konkrete Entität, basierend auf einer Klasse, und wird manchmal als Instanz einer Klasse bezeichnet.  
  
 Objekte können mithilfe des Schlüsselworts [new](../../../csharp/language-reference/keywords/new.md) erstellt werden, gefolgt vom Namen der Klasse, auf die das Objekt basiert, z.B.:  
  
 [!code-csharp[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 Wenn eine Instanz einer Klasse erstellt wird, wird ein Verweis auf das Objekt an den Programmierer übergeben. Im vorherigen Beispiel ist `object1` ein Verweis auf ein Objekt, das auf `Customer` basiert. Dieser Verweis bezieht sich auf das neue Objekt, enthält jedoch nicht die Objektdaten selbst. In der Tat können Sie einen Objektverweis erstellen, ohne ein Objekt zu erstellen:  
  
 [!code-csharp[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Es wird nicht empfohlen, einen Objektverweis wie diesen zu erstellen, der auf kein Objekt verweist. Der Versuch, auf ein Objekt über solch einen Verweis zuzugreifen, schlägt während der Laufzeit fehl. Allerdings kann ein solcher Verweis dazu veranlasst werden, auf ein Objekt zu verweisen, indem entweder ein neues Objekt erstellt wird oder indem es einem vorhandenen Objekt zugewiesen wird, z.B.:  
  
 [!code-csharp[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 Dieser Code erstellt zwei Objektverweise, die beide auf dasselbe Objekt verweisen. Aus diesem Grund werden alle Änderungen am Objekt, die über `object3` getätigt worden sind, bei nachfolgenden Verwendungen von `object4` berücksichtigt. Da auf Objekte, die auf Klassen basieren, durch Verweise zurückgegriffen werden, sind Klassen als Verweistypen bekannt.  
  
## <a name="class-inheritance"></a>Klassenvererbung  
 Die Vererbung erfolgt durch Verwendung einer *Ableitung*, d.h., dass eine Klasse mithilfe einer *Basisklasse* deklariert wird, aus der Sie Daten und das Verhalten erbt. Eine Basisklasse wird durch Anhängen eines Doppelpunkts sowie den Namen der Basisklasse angegeben, die dem abgeleiteten Klassennamen folgt, z.B.:  
  
 [!code-csharp[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Wenn eine Klasse eine Basisklasse deklariert, erbt sie alle Member der Basisklasse mit Ausnahme der Konstruktoren.  
  
 Anders als in C++ kann eine Klasse in C# nur direkt von einer Basisklasse erben. Da jedoch eine Basisklasse von einer anderen Klasse erben kann, kann eine Klasse indirekt von mehreren Basisklassen erben. Darüber hinaus kann eine Klasse mehr als eine Schnittstelle direkt implementieren. Weitere Informationen finden Sie unter [Schnittstellen](../../../csharp/programming-guide/interfaces/index.md).  
  
 Eine Klasse kann als [abstrakt](../../../csharp/language-reference/keywords/abstract.md) deklariert werden. Eine abstrakte Klasse enthält abstrakte Methoden, die über eine Signaturdefinition, aber keine Implementierung verfügen. Abstrakte Klassen dürfen nicht instanziiert werden. Sie können nur mithilfe von abgeleiteten Klassen verwendet werden, die die abstrakten Methoden implementieren. Im Gegensatz dazu lässt eine [versiegelte](../../../csharp/language-reference/keywords/sealed.md) Klasse nicht zu, dass andere Klassen von ihr ableiten. Weitere Informationen zu abstrakten Klassen finden Sie unter [Abstrakte und versiegelte Klassen und Klassenmember](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Klassendefinitionen können zwischen verschiedenen Quelldateien aufgeteilt werden. Weitere Informationen finden Sie unter [Partielle Klassen und Methoden](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="description"></a>Beschreibung  
 Im folgenden Beispiel wird eine öffentliche Klasse definiert, die ein einzelnes Feld, eine Methode und eine spezielle Methode namens Konstruktor enthält. Weitere Informationen finden Sie unter [Konstruktoren](../../../csharp/programming-guide/classes-and-structs/constructors.md). Die Klasse wird mit dem Schlüsselwort `new` instanziiert.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>C#-Programmiersprachenspezifikation  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Objektorientierte Programmierung](../concepts/object-oriented-programming.md)  
 [Polymorphismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Mitglieder](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [Methoden](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Konstruktoren](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizer](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Objekte](../../../csharp/programming-guide/classes-and-structs/objects.md)
