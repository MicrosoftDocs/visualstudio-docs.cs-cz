---
title: 'DA0503: Průměrná pracovní sada v bajtech pro proces, který se profiluje | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f2f349c4ca2172ac2be6c22f3fe999ca0a3cff0
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72910207"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Průměrná pracovní sada v bajtech pro proces profilace

|||
|-|-|
|ID pravidla|DA0503|
|Kategorie|Monitorování prostředků|
|Metoda profilace|Všechny|
|Zpráva|Tyto informace se shromáždily jenom pro informace. Čítač pracovní sady procesů měří využití fyzické paměti procesem, který vytváříte. Hodnota hlášené je průměr vypočítaný ve všech intervalech měření.|
|Typ pravidla|Informace o|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva oznamuje průměrnou velikost fyzické paměti, kterou proces aktuálně používá v bajtech (pracovní sada). Pracovní sada procesu představuje stránky z adresního prostoru procesu, který je aktuálně umístěn ve fyzické paměti.

 Vykazovaná hodnota zahrnuje rezidentní stránky ze sdílených segmentů paměti, na které proces odkazuje. Sdílené knihovny DLL, které odkazují na procesy, jsou zahrnuté do sdílených segmentů paměti, které se počítají. Hodnota pracovní sady procesu může být vyšší než velikost virtuální paměti, kterou byl proces přidělen z důvodu sdílených segmentů paměti.

 Vykazovaná hodnota je průměr ve všech intervalech měření, v nichž byl proces profilace aktivní.

 Velikost pracovní sady procesu odráží, kolik virtuální paměti proces aktivně používá. To je ovlivněno množstvím fyzické paměti (nebo paměti RAM), která je k dispozici pro spuštění aplikace a kolizí pro danou fyzickou paměť z jiných spuštěných procesů. Pokud je fyzická paměť omezená, je hodnota pracovní sady procesu apt tak, aby se významně lišila, protože operační systémy se snaží vyrovnávat využití paměti napříč aktivními procesy tím, že pravidelně vystřihuje poměrně neaktivní stránky ze procesních sad procesů.

 Další informace o pracovních sadách procesů najdete v tématu [Work set](/windows/win32/memory/working-set) v dokumentaci ke službě Windows Memory Management na webu MSDN.

## <a name="how-to-use-rule-data"></a>Jak používat data pravidla
 Použijte hodnotu pravidla pro porovnání výkonu různých verzí nebo sestavení programu nebo pro pochopení výkonu aplikace v rámci různých scénářů profilace.

 Dvojitým kliknutím na zprávu v okně Seznam chyb přejdete do zobrazení [značky](../profiling/marks-view.md) zobrazit data profilace. Vyhledejte sloupce **Process\Working sady** a **paměť \ stránky/s** . Porovnejte oba sloupce a určete, zda jsou k dispozici konkrétní fáze provádění programu, které se mají přidružit ke zvýšené vstupně-výstupní aktivitě stránkování.