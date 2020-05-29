---
title: Podmínky nástroje MSBuild | Microsoft Docs
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
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 926c54be9d31a6d0708b33248b6887c0ac7e324e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184065"
---
# <a name="msbuild-conditions"></a>Podmínky nástroje MSBuild

Nástroj MSBuild podporuje konkrétní sadu podmínek, které lze použít všude, kde `Condition` je atribut povolen. Tyto podmínky jsou vysvětleny v následující tabulce.

|Podmínka|Popis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Vyhodnotí jako, `true` Pokud `stringA` je rovno `stringB` .<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky. U této kontroly se nerozlišují malá a velká písmena.|
|'`stringA`' != '`stringB`'|Vyhodnotí, `true` Pokud `stringA` není rovno `stringB` .<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky. U této kontroly se nerozlišují malá a velká písmena.|
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí, `true` zda je relační vyhodnocení pravdivé. Operandy musí být vyhodnoceny jako desítkové nebo šestnáctkové číslo. Šestnáctková čísla musí začínat znakem "0x". **Poznámka:**  V jazyce XML jsou znaky `<` a `>` musí být uvozeny řídicím znakem. Symbol `<` je reprezentován jako `&lt;` . Symbol `>` je reprezentován jako `&gt;` .|
|Existuje (' `stringA` ')|Vyhodnotí, `true` jestli existuje soubor nebo složka s tímto názvem `stringA` .<br /><br /> Příklad:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|HasTrailingSlash ( `stringA` )|Vyhodnotí na, `true` Pokud zadaný řetězec obsahuje buď koncový znak zpětného lomítka ( \\ ), nebo lomítko (/).<br /><br /> Příklad:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|!|Vyhodnotí, `true` Pokud je operand vyhodnocen `false` .|
|`And`|Vyhodnotí, `true` Pokud jsou oba operandy vyhodnoceny `true` .|
|`Or`|Vyhodnotí, `true` Pokud je alespoň jeden z operandů vyhodnocen jako `true` .|
|()|Mechanizmus seskupení, který se vyhodnocuje, `true` Pokud výrazy obsažené uvnitř vyhodnocuje `true` .|
|$if $ (% Expression%), $else $, $endif $|Kontroluje, zda zadané `%expression%` hodnoty odpovídají hodnotě řetězce předaného parametru vlastní šablony. Pokud je `$if$` podmínka vyhodnocena jako `true` , pak jejich příkazy jsou spuštěny. v opačném případě `$else$` je zaškrtnuta podmínka. Pokud `$else$` je podmínka `true` , pak se spustí jeho příkazy. v opačném případě `$endif$` konec podmínky vyhodnocuje vyhodnocení výrazu.<br /><br /> Příklady použití naleznete v tématu [Logical Project/Item Template Parameter Logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Můžete použít řetězcové metody v podmínkách, jak je znázorněno v následujícím příkladu, ve kterém se funkce [trimEnd ()](/dotnet/api/system.string.trimend) používá k porovnání pouze příslušné části řetězce, k rozlišení mezi .NET Framework a cílovými rozhraními .NET Core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789.`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)
- [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
