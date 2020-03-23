---
title: Správce balíčků pro R
description: Jak použít správce balíčků R v sadě Visual Studio k instalaci a správce balíčků R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d35bfd45e862912ff78ae600eed01ce8dc002493
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62998854"
---
# <a name="package-manager"></a>Správce balíčků

Nástroje R pro správce balíčků sady Visual Studio (RTVS) je ui pro správu balíčků R. Chcete-li jej otevřít, vyberte možnost **R Nástroje** > **balíčků systému** **Windows** > nebo stisknutím **klávesctrl**+**7**.

Správce balíčků má tři karty. Každá karta zobrazuje seznam relevantních balíčků vlevo a konkrétní podrobnosti o vybraném balíčku vpravo, včetně verze balíčku, popisu, licence, umístění instalace a odkazů na další relevantní informace. Vyhledávací pole v pravém horním horním poli umožňuje filtrovat seznam.

> [!Tip]
> Termín ve vyhledávacím poli zůstává v platnosti při přepínání mezi kartami.

- **K dispozici** umožňuje procházet balíčky k instalaci. Pokud je balíček již nainstalován, tlačítko **Instalovat** vpravo změní na **Odinstalovat**.

    ![Karta Dostupné balíčky ve Správci balíčků Nástroje Jazyka R pro Visual Studio](media/package-manager-available.png)

- **Nainstalované** zobrazuje všechny nainstalované a načtené balíčky. Zelená tečka vedle balíčku označuje, že je načtena do relace R. Červená ikona X v levém seznamu nebo tlačítko **Odinstalovat** vpravo lze použít k odinstalaci balíčku. Pokud je k dispozici novější verze nainstalovaného balíčku, provede aktualizaci modrá šipka nahoru vpravo od balíčku.

    ![Karta Nainstalované balíčky ve Správci balíčků Nástroje jazyka R pro aplikaci Visual Studio](media/package-manager-installed.png)

- **Načtené** zobrazí pouze ty balíčky, které jsou načteny do relace R, které se zobrazí se zelenou tečkou. Balíčky můžete také odinstalovat a aktualizovat zde.

    ![Karta Načtené balíčky ve Správci balíčků Nástroje jazyka R pro visual studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Umístění balíčků

Balíčky jsou nainstalovány v následujících umístěních:

- Základní balíčky, které jsou součástí rtvs jsou nainstalovány v *c:\Program Files\Microsoft\R Client\R_SERVER\library*
- Do *%userprofile%\Documents\R\Win-library\3.3 jsou nainstalovány další balíčky.\Userprofile%\Documents\R\win-library\3.3*
