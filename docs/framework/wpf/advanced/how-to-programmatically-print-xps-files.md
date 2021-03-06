---
title: 'Gewusst wie: Programmgesteuertes Drucken von XPS-Dateien'
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
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 402568a78ccb2f56c6adb108536edfb121440642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-print-xps-files"></a>Gewusst wie: Programmgesteuertes Drucken von XPS-Dateien
Können Sie eine Überladung des der <xref:System.Printing.PrintQueue.AddJob%2A> Methode zum Drucken [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] Dateien ohne Öffnen einer <xref:System.Windows.Controls.PrintDialog> oder im Prinzip alle [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] überhaupt.  
  
 Sie können auch drucken [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] Dateien mit vielen <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> und <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> Methoden die <xref:System.Windows.Xps.XpsDocumentWriter>. Weitere Informationen dazu finden Sie unter [Drucken eines XPS-Dokuments](http://msdn.microsoft.com/en-us/849555c8-0c4e-48c0-86bc-a5494c69b36c).  
  
 Eine andere Möglichkeit der Druckfunktion von [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] ist die Verwendung der <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> oder <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> Methoden die <xref:System.Windows.Controls.PrintDialog> Steuerelement. Weitere Informationen finden Sie unter [Aufrufen eines Druckdialogfelds](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Beispiel  
 Die wichtigsten Schritte zur Verwendung des drei-Parameters <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> Methode lauten wie folgt. Im folgenden Beispiel werden Details.  
  
1.  Stellen Sie fest, ob es sich bei dem Drucker um einen XPSDrv-Drucker handelt. (Weitere Informationen zu XPSDrv finden Sie unter [Übersicht über das Drucken](../../../../docs/framework/wpf/advanced/printing-overview.md).)  
  
2.  Wenn es sich bei dem Drucker nicht um einen XPSDrv-Drucker handelt, legen Sie das Apartment des Threads auf Singlethread fest.  
  
3.  Instanziieren Sie einen Druckerserver und ein Druckwarteschlangenobjekt.  
  
4.  Rufen Sie die Methode, und geben einen Auftragsnamen an, die Datei, die gedruckt werden, und ein <xref:System.Boolean> flag, das angibt, ob der Drucker einen XPSDrv-Drucker ist.  
  
 Im folgenden Beispiel wird gezeigt, wie alle [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Dateien in einem Verzeichnis als Batch gedruckt werden. Obwohl die Anwendung den Benutzer zum Angeben des Verzeichnisses, das drei Parameter auffordert <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> Methode erfordert keine [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Sie kann in jedem Codepfad verwendet werden, in dem ein [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Dateiname und -Pfad vorhanden sind, die an sie übergeben werden können.  
  
 Die drei Parameter <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> Überladung der <xref:System.Printing.PrintQueue.AddJob%2A> muss in einem Singlethread-Apartment ausgeführt immer die <xref:System.Boolean> Parameter ist `false`, der er sein muss, wenn ein XPSDrv-Drucker verwendet wird. Mehrere Threads sind jedoch der Standardapartmentzustand für [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]. Dieser Standard muss umgekehrt werden, da im Beispiel kein XPSDrv-Drucker angenommen wird.  
  
 Es gibt zwei Möglichkeiten, die Standardeinstellung zu ändern. Fügen Sie einfach eine Möglichkeit ist die <xref:System.STAThreadAttribute> (d. h. "`[System.STAThreadAttribute()]`") direkt über die erste Zeile der Anwendung `Main` Methode (in der Regel "`static void Main(string[] args)`"). Viele Anwendungen erfordern jedoch, die die `Main` Methode verfügen über einen Multithread-Apartment-Zustand aus, damit die zweite Methode ist: den Aufruf von put <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> in einem separaten Thread, der Apartmentzustand, um festgelegt ist <xref:System.Threading.ApartmentState.STA> mit <xref:System.Threading.Thread.SetApartmentState%2A>. Im folgenden Beispiel wird dieses zweite Verfahren verwendet.  
  
 Das Beispiel beginnt durch Instanziierung entsprechend einer <xref:System.Threading.Thread> Objekt und zur Übergabe an eine **PrintXPS** -Methode, wie die <xref:System.Threading.ThreadStart> Parameter. (Die **PrintXPS**-Methode wird später im Beispiel definiert.) Danach wird der Thread auf ein Singlethreadapartment festgelegt. Mit dem verbleibenden Code der `Main`-Methode wird der neue Thread gestartet.  
  
 In diesem Beispiel geht es im Wesentlichen um die `static`**BatchXPSPrinter.PrintXPS**-Methode. Nach dem Erstellen eines Druckerservers und einer Druckwarteschlange wird der Benutzer von der Methode aufgefordert, ein Verzeichnis anzugeben, das [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Dateien enthält. Nachdem überprüft wurde, ob das Verzeichnis vorhanden ist und XPS-Dateien enthält, fügt die Methode jede dieser Dateien der Druckwarteschlange hinzu. Das Beispiel setzt voraus, dass der Drucker nicht-XPSDrv, ist, damit wir übergeben `false` auf den letzten Parameter <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> Methode. Aus diesem Grund überprüft die Methode das [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Markup in der Datei, bevor sie versucht, es in die Seitenbeschreibungssprache des Druckers umzuwandeln. Wenn die Validierung fehlschlägt, wird eine Ausnahme ausgelöst. Im Beispielcode wird die Ausnahme abgefangen, der Benutzer wird darüber informiert, und anschließend wird die nächste [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Datei verarbeitet.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Wenn Sie einen XPSDrv-Drucker verwenden, können Sie den abschließenden Parameter auf `true` festlegen. Da [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] die Seitenbeschreibungssprache des Druckers ist, sendet die Methode in diesem Fall die Datei ohne Überprüfung oder Umwandlung in eine andere Seitenbeschreibungssprache an den Drucker. Wenn Sie unsicher zur Entwurfszeit sind, ob die Anwendung einen XPSDrv-Drucker verwenden werden, können Sie die Anwendung zu lesen sein ändern die <xref:System.Printing.PrintQueue.IsXpsDevice%2A> -Eigenschaft und die Verzweigung entsprechend ReadState.Initial.  
  
 Da unmittelbar nach der Veröffentlichung von [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] und [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] nur wenige XPSDrv-Drucker zur Verfügung stehen werden, müssen Sie Nicht-XPSDrv-Drucker ggf. als XPSDrv-Drucker tarnen. Fügen Sie hierzu auf dem Computer, der die Anwendung ausführt, im folgenden Registrierungsschlüssel die Datei „Pipelineconfig.xml“ zur Liste der Dateien hinzu:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>*\DependentFiles  
  
 wobei *\<PseudoXPSPrinter>* für eine beliebige Druckwarteschlange steht. Der Computer muss anschließend neu gestartet werden.  
  
 Diese folgende Warnung aus können Sie durch Übergabe `true` als letzten Parameter der <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> ohne eine Ausnahme aus, da  *\<PseudoXPSPrinter für eine >* ist keine notfallwiederherstellungstopologie XPSDrv-Drucker auslösen.  
  
 **Hinweis** Der Einfachheit halber gilt im oben stehenden Beispiel das Vorhandensein der Dateinamenserweiterung XPS als Beleg dafür, dass es sich bei einer Datei um eine [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Datei handelt. [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Dateien müssen diese Erweiterung jedoch nicht haben. [isXPS.exe (isXPS-Tool für Übereinstimmungstests)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3) ist eine Möglichkeit, eine Datei auf [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Gültigkeit zu testen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](http://www.microsoft.com/xps)  
 [Drucken eines XPS-Dokuments](http://msdn.microsoft.com/en-us/849555c8-0c4e-48c0-86bc-a5494c69b36c)  
 [Verwaltete und nicht verwaltetes Threading](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [isXPS.exe (isXPS-Tool für Übereinstimmungstests)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3)  
 [Dokumente in WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Übersicht über das Drucken](../../../../docs/framework/wpf/advanced/printing-overview.md)
