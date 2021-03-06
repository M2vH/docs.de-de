---
title: "Vorgehensweise: Öffnen des Dialogfelds"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e6201b7dbcc57a15583b7d95d6b603ab50e951a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-dialog-box"></a>Vorgehensweise: Öffnen des Dialogfelds
In diesem Beispiel wird gezeigt, wie ein Dialogfeld geöffnet wird.  
  
## <a name="example"></a>Beispiel  
 Ein Dialogfeld wird ein Fenster, das durch Instanziierung geöffnet wird <xref:System.Windows.Window> und Aufrufen der <xref:System.Windows.Window.ShowDialog%2A> Methode. <xref:System.Windows.Window.ShowDialog%2A>Öffnet ein Fenster, und gibt zurück, bis das neue Dialogfeld geschlossen wurde. Diese Art von Fenster ist auch bekannt als ein *modale* Fenster, und schränkt Benutzereingaben.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Aufrufen von <xref:System.Windows.Window.ShowDialog%2A> erfordert die Berechtigung, alle Fenster und Benutzereingabeereignisse uneingeschränkt verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Return a Dialog Box Result](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md) (Zurückgeben eines Dialogfeldergebnisses)
