---
title: Standardereignismuster in .NET
description: "Erfahren Sie etwas über Ereignismuster in .NET und wie Sie standardmäßige Ereignisquellen erstellen und Standardereignisse in Ihrem Code abonnieren und verarbeiten können."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 703b7b13a2175fb9c40ff707f333a1bf1530df8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="standard-net-event-patterns"></a>Standardereignismuster in .NET

[Zurück](events-overview.md)

.NET-Ereignisse folgen in der Regel einigen bekannten Mustern. Standardisierung auf diese Muster bedeutet, dass Entwickler Kenntnisse über diese Standardmuster nutzen können, die auf ein beliebiges .NET Ereignisprogramm angewendet werden können.

Schauen wir uns diese Standardmuster an, sodass Sie über alle Kenntnisse verfügen, die Sie benötigen, um Standardereignisquellen zu erstellen und Standardereignisse in Ihrem Code zu abonnieren und zu verarbeiten.

## <a name="event-delegate-signatures"></a>Ereignisdelegatsignaturen

Die Standardsignatur für ein .NET-Ereignisdelegat lautet:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Der Rückgabetyp ist void. Ereignisse basieren auf Delegaten und sind Multicastdelegaten. Dies unterstützt mehrere Abonnenten für jede Ereignisquelle. Der einzelne Rückgabewert einer Methode wird nicht auf mehrere Ereignisabonnenten skaliert. Welchen Rückgabewert findet die Ereignisquelle nach dem Auslösen eines Ereignisses vor? In diesem Artikel sehen Sie später, wie Sie Ereignisprotokolle zur Unterstützung der Ereignisabonnenten, die Informationen an die Ereignisquelle senden, erstellen.

Die Argumentliste enthält zwei Argumente: Den Absender und die Ereignisargumente. Der Kompilierzeittyp von `sender` ist `System.Object`, obwohl Sie wahrscheinlich einen stärker abgeleiteten Typ kennen, die immer korrekt wäre. Verwenden Sie gemäß der Konvention `object`.

Das zweite Argument ist in der Regel ein Typ, der von `System.EventArgs` abgeleitet ist. (Im [nächsten Abschnitt](modern-events.md) werden Sie sehen, dass diese Konvention nicht mehr erzwungen wird.) Wenn der Ereignistyp keine zusätzlichen Argumente benötigt, werden Sie dennoch beide Argumente bereitstellen.
Es gibt einen speziellen Wert, `EventArgs.Empty`, den Sie verwenden sollten, um anzugeben, dass Ihr Ereignis keine weiteren Informationen enthält.

Erstellen Sie eine Klasse, die Dateien in einem Verzeichnis oder einem seiner Unterverzeichnisse, die einem Muster folgen, auflistet. Diese Komponente löst ein Ereignis für jede gefundene Datei aus, die mit dem Muster übereinstimmt.

Ein Ereignismodell bietet einige Vorteile beim Entwurf. Sie können mehrere Ereignislistener erstellen, die verschiedene Aktionen ausführen, wenn eine gesuchte Datei gefunden wird. Das Kombinieren der verschiedenen Listener kann robustere Algorithmen erstellen.

Hier ist die erste Ereignisargumentdeklaration für die Suche nach einer gesuchten Datei: 

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

Obwohl dieser Typ wie ein kleiner, Nur-Daten-Typ aussieht, sollten Sie die Konvention einhalten und ihm einen Verweis (`class`)-Typ geben. Dies bedeutet, dass das Argumentobjekt als Verweis übergeben wird, und alle Updates der Daten von allen Abonnenten gesehen werden. Die erste Version ist ein unveränderliches Objekt. Sie sollten die Eigenschaften im Ereignisargumenttyp auf unveränderlich einstellen. Auf diese Weise kann ein Abonnent die Werte nicht ändern, bevor ein anderer Abonnent sie sieht. (Es gibt Ausnahmen dafür, wie Sie unten sehen werden.)  

Als Nächstes müssen wir die Ereignisdeklaration in der FileSearcher-Klasse erstellen. Die Nutzung des `EventHandler<T>`-Typ bedeutet, dass Sie nicht noch eine Typdefinition erstellen müssen. Sie verwenden einfach eine generische Spezialisierung.

Füllen wir die FileSearcher-Klasse aus, um nach Dateien mit dem Muster zu suchen und das richtige Ereignis auszulösen, wenn eine Übereinstimmung gefunden wird.

```csharp
public class FileSearcher
{
    public event EventHandler<FileFoundArgs> FileFound;

    public void Search(string directory, string searchPattern)
    {
        foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
        {
            FileFound?.Invoke(this, new FileFoundArgs(file));
        }
    }
}
```

## <a name="definining-and-raising-field-like-events"></a>Definieren und Auslösen von feldähnlichen Ereignissen

