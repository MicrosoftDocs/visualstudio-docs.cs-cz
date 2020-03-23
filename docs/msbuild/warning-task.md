---
title: Výstražný úkol | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e95b59b4ccc0bd2df89e45512a5bdd05c027556
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631091"
---
# <a name="warning-task"></a>Warning – úloha

Protokoluje upozornění během sestavení na základě vyhodnoceného podmíněného příkazu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Warning` úkolu.

| Parametr | Popis |
|---------------| - |
| `Code` | Volitelný `String` parametr.<br /><br /> Kód upozornění přidružit k upozornění. |
| `File` | Volitelný `String` parametr.<br /><br /> Určuje příslušný soubor, pokud existuje. Pokud není k dispozici žádný soubor, soubor obsahující úlohu Upozornění se použije. |
| `HelpKeyword` | Volitelný `String` parametr.<br /><br /> Klíčové slovo nápovědy, které chcete přidružit k upozornění. |
| `Text` | Volitelný `String` parametr.<br /><br /> Text upozornění, který MSBuild `Condition` protokoluje, `true`pokud parametr vyhodnotí na . |

## <a name="remarks"></a>Poznámky

 Úkol `Warning` umožňuje MSBuild projekty zkontrolovat přítomnost požadované konfigurace nebo vlastnosti před pokračováním v dalším kroku sestavení.

 Pokud `Condition` je parametr `Warning` úlohy `true`vyhodnocen do `Text` , je hodnota parametru zaznamenána a sestavení pokračuje v provádění. Pokud `Condition` parametr neexistuje, je zaznamenán text upozornění. Další informace o protokolování naleznete v [tématu Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad kódu kontroluje vlastnosti, které jsou nastaveny na příkazovém řádku. Pokud nejsou nastaveny žádné vlastnosti, projekt vyvolá událost upozornění `Text` a zaznamená hodnotu parametru `Warning` úkolu.

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
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
