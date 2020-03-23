---
title: Chybová úloha | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5dd3214c9575a34e9265c33061b024648a221c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634224"
---
# <a name="error-task"></a>Error – úloha

Zastaví sestavení a zaznamená chybu na základě vyhodnoceného podmíněného příkazu.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Error` úkolu.

| Parametr | Popis |
|---------------| - |
| `Code` | Volitelný `String` parametr.<br /><br /> Kód chyby přidružit k chybě. |
| `File` | Volitelný `String` parametr.<br /><br /> Název souboru, který obsahuje chybu. Pokud není k dispozici žádný název souboru, bude použit soubor obsahující úlohu Chyba. |
| `HelpKeyword` | Volitelný `String` parametr.<br /><br /> Klíčové slovo nápovědy, které chcete přidružit k chybě. |
| `Text` | Volitelný `String` parametr.<br /><br /> Text chyby, který MSBuild `Condition` protokoluje, `true`pokud parametr vyhodnotí na . |

## <a name="remarks"></a>Poznámky

Úkol `Error` umožňuje MSBuild projekty vydávat chybový text do úhozů kláves a zastavit provádění sestavení.

Pokud `Condition` je parametr `true`vyhodnocen do , sestavení je zastaveno a je zaznamenána chyba. Pokud `Condition` parametr neexistuje, je zaznamenána chyba a zastavení spuštění sestavení. Další informace o protokolování naleznete v [tématu Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad kódu ověří, zda jsou nastaveny všechny požadované vlastnosti. Pokud nejsou nastaveny, projekt vyvolá chybovou událost a zaznamená hodnotu `Text` parametru `Error` úkolu.

```xml
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

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
