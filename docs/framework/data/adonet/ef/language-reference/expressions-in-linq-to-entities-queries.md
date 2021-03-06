---
title: "Ausdrücke in LINQ to Entities-Abfragen"
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
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d8bfeaa3eb96e69fdf3b10d132ea1e0266d56c78
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="expressions-in-linq-to-entities-queries"></a>Ausdrücke in LINQ to Entities-Abfragen
Ein Ausdruck ist ein Codefragment, das als einzelner Wert, einzelnes Objekt, einzelne Methode oder einzelner Namespace ausgewertet werden kann. Ausdrücke können einen literalen Wert, einen Methodenaufruf, einen Operator und die entsprechenden Operanden oder einen einfachen Namen enthalten. Einfache Namen können der Name einer Variablen, eines Typmembers, eines Methodenparameters, eines Namespaces oder eines Typs sein. Ausdrücke können Operatoren verwenden, die wiederum andere Ausdrücke als Parameter oder Methodenaufrufe verwenden können, deren Parameter wiederum andere Methodenaufrufe darstellen. Die Bandbreite der möglichen Ausdrücke reicht daher von einfach bis sehr komplex.  
  
 In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Abfragen Ausdrücke alles enthalten, zulässigen Typen innerhalb der <xref:System.Linq.Expressions> -Namespace, einschließlich Lambda-Ausdrücke. Die Ausdrücke, die in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]-Abfragen verwendet werden können, umfassen die Ausdrücke, mit denen das [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] abgefragt werden kann.  Ausdrücke, die Teil einer Abfrage werden die [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] sind nur für Vorgänge, die von unterstützt `ObjectQuery<T>` und der zugrunde liegenden Datenquelle.  
  
 Im folgenden Beispiel ist der Vergleich in der `Where`-Klausel ein Ausdruck:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Bestimmte Sprachkonstrukte, wie `unchecked` in C#, haben in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] keine Bedeutung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Constant Expressions (Konstante Ausdrücke)](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Vergleichsausdrücke](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [NULL-Vergleiche](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Initialisierungsausdrücke](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Navigationseigenschaften](http://msdn.microsoft.com/en-us/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>Siehe auch  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
