---
title: Implementieren von IEnumerable in Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45b4008f0bf3ae0f303aa029e7bff5b82ab6f259
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Exemplarische Vorgehensweise: Implementieren von IEnumerable(Of T) in Visual Basic
Die <xref:System.Collections.Generic.IEnumerable%601> Schnittstelle wird implementiert von Klassen, die eine Sequenz von Werten eines Elements zu einem Zeitpunkt zurückgeben können. Der Vorteil der Rückgabe von Daten an ein Element zu einem Zeitpunkt liegt darin, dass Sie nicht verfügen, laden Sie den vollständigen Satz von Daten in den Arbeitsspeicher, um damit zu arbeiten. Sie müssen nur ausreichend Arbeitsspeicher verwenden, um ein einzelnes Element aus den Daten zu laden. Klassen, in denen die `IEnumerable(T)` Schnittstelle verwendet werden kann, mit `For Each` Schleifen oder LINQ-Abfragen.  
  
 Betrachten Sie beispielsweise eine Anwendung, die eine große Textdatei lesen muss, und jede Zeile aus der Datei, die bestimmten Suchkriterien entspricht zurückzugeben. Die Anwendung verwendet eine LINQ-Abfrage zurückzugebenden Zeilen aus der Datei, die die angegebenen Kriterien entsprechen. Um den Inhalt der Datei mit einer LINQ-Abfrage Abfragen, konnte die Anwendung den Inhalt der Datei in ein Array oder eine Auflistung laden. Laden die gesamte Datei in ein Array- oder Auflistungselement belegen jedoch würde wesentlich mehr Arbeitsspeicher als erforderlich ist. Die LINQ-Abfrage konnte stattdessen den Inhalt der Datei mit Abfragen eine enumerable-Klasse, nur Werte zurückgeben, die den Suchkriterien entsprechen. Abfragen, die nur einige übereinstimmende Werte würde viel weniger Arbeitsspeicher beansprucht.  
  
 Sie können eine Klasse, die implementiert erstellen die <xref:System.Collections.Generic.IEnumerable%601> Schnittstelle, um die Quelldaten als aufzählbare Daten verfügbar zu machen. Die Klasse, die implementiert die `IEnumerable(T)` Schnittstelle erfordern eine andere Klasse, die implementiert die <xref:System.Collections.Generic.IEnumerator%601> Schnittstelle zum Durchlaufen der Quelldaten. Diese beiden Klassen können Sie Datenelemente sequenziell als bestimmten Typ zurückgeben.  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie eine Klasse, implementiert die `IEnumerable(Of String)` Schnittstelle und eine Klasse, implementiert die `IEnumerator(Of String)` Schnittstelle, um eine Text zu einem Zeitpunkt zu lesen.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Erstellen der Enumerable-Klasse  
  
|Zum Erstellen des Projekts enumerable-Klasse|  
|---|  
|1.  Zeigen Sie in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.<br />2.  Überprüfen Sie, ob im Dialogfeld **Neues Projekt** im Bereich **Projekttypen** der Eintrag **Windows** ausgewählt ist. Wählen Sie im Bereich **Vorlagen** die Option **Klassenbibliothek** aus. Geben Sie im Feld **Name** die Bezeichnung `StreamReaderEnumerable` ein, und klicken Sie dann auf **OK**. Das neue Projekt wird angezeigt.<br />3.  In **Projektmappen-Explorer**mit der rechten Maustaste auf die Datei Class1.vb, und klicken Sie auf **umbenennen**. Benennen Sie die Datei in `StreamReaderEnumerable.vb` um, und drücken Sie die EINGABETASTE. Durch Umbenennen der Datei wird die Klasse ebenfalls in `StreamReaderEnumerable` umbenannt. Diese Klasse implementiert die `IEnumerable(Of String)`-Schnittstelle.<br />4.  Mit der rechten Maustaste des Projekts StreamReaderEnumerable, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**. Wählen Sie die **Klasse** Vorlage. In der **Namen** geben `StreamReaderEnumerator.vb` , und klicken Sie auf **OK**.|  
  
 Die erste Klasse in diesem Projekt wird die enumerable-Klasse und Implementieren der `IEnumerable(Of String)` Schnittstelle. Diese generische Schnittstelle implementiert, die <xref:System.Collections.IEnumerable> -Schnittstelle. zudem ist gewährleistet, dass Consumer dieser Klasse als eingegebene Werte zugreifen können `String`.  
  
