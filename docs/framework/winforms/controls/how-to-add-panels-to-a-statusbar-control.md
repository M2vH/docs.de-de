---
title: "Gewusst wie: Hinzufügen von Bereichen zu einem StatusBar-Steuerelement"
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
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96fbfc86183afef047d210fbc13a0944f2b209b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>Gewusst wie: Hinzufügen von Bereichen zu einem StatusBar-Steuerelement
> [!IMPORTANT]
>  Die <xref:System.Windows.Forms.StatusStrip> und <xref:System.Windows.Forms.ToolStripStatusLabel> Steuerelemente ersetzen und Funktionen hinzufügen der <xref:System.Windows.Forms.StatusBar> und <xref:System.Windows.Forms.StatusBarPanel> steuert; allerdings die <xref:System.Windows.Forms.StatusBar> und <xref:System.Windows.Forms.StatusBarPanel> Steuerelemente werden für die Abwärtskompatibilität und für zukünftige Verwendung beibehalten, wenn Sie Wählen Sie aus.  
  
 Der programmierbare Bereich innerhalb einer [StatusBar-Steuerelement](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) Steuerelement besteht aus Instanzen von der <xref:System.Windows.Forms.StatusBarPanel> Klasse. Diese werden hinzugefügt, durch Hinzufügungen zu den <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> Klasse.  
  
### <a name="to-add-panels-to-a-status-bar"></a>Eine Statusleiste Bereiche hinzu  
  
1.  Erstellen Sie in einer Prozedur Statusleistenbereichs durch Hinzufügen der <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>. Geben Sie eigenschafteneinstellungen für einzelne Bereiche anhand des zugehörigen Indexes durch Übergeben der <xref:System.Windows.Forms.StatusBar.Panels%2A> Eigenschaft.  
  
     Im folgenden Codebeispiel legen der Pfad für der Speicherort des Symbols wird die **eigene** Ordner. Dieser Speicherort wird verwendet, da Sie davon ausgehen können, dass dieser Ordner die meisten Computer das Windows-Betriebssystem ausgeführt wird enthält. Dieser Speicherort kann sich Benutzer mit minimalen sicher auf die Anwendung auszuführen. Das folgende Beispiel erfordert ein Formular mit einem <xref:System.Windows.Forms.StatusBar> Steuerelement bereits hinzugefügt.  
  
    > [!NOTE]
    >  Die <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> ist nullbasiert, damit der Code entsprechend fortgesetzt werden soll.  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =   
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image   
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Auflistungs-Editor (Dialogfeld)](http://msdn.microsoft.com/en-us/53fb3aad-bffa-4da5-ac89-8438e6fc803c)  
 [Gewusst wie: Festlegen der Größe eines Statusleistenbereichs](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [Exemplarische Vorgehensweise: Aktualisieren von Statusleisteninformationen zur Laufzeit](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [Vorgehensweise: Bestimmen, auf welchen Bereich im StatusBar-Steuerelement in Windows Forms geklickt wurde](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [Übersicht über das StatusBar-Steuerelement](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
