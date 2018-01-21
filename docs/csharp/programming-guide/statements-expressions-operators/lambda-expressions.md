---
title: "Lambda-Ausdrücke (C#-Programmierhandbuch)"
ms.date: 03/03/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: "64"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9127cc5404fb85356f01cac26aa7b03a8ccd70da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda-Ausdrücke (C#-Programmierhandbuch)
Ein Lambda-Ausdruck ist eine [anonyme Funktion](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) , mit der Typen für [Delegaten](../../../csharp/programming-guide/delegates/using-delegates.md) oder die [Ausdrucksbaumstruktur](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) erstellt werden können. Mit Lambda-Ausdrücken können lokale Funktionen geschrieben werden, die als Argumente übergeben oder als Wert von Funktionsaufrufen zurückgegeben werden können. Lambda-Ausdrücke sind besonders für das Schreiben von LINQ-Abfrageausdrücken hilfreich.  
  
 Zum Erstellen eines Lambda-Ausdrucks geben Sie Eingabeparameter (falls vorhanden) auf der linken Seite des Lambda-Operators [=>](../../../csharp/language-reference/operators/lambda-operator.md)an und stellen den Ausdruck oder den Anweisungsblock auf die andere Seite. Beispielsweise gibt der Lambda-Ausdruck `x => x * x` einen Parameter an, der `x` heißt und den Wert `x` quadriert zurückgibt. Dieser Ausdruck kann einem Delegattyp zuwiesen werden, wie im folgenden Beispiel dargestellt:  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 So erstellen Sie einen Typ für die Ausdrucksbaumstruktur  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 Der Operator `=>` hat die gleiche Rangfolge wie Zuordnung (`=`) und ist [rechtsassoziativ](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (siehe Abschnitt „Assoziativität“ im Artikel „Operatoren“).  
  
 Lambdas werden in methodenbasierten [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]-Abfragen als Argumente für Standardabfrageoperator-Methoden wie <xref:System.Linq.Enumerable.Where%2A> verwendet.  
  
 Wenn Sie zum Aufrufen der <xref:System.Linq.Enumerable.Where%2A> -Methode in der <xref:System.Linq.Enumerable> -Klasse methodenbasierte Syntax verwenden (wie in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects und [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]), ist der Parameter ein Delegattyp <xref:System.Func%602?displayProperty=nameWithType>. Ein Lambda-Ausdruck ist die einfachste Möglichkeit zum Erstellen dieses Delegaten. Wenn Sie dieselbe Methode z.B. in der <xref:System.Linq.Queryable?displayProperty=nameWithType>-Klasse aufrufen (wie in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]), handelt es sich bei dem Parametertyp um eine <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Funktion\>, wobei „Funktion“ für beliebige Funktionsdelegaten mit bis zu 16 Eingabeparametern steht. Wie gesagt, ein Lambda-Ausdruck ist eine sehr präzise Methode, diese Ausdrucksbaumstruktur zu erstellen. Durch die Lambdas können die `Where` -Aufrufe ähnlich aussehen, obwohl sich der mithilfe des Lambdas erstellte Objekttyp unterscheidet.  
  
 Beachten Sie im vorigen Beispiel, dass die Signatur des Delegaten über einen implizit typisierten Eingabeparameter vom Typ `int`verfügt und `int`zurückgibt. Der Lambda-Ausdruck kann in einen Delegaten dieses Typs konvertiert werden, da er auch über einen Eingabeparameter (`x`) und einen Rückgabewert verfügt, der vom Compiler implizit in den Typ `int` konvertiert werden kann. (Der Typrückschluss wird in den folgenden Abschnitten ausführlicher erläutert.) Wenn der Delegat durch Verwendung des Eingabeparameters 5 aufgerufen wird, wird als Ergebnis 25 zurückgegeben.  
  
 Lambdas sind auf der linken Seite des Operators [is](../../../csharp/language-reference/keywords/is.md) oder [as](../../../csharp/language-reference/keywords/as.md) nicht zugelassen.  
  
 Alle Einschränkungen für anonyme Methoden gelten auch für Lambda-Ausdrücke. Weitere Informationen finden Sie unter [Anonyme Methoden](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## <a name="expression-lambdas"></a>Ausdruckslambdas  
 Ein Lambdaausdruck mit einem Ausdruck auf der rechten Seite des Operators „=>“ wird als *Ausdruckslambda* bezeichnet. Ausdruckslambdas werden häufig bei der Erstellung von [Ausdrucksbaumstrukturen](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)verwendet. Ein Ausdruckslambda gibt das Ergebnis des Ausdrucks zurück und hat folgende grundlegende Form:  
  
```csharp
(input-parameters) => expression
```

 Die Klammern sind nur optional, wenn das Lambda über einen Eingabeparameter verfügt; andernfalls sind sie erforderlich. Zwei oder mehr Eingabeparameter sind durch Kommas getrennt und in Klammern eingeschlossen:  
  
```csharp
(x, y) => x == y
```

 Für den Compiler kann es schwierig oder unmöglich sein, die Eingabetypen abzuleiten. Wenn dieses Problem auftritt, können Sie die Typen explizit angeben, wie im folgenden Beispiel dargestellt:  
  
```csharp
(int x, string s) => s.Length > x
```

 Geben Sie Eingabeparameter von 0 (null) mit leeren Klammern an:  
  
```csharp
() => SomeMethod()
```

 Beachten Sie im vorherigen Beispiel, dass der Text eines Ausdruckslambdas ein Methodenaufruf sein kann. Wenn Sie jedoch Ausdrucksbaumstrukturen erstellen, die auf einer anderen Plattform als .NET Framework ausgewertet werden, z. B. SQL Server, sollten Sie in Lambda-Ausdrücken keine Methodenaufrufe verwenden. Die Methoden haben außerhalb des Kontexts der .NET Common Language Runtime keine Bedeutung.  
  
## <a name="statement-lambdas"></a>Anweisungslambdas  
 Ein Anweisungslambda ähnelt einem Ausdruckslambda, allerdings sind die Anweisungen in Klammern eingeschlossen:  
  
(input-parameters) => { statement; }

 Der Text eines Anweisungslambdas kann aus einer beliebigen Anzahl von Anweisungen bestehen, wobei es sich meistens um höchstens zwei oder drei Anweisungen handelt.  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 Anweisungslambdas, wie anonyme Methoden, können nicht zum Erstellen von Ausdrucksbaumstrukturen verwendet werden.  
  
## <a name="async-lambdas"></a>Asynchrone Lambdas  
 Sie können mit den Schlüsselwörtern [async](../../../csharp/language-reference/keywords/async.md) und [await](../../../csharp/language-reference/keywords/await.md) Lambda-Ausdrücke und Anweisungen, die asynchrone Verarbeitung enthalten, leicht erstellen. Das folgende Windows Forms enthält z. B. einen Ereignishandler, der eine Async-Methode, `ExampleMethodAsync`, aufruft und erwartet.  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 Sie können denselben Ereignishandler hinzufügen, indem Sie ein asynchrones Lambda verwenden. Um diesen Handler hinzuzufügen, fügen Sie einen `async` -Modifizierer vor der Lambda-Parameterliste, wie im folgenden Beispiel dargestellt, hinzu.  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 Weitere Informationen zum Erstellen und Verwenden von asynchronen Methoden finden Sie unter [Asynchronous programming with async and await (Asynchrones Programmieren mit „async“ and „await“)](../../../csharp/programming-guide/concepts/async/index.md).  
  
## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas mit Standardabfrageoperatoren  
 Viele Standardabfrageoperatoren weisen einen Eingabeparameter auf, deren Typ einem der Typen aus der <xref:System.Func%602> -Familie generischer Delegaten entspricht. Diese Delegaten verwenden Typparameter zur Definition der Anzahl und des Typs der Eingabeparameter sowie des Rückgabetyps des Delegaten. `Func` -Delegaten sind für das Kapseln von benutzerdefinierten Ausdrücken, die für jedes Element in einem Satz von Quelldaten übernommen werden, sehr nützlich. Betrachten Sie z. B. den folgenden Delegattyp:  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 Der Delegat kann als `Func<int,bool> myFunc` instanziiert werden, wobei `int` ein Eingabeparameter und `bool` der Rückgabewert ist. Der Rückgabewert wird immer im letzten Typparameter angegeben. `Func<int, string, bool>` definiert einen Delegaten mit zwei Eingabeparametern, `int` und `string`, und einen Rückgabetyp von `bool`. Der folgende `Func` -Delegat gibt bei einem Aufruf true oder false zurück, um anzugeben, ob der Eingabeparameter gleich 5 ist:  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Sie können einen Lambda-Ausdruck auch dann angeben, wenn der Argumenttyp `Expression<Func>`ist, beispielsweise in den Standardabfrageoperatoren, die in System.Linq.Queryable definiert sind. Wenn Sie ein `Expression<Func>` -Argument angeben, wird der Lambda-Ausdruck in eine Ausdrucksbaumstruktur kompiliert.  
  
 Hier wird ein Standardabfrageoperator, die <xref:System.Linq.Enumerable.Count%2A> -Methode, angezeigt:  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 Der Compiler kann den Typ des Eingabeparameters ableiten, Sie können ihn aber auch explizit angeben. Dieser bestimmte Lambda-Ausdruck zählt die ganzen Zahlen `n`, bei denen nach dem Dividieren durch 2 als Rest 1 bleibt.  
  
 Mit der folgenden Codezeile wird eine Sequenz erzeugt, die alle Elemente im `numbers` -Array enthält, die vor der 9 auftreten, da dies die erste Zahl in der Sequenz ist, die die Bedingung nicht erfüllt:  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 In diesem Beispiel wird gezeigt, wie Sie mehrere Eingabeparameter angeben, indem Sie sie in Klammern einschließen. Mit der Methode werden alle Elemente im Zahlenarray zurückgegeben, bis eine Zahl erreicht wird, deren Wert kleiner ist als seine Position. Verwechseln Sie den Lambda-Operator `=>` nicht mit dem Operator "Größer als oder gleich" `>=`.  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a>Typrückschluss in Lambdas  
 Beim Schreiben von Lambdas müssen Sie oftmals keinen Typ für die Eingabeparameter angeben, da der Compiler den Typ auf der Grundlage des Lambda-Texts, des zugrunde liegenden Delegattyps des Parameters und anderer Faktoren per Rückschluss ableiten kann, wie in der C#-Programmiersprachenspezifikation beschrieben. Bei den meisten Standardabfrageoperatoren entspricht die erste Eingabe dem Typ der Elemente in der Quellsequenz. Beim Abfragen von `IEnumerable<Customer>` wird die Eingabevariable als `Customer`-Objekt abgeleitet, sodass Sie auf die zugehörigen Methoden und Eigenschaften zugreifen können:  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 Die allgemeinen Regeln für Lambdas lauten wie folgt:  
  
-   Der Lambda-Ausdruck muss dieselbe Anzahl von Parametern enthalten wie der Delegattyp.  
  
-   Jeder Eingabeparameter im Lambda muss implizit in den entsprechenden Delegatparameter konvertiert werden können.  
  
-   Der Rückgabewert des Lambdas (falls vorhanden) muss implizit in den Rückgabetyp des Delegaten konvertiert werden können.  
  
 Beachten Sie, dass Lambda-Ausdrücke keinen eigenen Typ haben, da das allgemeine Typsystem kein internes Konzept von "Lambda-Ausdrücken" aufweist. Es kann manchmal praktisch sein, informell vom "Typ" eines Lambda-Ausdrucks zu sprechen. In einem solchen Fall bezeichnet Typ den Delegattyp bzw. den <xref:System.Linq.Expressions.Expression> -Typ, in den der Lambda-Ausdruck konvertiert wird.  
  
## <a name="variable-scope-in-lambda-expressions"></a>Variablenbereich in Lambda-Ausdrücken  
 Lambdas können auf *äußere Variablen* verweisen (siehe [Anonyme Methoden](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)), die im Bereich der Methode, mit der die Lambdafunktion definiert wird, oder im Bereich des Typs liegen, der den Lambdaausdruck enthält. Variablen, die auf diese Weise erfasst werden, werden zur Verwendung in Lambda-Ausdrücken gespeichert, auch wenn die Variablen andernfalls außerhalb des Gültigkeitsbereichs liegen und an die Garbage Collection übergeben würden. Eine äußere Variable muss definitiv zugewiesen sein, bevor sie in einem Lambda-Ausdruck verwendet werden kann. Das folgende Beispiel veranschaulicht diese Regeln:  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 Die folgenden Regeln gelten für den Variablenbereich in Lambda-Ausdrücken:  
  
-   Eine erfasste Variable wird erst dann an die Garbage Collection übergeben, wenn der darauf verweisende Delegat für die Garbage Collection geeignet ist.  
  
-   Variablen, die in einem Lambda-Ausdruck eingeführt wurden, sind in der äußeren Methode nicht sichtbar.  
  
-   Ein Lambda-Ausdruck kann einen `ref` - oder `out` -Parameter nicht direkt von einer einschließenden Methode erfassen.  
  
-   Eine `return`-Anweisung in einem Lambda-Ausdruck bewirkt keine Rückgabe durch die einschließende Methode.  
  
-   Ein Lambda-Ausdruck kann eine `goto` -Anweisung, `break` -Anweisung oder `continue` -Anweisung enthalten, die innerhalb der Lambda-Funktion liegt, wenn das Ziel der jump-Anweisung außerhalb des Blocks liegt. Eine jump-Anweisung darf auch nicht außerhalb des Lambda-Funktionsblocks sein, wenn das Ziel im Block ist.  
  
## <a name="c-language-specification"></a>C#-Programmiersprachenspezifikation  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a>Enthaltenes Buchkapitel  
 [Delegaten, Ereignisse und Lambda-Ausdrücke](http://go.microsoft.com/fwlink/?LinkId=195395) im [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Anonyme Methoden](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [Ausdrucksbaumstrukturen](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Visual Studio 2008 C#-Beispiele (Siehe LINQ Beispielabfragedateien und XQuery-Programm)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [Rekursive Lambda-Ausdrücke](http://go.microsoft.com/fwlink/?LinkId=112395)
