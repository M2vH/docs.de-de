---
title: 'Gewusst wie: Verwalten lokalisierbarer Zeichenfolgenressourcen mit einem ResourceDictionary'
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
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fba115ea8c954da177afcacbf679f41474e2b68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Gewusst wie: Verwalten lokalisierbarer Zeichenfolgenressourcen mit einem ResourceDictionary
Dieses Beispiel zeigt, wie eine <xref:System.Windows.ResourceDictionary> Paket lokalisierbare Zeichenfolgenressourcen für [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Anwendungen.  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>So verwenden Sie ResourceDictionary zum Verwalten lokalisierbarer Zeichenfolgenressourcen  
  
1.  Erstellen einer <xref:System.Windows.ResourceDictionary> , enthält die Zeichenfolgen, die Sie lokalisieren möchten. Der folgende Code zeigt ein Beispiel.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Dieser Code definiert eine Zeichenfolgenressource `localizedMessage`, des Typs <xref:System.String>, aus der <xref:System> -Namespace in "mscorlib.dll".  
  
2.  Hinzufügen der <xref:System.Windows.ResourceDictionary> für Ihre Anwendung mithilfe des folgenden Codes.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  Verwenden Sie die Zeichenfolgenressource über das Markup, mit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wie folgt.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  Verwenden Sie die Zeichenfolge von CodeBehind mithilfe von Code so wie folgt.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  Lokalisieren Sie die Anwendung. Weitere Informationen finden Sie unter [Lokalisieren einer Anwendung](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).
