---
title: Úloha upozornění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: adbddc2fb36e5036e535dfc1049945187fe14ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62558486"
---
# <a name="warning-task"></a>Warning – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zaznamená upozornění během sestavení na základě vyhodnoceného podmíněného příkazu.  
  
## <a name="parameters"></a>Parametry  
 Tabulka tato popisuje parametry `Warning` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Code`|Volitelný `String` parametr.<br /><br /> Kód upozornění, který se má přidružit k upozornění.|  
|`File`|Volitelný `String` parametr.<br /><br /> Určuje relevantní soubor, pokud existuje. Pokud není zadán žádný soubor, bude použit soubor obsahující varovná úloha.|  
|`HelpKeyword`|Volitelný `String` parametr.<br /><br /> Klíčové slovo Help pro přidružení k upozornění|  
|`Text`|Volitelný `String` parametr.<br /><br /> Text upozornění, který se [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zaznamená, pokud se `Condition` parametr vyhodnotí jako `true` .|  
  
## <a name="remarks"></a>Poznámky  
 `Warning`Úloha umožňuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektům kontrolovat přítomnost požadované konfigurace nebo vlastnosti před pokračováním v dalším kroku sestavení.  
  
 Pokud se `Condition` parametr `Warning` úlohy vyhodnotí jako `true` , hodnota `Text` parametru je protokolována a sestavení pokračuje v provádění. Pokud se `Condition` parametr neexisit, text upozornění se zaznamená do protokolu. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu kontroluje vlastnosti, které jsou nastaveny na příkazovém řádku. Pokud nejsou nastaveny žádné vlastnosti, projekt vyvolá událost upozornění a zaznamená hodnotu `Text` parametru `Warning` úkolu.  
  
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
 [Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
