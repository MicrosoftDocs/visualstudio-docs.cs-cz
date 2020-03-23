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
ms.openlocfilehash: 2e69e5c8fc7404c0c313774271fd07b6315e5270
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633366"
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

## <a name="see-also"></a>Viz také

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)
- [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
