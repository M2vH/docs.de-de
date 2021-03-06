---
title: 'Gewusst wie: Aufrufen modelldefinierter Funktionen als Objektmethoden'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d769eca17a45449505e1df96e1cbde584e42d65e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Gewusst wie: Aufrufen modelldefinierter Funktionen als Objektmethoden
In diesem Thema wird beschrieben, wie eine modelldefinierte Funktion als Methode für ein <xref:System.Data.Objects.ObjectContext>-Objekt oder als statische Methode für eine benutzerdefinierte Klasse aufgerufen wird. Ein *modelldefinierte Funktion* ist eine Funktion, die im konzeptionellen Modell definiert ist. Die folgenden Prozeduren beschreiben, wie diese Funktionen direkt aufgerufen werden, anstatt sie von LINQ to Entities-Abfragen aufzurufen. Informationen zum Aufrufen modelldefinierter Funktionen in LINQ to Entities-Abfragen finden Sie unter [Vorgehensweise: Call Model-Defined-Funktionen in Abfragen](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).  
  
 Egal, ob Sie eine modelldefinierte Funktion als <xref:System.Data.Objects.ObjectContext>-Methode oder statische Methode für eine benutzerdefinierte Klasse aufrufen: Zuerst muss die Methode der modelldefinierten Funktion mit einem <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> zugeordnet werden. Wenn Sie jedoch für die <xref:System.Data.Objects.ObjectContext>-Klasse eine Methode definieren, müssen Sie den LINQ-Anbieter mithilfe der <xref:System.Data.Objects.ObjectContext.QueryProvider%2A>-Eigenschaft bereitstellen. Wenn Sie jedoch für eine benutzerdefinierte Klasse eine statische Methode definieren, müssen Sie den LINQ-Anbieter mithilfe der <xref:System.Linq.IQueryable.Provider%2A>-Eigenschaft bereitstellen. Weitere Informationen finden Sie in den Beispielen im Anschluss an die folgenden Prozeduren.  
  
 Die folgenden Prozeduren stellen in knapper Form dar, wie eine modelldefinierte Funktion als Methode für ein <xref:System.Data.Objects.ObjectContext>-Objekt und als statische Methode für eine benutzerdefinierte Klasse aufgerufen wird. Die folgenden Beispiele enthalten weitere Details zu den Schritten in den Prozeduren. In den Prozeduren wird davon ausgegangen, dass eine Funktion im konzeptionellen Modell definiert wurde. Weitere Informationen finden Sie unter [wie: Definieren von benutzerdefinierten Funktionen im konzeptionellen Modell](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>So rufen Sie eine modelldefinierte Funktion als Methode für ein ObjectContext-Objekt auf  
  
1.  Fügen Sie eine Quelldatei hinzu, um die partielle von den Entity Framework-Tools generierte und von der <xref:System.Data.Objects.ObjectContext> Klasse abgeleitete Klasse zu erweitern. Durch die Definition des CLR-Stub in einer separaten Quelldatei werden die Änderungen bei der erneuten Erstellung der Datei beibehalten.  
  
2.  Fügen Sie der <xref:System.Data.Objects.ObjectContext>-Klasse, die wie folgt vorgeht, eine Common Language Runtime (CLR)-Methode hinzu:  
  
    -   Sie ordnet der im konzeptionellen Modell definierten Funktion Objekte zu. Zum Zuordnen der Methode müssen Sie ein <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> für die Methode übernehmen. Beachten Sie, dass der <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A>-Parameter und der <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A>-Parameter des Attributs im konzeptionellen Modell den Namespacenamen und den Funktionsnamen darstellen. Bei der Funktionsnamenauflösung für LINQ wird die Groß-/Kleinschreibung berücksichtigt.  
  
    -   Gibt die Ergebnisse der <xref:System.Linq.IQueryProvider.Execute%2A>-Methode zurück, die von der <xref:System.Data.Objects.ObjectContext.QueryProvider%2A>-Eigenschaft zurückgegeben werden.  
  
3.  Rufen Sie die statische Methode als ein Member für eine Instanz der <xref:System.Data.Objects.ObjectContext>-Klasse auf.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>So rufen Sie eine modelldefinierte Funktion als statische Methode für eine benutzerdefinierte Klasse auf  
  
1.  Fügen Sie der Anwendung eine Klasse mit einer statischen Methode hinzu, die wie folgt vorgeht:  
  
    -   Sie ordnet der im konzeptionellen Modell definierten Funktion Objekte zu. Zum Zuordnen der Methode müssen Sie ein <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> für die Methode übernehmen. Beachten Sie, dass der <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A>-Parameter und der <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A>-Parameter des Attributs im konzeptionellen Modell den Namespacenamen und den Funktionsnamen darstellen.  
  
    -   Akzeptiert ein <xref:System.Linq.IQueryable>-Argument.  
  
    -   Gibt die Ergebnisse der <xref:System.Linq.IQueryProvider.Execute%2A>-Methode zurück, die von der <xref:System.Linq.IQueryable.Provider%2A>-Eigenschaft zurückgegeben werden.  
  
2.  Aufrufen der Methode als Member einer statischen Methode für die benutzerdefinierte Klasse  
  
## <a name="example"></a>Beispiel  
 **Aufrufen einer Modelldefinierten Funktion als Methode für ein ObjectContext-Objekt**  
  
 Im folgenden Beispiel wird veranschaulicht, wie eine modelldefinierte Funktion als Methode für ein <xref:System.Data.Objects.ObjectContext>-Objekt aufgerufen wird. Im Beispiel wird die [AdventureWorks Sales-Modell](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).  
  
 Erwägen Sie die Verwendung der folgenden konzeptionellen Modellfunktion, die Produkteinnahmen für ein angegebenes Produkt zurückgibt. (Informationen zum Hinzufügen von der Funktion mit dem konzeptionellen Modell finden Sie unter [wie: Definieren von benutzerdefinierten Funktionen im konzeptionellen Modell](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Beispiel  
 Mit dem folgenden Code wird der `AdventureWorksEntities`-Klasse eine Methode hinzugefügt, die der konzeptionellen Modellfunktion oben zugeordnet wird.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Methode oben aufgerufen, um die Produkteinnahmen oben für ein angegebenes Produkt anzuzeigen:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie eine modelldefinierte Funktion, die eine Auflistung (als <xref:System.Linq.IQueryable%601>-Objekt) zurückgibt, aufgerufen wird. Erwägen Sie den Einsatz der folgenden konzeptionellen Modellfunktion, die alle `SalesOrderDetails` für eine angegebene Produkt-ID zurückgibt.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Beispiel  
 Mit dem folgenden Code wird der `AdventureWorksEntities`-Klasse eine Methode hinzugefügt, die der konzeptionellen Modellfunktion oben zugeordnet wird.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Beispiel  
 Der folgende Code ruft die Methode auf. Beachten Sie, dass die zurückgegebene <xref:System.Linq.IQueryable%601>-Abfrage weiter verfeinert wird, um für jedes `SalesOrderDetail` Zeilengesamtbeträge zurückzugeben.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Beispiel  
 **Aufrufen einer Modelldefinierten Funktion als statische Methode für eine benutzerdefinierte Klasse**  
  
 Im nächsten Beispiel wird veranschaulicht, wie eine modelldefinierte Funktion als statische Methode für eine benutzerdefinierte Klasse aufgerufen wird. Im Beispiel wird die [AdventureWorks Sales-Modell](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).  
  
> [!NOTE]
>  Wenn Sie eine modelldefinierte Funktion als statische Methode für eine benutzerdefinierte Klasse aufrufen, muss die modelldefinierte Funktion eine Auflistung akzeptieren und eine Aggregation von Werten in der Auflistung zurückgeben.  
  
 Erwägen Sie die Verwendung der folgenden konzeptionellen Modellfunktion, die Produkteinnahmen für eine SalesOrderDetail-Auflistung zurückgibt. (Informationen zum Hinzufügen von der Funktion mit dem konzeptionellen Modell finden Sie unter [wie: Definieren von benutzerdefinierten Funktionen im konzeptionellen Modell](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Beispiel  
 Der folgende Code fügt der Anwendung eine Klasse hinzu, die eine statische Methode enthält, die der konzeptionellen Modellfunktion oben zugeordnet wird.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Beispiel  
 Der folgenden Code ruft die Methode oben auf, um die Produkteinnahmen für eine SalesOrderDetail-Auflistung anzuzeigen:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über die EDMX-Datei](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Abfragen in LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Aufrufen von Funktionen in LINQ to Entities-Abfragen](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
