---
title: Okno s nápovědu pro R
description: Nápovědu pro jazyk R je integrována přímo do interaktivního okna v aplikaci Visual Studio prostřednictvím? systému.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 551f929e4d42b208dd222f052b27720edb273761
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885765"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Nástroje R pro Visual Studio nápovědě

Nápovědu pro jazyk R je integrována přímo do interaktivního okna v aplikaci Visual Studio. Pokaždé, když použijete `?` příkaz, například `?mtcars` , se zobrazí zpráva z dokumentace R v okně sady Visual Studio:

![Okno Help v aplikaci Visual Studio](media/help-window.png)

> [!Tip]
> Okno Help, podobně jako všechny ostatní v aplikaci Visual Studio, lze uspořádat a ukotvit, například. Viz [přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Chcete-li otevřít výsledky aplikace Help v prohlížeči, vyberte nabídku možnosti **nástrojů jazyka R**  >   a nastavte vlastnost **Nápověda pro R prohlížeče** na `External` . Viz [Možnosti](options-for-r-tools-in-visual-studio.md).

Pokud chcete hledat v nápovědě, použijte `??` příkaz následovaný hledaným termínem. Pokud hledaný termín obsahuje mezery, použijte uvozovky:

```R
??"Motor Trend"
```

![Výsledky hledání v nápovědě](media/help-search1.png)

Okno help obsahuje také vstupní pole hledání, pomocí kterého můžete provádět další hledání přímo v dokumentaci jazyka R:

![Help výsledky hledání pomocí vstupního pole](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Integrované vyhledávání v nápovědě

Vývojáři často prohledají dokumentaci R, kde najdete nápovědu pro názvy funkcí, datové sady a další prvky. Nástroje R pro Visual Studio (RTVS) zjednodušuje proces integrací vyhledávání v nápovědě přímo do editoru a interaktivních oken.

- Stisknutí **klávesy F1** během operace automatického dokončení vytvoří seznam výsledků pro nápovědu, které odpovídají podřetězci.
- Kliknutím pravým tlačítkem myši na hledaný termín (například funkce) a výběrem příkazu **help on** (otevřít nápovědu) se zobrazí nápovědu k této funkci. Můžete také vyvolat **nápovědu** pro libovolný výběr.

    ![Vyvolání pomocníka při kliknutí pravým tlačítkem na místní nabídku](media/help-right-click.png)

> [!Tip]
> Chcete-li otevřít integrovanou nápovědu v prohlížeči, vyberte možnost možnosti **nástrojů R**  >   a nastavte možnost **F1 webový prohlížeč** na `External` . Viz [Možnosti](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Integrované hledání StackOverflow

Kromě vyhledávání v dokumentaci jazyka R, vývojáři často hledají StackOverflow při psaní kódu. RTVS tento proces i zjednodušuje. Klikněte pravým tlačítkem na termín nebo výběr, vyberte **vyhledat web pro** příkaz (**CTRL** + **F1**) a Visual Studio otevře okno s výsledky hledání podle rozsahu StackOverflow:

![Výsledky hledání na webu v aplikaci Visual Studio](media/help-web-search-results.png)

Přidaný řetězec oboru můžete změnit `R site:stackoverflow` pomocí možností **nástroje R**  >  **Možnosti**  >  **řetězce hledání na webu F1** :

![Změna možnosti řetězce hledání na webu F1](media/options-dialog.png)

Pokud dáváte přednost zobrazení výsledků v prohlížeči, změňte možnost **webový prohlížeč F1** , jak je popsáno v tématu [Možnosti](options-for-r-tools-in-visual-studio.md).