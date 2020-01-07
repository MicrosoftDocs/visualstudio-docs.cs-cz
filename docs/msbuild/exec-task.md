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
ms.openlocfilehash: 78aef20a322ad3743ed1cb89955654456dff670e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591447"
---
# <a name="exec-task"></a>Exec – úloha
Spustí zadaný program nebo příkaz pomocí zadaných argumentů.

## <a name="parameters"></a>Parametry
Následující tabulka popisuje parametry pro úlohu `Exec`.

|Parametr|Popis|
|---------------|-----------------|
|`Command`|Vyžaduje se `String` parametr.<br /><br /> Příkazy, které mají být spuštěny. Může se jednat o systémové příkazy, jako je například attrib nebo spustitelný soubor, například *program. exe*, *runprogram. bat*nebo *Setup. msi*.<br /><br /> Tento parametr může obsahovat více řádků příkazů. Alternativně můžete do dávkového souboru vložit několik příkazů a spustit ho pomocí tohoto parametru.|
|`ConsoleOutput`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Výstup každé položky je řádek ze standardního výstupního nebo standardního chybového datového proudu vygenerovaného nástrojem. Je zachycena pouze v případě, že je `ConsoleToMsBuild` nastaveno na `true`.|
|`ConsoleToMsBuild`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, bude úloha zachytit standardní chybu a standardní výstup nástroje a zpřístupní je v parametru `ConsoleOutput` Output.<br /><br />Výchozí: `false`.|
|`CustomErrorRegularExpression`|Volitelný parametr `String`.<br /><br /> Určuje regulární výraz, který se používá k zaznamenání chybových řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytváří neobvykle formátovaný výstup.<br /><br />Výchozí: `null` (žádné vlastní zpracování).|
|`CustomWarningRegularExpression`|Volitelný parametr `String`.<br /><br /> Určuje regulární výraz, který se používá k vypsání výstražných řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytváří neobvykle formátovaný výstup.<br /><br />Výchozí: `null` (žádné vlastní zpracování).|
|`EchoOff`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, úloha negeneruje rozšířenou formu `Command` do protokolu MSBuild.<br /><br />Výchozí: `false`.|
|`ExitCode`|Volitelný `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytnut spuštěným příkazem.|
|`IgnoreExitCode`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, úloha ignoruje ukončovací kód, který je poskytnut spuštěným příkazem. V opačném případě úloha vrátí `false`, pokud se spustí příkaz, který vrátí nenulový ukončovací kód.<br /><br />Výchozí: `false`.|
|`IgnoreStandardErrorWarningFormat`|Volitelný parametr `Boolean`.<br /><br /> Pokud `false`, vyberou řádky ve výstupu, které odpovídají standardnímu formátu chyb nebo upozornění, a zaprotokoluje je jako chyby nebo upozornění. Pokud `true`, toto chování vypněte.<br /><br />Výchozí: `false`.|
|`Outputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje výstupní položky úkolu. `Exec` úloha je nenastavuje. Místo toho je můžete zadat, jako by ji nastavili, aby bylo možné je použít později v projektu.|
|`StdErrEncoding`|Volitelný výstupní parametr `String`.<br /><br /> Určuje kódování standardního streamu chyb zaznamenané úlohy. Výchozí hodnota je aktuální kódování výstupu konzoly.|
|`StdOutEncoding`|Volitelný výstupní parametr `String`.<br /><br /> Určuje kódování standardního výstupního datového proudu zachycené úlohy. Výchozí hodnota je aktuální kódování výstupu konzoly.|
|`WorkingDirectory`|Volitelný parametr `String`.<br /><br /> Určuje adresář, ve kterém se příkaz spustí.<br /><br />Výchozí: aktuální pracovní adresář projektu.|

## <a name="remarks"></a>Poznámky
Tato úloha je užitečná v případě, že konkrétní úloha [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] úlohy, kterou chcete provést, není k dispozici. `Exec` úloha ale na rozdíl od konkrétnější úlohy ale nemůže provádět další zpracování nebo podmíněné operace na základě výsledku nástroje nebo příkazu, který spouští.

Úloha `Exec` volá program *cmd. exe* namísto přímého vyvolání procesu.

Kromě parametrů uvedených v tomto dokumentu dědí tento úkol parametry z třídy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad
Následující příklad používá úlohu `Exec` ke spuštění příkazu.

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

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
