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
ms.openlocfilehash: 0d51aa0a5ef995abbe150160e378aa8885cc9706
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472682"
---
# <a name="msbuild-conditions"></a>Podmínky msbuildu

MSBuild podporuje konkrétní sadu podmínek, které `Condition` lze použít všude tam, kde je povolen atribut. Tyto podmínky jsou vysvětleny v následující tabulce.

|Podmínka|Popis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Vyhodnotí `true` `stringA` if `stringB`rovná se .<br /><br /> Například:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|'`stringA`' != '`stringB`'|`true` Vyhodnotí, `stringA` pokud není `stringB`rovno .<br /><br /> Například:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí, `true` pokud je relační hodnocení true. Operandy musí být vyhodnoceny na desetinné nebo šestnáctkové číslo. Šestnáctková čísla musí začínat písmenem "0x". **Poznámka:**  V XML musí `<` `>` být znaky a musí být uvozeny. Symbol `<` je reprezentován jako `&lt;`. Symbol `>` je reprezentován jako `&gt;`.|
|Existuje('`stringA`')|Vyhodnotí, `true` zda existuje soubor `stringA` nebo složka s názvem.<br /><br /> Například:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|HasTrailingSlash('`stringA`')|Vyhodnotí, `true` pokud zadaný řetězec obsahuje koncový\\znak zpětného lomítka ( ) nebo lomítko (/).<br /><br /> Například:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Pro prázdné hodnoty jsou však vyžadovány jednoduché uvozovky.|
|!|Vyhodnotí, `true` pokud operand `false`vyhodnotí .|
|And|Vyhodnotí, `true` pokud oba operandy vyhodnotit `true`.|
|Nebo|Vyhodnotí, `true` pokud alespoň jeden z operandů vyhodnotí `true`.|
|()|Seskupovací mechanismus, který vyhodnocuje, `true` pokud výrazy obsažené uvnitř vyhodnotit `true`.|
|$if$ ( %expression% ), $else$, $endif$|Zkontroluje, `%expression%` zda zadaný odpovídá řetězcové hodnotě předaného parametru vlastní šablony. Pokud `$if$` je podmínka `true`vyhodnocena do , pak jsou její příkazy spuštěny; v opačném `$else$` případě je podmínka zkontrolována. Pokud `$else$` je `true`podmínka , pak jeho příkazy jsou spuštěny; v opačném `$endif$` případě podmínka ukončí vyhodnocení výrazu.<br /><br /> Příklady použití naleznete v tématu [Visual Studio project/item template parameter logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Můžete použít metody řetězce v podmínkách, jak je znázorněno v následujícím příkladu, ve kterém <xref:System.String.TrimEnd> se používá funkce k porovnání pouze příslušné části řetězce, k rozlišení mezi rozhraními .NET Framework a .NET Core target frameworks.

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
