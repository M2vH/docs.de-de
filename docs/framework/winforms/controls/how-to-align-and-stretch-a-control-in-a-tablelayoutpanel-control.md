---
title: 'Gewusst wie: Ausrichten und Strecken eines Steuerelements in einem TableLayoutPanel-Steuerelement'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8a852926f8b7a33fdaa1e2e16fea7eb1a1dac4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Gewusst wie: Ausrichten und Strecken eines Steuerelements in einem TableLayoutPanel-Steuerelement
Sie können das Ausrichten und Dehnen von Steuerelementen in einem <xref:System.Windows.Forms.TableLayoutPanel> mit der <xref:System.Windows.Forms.Control.Anchor%2A> und <xref:System.Windows.Forms.Control.Dock%2A> Eigenschaften.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-align-and-stretch-a-control"></a>Formen ausrichten und Strecken eines Steuerelements  
  
1.  Ziehen Sie eine <xref:System.Windows.Forms.TableLayoutPanel> -Steuerelement aus der **Toolbox** auf das Formular.  
  
2.  Ziehen Sie eine <xref:System.Windows.Forms.Button> -Steuerelement aus der **Toolbox** in der linken oberen Zelle von den <xref:System.Windows.Forms.TableLayoutPanel> Steuerelement. Die <xref:System.Windows.Forms.Button> Steuerelement wird in der Zelle zentriert.  
  
3.  Legen Sie den Wert, der die <xref:System.Windows.Forms.Button> des Steuerelements <xref:System.Windows.Forms.Control.Anchor%2A> Eigenschaft `Left,Right`. Die <xref:System.Windows.Forms.Button> Steuerung wird an die Breite der Zelle angepasst.  
  
4.  Legen Sie den Wert, der die <xref:System.Windows.Forms.Button> des Steuerelements <xref:System.Windows.Forms.Control.Anchor%2A> Eigenschaft `Top,Bottom`. Die <xref:System.Windows.Forms.Button> Steuerung wird an die Höhe der Zelle angepasst.  
  
5.  Legen Sie den Wert, der die <xref:System.Windows.Forms.Button> des Steuerelements <xref:System.Windows.Forms.Control.Dock%2A> Eigenschaft <xref:System.Windows.Forms.DockStyle.Fill>. Die <xref:System.Windows.Forms.Button> Steuerelement wird erweitert, um die gesamte Zelle ausfüllt.  
  
6.  Legen Sie den Wert, der die <xref:System.Windows.Forms.Button> des Steuerelements <xref:System.Windows.Forms.Control.Dock%2A> Eigenschaft <xref:System.Windows.Forms.DockStyle.None>. Die <xref:System.Windows.Forms.Button> Steuerelement gibt die ursprüngliche Größe und wird in der oberen linken Ecke der Zelle verschoben. Die **Windows Forms-Designer** festgelegt hat die <xref:System.Windows.Forms.Control.Anchor%2A> Eigenschaft `Top, Left`.  
  
7.  Legen Sie den Wert, der die <xref:System.Windows.Forms.Button> des Steuerelements <xref:System.Windows.Forms.Control.Anchor%2A> Eigenschaft `Bottom,Right`. Die <xref:System.Windows.Forms.Button> -Steuerelement wird in der unteren rechten Ecke der Zelle.  
  
8.  Legen Sie den Wert, der die <xref:System.Windows.Forms.Button> des Steuerelements <xref:System.Windows.Forms.Control.Anchor%2A> Eigenschaft <xref:System.Windows.Forms.AnchorStyles.None>. Die <xref:System.Windows.Forms.Button> Steuerelement bewegt wird, in die Mitte der Zelle.  
  
## <a name="see-also"></a>Siehe auch  
 [TableLayoutPanel-Steuerelement](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
