---
title: "Abgeleitete Klassen können keine Basisklassenereignisse auslösen."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Abgeleitete Klassen können keine Basisklassenereignisse auslösen.
Ein Ereignis kann nur vom Deklarationsabschnitt ausgelöst werden, in der sie deklariert ist. Aus diesem Grund kann keine Klasse von einer anderen Klasse, eine Auslösen von Ereignissen von der sie abgeleitet ist.  
  
 **Fehler-ID:** BC30029  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Verschieben der `Event` Anweisung oder der `RaiseEvent` Anweisung, sodass sie sich in derselben Klasse befinden.  
  
## <a name="see-also"></a>Siehe auch  
 [Event-Anweisung](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent-Anweisung](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
