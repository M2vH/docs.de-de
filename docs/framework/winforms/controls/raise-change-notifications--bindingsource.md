---
title: "Gewusst wie: Auslösen von Änderungsbenachrichtigungen mithilfe von BindingSource und der INotifyPropertyChanged-Schnittstelle"
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
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3983b2544a4586f6f53e19a7f5fcdcd384a6bc2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Gewusst wie: Auslösen von Änderungsbenachrichtigungen mithilfe von BindingSource und der INotifyPropertyChanged-Schnittstelle
Die <xref:System.Windows.Forms.BindingSource>-Komponente erkennt automatisch Änderungen in einer Datenquelle, wenn der in der Datenquelle enthaltene Typ die <xref:System.ComponentModel.INotifyPropertyChanged>-Schnittstelle implementiert und <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>-Ereignisse auslöst, sobald ein Eigenschaftswert geändert wird. Dies ist nützlich, da an die <xref:System.Windows.Forms.BindingSource> gebundene Steuerelemente automatisch aktualisiert werden, wenn sich die Datenquellenwerte ändern.  
  
> [!NOTE]
>  Wenn die Datenquelle <xref:System.ComponentModel.INotifyPropertyChanged> implementiert, sollten Sie beim Durchführen asynchroner Operationen keine Änderungen an der Datenquelle in einem Hintergrundthread vornehmen. Lesen Sie die Daten stattdessen in einem Hintergrundthread, und führen Sie sie in einer Liste auf dem UI-Thread zusammen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine einfache Implementierung der <xref:System.ComponentModel.INotifyPropertyChanged>-Schnittstelle. Darüber hinaus wird gezeigt, wie <xref:System.Windows.Forms.BindingSource> automatisch eine Datenquellenänderung an ein gebundenes Steuerelement übergibt, wenn <xref:System.Windows.Forms.BindingSource> an eine Liste des <xref:System.ComponentModel.INotifyPropertyChanged>-Typs gebunden ist.   
  
 Wenn Sie das `CallerMemberName`-Attribut verwenden, müssen Aufrufe der `NotifyPropertyChanged`-Methode den Eigenschaftennamen nicht als Zeichenfolgenargument angeben. Weitere Informationen finden Sie unter [Aufruferinformationen](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Verweise auf die Assemblys "System", "System.Data", "System.Drawing" und "System.Windows.Forms".  
  
 Informationen zum Erstellen dieses Beispiels über die Befehlszeile für [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] finden Sie unter [Erstellen von der Befehlszeile aus](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) oder [Erstellen über die Befehlszeile mit „csc.exe“](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Sie können dieses Beispiel auch in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] erstellen, indem Sie den Code in ein neues Projekt einfügen.  Siehe auch [HYPERLINK "http://msdn.microsoft.com/library/Bb129228 (110)" Vorgehensweise: Kompilieren und Ausführen einer vollständigen Windows Forms Code mit Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [BindingSource-Komponente](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Vorgehensweise: Auslösen von Änderungsbenachrichtigungen mit der ResetItem-Methode einer BindingSource](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
