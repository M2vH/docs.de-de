---
title: "Beispiele für die methodenbasierte Abfragesyntax: Set-Operatoren (LINQ to DataSet)"
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
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 637e1c2fe66bcfd31b0392076b8b1058d0008482
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a>Beispiele für die methodenbasierte Abfragesyntax: Set-Operatoren (LINQ to DataSet)
In den Beispielen in diesem Thema wird gezeigt, wie mithilfe der <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, und <xref:System.Linq.Enumerable.Union%2A> Operatoren wertbasierte Vergleichsoperationen für einen Satz von Datenzeilen ausführen.[ Laden von Daten in ein DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) finden Sie unter [Vergleichen von DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) Weitere Informationen zu <xref:System.Data.DataRowComparer>.  
  
 Die `FillDataSet` in diesen Beispielen verwendete Methode angegeben, [Laden von Daten in ein DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 In den Beispielen in diesem Thema wird auf die Tabellen <legacyBold>Contact</legacyBold>, <legacyBold>Address</legacyBold>, <legacyBold>Product</legacyBold>, <legacyBold>SalesOrderHeader</legacyBold> und <legacyBold>SalesOrderDetail</legacyBold> in der <legacyBold>AdventureWorks</legacyBold>-Beispieldatenbank zurückgegriffen.  
  
 In den Beispielen in diesem Thema verwenden Sie die folgenden `using` / `Imports` Anweisungen:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines LINQ to DataSet-Projekt In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="distinct"></a>Distinct  
  
### <a name="example"></a>Beispiel  
 In diesem Beispiel wird die <xref:System.Linq.Enumerable.Distinct%2A>-Methode verwendet, um doppelte Elemente in einer Sequenz zu entfernen.  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a>Except  
  
### <a name="example"></a>Beispiel  
 In diesem Beispiel wird die <xref:System.Linq.Enumerable.Except%2A>-Methode verwendet, um die Kontakte abzurufen, die zwar in der ersten, nicht aber in der zweiten Tabelle aufgeführt sind.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a>Überschneiden  
  
### <a name="example"></a>Beispiel  
 In diesem Beispiel wird die <xref:System.Linq.Enumerable.Intersect%2A>-Methode verwendet, um die Kontakte abzurufen, die in beiden Tabellen aufgeführt sind.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a>Union  
  
### <a name="example"></a>Beispiel  
 In diesem Beispiel wird die <xref:System.Linq.Enumerable.Union%2A>-Methode verwendet, um die Kontakte abzurufen, die in nur einer der beiden Tabellen aufgeführt sind.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a>Siehe auch  
 [Laden von Daten in ein DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Beispiele für LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Übersicht über Standardabfrageoperatoren](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
