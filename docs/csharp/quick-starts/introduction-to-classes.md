---
title: "Schnellstarts – Einführung in Klassen – C#-Handbuch"
description: Erstellen Ihres ersten C#-Programms und Erforschen objektorientierter Konzepte
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 55d6050d7573b9088b361fb571b96425533bda1f
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="introduction-to-classes"></a>Einführung in Klassen

Für diesen Schnellstart wird vorausgesetzt, dass Sie über einen Computer verfügen, den Sie für die Entwicklung nutzen können. Das .NET-Thema [Erste Schritte in 10 Minuten](https://www.microsoft.com/net/core) umfasst Anweisungen zum Einrichten Ihrer lokalen Entwicklungsumgebung auf einem Mac-, Windows- oder Linux-PC. Einen schnellen Überblick über die Befehle, die Sie verwenden werden, finden Sie in den [Schnellstarts mit der Einführung zu lokalen Umgebungen](local-environment.md), die Links mit weiteren Einzelheiten enthalten.

## <a name="create-your-application"></a>Erstellen Ihrer Anwendung

Erstellen Sie in einem Terminalfenster ein Verzeichnis namens **classes**. Dort werden Sie Ihre Anwendung erstellen. Wechseln Sie in dieses Verzeichnis, und geben Sie `dotnet new console` im Konsolenfenster ein. Dieser Befehl erstellt die Anwendung. Öffnen Sie **Program.cs**. Es sollte wie folgt aussehen:

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

In diesem Schnellstart erstellen Sie neue Typen, die ein Bankkonto darstellen. Entwickler definieren jede Klasse in der Regel in einer anderen Textdatei. Dies erleichtert die Verwaltung bei zunehmender Programmgröße.  Erstellen Sie eine neue Datei mit dem Namen **BankAccount.cs** im Verzeichnis **classes**. 

Diese Datei enthält die Definition eines ***Bankkontos***. In der objektorientierten Programmierung wird der Code organisiert, indem Typen in Form von ***Klassen*** erstellt werden. Diese Klassen enthalten den Code, der eine bestimmte Entität darstellt. Die `BankAccount`-Klasse stellt ein Bankkonto dar. Der Code implementiert bestimmte Vorgänge mittels Methoden und Eigenschaften. In diesem Schnellstart unterstützt das Bankkonto dieses Verhalten:

1. Es enthält eine 10-stellige Zahl, die das Bankkonto eindeutig identifiziert.
1. Es enthält eine Zeichenfolge, die den bzw. die Namen des Besitzers speichert.
1. Der Kontostand kann abgerufen werden.
1. Es akzeptiert Einzahlungen.
1. Es akzeptiert Abbuchungen.
1. Der anfängliche Kontostand muss positiv sein.
1. Abbuchungen dürfen nicht in einem negativen Kontostand resultieren.

## <a name="define-the-bank-account-type"></a>Definieren des Bankkontotyps

Sie können beginnen, indem Sie die Grundlagen einer Klasse erstellen, die dieses Verhalten definiert. Die sollte wie folgt aussehen:

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

Bevor wir fortfahren, lassen Sie uns anschauen, was Sie erstellt haben.  Die `namespace`-Deklaration ist eine Möglichkeit, Ihren Code logisch zu organisieren. Da dieser Schnellstart relativ klein ist, platzieren Sie den gesamten Code in einem einzelnen Namespace. 

`public class BankAccount` definiert die Klasse oder den Typ, die/den Sie erstellen. Sämtliche Inhalte zwischen `{` und `}`, die der Klassendeklaration folgen, definieren das Verhalten der Klasse. Die `BankAccount`-Klasse verfügt über fünf ***Member***. Die ersten drei sind ***Eigenschaften***. Eigenschaften sind Datenelemente und können Code aufweisen, der eine Überprüfung oder andere Regeln erzwingt. Die letzten beiden sind ***Methoden***. Methoden sind Codeblöcke, die eine einzelne Funktion ausführen. Das Lesen der Namen der einzelnen Member sollte Ihnen oder anderen Entwicklern genug Informationen liefern, um zu verstehen, welche Aufgabe die Klasse hat.

## <a name="open-a-new-account"></a>Eröffnen eines neuen Kontos

Die erste zu implementierende Funktion ist das Eröffnen eines Bankkontos. Wenn ein Kunde ein Konto eröffnet, muss er einen anfänglichen Kontostand bereitstellen und Informationen über den/die Besitzer dieses Kontos angeben. 

Das Erstellen eines neuen Objekts des `BankAccount`-Typs bedeutet Definieren eines ***Konstruktors***, der diese Werte zuweist. Ein ***Konstruktor*** ist ein Member, der den gleichen Namen wie die Klasse hat. Er wird verwendet, um Objekte dieses Klassentyps zu initialisieren. Fügen Sie dem `BankAccount`-Typ folgenden Konstruktor hinzu:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktoren werden bei der Erstellung eines Objekts mit [`new`](../language-reference/keywords/new.md) aufgerufen. Ersetzen Sie die Zeile `Console.WriteLine("Hello World!");` in ***program.cs*** mit der folgenden Zeile (ersetzen Sie `<name>` durch Ihren Namen):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Geben Sie `dotnet run` ein, und beobachten Sie, was passiert.  

Haben Sie bemerkt, dass die Kontonummer leer ist? Es ist höchste Zeit, dies zu ändern. Die Kontonummer sollten zugewiesen werden, wenn das Objekt erstellt wird. Jedoch sollte nicht der Aufrufende für das Erstellen verantwortlich sein. Der `BankAccount`-Klassencode sollte wissen, wie neue Kontonummern zugewiesen werden.  Eine einfache Möglichkeit hierzu ist, mit einer 10-stelligen Zahl zu beginnen. Lassen Sie sie bei jeder Erstellung eines neuen Kontos erhöhen. Speichern Sie schließlich die aktuelle Kontonummer, wenn ein Objekt erstellt wird.

Fügen Sie der `BankAccount`-Klasse die folgende Memberdeklaration hinzu:

```csharp
private static int accountNumberSeed = 1234567890;
```

Dies ist ein Datenelement. Es ist `private`, d.h. der Zugriff darauf ist nur über Code in der `BankAccount`-Klasse möglich. Dies ist eine Möglichkeit, die öffentlichen Verantwortlichkeiten (z.B. Besitz einer Kontonummer) von der privaten Implementierung (wie Kontonummern generiert werden) zu trennen. Fügen Sie dem Konstruktor die folgenden zwei Zeilen hinzu, um die Kontonummer zuzuweisen:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Geben Sie `dotnet run` ein, um die Ergebnisse anzuzeigen.

## <a name="create-deposits-and-withdrawals"></a>Erstellen von Einzahlungen und Abbuchungen

Um ordnungsgemäß zu funktionieren, muss Ihre Bankkontoklasse Einzahlungen und Abbuchungen akzeptieren. Einzahlungen und Abbuchungen implementieren Sie, indem Sie eine Erfassung jeder Transaktion für das Konto erstellen. Dies ist vorteilhafter, als den Kontostand bei jeder Transaktion einfachen zu aktualisieren. Der Verlauf kann zum Überwachen aller Transaktionen und Verwalten täglicher Kontostände verwendet werden. Indem der Kontostand ggf. aus dem Verlauf aller Transaktionen berechnet wird, werden etwaige Korrekturen von Fehlern in einer einzelnen Transaktion bei der nächsten Berechnung im Kontostand ordnungsgemäß widergespiegelt.

Zunächst erstellen wir einen neuen Typ, um eine Transaktion darzustellen. Dies ist ein einfacher Typ, der keine Verantwortlichkeiten hat. Er benötigt einige Eigenschaften. Erstellen Sie eine neue Datei mit dem Namen ***Transaction.cs***. Fügen Sie ihr folgenden Code hinzu:

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Nun fügen wir eine <xref:System.Collections.Generic.List%601> von `Transaction`-Objekten der `BankAccount`-Klasse hinzu. Fügen Sie die folgende Deklaration hinzu:

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

Die <xref:System.Collections.Generic.List%601>-Klasse erfordert, dass Sie einen anderen Namespace importieren. Fügen Sie am Anfang von **BankAccount.cs** Folgendes hinzu:

```csharp
using System.Collections.Generic;
```

Jetzt ändern wir die Art, in der `Balance` gemeldet wird.  Er kann durch Summierung der Werte aller Transaktionen gefunden werden. Ändern Sie die Deklaration von `Balance` in der `BankAccount`-Klasse folgendermaßen:

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Dieses Beispiel zeigt einen wichtigen Aspekt der ***Eigenschaften***. Jetzt berechnen Sie den Kontostand, wenn ein anderer Programmierer den Wert anfordert. Die Berechnung zählt alle Transaktionen auf und gibt die Summe als aktuellen Kontostand zurück.

Implementieren Sie nun die `MakeDeposit`- und `MakeWithdrawal`-Methode. Diese Methoden erzwingen die letzten beiden Regeln: Der anfängliche Kontostand muss positiv sein, und eine Abbuchung darf nicht in einem negativen Kontostand resultieren. 

Dies führt das Konzept der ***Ausnahmen*** ein. Standardmäßig wird eine Ausnahme ausgelöst, um anzuzeigen, dass eine Methode ihre Aufgabe nicht erfolgreich ausführen kann. Der Typ der Ausnahme und die zugeordnete Nachricht beschreiben den Fehler. Hier löst die `MakeDeposit`-Methode eine Ausnahme aus, wenn der Einzahlungsbetrag negativ ist. Die `MakeWithdrawal`-Methode löst eine Ausnahme aus, wenn der Abbuchungsbetrag negativ ist, oder wenn aus der Abbuchung ein negativer Kontostand resultiert:

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

Die [`throw`](../language-reference/keywords/throw.md)-Anweisung **löst** eine Ausnahme aus. Die Ausführung der aktuellen Methode endet und wird fortgesetzt, wenn ein entsprechender `catch`-Block gefunden wird. Sie fügen einen `catch`-Block hinzu, um diesen Code etwas später zu testen.

Der Konstruktor sollte so geändert werden, dass er eine anfängliche Transaktion hinzufügt, anstatt den Kontostand direkt zu aktualisieren. Da Sie die `MakeDeposit`-Methode bereits geschrieben haben, rufen Sie sie aus dem Konstruktor auf. Der fertige Konstruktor sollte wie folgt aussehen:

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> ist eine Eigenschaft, die das aktuelle Datum und die Uhrzeit zurückgibt. Testen Sie dies durch Hinzufügen von ein paar Einzahlungen und Abbuchungen in Ihrer `Main`-Methode:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

Testen Sie anschließend, ob Sie Fehlerbedingungen abfangen, indem Sie versuchen, ein Konto mit einem negativen Kontostand zu erstellen:

```csharp
// Test that the initial balances must be positive:
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

Markieren Sie mit den Anweisungen [`try` und `catch` ](../language-reference/keywords/try-catch.md) einen Codeblock, der Ausnahmen auslösen kann und die Fehler abfangen kann, die Sie erwarten. Mit dem gleichen Verfahren können Sie den Code testen, der bei einem negativen Kontostand eine Ausnahme auslöst:

```csharp
// Test for a negative balance
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

Speichern Sie die Datei, und geben Sie `dotnet run` zum Testen ein.

## <a name="challenge---log-all-transactions"></a>Herausforderung – Protokollieren aller Transaktionen

Um diesen Schnellstart abzuschließen, können Sie die `GetAccountHistory`-Methode schreiben, die einen `string` für den Transaktionsverlauf erstellt. Fügen Sie diese Methode dem `BankAccount`-Typ hinzu:

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Hier wird die <xref:System.Text.StringBuilder>-Klasse zum Formatieren einer Zeichenfolge verwendet, die eine Zeile für jede Transaktion enthält. Sie haben den Zeichenfolgen-Formatierungscode bereits früher in diesen Schnellstarts gesehen. `\t` ist ein neues Zeichen. Damit wird ein Tabulator zum Formatieren der Ausgabe hinzugefügt.

Fügen Sie diese Zeile **Program.cs** zum Testen hinzu:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Geben Sie `dotnet run` ein, um die Ergebnisse anzuzeigen.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie „stecken geblieben“ sind, finden Sie die Quelle für diesen Schnellstart [in unserem GitHub-Repository](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/).

Herzlichen Glückwunsch, Sie haben nun alle unsere Schnellstarts absolviert. Wenn Sie mehr lernen möchten, nutzen Sie unsere [Tutorials](../tutorials/index.md).
