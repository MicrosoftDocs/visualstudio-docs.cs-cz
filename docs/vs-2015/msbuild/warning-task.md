---
title: Warning – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0447c3803de6845dcfb02a30270cfe9b96b96f0a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213589"
---
# <a name="warning-task"></a>Warning – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Protokoly upozornění během sestavení podle Vyhodnocená podmíněném příkazu.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Warning` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Code`|Volitelné `String` parametru.<br /><br /> Kód upozornění pro přidružení k upozornění.|  
|`File`|Volitelné `String` parametru.<br /><br /> Určuje příslušný soubor, pokud existuje. Pokud není žádný soubor zadaný v souboru, který obsahuje upozornění úkolů se používá.|  
|`HelpKeyword`|Volitelné `String` parametru.<br /><br /> Klíčové slovo nápovědy pro přidružení k upozornění.|  
|`Text`|Volitelné `String` parametru.<br /><br /> Text upozornění, která [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] protokoly, pokud `Condition` vyhodnotí jako parametr `true`.|  
  
## <a name="remarks"></a>Poznámky  
 `Warning` Úloha umožňuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty ke kontrole přítomnosti požadovanou konfiguraci nebo vlastnost před pokračováním na další krok sestavení.  
  
 Pokud `Condition` parametr `Warning` vyhodnotí jako úloha `true`, hodnota `Text` parametr je zaznamenána do protokolu a pokračuje v provádění sestavení. Pokud `Condition` parametr nemá případech není, se do protokolu zapíše text upozornění. Další informace o protokolování naleznete v tématu [získávání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu zkontroluje pro vlastnosti, které jsou nastaveny na příkazovém řádku. Pokud neexistují žádná sada vlastností, vyvolá událost upozornění projektu a protokoly hodnotu `Text` parametr `Warning` úloh.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Získávání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)



