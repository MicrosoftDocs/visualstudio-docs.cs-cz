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
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9576bdf06593ae3cde3bc29e2585a7ab475671a3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566615"
---
# <a name="msbuild-conditions"></a>Podmínky nástroje MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] podporuje konkrétní sadu podmínek, které lze použít všude, kde je povolen atribut `Condition`. Tyto podmínky jsou vysvětleny v následující tabulce.

|Podmínka|Popis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Vyhodnotí na `true`, pokud `stringA` rovná `stringB`.<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|'`stringA`' != '`stringB`'|Vyhodnotí na `true`, pokud `stringA` není rovno `stringB`.<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí `true`, pokud je relační vyhodnocení true. Operandy musí být vyhodnoceny jako desítkové nebo šestnáctkové číslo. Šestnáctková čísla musí začínat znakem "0x". **Poznámka:**  V jazyce XML musí být znaky `<` a `>` uvozeny řídicími znaky. Symbol `<` je reprezentován jako `&lt;`. Symbol `>` je reprezentován jako `&gt;`.|
|Existuje ('`stringA`')|Vyhodnotí pro `true`, jestli existuje soubor nebo složka s názvem `stringA`.<br /><br /> Příklad:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|HasTrailingSlash('`stringA`')|Vyhodnotí na `true`, pokud zadaný řetězec obsahuje buď koncové zpětné lomítko (\\), nebo znak lomítka (/).<br /><br /> Příklad:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|
|!|Vyhodnotí na `true`, pokud je operand vyhodnocen jako `false`.|
|A|Vyhodnotí na `true`, pokud se oba operandy vyhodnotí jako `true`.|
|Nebo|Vyhodnotí na `true`, pokud se alespoň jeden z operandů vyhodnocuje jako `true`.|
|()|Mechanismus seskupení, který se vyhodnotí jako `true`, pokud jsou výrazy obsažené uvnitř vyhodnoceny jako `true`.|
|$if $ (% Expression%), $else $, $endif $|Kontroluje, zda zadaný `%expression%` odpovídá hodnotě řetězce předaného parametru vlastní šablony. Pokud je podmínka `$if$` vyhodnocena jako `true`, pak se jejich příkazy spouštějí; v opačném případě je zaškrtnuta podmínka `$else$`. Pokud je `$else$` podmínka `true`, pak se spustí jeho příkazy; v opačném případě `$endif$` podmínka ukončí vyhodnocení výrazu.<br /><br /> Příklady použití naleznete v tématu [Logical Project/Item Template Parameter Logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)
- [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
