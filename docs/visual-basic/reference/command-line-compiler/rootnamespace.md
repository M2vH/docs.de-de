---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2017
---
# <a name="rootnamespace"></a>/rootnamespace
Gibt einen Namespace für alle Typdeklarationen an.  
  
## <a name="syntax"></a>Syntax  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|---|---|  
|`namespace`|Der Name des Namespace, in dem alle Typdeklarationen für das aktuelle Projekt zu schließen.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie die ausführbare Datei (Devenv.exe) von Visual Studio verwenden, um ein erstelltes Projekt kompilieren in der Visual Studio integrierten Entwicklungsumgebung verwenden `/rootnamespace` zum Angeben des Werts, der die <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> Eigenschaft. Finden Sie unter [Devenv-Befehlszeilenschalter](/visualstudio/ide/reference/devenv-command-line-switches) für Weitere Informationen.  
  
 Verwenden Sie die common Language Runtime MSIL-Disassembler (`Ildasm.exe`) die Namespacenamen in der Ausgabedatei an.  
  
|Zum Festlegen von/RootNamespace in Visual Studio integrierte Entwicklungsumgebung|  
|---|  
|1.  Ein Projekt auswählen in **Projektmappen-Explorer**. Klicken Sie im Menü **Projekt** auf **Eigenschaften**. <br />2.  Klicken Sie auf die Registerkarte **Anwendung** .<br />3.  Ändern Sie den Wert in der **Stamm-Namespace** Feld.|  
  
## <a name="example"></a>Beispiel  
 Der folgende code kompiliert `In.vb` eingeschlossen sind alle Deklarationen von Typen im Namespace `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Basic-Befehlszeilencompiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (IL-Disassembler)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Beispiele für Kompilierungsbefehlszeilen](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
