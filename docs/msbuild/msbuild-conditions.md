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
ms.openlocfilehash: 61ffb650a87fa992a07d749687498cbb8ec6482d
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586831"
---
# <a name="msbuild-conditions"></a>Podmínky nástroje MSBuild

Nástroj MSBuild podporuje konkrétní sadu podmínek, které lze použít všude, kde `Condition` je atribut povolen. Tyto podmínky jsou vysvětleny v následující tabulce.

|Podmínka|Popis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Vyhodnotí `true` jako `stringA` , pokud `stringB`je rovno.<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky. U této kontroly se nerozlišují malá a velká písmena.|
|'`stringA`' != '`stringB`'|Vyhodnotí `true` , `stringA` Pokud není rovno `stringB`.<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky. U této kontroly se nerozlišují malá a velká písmena.|
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí `true` , zda je relační vyhodnocení pravdivé. Operandy musí být vyhodnoceny jako desítkové nebo šestnáctkové číslo. Šestnáctková čísla musí začínat znakem "0x". **Poznámka:**  V jazyce XML jsou znaky `<` a `>` musí být uvozeny řídicím znakem. Symbol `<` je reprezentován jako `&lt;`. Symbol `>` je reprezentován jako `&gt;`.|
|Existuje ('`stringA`')|Vyhodnotí `true` , jestli existuje soubor nebo složka s tímto `stringA` názvem.<br /><br /> Příklad:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|HasTrailingSlash (`stringA`)|Vyhodnotí `true` na, pokud zadaný řetězec obsahuje buď koncový znak zpětného lomítka (\\), nebo lomítko (/).<br /><br /> Příklad:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|!|Vyhodnotí `true` , pokud je operand vyhodnocen `false`.|
|And|Vyhodnotí `true` , pokud jsou oba operandy `true`vyhodnoceny.|
|Nebo|Vyhodnotí `true` , pokud je alespoň jeden z operandů vyhodnocen jako `true`.|
|()|Mechanizmus seskupení, který se `true` vyhodnocuje, pokud výrazy obsažené `true`uvnitř vyhodnocuje.|
|$if $ (% Expression%), $else $, $endif $|Kontroluje, zda zadané `%expression%` hodnoty odpovídají hodnotě řetězce předaného parametru vlastní šablony. Pokud se `$if$` podmínka vyhodnotí `true`jako, pak se spustí jeho příkazy; v opačném `$else$` případě je podmínka zaškrtnuta. Pokud je `$else$` `true`podmínka, pak se spustí jeho příkazy; jinak `$endif$` podmínka ukončí vyhodnocení výrazu.<br /><br /> Příklady použití naleznete v tématu [Logical Project/Item Template Parameter Logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

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
