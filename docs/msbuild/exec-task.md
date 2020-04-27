---
title: Úloha Exec | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 634916d9ab4ef0ce3119fcb5695301598992f38c
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167294"
---
# <a name="exec-task"></a>Exec – úloha

Spustí zadaný program nebo příkaz pomocí zadaných argumentů.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry pro `Exec` úlohu.

|Parametr|Popis|
|---------------|-----------------|
|`Command`|Požadovaný parametr `String`.<br /><br /> Příkazy, které mají být spuštěny. Může se jednat o systémové příkazy, jako je například attrib nebo spustitelný soubor, například *program. exe*, *runprogram. bat*nebo *Setup. msi*.<br /><br /> Tento parametr může obsahovat více řádků příkazů. Alternativně můžete do dávkového souboru vložit několik příkazů a spustit ho pomocí tohoto parametru.|
|`ConsoleOutput`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Výstup každé položky je řádek ze standardního výstupního nebo standardního chybového datového proudu vygenerovaného nástrojem. Je zachycena pouze v `ConsoleToMsBuild` případě, že `true`je nastavena na.|
|`ConsoleToMsBuild`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`bude úloha zachytit standardní chybu a standardní výstup nástroje a zpřístupní je v parametru `ConsoleOutput` Output.<br /><br />Výchozí: `false`.|
|`CustomErrorRegularExpression`|Volitelný `String` parametr.<br /><br /> Určuje regulární výraz, který se používá k zaznamenání chybových řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytváří neobvykle formátovaný výstup.<br /><br />Výchozí: `null` (žádné vlastní zpracování).|
|`CustomWarningRegularExpression`|Volitelný `String` parametr.<br /><br /> Určuje regulární výraz, který se používá k vypsání výstražných řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytváří neobvykle formátovaný výstup.<br /><br />Výchozí: `null` (žádné vlastní zpracování).|
|`EchoOff`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha nevydá rozšířený tvar nástroje `Command` k protokolu MSBuild.<br /><br />Výchozí: `false`.|
|`ExitCode`|Volitelný `Int32` výstup – parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytnut spuštěným příkazem.|
|`IgnoreExitCode`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, úloha ignoruje ukončovací kód, který je poskytnut spuštěným příkazem. V opačném případě se `false` úloha vrátí, pokud se spustí příkaz, který vrátí nenulový ukončovací kód.<br /><br />Výchozí: `false`.|
|`IgnoreStandardErrorWarningFormat`|Volitelný `Boolean` parametr.<br /><br /> Pokud `false`se vybere řádky ve výstupu, které odpovídají standardnímu formátu chyb nebo upozornění, a zaprotokoluje je jako chyby nebo upozornění. V `true`takovém případě toto chování zakažte.<br /><br />Výchozí: `false`.|
|`Outputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výstupní položky úkolu. Tato `Exec` úloha je nenastavuje. Místo toho je můžete zadat, jako by ji nastavili, aby bylo možné je použít později v projektu.|
|`StdErrEncoding`|Volitelný `String` výstupní parametr.<br /><br /> Určuje kódování standardního streamu chyb zaznamenané úlohy. Výchozí hodnota je aktuální kódování výstupu konzoly.|
|`StdOutEncoding`|Volitelný `String` výstupní parametr.<br /><br /> Určuje kódování standardního výstupního datového proudu zachycené úlohy. Výchozí hodnota je aktuální kódování výstupu konzoly.|
|`WorkingDirectory`|Volitelný `String` parametr.<br /><br /> Určuje adresář, ve kterém se příkaz spustí.<br /><br />Výchozí: aktuální pracovní adresář projektu.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>Poznámky

Tato úloha je užitečná v případě, že konkrétní úloha MSBuild pro úlohu, kterou chcete provést, není k dispozici. `Exec` Úkol na rozdíl od konkrétnější úlohy ale nemůže provádět další zpracování nebo podmíněné operace na základě výsledku nástroje nebo příkazu, který spouští.

`Exec` Úloha volá program *cmd. exe* místo přímého vyvolání procesu.

## <a name="example"></a>Příklad

Následující příklad používá `Exec` úlohu ke spuštění příkazu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Binaries Include="*.dll;*.exe"/>
    </ItemGroup>

    <Target Name="SetACL">
        <!-- set security on binaries-->
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