|So fügen Sie den Code, um die "IEnumerable" implementieren hinzu|  
|---|  
|1.  Öffnen Sie die Datei StreamReaderEnumerable.vb.<br />2.  In der Zeile nach `Public Class StreamReaderEnumerable`, geben Sie Folgendes ein, und drücken Sie die EINGABETASTE.<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]füllt automatisch die Klasse mit den Elementen, die erforderlich sind die `IEnumerable(Of String)` Schnittstelle.<br />3.  Diese Klasse aufzählbare gelesenen Zeilen aus einer Textdatei zeilenweise zu einem Zeitpunkt. Fügen Sie den folgenden Code, um die Klasse einen öffentlichen Konstruktor verfügbar machen, der einen Dateipfad als Eingabeparameter akzeptiert.<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  Ihre Implementierung von der <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Methode der `IEnumerable(Of String)` Schnittstelle wird eine neue Instanz der Zurückgeben der `StreamReaderEnumerator` Klasse. Die Implementierung von der `GetEnumerator` Methode der `IEnumerable` Schnittstelle erfolgen `Private`, da Sie nur Member verfügbar machen müssen die `IEnumerable(Of String)` Schnittstelle. Ersetzen Sie den Code, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] für generiert die `GetEnumerator` Methoden mit den folgenden Code.<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|So fügen Sie den Code zum Implementieren von IEnumerator hinzu|  
|---|  
|1.  Öffnen Sie die Datei StreamReaderEnumerator.vb.<br />2.  In der Zeile nach `Public Class StreamReaderEnumerator`, geben Sie Folgendes ein, und drücken Sie die EINGABETASTE.<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]füllt automatisch die Klasse mit den Elementen, die erforderlich sind die `IEnumerator(Of String)` Schnittstelle.<br />3.  Die Enumeratorklasse öffnet die Textdatei und führt die Datei-e/a auf die Zeilen aus der Datei zu lesen. Fügen Sie den folgenden Code, auf die Klasse zur Verfügung stellen einen öffentlichen Konstruktor, der einen Dateipfad als Eingabeparameter akzeptiert und die Textdatei zum Lesen öffnen.<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  Die `Current` für beide Eigenschaften der `IEnumerator(Of String)` und `IEnumerator` Schnittstellen zurückgeben, die das aktuelle Element aus der Textdatei als eine `String`. Die Implementierung von der `Current` Eigenschaft der `IEnumerator` Schnittstelle erfolgen `Private`, da Sie nur Member verfügbar machen müssen die `IEnumerator(Of String)` Schnittstelle. Ersetzen Sie den Code, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] für generiert die `Current` Eigenschaften mit den folgenden Code.<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  Die `MoveNext` Methode der `IEnumerator` Schnittstelle navigiert zum nächsten Element in der Textdatei und aktualisiert den Wert, der von zurückgegeben wird die `Current` Eigenschaft. Wenn es keine Elemente mehr sind zu lesen, die `MoveNext` -Methode zurückkehrt `False`andernfalls die `MoveNext` -Methode zurückkehrt `True`. Fügen Sie der `MoveNext` -Methode folgenden Code hinzu.<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  Die `Reset` Methode der `IEnumerator` Schnittstelle weist den Iterator auf den Anfang der Datei und löscht den aktuellen Elementwert. Fügen Sie der `Reset` -Methode folgenden Code hinzu.<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  Die `Dispose` Methode der `IEnumerator` Schnittstelle garantiert, dass alle nicht verwaltete Ressourcen freigegeben werden, bevor der Iterator zerstört wird. Das Dateihandle, mit der die `StreamReader` -Objekt ist eine nicht verwaltete Ressource und muss geschlossen werden, bevor die Iteratorinstanz zerstört wird. Ersetzen Sie den Code, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] für generiert die `Dispose` -Methode durch folgenden Code.<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>Mithilfe des Beispieliterators  
 Sie können eine enumerable-Klasse in Ihrem Code zusammen mit Steuerungsstrukturen, die ein Objekt erfordern, die implementiert `IEnumerable`, z. B. eine `For Next` Schleife oder einer LINQ-Abfrage. Das folgende Beispiel zeigt die `StreamReaderEnumerable` in einer LINQ-Abfrage.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Ablaufsteuerung](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Schleifenstruktur](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For Each...Next-Anweisung](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
