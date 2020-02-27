---
title: Chybová úloha | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634224"
---
# <a name="error-task"></a>Error – úloha

Zastaví sestavení a zaznamená chybu na základě vyhodnoceného podmíněného příkazu.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy `Error`.

| Parametr | Popis |
|---------------| - |
| `Code` | Volitelný parametr `String`.<br /><br /> Kód chyby, který se má přidružit k chybě |
| `File` | Volitelný parametr `String`.<br /><br /> Název souboru, který obsahuje chybu. Pokud není zadán žádný název souboru, bude použit soubor obsahující chybovou úlohu. |
| `HelpKeyword` | Volitelný parametr `String`.<br /><br /> Klíčové slovo Help k přidružení k chybě |
| `Text` | Volitelný parametr `String`.<br /><br /> Chybový text, který nástroj MSBuild zaznamená, pokud je parametr `Condition` vyhodnocen jako `true`. |

## <a name="remarks"></a>Poznámky

Úloha `Error` umožňuje projektům MSBuild vystavovat chybový text pro protokolovací nástroje a zastavit provádění sestavení.

Pokud je parametr `Condition` vyhodnocen jako `true`, sestavení je zastaveno a zaprotokoluje se chyba. Pokud parametr `Condition` neexistuje, zaznamená se chyba a spuštění sestavení se zastaví. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad kódu ověřuje, zda jsou nastaveny všechny požadované vlastnosti. Pokud nejsou nastaveny, projekt vyvolá událost chyby a zaznamená hodnotu parametru `Text` úlohy `Error`.

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
