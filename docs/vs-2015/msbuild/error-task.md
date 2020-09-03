---
title: Chybová úloha | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b220d12b872a81cba5f46bd14fdebafaa58cf4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201815"
---
# <a name="error-task"></a>Error – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zastaví sestavení a zaznamená chybu na základě vyhodnoceného podmíněného příkazu.  
  
## <a name="parameters"></a>Parametry  
 Tabulka tato popisuje parametry `Error` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Code`|Volitelný `String` parametr.<br /><br /> Kód chyby, který se má přidružit k chybě|  
|`File`|Volitelný `String` parametr.<br /><br /> Název souboru, který obsahuje chybu. Pokud není zadán žádný název souboru, bude použit soubor obsahující chybovou úlohu.|  
|`HelpKeyword`|Volitelný `String` parametr.<br /><br /> Klíčové slovo Help k přidružení k chybě|  
|`Text`|Volitelný `String` parametr.<br /><br /> Text chyby, který se [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zaznamená, pokud se `Condition` parametr vyhodnotí jako `true` .|  
  
## <a name="remarks"></a>Poznámky  
 `Error`Úloha umožňuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektům vystavovat chybový text pro protokolovací nástroje a zastavit provádění sestavení.  
  
 Pokud je `Condition` parametr vyhodnocen jako `true` , je sestavení zastaveno a dojde k zaznamenání chyby. Pokud `Condition` parametr neexistuje, zaznamená se chyba a spuštění sestavení se zastaví. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ověřuje, zda jsou nastaveny všechny požadované vlastnosti. Pokud nejsou nastaveny, projekt vyvolá událost chyby a zaznamená hodnotu `Text` parametru `Error` úkolu.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Získávání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
