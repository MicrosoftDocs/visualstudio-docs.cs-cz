---
title: Podmínky msbuildu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbed62c13fc963af382ede113b138451303d9382
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759709"
---
# <a name="msbuild-conditions"></a>Podmínky msbuildu

MSBuild podporuje konkrétní sadu podmínek, které `Condition` lze použít všude tam, kde je povolen atribut. Tyto podmínky jsou vysvětleny v následující tabulce.

|Podmínka|Popis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Vyhodnotí `true` `stringA` if `stringB`rovná se .<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|'`stringA`' != '`stringB`'|`true` Vyhodnotí, `stringA` pokud není `stringB`rovno .<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí, `true` pokud je relační hodnocení true. Operandy musí být vyhodnoceny na desetinné nebo šestnáctkové číslo. Šestnáctková čísla musí začínat písmenem "0x". **Poznámka:**  V XML musí `<` `>` být znaky a musí být uvozeny. Symbol `<` je reprezentován jako `&lt;`. Symbol `>` je reprezentován jako `&gt;`.|
|Existuje('`stringA`')|Vyhodnotí, `true` zda existuje soubor `stringA` nebo složka s názvem.<br /><br /> Příklad:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|HasTrailingSlash('`stringA`')|Vyhodnotí, `true` pokud zadaný řetězec obsahuje koncový\\znak zpětného lomítka ( ) nebo lomítko (/).<br /><br /> Příklad:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|!|Vyhodnotí, `true` pokud operand `false`vyhodnotí .|
|And|Vyhodnotí, `true` pokud oba operandy vyhodnotit `true`.|
|Nebo|Vyhodnotí, `true` pokud alespoň jeden z operandů vyhodnotí `true`.|
|()|Seskupovací mechanismus, který vyhodnocuje, `true` pokud výrazy obsažené uvnitř vyhodnotit `true`.|
|$if$ ( %expression% ), $else$, $endif$|Zkontroluje, `%expression%` zda zadaný odpovídá řetězcové hodnotě předaného parametru vlastní šablony. Pokud `$if$` je podmínka `true`vyhodnocena do , pak jsou její příkazy spuštěny; v opačném `$else$` případě je podmínka zkontrolována. Pokud `$else$` je `true`podmínka , pak jeho příkazy jsou spuštěny; v opačném `$endif$` případě podmínka ukončí vyhodnocení výrazu.<br /><br /> Příklady použití naleznete v tématu [Visual Studio project/item template parameter logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Můžete použít metody řetězce v podmínkách, jak je znázorněno v následujícím příkladu, ve kterém [TrimEnd()](/dotnet/api/system.string.trimend) funkce se používá k porovnání pouze příslušné části řetězce, rozlišovat mezi rozhraní .NET Framework a .NET Core cílové architektury.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd('0123456789.'))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Viz také

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)
- [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
