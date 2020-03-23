---
title: Okno nápovědy pro R
description: Nápověda pro R je integrována přímo do interaktivního okna v sadě Visual Studio prostřednictvím aplikace ? Příkaz.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950604"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Nápověda k nástrojům R pro visual studio

Nápověda pro R je integrována přímo do interaktivního okna v sadě Visual Studio. Vždy, když `?` použijete `?mtcars`příkaz, například , se v okně sady Visual Studio zobrazí nápověda z dokumentace jazyka R:

![Okno nápovědy v sadě Visual Studio](media/help-window.png)

> [!Tip]
> Okno nápovědy, stejně jako všechny ostatní v sadě Visual Studio, lze uspořádat a ukotvit, jak se vám líbí. Viz [Přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Chcete-li otevřít výsledky nápovědy v prohlížeči, vyberte nabídku `External`**Možnosti** **nástrojů** > R a nastavte vlastnost **Prohlížeč nápovědy R** na . Viz [Možnosti](options-for-r-tools-in-visual-studio.md).

Chcete-li vyhledat `??` nápovědu, použijte příkaz následovaný hledaným výrazem. Pokud hledaný výraz obsahuje mezery, použijte uvozovky:

```R
??"Motor Trend"
```

![Nápověda k výsledkům hledání](media/help-search1.png)

Okno nápovědy má také vyhledávací vstupní pole, jehož prostřednictvím můžete provádět další vyhledávání přímo v dokumentaci R:

![Pomoc s hledáním výsledků pomocí vstupního pole](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Integrované vyhledávání nápovědy

Vývojáři často vyhledávají nápovědu v dokumentaci jazyka R k názvům funkcí, datovým mase a dalším prvkům. Nástroje R pro visual studio (RTVS) zjednodušují proces integrací vyhledávání nápovědy přímo do editoru a interaktivních oken.

- Stisknutím **klávesy F1** během operace automatického dokončování se vytvoří seznam výsledků nápovědy, které odpovídají podřetězci.
- Kliknutím pravým tlačítkem myši na hledaný výraz (například funkcí) a výběrem **příkazu Nápověda se** otevře nápověda pro tuto funkci. Můžete také vyvolat **nápovědu pro** libovolný výběr.

    ![Vyvolání nápovědy prostřednictvím kontextové nabídky pravým tlačítkem myši](media/help-right-click.png)

> [!Tip]
> Chcete-li otevřít integrovanou nápovědu v prohlížeči, vyberte**možnosti** **nástrojů** > R a nastavte webový **prohlížeč F1** na `External`. Viz [Možnosti](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Integrované vyhledávání StackOverflow

Kromě vyhledávání v dokumentaci R vývojáři často prohledávají StackOverflow při psaní kódu. RTVS tento proces také zjednodušuje. Klepněte pravým tlačítkem myši na termín nebo výběr, vyberte příkaz **Hledat na webu** (**Ctrl**+**F1**) a Visual Studio otevře okno s výsledky hledání s rozsahem StackOverflow:

![Výsledky hledání na webu v sadě Visual Studio](media/help-web-search-results.png)

Připojený řetězec oborů můžete změnit `R site:stackoverflow`pomocí možnosti řetězce vyhledávání **na webu nástroje** > **Options** > R**Options F1:**

![Změna možnosti vyhledávacího řetězce webu F1](media/options-dialog.png)

Pokud dáváte přednost zobrazení výsledků v prohlížeči, změňte možnost **webového prohlížeče F1,** jak je popsáno v části [Možnosti](options-for-r-tools-in-visual-studio.md).