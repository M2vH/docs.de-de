---
title: 'Gewusst wie: Ausschneiden mit einem Bereich'
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 281ae701bc3e5cee38952a05474360019f76a665
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-clipping-with-a-region"></a>Gewusst wie: Ausschneiden mit einem Bereich
Eine der Eigenschaften von der <xref:System.Drawing.Graphics> Klasse ist die Clip-Bereich. Alle Zeichnungen geschieht, indem eine angegebene <xref:System.Drawing.Graphics> Objekt ist nur für den Ausschneidebereich dieses <xref:System.Drawing.Graphics> Objekt. Sie können die Clip-Bereich festlegen, durch Aufrufen der <xref:System.Drawing.Graphics.SetClip%2A> Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt einen Pfad, der ein einzelnes Polygon besteht. Anschließend erstellt der Code eine Region, basierend auf diesen Pfad. Die Region wird zum Übergeben der <xref:System.Drawing.Graphics.SetClip%2A> Methode eine <xref:System.Drawing.Graphics> -Objekt, und klicken Sie dann zwei Zeichenfolgen werden gezeichnet.  
  
 Die folgende Abbildung zeigt die abgeschnittenen Zeichenfolgen.  
  
 ![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Das obige Beispiel ist für die Verwendung in Windows Forms konzipiert und erfordert die <xref:System.Windows.Forms.PaintEventArgs> `e`-Klasse, die ein Parameter von <xref:System.Windows.Forms.PaintEventHandler> ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereiche in GDI+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Verwenden von Bereichen](../../../../docs/framework/winforms/advanced/using-regions.md)
