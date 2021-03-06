---
title: Energieverwaltung in Windows Forms
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
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7600ae42194b3333c404d217c2605a226df99e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="power-management-in-windows-forms"></a>Energieverwaltung in Windows Forms
Windows Forms-Anwendungen können die Power Management-Funktionen in Windows-Betriebssystems nutzen. Ihre Anwendungen können den Energiezustand eines Computers überwachen und Maßnahmen ergreifen, tritt eine statusänderung. Wenn Ihre Anwendung auf einem tragbaren Computer ausgeführt wird, sollten Sie z. B. bestimmte Funktionen in Ihrer Anwendung deaktivieren, wenn der Akku des Computers unter einer bestimmten Ebene liegt.  
  
 Die [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bietet eine <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> Ereignis, das auftritt, sobald sich eine Änderung im Energiestatus, z. B. wenn ein Benutzer hält oder das Betriebssystem, oder wenn der Status des AC oder Akkustatus ändert. Die <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Eigenschaft von der <xref:System.Windows.Forms.SystemInformation> Klasse kann Folgendes sein zur Abfrage für den aktuellen Status, wie im folgenden Codebeispiel gezeigt.  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Neben den <xref:System.Windows.Forms.BatteryChargeStatus> Enumerationen, die <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Eigenschaft enthält auch Enumerationen zur Bestimmung der Akkukapazität (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) und Akku Prozent Rechnung zu stellen (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Können Sie die <xref:System.Windows.Forms.Application.SetSuspendState%2A> Methode der <xref:System.Windows.Forms.Application> auf einen Computer in den Ruhezustand oder Standby-Modus. Wenn die `force` -Argument festgelegt wird `false`, das Betriebssystem ein Ereignis für alle Anwendungen, die Zustimmung zum Anhalten übertragen wird. Wenn die `disableWakeEvent` -Argument festgelegt wird `true`, des Betriebssystems deaktiviert alle Aktivierungsereignisse.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie auf einen Computer in den Ruhezustand versetzt wird.  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
