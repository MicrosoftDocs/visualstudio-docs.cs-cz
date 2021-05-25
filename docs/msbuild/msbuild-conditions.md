---
title: Podmínky nástroje MSBuild | Microsoft Docs
description: Zjistěte, jak NÁSTROJ MSBuild podporuje konkrétní sadu podmínek, které lze použít všude, kde je atribut Podmínky povolený.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76bafaf5192c59e0f23078e396ae553b3023e060
ms.sourcegitcommit: d3577395cf016f2836eb5a3c1d496cca6d449baa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2021
ms.locfileid: "110413322"
---
# <a name="msbuild-conditions"></a>Podmínky nástroje MSBuild

Nástroj MSBuild podporuje konkrétní sadu podmínek, které lze použít všude, kde `Condition` je atribut povolen. Tyto podmínky jsou vysvětlené v následující tabulce.

|Podmínka|Description|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Vyhodnotí `true` hodnotu , pokud je rovno `stringA` `stringB` .<br /><br /> Například:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Jednoduché uvozovky jsou však vyžadovány pro prázdné hodnoty. Tato kontrola se nelišují malá a velká písmena.|
|'`stringA`' != '`stringB`'|Vyhodnotí `true` hodnotu , pokud není rovno `stringA` `stringB` .<br /><br /> Například:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Jednoduché uvozovky nejsou vyžadovány pro jednoduché alfanumerické řetězce nebo logické hodnoty. Jednoduché uvozovky jsou však vyžadovány pro prázdné hodnoty. Tato kontrola se nelišují malá a velká písmena.|
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí `true` hodnotu , pokud je relační vyhodnocení pravdivé. Operandy musí být vyhodnoceny jako desetinné nebo šestnáctkové číslo nebo čtyřsekuťová tečkovaná verze. Šestnáctková čísla musí začínat "0x". **Poznámka:**  V XML musí být znaky `<` `>` a uvozeny. Symbol je `<` reprezentován jako `&lt;` . Symbol `>` je reprezentován jako `&gt;` .|
|Existuje (' `stringA` ')|Vyhodnotí, `true` jestli existuje soubor nebo složka s tímto názvem `stringA` .<br /><br /> Například:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|HasTrailingSlash ( `stringA` )|Vyhodnotí na, `true` Pokud zadaný řetězec obsahuje buď koncový znak zpětného lomítka ( \\ ), nebo lomítko (/).<br /><br /> Například:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
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

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

V souborech projektu MSBuild neexistuje žádný pravdivý typ Boolean. Logická data jsou reprezentována ve vlastnostech, které můžou být prázdné nebo nastavené na libovolnou hodnotu. Proto znamená `'$(Prop)' == 'true'` "pokud je prop `true` ,", ale `'$(Prop)' != 'false'` znamená "pokud je prop nebo `true` unset nebo nastavený na něco jiného".

Logická logika se vyhodnocuje pouze v kontextu podmínek, takže nastavení vlastností, jako je , jsou reprezentována jako řetězec (po rozšíření proměnné), nevyhodnocuje `<Prop2>'$(Prop1)' == 'true'</Prop>` se jako logické hodnoty.  

Nástroj MSBuild implementuje několik speciálních pravidel zpracování, která usnadňují práci s řetězci vlastnostmi, které se používají jako logické hodnoty. Logické literály jsou přijímány, takže `Condition="true"` `Condition="false"` fungují podle očekávání. Nástroj MSBuild obsahuje také speciální pravidla pro podporu logického operátoru negace. Takže pokud je hodnota "true", rozbalí se na a porovná se s hodnotou `$(Prop)` `!$(Prop)` , jak byste `!true` `false` očekávali.

## <a name="comparing-versions"></a>Porovnání verzí

Relační operátory , , a podporují verze parsované pomocí , takže můžete vzájemně porovnat verze, které `<` `>` mají čtyři číselné `<=` `>=` <xref:System.Version?displayProperty=fullName> části. Například je `'1.2.3.4' < '1.10.0.0'` `true` .

> [!CAUTION]
> `System.Version` Porovnání mohou mít překvapivé výsledky, pokud jedna nebo obě verze nezadá všechny čtyři části. Například verze 1.1 je starší než verze 1.1.0.

Nástroj MSBuild poskytuje [funkce vlastností pro porovnání verzí,](property-functions.md#MSBuild-version-comparison-functions) které mají jinou sadu pravidel kompatibilních se sémantickou sémantickou sekcí verzí (semver).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)
- [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
