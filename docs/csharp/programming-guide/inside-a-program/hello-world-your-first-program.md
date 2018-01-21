---
title: "Hello World – Ihr erstes Programm (C#-Programmierhandbuch)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17dcce921f3a6ff1a9c547c5ff5d34c3dbbf28d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World – Ihr erstes Programm (C#-Programmierhandbuch)
Die folgende Prozedur erstellt eine C#-Version des herkömmlichen „Hallo Welt!“ -Programms. Das Programm zeigt die Zeichenfolge `Hello World!` an.  
  
 Weitere Beispiele zu einführenden Konzepten finden Sie unter [Erste Schritte mit Visual C# und Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>So erstellen Sie eine neue Konsolenanwendung und führen diese aus  
  
1.  Starten Sie Visual Studio.  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Erweitern Sie nacheinander **Installiert**, **Vorlagen**, **Visual C#**, und wählen Sie dann **Konsolenanwendung** aus.  
  
4.  Geben Sie im Feld **Name** einen Namen für das Projekt an, und klicken Sie dann auf die Schaltfläche **OK**.  
  
     Das neue Projekt wird im **Projektmappen-Explorer** angezeigt.  
  
5.  Wenn „Program.cs“ im **Code-Editor** nicht geöffnet ist, öffnen Sie das Kontextmenü für **Program.cs** im **Projektmappen-Explorer**, und wählen Sie dann **Code anzeigen** aus.  
  
6.  Ersetzen Sie den Inhalt von Program.cs durch den folgenden Code.  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Drücken Sie die Taste F5, um das Projekt auszuführen. Ein Eingabeaufforderungsfenster wird angezeigt, das die Zeile `Hello World!` enthält  
  
 Im nächsten Schritt werden die wichtigen Bereiche des Programms überprüft.  
  
## <a name="comments"></a>Kommentare  
 Die erste Zeile enthält einen Kommentar. Durch die Zeichen `//` wird die restliche Zeile in einen Kommentar konvertiert.  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 Sie können auch einen Kommentar aus einem Textblock einfügen, indem Sie ihn zwischen den Zeichen `/*` und `*/` einschließen. Dies wird im folgenden Beispiel gezeigt.  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Die 'Main'-Methode  
 Eine C#-Konsolenanwendung muss eine `Main`-Methode enthalten, in der die Steuerung beginnt und endet. Innerhalb der `Main`-Methode erstellen Sie Objekte und führen andere Methoden aus.  
  
 Bei der `Main`-Methode handelt es sich um eine [statische](../../../csharp/language-reference/keywords/static.md) Methode, die sich innerhalb einer Klasse oder Struktur befindet. Im vorherigen „Hello World!“-Beispiel befindet sie sich in einer Klasse namens `Hello`. Sie können die `Main`-Methode auf eine der folgenden Arten deklarieren:  
  
-   Es kann `void` zurückgegeben werden.  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Zudem kann eine ganze Zahl zurückgegeben werden.  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Bei beiden Rückgabetypen können Argumente verwendet werden.  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     - oder -   
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 Der Parameter der `Main`-Methode, `args`, ist ein `string`-Array, das die Befehlszeilenargumente enthält, die zum Aufrufen des Programms verwendet werden. Im Gegensatz zu C++ enthält dieses Array nicht den Namen der ausführbaren Datei (EXE).  
  
 Weitere Informationen zur Verwendung von Befehlszeilenargumenten finden Sie unter [Main() und Befehlszeilenargumente](../../../csharp/programming-guide/main-and-command-args/index.md) und [Vorgehensweise: Erstellen und Verwenden von Assemblys über die Befehlszeile](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
 Der Aufruf von <xref:System.Console.ReadKey%2A> am Ende der `Main`-Methode verhindert, dass das Konsolenfenster geschlossen wird, bevor Sie die Ausgabe lesen können, wenn Sie das Programm durch Drücken von F5 im Debugmodus ausführen.  
  
## <a name="input-and-output"></a>Eingabe und Ausgabe  
 C#-Programme verwenden im Allgemeinen die Eingabe-/Ausgabedienste der Laufzeitbibliothek von .NET Framework. Die Anweisung `System.Console.WriteLine("Hello World!");` verwendet die <xref:System.Console.WriteLine%2A>-Methode. Dies ist eine der Ausgabemethoden der <xref:System.Console>-Klasse in der Laufzeit-Bibliothek. Bei dieser Methode wird der Zeichenfolgenparameter für den Standardausgabestream gefolgt von einer neuen Zeile angezeigt. Für andere Eingabe-/Ausgabevorgänge sind andere <xref:System.Console>-Methoden verfügbar. Wenn Sie die `using System;`-Direktive am Anfang des Programms einfügen, können Sie die <xref:System>-Klassen und -Methoden direkt verwenden, ohne sie voll zu qualifizieren. Zum Beispiel können Sie `Console.WriteLine` statt `System.Console.WriteLine` aufrufen:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Weitere Informationen zu Eingabe-/Ausgabemethoden finden Sie unter <xref:System.IO>.  
  
## <a name="command-line-compilation-and-execution"></a>Befehlszeilenkompilierung und -ausführung  
 Sie können das „Hallo Welt“ -Programm über die Befehlszeile statt mit der integrierten Entwicklungsumgebung (IDE) von Visual Studio kompilieren.  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>So funktionieren Kompilierungsvorgänge und Ausführungen von einer Eingabeaufforderung aus  
  
1.  Fügen Sie den Code aus der vorherigen Prozedur in einem beliebigen Text-Editor ein, und speichern Sie die Datei als Textdatei. Nennen Sie die Datei `Hello.cs`. C#-Quellcodedateien weisen die Erweiterung `.cs` auf.  
  
2.  Führen Sie einen der folgenden Schritte aus, um ein Eingabeaufforderungsfenster zu öffnen:  
  
    -   Suchen Sie in Windows 10 auf dem **Startbildmenü** nach `Developer Command Prompt`, und wählen Sie dann **Developer-Eingabeaufforderung für VS2017** aus.  
  
         Ein Entwickler-Eingabeaufforderungsfenster wird angezeigt.  
  
    -   Öffnen Sie in Windows 7 das **Startmenü**, erweitern Sie den Ordner der aktuellen Version von Visual Studio, öffnen Sie das Kontextmenü für **Visual Studio-Tools**, und wählen Sie dann **Developer-Eingabeaufforderung für VS2017** aus.  
  
         Ein Entwickler-Eingabeaufforderungsfenster wird angezeigt.  
  
    -   Aktivieren Sie Befehlszeilenbuilds von einem Standardeingabeaufforderungsfenster.  
  
         Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Umgebungsvariablen für die Visual Studio-Befehlszeile](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  Navigieren Sie im Eingabeaufforderungsfenster zu dem Ordner, der die Datei `Hello.cs` enthält.  
  
4.  Geben Sie zum Kompilieren von `Hello.cs` den folgenden Befehl ein.  
  
     `csc Hello.cs`  
  
     Wenn das Programm keine Kompilierungsfehler aufweist, wird eine ausführbare Datei mit dem Namen `Hello.exe` erstellt.  
  
5.  Geben Sie den folgenden Befehl im Eingabeaufforderungsfenster ein, um das Programm auszuführen:  
  
     `Hello`  
  
 Weitere Informationen über den C#-Compiler und seine Optionen finden Sie unter [C#-Compileroptionen](../../../csharp/language-reference/compiler-options/index.md).
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Einblicke in ein C#-Programm](../../../csharp/programming-guide/inside-a-program/index.md)  
 [Zeichenfolgen](../../../csharp/programming-guide/strings/index.md)  
 [\<paveover>Beispielanwendungen für C#](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [C#-Referenz](../../../csharp/language-reference/index.md)  
 [Main() und Befehlszeilenargumente](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Erste Schritte mit Visual C# und Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
