---
title: Úkol exec | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: f588ae1b32b8b8d47d6323ee32d02c9053a3de32
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634211"
---
# <a name="exec-task"></a>Exec – úloha

Spustí zadaný program nebo příkaz pomocí zadaných argumentů.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Exec` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Command`|Požadovaný parametr `String`.<br /><br /> Příkazy ke spuštění. Mohou to být systémové příkazy, například attrib, nebo spustitelný soubor, například *program.exe*, *runprogram.bat*nebo *setup.msi*.<br /><br /> Tento parametr může obsahovat více řádků příkazů. Případně můžete umístit více příkazů do dávkového souboru a spustit jej pomocí tohoto parametru.|
|`ConsoleOutput`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Každý výstup položky je řádek ze standardního výstupu nebo standardní chybový proud vyzařovaný nástrojem. Tato akce je `ConsoleToMsBuild` zachycena `true`pouze v případě, že je nastavena na .|
|`ConsoleToMsBuild`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha zachytí standardní chybu a standardní výstup nástroje a `ConsoleOutput` zpřístupní je ve výstupním parametru.<br /><br />Výchozí: `false`.|
|`CustomErrorRegularExpression`|Volitelný `String` parametr.<br /><br /> Určuje regulární výraz, který se používá k najetí chybových řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytvářejí neobvykle formátovaný výstup.<br /><br />Výchozí: `null` (žádné vlastní zpracování).|
|`CustomWarningRegularExpression`|Volitelný `String` parametr.<br /><br /> Určuje regulární výraz, který se používá k najetí výstražných řádků ve výstupu nástroje. To je užitečné pro nástroje, které vytvářejí neobvykle formátovaný výstup.<br /><br />Výchozí: `null` (žádné vlastní zpracování).|
|`EchoOff`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha nebude vyzařovat `Command` rozšířenou formu msbuild protokolu.<br /><br />Výchozí: `false`.|
|`ExitCode`|Volitelný `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je k dispozici provedeným příkazem.|
|`IgnoreExitCode`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha ignoruje ukončovací kód, který je k dispozici provedeným příkazem. V opačném případě `false` se úloha vrátí, pokud provedený příkaz vrátí nenulový ukončovací kód.<br /><br />Výchozí: `false`.|
|`IgnoreStandardErrorWarningFormat`|Volitelný `Boolean` parametr.<br /><br /> Pokud `false`vybere řádky ve výstupu, které odpovídají standardnímu formátu chyby/upozornění, a zaznamená je jako chyby/upozornění. Pokud `true`zakažte toto chování.<br /><br />Výchozí: `false`.|
|`Outputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výstupní položky z úkolu. Úloha `Exec` nenastaví tyto samotné. Místo toho je můžete poskytnout, jako by je nastavil, aby je bylo možné použít později v projektu.|
|`StdErrEncoding`|Volitelný `String` výstupní parametr.<br /><br /> Určuje kódování sběrného standardního datového proudu chyb. Výchozí je aktuální kódování výstupu konzoly.|
|`StdOutEncoding`|Volitelný `String` výstupní parametr.<br /><br /> Určuje kódování standardního výstupního datového proudu zachyceného úkolu. Výchozí je aktuální kódování výstupu konzoly.|
|`WorkingDirectory`|Volitelný `String` parametr.<br /><br /> Určuje adresář, ve kterém bude příkaz spuštěn.<br /><br />Výchozí: Aktuální pracovní adresář projektu.|

## <a name="remarks"></a>Poznámky

Tento úkol je užitečný, pokud není k dispozici konkrétní úloha MSBuild pro úlohu, kterou chcete provést. `Exec` Úkol však na rozdíl od konkrétnější úlohy nemůže provádět další operace zpracování nebo podmíněné operace na základě výsledku nástroje nebo příkazu, který je spuštěn.

Úloha `Exec` volá *cmd.exe* namísto přímého vyvolání procesu.

Kromě parametrů uvedených v tomto dokumentu tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [ToolTaskExtension base class](../msbuild/tooltaskextension-base-class.md).

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
