---
title: -appconfig (C#-Compileroptionen)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords: /appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca752c6264d0ee886aa4c248738097e0caf1d756
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="appconfig-c-compiler-options"></a>/appconfig (C#-Compileroptionen)
Mit der Compileroption **/appconfig** kann eine C#-Anwendung den Speicherort der Anwendungskonfigurationsdatei („app.config“) der Assembly für die Common Language Runtime (CLR) zur Assemblybindungszeit festlegen.  
  
## <a name="syntax"></a>Syntax  
  
```console  
/appconfig:file  
```  
  
## <a name="arguments"></a>Argumente  
 `file`  
 Erforderlich. Die Anwendungskonfigurationsdatei mit den Assemblybindungseinstellungen  
  
## <a name="remarks"></a>Hinweise  
 Der Gebrauch von **/appconfig** ist ein erweitertes Szenario, in dem eine Assembly gleichzeitig auf die Version von .NET Framework und von .NET Framework for Silverlight einer bestimmten Verweisassembly verweisen muss. Ein in Windows Presentation Foundation (WPF) geschriebener XAML-Designer muss möglicherweise für die Benutzeroberfläche des Designers sowohl auf den WPF-Desktop als auch auf die Teilmenge von WPF, die in Silverlight enthalten ist, verweisen. Dieselbe Designerassembly muss auf beide Assembly zugreifen. Standardmäßig verursachen die separaten Verweise einen Compilerfehler, da die Assemblybindung die zwei Assemblys als Entsprechung ansieht.  
  
 Mit der Compileroption **/appconfig** können Sie den Speicherort einer app.config-Datei festlegen, die das Standardverhalten mit dem `<supportPortability>`-Tag deaktiviert, wie in folgendem Beispiel gezeigt.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Der Compiler übergibt den Speicherort der Datei an die Assemblybindungslogik der CLR.  
  
> [!NOTE]
>  Wenn Sie das Microsoft-Buildmodul (MSBuild) verwenden, um Ihre Anwendung zu erstellen, können Sie die Compileroption **/appconfig** festlegen, indem Sie ein Eigenschaftentag in die CSPROJ-Datei einfügen. Fügen Sie den Eigenschaftentag `<UseAppConfigForCompiler>` in die CSPROJ-Datei ein, und legen Sie dessen Wert auf `true` fest, um die app.config-Datei zu verwenden, die bereits im Projekt angegeben ist. Fügen Sie den Eigenschaftentag `<AppConfigForCompiler>` in die CSPROJ-Datei ein, und legen Sie dessen Wert auf den Speicherort der Datei fest, um eine andere app.config-Datei anzugeben.  
  
## <a name="example"></a>Beispiel  
 In folgendem Beispiel wird eine app.config-Datei gezeigt, die es einer Anwendung ermöglicht, über Verweise sowohl auf die .NET Framework-Implementierung als auch die .NET Framework for Silverlight-Implementierung jeder .NET Framework-Assembly zu verfügen, die in beiden Implementierungen vorhanden ist. Die Compileroption **/appconfig** gibt den Speicherort der app.config-Datei an.  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<SupportPortability >-Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [C#-Compileroptionen alphabetisch sortiert](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
