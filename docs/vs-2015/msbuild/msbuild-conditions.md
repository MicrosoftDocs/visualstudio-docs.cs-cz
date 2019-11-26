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
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303121"
---
# <a name="msbuild-conditions"></a>Podmínky nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podporuje konkrétní sadu podmínek, které lze použít všude, kde je povolen atribut `Condition`. Tyto podmínky jsou vysvětleny v následující tabulce.  
  
|Podmínka|Popis|  
|---------------|-----------------|  
|'`stringA`' = '`stringB`'|Vyhodnotí na `true`, pokud `stringA` rovná `stringB`.<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|'`stringA`'! = '`stringB`'|Vyhodnotí na `true`, pokud `stringA` není rovno `stringB`.<br /><br /> Příklad:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|\<, >, \<=, > =|Vyhodnotí číselné hodnoty operandů. Vrátí `true`, pokud je relační vyhodnocení true. Operandy musí být vyhodnoceny jako desítkové nebo šestnáctkové číslo. Šestnáctková čísla musí začínat znakem "0x". **Poznámka:**  V jazyce XML musí být znaky `<` a `>` uvozeny řídicími znaky. Symbol `<` je reprezentován jako `<`. Symbol `>` je reprezentován jako `>`.|  
|Existuje ('`stringA`')|Vyhodnotí pro `true`, jestli existuje soubor nebo složka s názvem `stringA`.<br /><br /> Příklad:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|HasTrailingSlash ('`stringA`')|Vyhodnotí na `true`, pokud zadaný řetězec obsahuje buď koncové zpětné lomítko (\\), nebo znak lomítka (/).<br /><br /> Příklad:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pro jednoduché alfanumerické řetězce nebo logické hodnoty se nevyžadují jednoduché uvozovky. Pro prázdné hodnoty jsou však požadovány jednoduché uvozovky.|  
|!|Vyhodnotí na `true`, pokud je operand vyhodnocen jako `false`.|  
|A|Vyhodnotí na `true`, pokud se oba operandy vyhodnotí jako `true`.|  
|Nebo|Vyhodnotí na `true`, pokud se alespoň jeden z operandů vyhodnocuje jako `true`.|  
|()|Mechanismus seskupení, který se vyhodnotí jako `true`, pokud jsou výrazy obsažené uvnitř vyhodnoceny jako `true`.|  
|$if $ (% Expression%), $else $, $endif $|Kontroluje, zda zadaný `%expression%` odpovídá hodnotě řetězce předaného parametru vlastní šablony. Pokud je podmínka `$if$` vyhodnocena jako `true`, pak se jejich příkazy spouštějí; v opačném případě je zaškrtnuta podmínka `$else$`. Pokud je `$else$` podmínka `true`, pak se spustí jeho příkazy; v opačném případě `$endif$` podmínka ukončí vyhodnocení výrazu.<br /><br /> Příklady použití naleznete v tématu [Logical Project/Item Template Parameter Logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Viz také  
 [Referenční](../msbuild/msbuild-reference.md)  nástroje MSBuild  
 [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)   
 [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
