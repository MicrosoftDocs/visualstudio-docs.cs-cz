---
title: Chybová úloha | Microsoft Docs
description: Použijte úlohu chyby nástroje MSBuild k zastavení sestavení a Zaprotokolujte chybu na základě vyhodnoceného podmíněného příkazu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e4e1a91bc018bdf77671b13994ce57e4e10e694
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877197"
---
# <a name="error-task"></a>Error – úloha

Zastaví sestavení a zaznamená chybu na základě vyhodnoceného podmíněného příkazu.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Error` úkolu.

| Parametr | Popis |
|---------------| - |
| `Code` | Volitelný `String` parametr.<br /><br /> Kód chyby, který se má přidružit k chybě |
| `File` | Volitelný `String` parametr.<br /><br /> Název souboru, který obsahuje chybu. Pokud není zadán žádný název souboru, bude použit soubor obsahující chybovou úlohu. |
| `HelpKeyword` | Volitelný `String` parametr.<br /><br /> Klíčové slovo Help k přidružení k chybě |
| `Text` | Volitelný `String` parametr.<br /><br /> Chybový text, který nástroj MSBuild zaznamená, pokud je `Condition` parametr vyhodnocen jako `true` . |

## <a name="remarks"></a>Poznámky

`Error`Úloha umožňuje projektům MSBuild vystavovat chybový text pro protokolovací nástroje a zastavit provádění sestavení.

Pokud je `Condition` parametr vyhodnocen jako `true` , je sestavení zastaveno a dojde k zaznamenání chyby. Pokud `Condition` parametr neexistuje, zaznamená se chyba a spuštění sestavení se zastaví. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad kódu ověřuje, zda jsou nastaveny všechny požadované vlastnosti. Pokud nejsou nastaveny, projekt vyvolá událost chyby a zaznamená hodnotu `Text` parametru `Error` úkolu.

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

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
