---
title: Úloha upozornění | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu upozornění k protokolování upozornění během sestavení na základě vyhodnoceného podmíněného příkazu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f31ad26b6efffa540ecae6a61f0f7ff12115cef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933801"
---
# <a name="warning-task"></a>Warning – úloha

Zaznamená upozornění během sestavení na základě vyhodnoceného podmíněného příkazu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Warning` úkolu.

| Parametr | Popis |
|---------------| - |
| `Code` | Volitelný `String` parametr.<br /><br /> Kód upozornění, který se má přidružit k upozornění. |
| `File` | Volitelný `String` parametr.<br /><br /> Určuje relevantní soubor, pokud existuje. Pokud není zadán žádný soubor, bude použit soubor obsahující varovná úloha. |
| `HelpKeyword` | Volitelný `String` parametr.<br /><br /> Klíčové slovo Help pro přidružení k upozornění |
| `Text` | Volitelný `String` parametr.<br /><br /> Text upozornění, který nástroj MSBuild zaznamená, pokud je `Condition` parametr vyhodnocen jako `true` . |

## <a name="remarks"></a>Poznámky

 `Warning`Úloha umožňuje projektům MSBuild kontrolovat přítomnost požadované konfigurace nebo vlastnosti před pokračováním v dalším kroku sestavení.

 Pokud se `Condition` parametr `Warning` úlohy vyhodnotí jako `true` , hodnota `Text` parametru je protokolována a sestavení pokračuje v provádění. Pokud `Condition` parametr neexistuje, text upozornění se zaznamená do protokolu. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad kódu kontroluje vlastnosti, které jsou nastaveny na příkazovém řádku. Pokud nejsou nastaveny žádné vlastnosti, projekt vyvolá událost upozornění a zaznamená hodnotu `Text` parametru `Warning` úkolu.

```xml
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

- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
