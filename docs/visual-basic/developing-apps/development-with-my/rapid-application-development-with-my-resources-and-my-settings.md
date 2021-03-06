---
title: Schnelle Anwendungsentwicklung mit My.Resources und My.Settings (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7339afdc35341739b592b2a327094754031c346c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Schnelle Anwendungsentwicklung mit My.Resources und My.Settings (Visual Basic)
Die `My.Resources` -Objekt ermöglicht den Zugriff auf die Ressourcen der Anwendung und ermöglicht Ihnen, Ressourcen für Ihre Anwendung dynamisch abzurufen.  
  
## <a name="retrieving-resources"></a>Abrufen von Ressourcen  
 Eine Reihe von Ressourcen wie Audiodateien, Symbole, Bilder und Zeichenfolgen abgerufen werden kann, über die `My.Resources` Objekt. Beispielsweise können Sie die Anwendung kulturspezifische Ressourcendateien zugreifen. Im folgenden Beispiel wird das Symbol des Formulars auf das Symbol mit dem Namen `Form1Icon` in der Anwendung Ressourcendatei gespeichert.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 Die `My.Resources` Objekt macht nur globale Ressourcen verfügbar. Es stellt nicht den Zugriff auf Formularen zugeordnete Ressourcendateien bereit. Sie müssen die Formularressourcen aus dem Formular zugreifen.  
  
 Auf ähnliche Weise die `My.Settings` Objekt ermöglicht den Zugriff auf die Einstellungen der Anwendung, und lassen sich dynamisch speichern und Abrufen von Einstellungen und andere Informationen für Ihre Anwendung. Weitere Informationen finden Sie unter [My.Resources-Objekt](../../../visual-basic/language-reference/objects/my-resources-object.md) und [My.Settings-Objekt](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Siehe auch  
 [My.Resources-Objekt](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [My.Settings-Objekt](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Zugreifen auf Anwendungseinstellungen](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
