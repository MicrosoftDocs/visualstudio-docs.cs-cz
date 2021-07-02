---
title: MSBuild Podmínky | Microsoft Docs
description: přečtěte si, jak MSBuild podporuje konkrétní sadu podmínek, které se dají použít všude, kde je povolený atribut podmínky.
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
ms.openlocfilehash: d72b69b2c80c4e20b5a4dadae18764a138210295
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222705"
---
# <a name="msbuild-conditions"></a>Podmínky nástroje MSBuild

MSBuild podporuje konkrétní sadu podmínek, které lze použít všude, kde `Condition` je atribut povolen. Tyto podmínky jsou vysvětleny v následující tabulce.

|Podmínka|Description|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Vyhodnotí jako, `true` Pokud `stringA` je rovno `stringB` .<br /><br /> Příklad:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky. U této kontroly se nerozlišují malá a velká písmena.|
|'`stringA`' != '`stringB`'|Vyhodnotí, `true` Pokud `stringA` není rovno `stringB` .<br /><br /> Příklad:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky. U této kontroly se nerozlišují malá a velká písmena.|
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí, `true` zda je relační vyhodnocení pravdivé. Operandy musí být vyhodnoceny jako desítkové nebo šestnáctkové číslo nebo z tečkované verze se čtyřmi částmi. Šestnáctková čísla musí začínat znakem "0x". **Poznámka:**  V jazyce XML jsou znaky `<` a `>` musí být uvozeny řídicím znakem. Symbol `<` je reprezentován jako `&lt;` . Symbol `>` je reprezentován jako `&gt;` .|
|Existuje (' `stringA` ')|Vyhodnotí, `true` jestli existuje soubor nebo složka s tímto názvem `stringA` .<br /><br /> Příklad:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|HasTrailingSlash ( `stringA` )|Vyhodnotí na, `true` Pokud zadaný řetězec obsahuje buď koncový znak zpětného lomítka ( \\ ), nebo lomítko (/).<br /><br /> Příklad:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|!|Vyhodnotí, `true` Pokud je operand vyhodnocen `false` .|
|`And`|Vyhodnotí, `true` Pokud jsou oba operandy vyhodnoceny `true` .|
|`Or`|Vyhodnotí, `true` Pokud je alespoň jeden z operandů vyhodnocen jako `true` .|
|()|Mechanizmus seskupení, který se vyhodnocuje, `true` Pokud výrazy obsažené uvnitř vyhodnocuje `true` .|
|$if $ (% Expression%), $else $, $endif $|Kontroluje, zda zadané `%expression%` hodnoty odpovídají hodnotě řetězce předaného parametru vlastní šablony. Pokud je `$if$` podmínka vyhodnocena jako `true` , pak jejich příkazy jsou spuštěny. v opačném případě `$else$` je zaškrtnuta podmínka. Pokud `$else$` je podmínka `true` , pak se spustí jeho příkazy. v opačném případě `$endif$` konec podmínky vyhodnocuje vyhodnocení výrazu.<br /><br /> příklady použití naleznete v tématu [Visual Studio logic template a item parameter](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

můžete použít řetězcové metody v podmínkách, jak je znázorněno v následujícím příkladu, ve kterém se funkce [TrimEnd ()](/dotnet/api/system.string.trimend) používá k porovnání pouze příslušné části řetězce, k rozlišení mezi .NET Framework a cílovými rozhraními .net Core.

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

v MSBuild soubory projektu neexistuje žádný pravdivý typ Boolean. Logická data jsou reprezentována ve vlastnostech, které mohou být prázdné nebo nastaveny na libovolnou hodnotu. Proto `'$(Prop)' == 'true'` znamená "if Prop is" `true` , ",", ale znamená "," je-li nastavena možnost "nebo" `'$(Prop)' != 'false'` `true` na něco jiného. "

Logická logika je vyhodnocována pouze v kontextu podmínek, takže nastavení vlastností, jako `<Prop2>'$(Prop1)' == 'true'</Prop>` jsou reprezentována jako řetězec (po rozšíření proměnné), není vyhodnoceno jako logické hodnoty.  

MSBuild implementuje několik speciálních pravidel zpracování, která usnadňují práci s vlastnostmi řetězce, které se používají jako logické hodnoty. Logické literály jsou přijaty, takže `Condition="true"` a `Condition="false"` fungují podle očekávání. MSBuild také obsahuje zvláštní pravidla pro podporu logického operátoru negace. Takže pokud `$(Prop)` je "true", `!$(Prop)` rozbalí se a tato hodnota se rovná `!true` `false` , jak byste očekávali.

## <a name="comparing-versions"></a>Porovnání verzí

Relační operátory `<` , `>` , `<=` a `>=` verze podpory, které jsou analyzovány nástrojem <xref:System.Version?displayProperty=fullName> , takže můžete porovnat verze, které mají čtyři číselné části. Instance `'1.2.3.4' < '1.10.0.0'` je například `true` .

> [!CAUTION]
> `System.Version` porovnání mohou způsobit překvapivé výsledky, pokud jedna nebo obě verze nespecifikují všechny čtyři části. Například verze 1,1 je starší než 1.1.0 verze.

MSBuild poskytuje [funkce vlastností pro porovnání verzí](property-functions.md#msbuild-version-comparison-functions) , které mají jinou sadu pravidel kompatibilních se sémantickou správou verzí (semver).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)
- [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
