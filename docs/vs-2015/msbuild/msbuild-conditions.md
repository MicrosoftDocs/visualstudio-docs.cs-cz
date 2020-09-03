---
title: Podmínky nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71bb48290d0eb64f91b918d22624755c2edb6153
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74303121"
---
# <a name="msbuild-conditions"></a>Podmínky nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podporuje konkrétní sadu podmínek, které lze použít všude, kde `Condition` je atribut povolen. Tyto podmínky jsou vysvětleny v následující tabulce.  
  
|Stav|Popis|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Vyhodnotí jako, `true` Pokud `stringA` je rovno `stringB` .<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|'`stringA`' != '`stringB`'|Vyhodnotí, `true` Pokud `stringA` není rovno `stringB` .<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|\<, >, \<=, >=|Vyhodnotí číselné hodnoty operandů. Vrátí, `true` zda je relační vyhodnocení pravdivé. Operandy musí být vyhodnoceny jako desítkové nebo šestnáctkové číslo. Šestnáctková čísla musí začínat znakem "0x". **Poznámka:**  V jazyce XML jsou znaky `<` a `>` musí být uvozeny řídicím znakem. Symbol `<` je reprezentován jako `<` . Symbol `>` je reprezentován jako `>` .|  
|Existuje (' `stringA` ')|Vyhodnotí, `true` jestli existuje soubor nebo složka s tímto názvem `stringA` .<br /><br /> Příklad:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|HasTrailingSlash ( `stringA` )|Vyhodnotí na, `true` Pokud zadaný řetězec obsahuje buď koncový znak zpětného lomítka ( \\ ), nebo lomítko (/).<br /><br /> Příklad:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|!|Vyhodnotí, `true` Pokud je operand vyhodnocen `false` .|  
|And|Vyhodnotí, `true` Pokud jsou oba operandy vyhodnoceny `true` .|  
|Nebo|Vyhodnotí, `true` Pokud je alespoň jeden z operandů vyhodnocen jako `true` .|  
|()|Mechanizmus seskupení, který se vyhodnocuje, `true` Pokud výrazy obsažené uvnitř vyhodnocuje `true` .|  
|$if $ (% Expression%), $else $, $endif $|Kontroluje, zda zadané `%expression%` hodnoty odpovídají hodnotě řetězce předaného parametru vlastní šablony. Pokud je `$if$` podmínka vyhodnocena jako `true` , pak jejich příkazy jsou spuštěny. v opačném případě `$else$` je zaškrtnuta podmínka. Pokud `$else$` je podmínka `true` , pak se spustí jeho příkazy. v opačném případě `$endif$` konec podmínky vyhodnocuje vyhodnocení výrazu.<br /><br /> Příklady použití naleznete v tématu [Logical Project/Item Template Parameter Logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)   
 [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
