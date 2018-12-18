---
title: Okno nápovědy pro R
description: Nápověda pro R je integrovaný přímo do interaktivního okna v sadě Visual Studio prostřednictvím? příkaz.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 6576a701abe699bfe47666acfc21c848dde1f53a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666680"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Nápovědu v nástroje jazyka R pro Visual Studio

Nápověda pro R je integrovaný přímo do interaktivního okna v sadě Visual Studio. Vždy, když použijete `?` příkazu, jako například `?mtcars`, Nápověda v dokumentaci ke službě jazyka R se zobrazí v okně aplikace Visual Studio:

![Okno nápovědy v aplikaci Visual Studio](media/help-window.png)

> [!Tip]
> Okně nápovědy, stejně jako všechny ostatní v sadě Visual Studio, můžete uspořádat a ukotven libovolně. Zobrazit [přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Otevřít nápovědu výsledků v prohlížeči, vyberte **nástroje R** > **možnosti** nabídky a nastavte **Prohlížeč nápovědy R** vlastnost `External`. Zobrazit [možnosti](options-for-r-tools-in-visual-studio.md).

Chcete-li v nápovědě, použijte `??` příkaz následovaný hledaný termín. Pokud hledaný výraz obsahuje mezery, použijte uvozovky:

```R
??"Motor Trend"
```

![Výsledky hledání nápovědy](media/help-search1.png)

V okně nápovědy obsahuje také hledání vstupního pole, jehož prostřednictvím můžete provést další hledání v dokumentaci k R přímo:

![Výsledky hledání nápovědy pomocí vstupního pole](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Integrovaná nápověda vyhledávání

Vývojáři často hledání dokumentace R pro pomoc s názvy funkcí, datové sady a další prvky. Nástroje R pro Visual Studio (RTVS) zjednodušuje proces prostřednictvím integrace vyhledávání pomoc přímo do editoru a interaktivních oken.

- Stisknutím klávesy **F1** během operace automatického dokončování vytváří seznam výsledků nápovědy, které odpovídají dílčí řetězec.
- Hledaný výraz (např. funkce) pravým tlačítkem a výběrem **nápovědy na** příkaz otevře nápovědu pro tuto funkci. Můžete také vyvolat **nápovědy na** pro výběr.

    ![Vyvolání nápovědy přes kliknutí pravým tlačítkem na kontextové nabídky](media/help-right-click.png)

> [!Tip]
> Integrovaná nápověda otevřete v prohlížeči, vyberte **nástroje R** > **možnosti** a nastavte **F1 webový prohlížeč** k `External`. Zobrazit [možnosti](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Integrované hledání StackOverflow

Kromě hledání v dokumentaci k R, vývojáři často hledání StackOverflow při psaní kódu. RTVS zjednodušuje tento proces také. Klikněte pravým tlačítkem na termín nebo výběru, vyberte **vyhledávání na webu pro** příkazu (**Ctrl**+**F1**), a sady Visual Studio otevře okno s výsledky hledání s rozsahem StackOverflow:

![Výsledky hledání na webu v sadě Visual Studio](media/help-web-search-results.png)

Připojený řetězec oborů, můžete změnit `R site:stackoverflow`, až **nástroje R** > **možnosti** > **F1 webové hledaný řetězec** možnost:

![Změna možnosti řetězec F1 webové vyhledávání](media/options-dialog.png)

Pokud chcete zobrazit výsledky v prohlížeči, změnit **F1 webový prohlížeč** možnosti, jak je popsáno na [možnosti](options-for-r-tools-in-visual-studio.md).