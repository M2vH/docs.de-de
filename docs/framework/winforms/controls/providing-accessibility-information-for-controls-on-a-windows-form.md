---
title: "Informationen über Eingabehilfen für Steuerelemente in Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b7c0d570dbb6389ef22dba635bbbc2885c5f3a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Informationen über Eingabehilfen für Steuerelemente in Windows Forms
Eingabehilfen sind spezielle Programme und Geräte, die es Personen mit Behinderungen ermöglichen, einen Computer effizienter zu nutzen. Beispiele hierfür sind Sprachausgaben für Blinde sowie Spracheingabe-Hilfsprogramme für Personen, die verbale Befehle geben, statt Maus oder Tastatur zu verwenden. Diese Eingabehilfen interagieren mit den Eingabehilfeeigenschaften, die von Windows Forms-Steuerelementen verfügbar gemacht werden. Dies sind die folgenden Eigenschaften:  
  
-   **AccessibilityObject**  
  
-   **AccessibleDefaultActionDescription**  
  
-   **AccessibleDescription**  
  
-   **AccessibleName**  
  
-   **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>AccessibilityObject-Eigenschaft  
 Diese schreibgeschützte Eigenschaft enthält eine Instanz der <xref:System.Windows.Forms.AccessibleObject> . Die **AccessibleObject** -Klasse implementiert die <xref:Accessibility.IAccessible> -Schnittstelle, die Informationen zur Beschreibung, zur Bildschirmposition, zu den Navigationsfähigkeiten und zum Wert des Steuerelements enthält. Der Entwickler legt diesen Wert fest, wenn das Steuerelement zum Formular hinzugefügt wird.  
  
## <a name="accessibledefaultactiondescription-property"></a>AccessibleDefaultActionDescription-Eigenschaft  
 Diese Zeichenfolge beschreibt die Aktion des Steuerelements. Sie wird nicht im Eigenschaftenfenster angezeigt und kann nur in Code festgelegt werden. Im folgenden Beispiel wird diese Eigenschaft für ein Schaltflächen-Steuerelement (Button) festgelegt.  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a>Control.AccessibleDescription-Eigenschaft  
 Diese Zeichenfolge beschreibt das Steuerelement. Sie kann im Eigenschaftenfenster oder wie folgt in Code festgelegt werden:  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Control.AccessibleName-Eigenschaft  
 Diese Eigenschaft enthält den Namen des Steuerelements, der an Eingabehilfen gemeldet wird. Sie kann im Eigenschaftenfenster oder wie folgt in Code festgelegt werden:  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>AccessibleRole-Eigenschaft  
 Diese Eigenschaft, die eine <xref:System.Windows.Forms.AccessibleRole> enthält, beschreibt die Rolle des Steuerelements in der Benutzeroberfläche. Bei einem neuen Steuerelement ist die Eigenschaft auf `Default`festgelegt. Das heißt, dass sich ein **Schaltflächen** -Steuerelement standardmäßig wie eine **Schaltfläche**verhält. Sie können diese Eigenschaft auf einen anderen Wert festlegen, wenn das jeweilige Steuerelement eine andere Rolle hat. Beispielsweise könnte es sein, dass Sie ein **PictureBox** -Steuerelement als **Diagramm**verwenden und möchten, dass Eingabehilfen die Rolle als **Diagramm**, nicht als **PictureBox**melden. Es ist auch möglich, dass Sie diese Eigenschaft für benutzerdefinierte Steuerelemente angeben, die Sie entwickelt haben. Diese Eigenschaft kann im Eigenschaftenfenster oder wie folgt in Code festgelegt werden:  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.AccessibleObject>  
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.AccessibleRole>
