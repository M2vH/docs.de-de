---
title: 'Gewusst wie: Binden von Daten an das DataGridView-Steuerelement in Windows Forms'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04fee5f753cb4b3786d5ca58f85880f151caf0b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Gewusst wie: Binden von Daten an das DataGridView-Steuerelement in Windows Forms
Das <xref:System.Windows.Forms.DataGridView>-Steuerelement unterstützt das Standard-Datenbindungsmodell von Windows Forms und ermöglicht so die Bindung an eine Vielzahl von Datenquellen. In den meisten Fällen erfolgt jedoch eine Bindung an eine <xref:System.Windows.Forms.BindingSource>-Komponente, die die Details der Interaktion mit der Datenquelle verwaltet. Die <xref:System.Windows.Forms.BindingSource>-Komponente kann eine beliebige Windows Forms-Datenquelle darstellen und bietet Ihnen viel Flexibilität bei der Auswahl oder Änderung des Speicherorts Ihrer Daten. Weitere Informationen zu den Datenquellen, die von unterstützt die <xref:System.Windows.Forms.DataGridView> steuern, finden Sie unter [Übersicht über das DataGridView-Steuerelement](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
 Visual Studio bietet umfassende Unterstützung für diese Aufgabe.  Siehe auch [Vorgehensweise: Binden von Daten an das DataGridView-Steuerelement in Windows Forms mithilfe des Designers](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a>So verbinden Sie ein DataGridView-Steuerelement mit Daten  
  
1.  Implementieren Sie eine Methode, mit der die Details des Abrufens von Daten aus einer Datenbank behandelt werden. Das folgende Codebeispiel implementiert eine `GetData`-Methode, die eine <xref:System.Data.SqlClient.SqlDataAdapter>-Komponente initialisiert, und verwendet diese, um ein <xref:System.Data.DataTable> mit Daten aufzufüllen. Die <xref:System.Data.DataTable> wird dann an die <xref:System.Windows.Forms.BindingSource>-Komponente gebunden. Sorgen Sie dafür, dass die `connectionString`-Variable auf einen Wert gesetzt wird, der für Ihre Datenbank geeignet ist. Sie benötigen Zugriff auf einen Server, auf dem die SQL Server-Beispieldatenbank "Northwind" installiert ist.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  Binden Sie im <xref:System.Windows.Forms.Form.Load>-Ereignishandler Ihres Formulars das <xref:System.Windows.Forms.DataGridView>-Steuerelement an die <xref:System.Windows.Forms.BindingSource>-Komponente, und verwenden Sie die `GetData`-Methode, um Daten aus der Datenbank abzurufen.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a>Beispiel  
 Das folgende vollständige Codebeispiel stellt Schaltflächen zum erneuten Laden von Daten aus der Datenbank und Übermitteln von Änderungen an die Datenbank bereit.  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Verweise auf die Assemblys "System", "System.Windows.Forms", "System.Data" und "System.XML".  
  
 Informationen zum Erstellen dieses Beispiels über die Befehlszeile für [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] finden Sie unter [Erstellen von der Befehlszeile aus](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) oder [Erstellen über die Befehlszeile mit „csc.exe“](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Sie können dieses Beispiel auch in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] erstellen, indem Sie den Code in ein neues Projekt einfügen.  Siehe auch: [Vorgehensweise: Kompilieren und Ausführen eines vollständigen Windows Forms-Codebeispiels mit Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Das Speichern vertraulicher Informationen (z. B. eines Kennworts) innerhalb der Verbindungszeichenfolge kann die Sicherheit einer Anwendung beeinträchtigen. Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows-Authentifizierung (wird auch als integrierte Sicherheit bezeichnet) sicherer steuern. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [Anzeigen von Daten im DataGridView-Steuerelement in Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Protecting Connection Information (Schützen von Verbindungsinformationen)](../../../../docs/framework/data/adonet/protecting-connection-information.md)
