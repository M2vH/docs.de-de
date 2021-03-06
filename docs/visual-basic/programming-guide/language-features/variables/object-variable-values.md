---
title: Werte von Objektvariablen (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccab22920923500a2332db2372e52813c890e5e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-values-visual-basic"></a>Werte von Objektvariablen (Visual Basic)
Eine Variable, der die [Object-Datentyp](../../../../visual-basic/language-reference/data-types/object-data-type.md) kann auf Daten eines beliebigen Typs verweisen. Der Wert, die Sie, in speichern eine `Object` Variable wird an anderer Stelle im Arbeitsspeicher beibehalten, während die Variable selbst einen Zeiger auf die Daten enthält.  
  
## <a name="object-classifier-functions"></a>Objekt-Klassifizierungsfunktionen  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]enthält Funktionen, Zurückgeben von Informationen darüber, was, eine `Object` Variable verweist auf, wie in der folgenden Tabelle gezeigt.  
  
|Funktion|Gibt True zurück, wenn auf die Objektvariable verweist|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Ein Array von Werten, anstatt einen einzelnen Wert|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Ein [Datumsdatentyp](../../../../visual-basic/language-reference/data-types/date-data-type.md) Wert oder eine Zeichenfolge, die als Wert für Datum und Uhrzeit interpretiert werden kann|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Ein Objekt des Typs <xref:System.DBNull>, der fehlende oder nicht vorhandene Daten darstellt|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Ein Exception-Objekt, das von abgeleitet ist<xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nichts](../../../../visual-basic/language-reference/nothing.md), d. h. kein Objekt auf die Variable derzeit zugewiesen ist|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Eine Zahl oder eine Zeichenfolge, die als Zahl interpretiert werden kann|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Ein Verweistyp (z. B. eine Zeichenfolge, Array, Delegat oder Klassentyp)|  
  
 Diese Funktionen können Sie vermeiden, senden einen ungültigen Wert für einen Vorgang oder einer Prozedur.  
  
## <a name="typeof-operator"></a>Operator TypeOf  
 Sie können auch die [TypeOf-Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) zu bestimmen, ob eine Objektvariable gegenwärtig auf einen bestimmten Datentyp verweist. Die `TypeOf`... `Is` Ausdruck wird zu `True` , wenn der Laufzeittyp des Operanden abgeleitet wird, oder den angegebenen Typ implementiert.  
  
 Im folgenden Beispiel wird `TypeOf` in Objektvariablen verweisen auf Wert-und Verweistypen.  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 Im obige Beispiel schreibt die folgenden Zeilen, die die **Debuggen** Fenster:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Die Objektvariable `num` bezieht sich auf die Daten des Typs `Integer`, und `frm` bezieht sich auf ein Objekt der Klasse <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Objektarrays  
 Sie können deklarieren und verwenden Sie ein Array von `Object` Variablen. Dies ist hilfreich, wenn Sie eine Vielzahl von Datentypen und Objektklassen behandeln müssen. Alle Elemente in einem Array müssen den gleichen deklarierten Datentyp haben. Dieser Datentyp als deklarieren `Object` können Sie zum Speichern von Objekten und-Klasseninstanzen zusammen mit anderen Datentypen in das Array.  
  
## <a name="see-also"></a>Siehe auch  
 [Objektvariablen](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklaration von Objektvariablen](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Zuweisen von Objektvariablen](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Gewusst wie: Verweisen auf die aktuelle Instanz eines Objekts](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Gewusst wie: Bestimmen des Typs, auf den eine Objektvariable verweist](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Gewusst wie: Bestimmen des Bezugs zwischen zwei Objekten](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Gewusst wie: Bestimmen der Gleichheit zweier Objekte](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [Datentypen](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