Die einfachste Möglichkeit, Ihrer Klasse ein Ereignis hinzuzufügen, ist das Deklarieren des Ereignisses als öffentliches Feld, wie im obigen Beispiel:

```csharp
public event EventHandler<FileFoundArgs> FileFound;
```

Dies scheint ein öffentliches Feld zu deklarieren, das als eine Vorgehensweise eines ungültigen Objekts erscheinen würde. Sie möchten den Datenzugriff über Eigenschaften oder Methoden schützen. Während dies anscheinend kein empfehlenswertes Verfahren ist, erstellt der vom Compiler generierte Code Wrapper, damit auf die Ereignisobjekte nur auf sichere Weise zugegriffen werden kann. Die einzig verfügbaren Vorgänge für ein feldähnliches Ereignis sind das Hinzufügen von Handlern:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);
lister.FileFound += onFIleFound;
```

und das Entfernen von Handlern:

```csharp
lister.FileFound -= onFileFound;
```

Beachten Sie, dass eine lokale Variable für den Handler vorhanden ist. Wenn Sie den Text des Lambda-Ausdrucks verwenden, würde das Entfernen nicht ordnungsgemäß funktionieren. Es wäre eine andere Instanz des Delegaten, und es würde stillschweigend nichts geschehen.

Code außerhalb der Klasse kann das Ereignis nicht auslösen, noch kann er andere Vorgänge ausführen.

## <a name="returning-values-from-event-subscribers"></a>Rückgabe von Werten aus Ereignisabonnenten

Ihre einfache Version funktioniert einwandfrei. Fügen wir eine weitere Funktion hinzu: Abbruch.

Beim Auslösen des gefunden Ereignisses sollten Listener die weitere Verarbeitung beenden können, wenn diese Datei die letzte gesuchte Datei ist.

Die Ereignishandler geben keinen Wert zurück. Daher müssen Sie dies auf andere Weise kommunizieren. Das Standardereignismuster verwendet das EventArgs-Objekt, um Felder einzuschließen, die Ereignisabonnenten zum Kommunizieren von „Abbrechen“ verwenden.

Es gibt zwei unterschiedliche Muster, die verwendet werden können, auf der Grundlage der Semantik des Vertrags „Abbrechen“. In beiden Fällen werden Sie ein boolesches Feld zum EventArguments für das gefundene Dateiereignis hinzufügen. 

Ein Muster ermöglicht jedem Abonnenten, den Vorgang abzubrechen.
Für dieses Muster wird ein neues Feld mit `false` initialisiert. Jeder Abonnent kann es in `true` ändern. Nachdem alle Abonnenten das ausgelöste Ereignis gesehen haben, untersucht die Komponente FileSearcher den booleschen Wert und ergreift Maßnahmen.

Das zweite Muster würde nur den Vorgang abbrechen, wenn alle Abonnenten den Vorgang abgebrochen haben möchten. In diesem Muster wird das neue Feld initialisiert, um anzugeben, dass der Vorgang abgebrochen werden soll, und jeder Abonnent kann dies ändern, um anzugeben, dass der Vorgang fortgesetzt werden soll.
Nachdem alle Abonnenten das ausgelöste Ereignis gesehen haben, untersucht die Komponente FileSearcher den booleschen Wert und ergreift Maßnahmen. Es gibt einen zusätzlichen Schritt in diesem Muster: Die Komponente muss wissen, ob jeder Abonnent das Ereignis gesehen hat. Wenn keine Abonnenten vorhanden sind, würde das Feld fälschlicherweise einen Abbruch angeben.

Implementieren wir die erste Version für dieses Beispiel. Sie müssen ein boolesches Feld zum FileFoundEventArgs-Typ hinzufügen:

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }
    public bool CancelRequested { get; set; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

Dieses neue Feld sollte mit FALSE initialisiert werden, damit Sie nicht ohne Grund abbrechen. Das ist der Standardwert für ein boolesches Feld, damit dies automatisch geschieht. Die einzige andere Änderung der Komponente ist das Überprüfen des Flag nach dem Auslösen des Ereignisses, um festzustellen, ob einer der Abonnenten einen Abbruch angefordert hat:

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

Ein Vorteil dieses Musters ist, dass es keine unterbrechende Änderung ist.
Keiner der Abonnenten hat vorher einen Abbruch angefordert und macht es noch immer nicht. Kein Teil des Abonnentencodes benötigt eine Aktualisierung, sofern sie das neue Abbrechen-Protokoll nicht unterstützen möchten. Es ist sehr lose gekoppelt.

Aktualisieren wir den Abonnenten, damit ein Abbruch angefordert wird, sobald die erste ausführbare Datei gefunden wird:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Hinzufügen einer anderen Ereignisdeklaration

Fügen wir eine weitere Funktion hinzu, und zeigen andere Sprachausdrücke für Ereignisse. Fügen wir eine Überladung der `Search()`-Methode, die alle Unterverzeichnisse auf der Suche nach Dateien durchsucht.

In einem Verzeichnis mit vielen Unterverzeichnisse könnte dies ein längerer Vorgang werden. Fügen wir ein Ereignis hinzu, das zu Beginn jeder neuen Verzeichnissuche ausgelöst wird. Dies ermöglicht es Abonnenten, den Fortschritt zu verfolgen und den Benutzer während des Fortschritts zu aktualisieren. Die Beispiele, die Sie bisher erstellt haben, sind öffentlich. Dieses erstellen wir als internes Ereignis. Das bedeutet, dass Sie auch die Typen für die Argumente intern erstellen können.

Sie beginnen mit dem Erstellen der neuen abgeleiteten EventArgs-Klasse für die Berichte des neuen Verzeichnisses und Status. 

```csharp
internal class SearchDirectoryArgs : EventArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs)
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
``` 

In diesem Fall können Sie erneut der Empfehlung für das Erstellen eines nicht änderbaren Verweistyps für die Ereignisargumente folgen.

Definieren Sie als Nächstes das Ereignis. Dieses Mal werden Sie eine andere Syntax verwenden. Zusätzlich zur Verwendung der Feldsyntax, können Sie die Eigenschaft explizit erstellen, mit dem Hinzufügen- und Entfernen-Handler. In diesem Beispiel werden Sie für diese Handler in diesem Projekt keinen zusätzlichen Code benötigen, aber dies zeigt, wie Sie sie erstellen würden.

```csharp
internal event EventHandler<SearchDirectoryArgs> DirectoryChanged
{
    add { directoryChanged += value; }
    remove { directoryChanged -= value; }
}
private EventHandler<SearchDirectoryArgs> directoryChanged;
```

In vielerlei Hinsicht spiegelt der Code, den Sie hier schreiben, den vom Compiler generierten Code für die Feldereignisdefinitionen wider, die Sie zuvor gesehen haben. Sie erstellen das Ereignis mithilfe der Syntax ähnlich der für [Eigenschaften](properties.md). Beachten Sie, dass die Handler unterschiedliche Namen haben: `add` und `remove`. Diese werden aufgerufen, um das Ereignis zu abonnieren oder sich vom Ereignis abzumelden. Beachten Sie, dass Sie auch ein privates Unterstützungsfeld zum Speichern der Ereignisvariable deklarieren müssen. Es wird mit NULL initialisiert.

Als Nächstes fügen wir die Überladung der Search()-Methode hinzu, die Unterverzeichnisse durchsucht und beide Ereignisse auslöst. Die einfachste Möglichkeit besteht darin, ein Standardargument zu verwenden, um anzugeben, dass alle Verzeichnisse durchsucht werden sollen:

```csharp
public void Search(string directory, string searchPattern, bool searchSubDirs = false)
{
    if (searchSubDirs)
    {
        var allDirectories = Directory.GetDirectories(directory, "*.*", SearchOption.AllDirectories);
        var completedDirs = 0;
        var totalDirs = allDirectories.Length + 1;
        foreach (var dir in allDirectories)
        {
            directoryChanged?.Invoke(this,
                new SearchDirectoryArgs(dir, totalDirs, completedDirs++));
            // Recursively search this child directory:
            SearchDirectory(dir, searchPattern);
        }
        // Include the Current Directory:
        directoryChanged?.Invoke(this,
            new SearchDirectoryArgs(directory, totalDirs, completedDirs++));
        SearchDirectory(directory, searchPattern);
    }
    else
    {
        SearchDirectory(directory, searchPattern);
    }
}

private void SearchDirectory(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

An diesem Punkt können Sie die Anwendung durch das Aufrufen der Überladung für die Suche aller Unterverzeichnisse ausführen. Es sind keine Abonnenten auf dem neuen `ChangeDirectory`-Ereignis vorhanden, aber mit den `?.Invoke()`-Ausdruck wird sichergestellt, dass es ordnungsgemäß funktioniert.

 Fügen wir einen Handler hinzu, um eine Zeile zu schreiben, die den Status im Konsolenfenster anzeigt. 

```csharp
lister.DirectoryChanged += (sender, eventArgs) =>
{
    Console.Write($"Entering '{eventArgs.CurrentSearchDirectory}'.");
    Console.WriteLine($" {eventArgs.CompletedDirs} of {eventArgs.TotalDirs} completed...");
};
```

Sie haben Muster gesehen, die im .NET-Ökosystem eingehalten werden.
Indem Sie diese Muster und Konventionen erlernen, werden Sie schnell idiomatische C# und .NET schreiben können.

Als Nächstes sehen Sie einige Änderungen in diesen Mustern in der neuesten Version von .NET.

[Weiter](modern-events.md)
