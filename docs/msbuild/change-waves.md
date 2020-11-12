---
title: Změnit vlny
description: Naučte se, jak v nástroji MSBuild povolit nebo zakázat funkce, které jsou potenciálně rušivé.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 68aafd8ebb97b4bf649cc41eb7739e1700c9cb1a
ms.sourcegitcommit: 83a39d48b00c6c351e5c1707942633b7f73aaad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2020
ms.locfileid: "94532068"
---
# <a name="change-waves"></a>Změnit vlny

*Změna Wave* je sada změn chování v nástroji MSBuild, kterou můžete odsouhlasit zadáním konkrétního příznaku jako proměnné prostředí. Účelem tohoto upozornění je upozornit na potenciálně rušivé změny, abyste měli flexibilitu při přizpůsobování těchto změn, než se stanou standardními funkcemi. Všechny funkce v konkrétní změně vlny lze povolit nebo zakázat pouze společně, nikoli jednotlivě.

Při upgradu na novou verzi nástroje MSBuild jsou změny, které jsou potenciálně lomeny, povoleny ve výchozím nastavení, ale pokud funkce ovlivní vaše sestavení negativně, můžete tyto vlny změny snadno zakázat. Každá změna Wave je identifikována číslem verze nástroje MSBuild (například 16,8), ale nastavení změny formátu Wave řídí pouze některé funkce, které mají potenciál ovlivnit proces sestavení, ne všechny změny v této verzi nástroje MSBuild. Seznam funkcí v jednotlivých změnách Wave se zobrazí [dále v tomto článku](#change-waves-and-associated-features). Vypnutí změn Wave také zakáže změnu vlny vyšších verzí.

## <a name="opt-out-of-change-wave-features"></a>Výslovný nesouhlas s funkcí Change Wave

Chcete-li zakázat funkce v změněné vlně, nastavte proměnnou prostředí `MSBuildDisableFeaturesFromVersion` na změnu Wave (nebo verzi nástroje MSBuild) obsahující funkci, kterou chcete **Zakázat**. Toto je verze nástroje MSBuild, pro kterou byly vyvinuty funkce. Podívejte se na téma mapování změny vlny na následující funkce.

### <a name="msbuilddisablefeaturesfromversion-values"></a>Hodnoty MSBuildDisableFeaturesFromVersion

Pokud nenastavíte platnou změnu Wave, zobrazí se vám upozornění nebo výchozí hodnota pro určitý Wave `MSBuildDisableFeaturesFromVersion` . Následující tabulka uvádí možná nastavení:

| `MSBuildDisableFeaturesFromVersion` Osa                         | Výsledek        | Dostávat upozornění? |
| :-------------                                                    | :----------   | :----------: |
| Stav                                                             | Povolit všechny změny vlny, což znamená, že všechny funkce za každou změnou vlny jsou povoleny.               | Ne   |
| Jakákoli platná a aktuální změna Wave (například `16.8` )                      | Zakažte všechny funkce na pozadí Change Wave `16.8` **a vyšší**.                                           | Ne   |
| Neplatná hodnota (například `16.9` když jsou platné vlny `16.8` a `16.10` )| Použije se výchozí hodnota nejbližší platné hodnoty (vzestupně). Například nastavení bude mít `16.9` výchozí hodnotu `16.10` .               | Ne   |
| Mimo rotace (například `17.1` když je nejvyšší vlna `17.0` )      | Přitlačí se k nejbližší platné hodnotě. Například `17.1` svorky do a `17.0` `16.5` svorky do `16.8`                    | Yes  |
| Neplatný formát (například,, `16x8` `17_0` `garbage` )                    | Povolit všechny změny vlny, což znamená, že všechny funkce za každou změnou vlny jsou povoleny.               | Yes  |

## <a name="change-waves-and-associated-features"></a>Změna vln a přidružených funkcí

Odkazy v následujícím seznamu odkazují na žádosti o přijetí změn na GitHubu.

### <a name="168"></a>16,8

- [Povolit upozornění](https://github.com/dotnet/msbuild/pull/5671)
- [Ořízne zprávy protokolu, které cíl/úloha přeskakuje, na 1024 znaků.](https://github.com/dotnet/msbuild/pull/5553)
- [Nerozšiřovat celou jednotku globy s podmínkou false](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16,10

- [Chyba v případě, že rozšíření vlastnosti v podmínce obsahuje prázdné znaky](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17,0

V této změně Wave zatím nejsou žádné položky.

## <a name="change-waves-that-are-out-of-rotation"></a>Změnit nenatočené vlny

V tuto chvíli neexistují žádné vlny změny rotace.

## <a name="faq"></a>Nejčastější dotazy

**Proč cílit na každou jinou vydanou verzi pro otočení změn vlny?**

Věříme, že je dostatek času pro diskuzi s ovlivněnými a pomoc s přizpůsobením změn.

**Proč proměnná prostředí a ne vlastnost projektu?**

Existují situace, kdy chceme umístit funkci pod změnu Wave předtím, než MSBuild načte projekt. Z tohoto důvodu je třeba změnit vlny pomocí proměnných prostředí.

**Proč se odhlásit přes výslovný souhlas?**

Výslovný přístup je lepším řešením pro nás, jinak se vám při dopadu na zákaznická sestavení může zobrazit omezená zpětná vazba.

## <a name="see-also"></a>Viz také:

- [Nástroji](msbuild.md)
- [Co je nového v nástroji MSBuild 16](whats-new-msbuild-16-0.md)
