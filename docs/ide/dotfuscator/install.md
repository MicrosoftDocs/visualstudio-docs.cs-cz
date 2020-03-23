---
title: Instalace Dotfuscatoru Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, Protection, Community Edition, obfuscation, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio, install
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Přečtěte si, jak nainstalovat bezplatnou kopii komunity Dotfuscator, která je součástí sady Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: bb659976126713a11594ad1b4aeb536510744c38
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596811"
---
# <a name="install-dotfuscator-community"></a>Instalace Dotfuscatoru Community

Dotfuscator Community je volitelnou součástí sady Visual Studio.
Tyto pokyny vysvětlují, jak ji nainstalovat.

> [!NOTE]
> Kromě verzí Dotfuscator Community dodávaných s verzemi sady Visual Studio preemptive Solutions také pravidelně poskytuje aktualizované verze na svých webových stránkách.
> Pokud chcete stáhnout **nejnovější verzi** přímo namísto instalace z aplikace Visual Studio, **[klikněte sem a přejděte na stránku Stahování Dotfuscator][download]**.

## <a name="within-visual-studio"></a>V rámci sady Visual Studio

::: moniker range="vs-2019"

Komunitu Dotfuscator můžete nainstalovat z ide Sady Visual Studio:

1. Do **vyhledávacího pole** (Ctrl+Q) zadejte `dotfuscator`. <br/> <br/> ![Vyhledávací pole](media/install_in_vs19_12.png) <br/> <br/>

2. Ve zobrazených výsledcích hledání vyberte v části *Součásti položku* **Install PreEmptive Protection - Dotfuscator**.
   * Pokud se místo toho zobrazí pod nadpisem *Nabídky* **PreEmptive Protection – Dotfuscator Community**, pak je komunita Dotfuscator již nainstalována. Tuto možnost vyberte, [chcete-li začít][get-started].

3. Spustí se okno instalačního programu sady Visual Studio, které je předem nakonfigurováno pro instalaci komunity Dotfuscator.
   > [!NOTE]
   > Můžete být požádáni o zadání pověření správce, abyste mohli pokračovat.

4. V okně Instalační služba sady Visual Studio klepněte na tlačítko *Instalovat*. <br/> <br/> ![Kliknutí na Nainstalovat](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Komunitu Dotfuscator můžete nainstalovat z ide Sady Visual Studio:

1. Na panelu hledání **Snadné spuštění** (Ctrl+Q) zadejte . `dotfuscator` <br/> <br/> ![Snadné spuštění](media/install_from_vs_12.png) <br/> <br/>

2. Ve zobrazených výsledcích snadného spuštění vyberte v části *Instalace* **možnost PreEmptivní ochrana – dotfuscator (jednotlivá součást).**
   * Pokud se místo toho zobrazí pod nadpisem *Nabídky* **Nástroje – PreEmptivní ochrana - Dotfuscator**, pak je dotfuscator CE již nainstalován. Tuto možnost vyberte, [chcete-li začít][get-started].

3. Spustí se okno instalačního programu sady Visual Studio, které je předem nakonfigurováno pro instalaci dotfuscatoru CE.
   > [!NOTE]
   > Můžete být požádáni o zadání pověření správce, abyste mohli pokračovat.

4. V okně Instalační služba sady Visual Studio klepněte na tlačítko *Instalovat*. <br/> <br/> ![Kliknutí na Nainstalovat](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Po dokončení instalace můžete [začít používat Dotfuscator Community][get-started].

## <a name="during-visual-studio-installation"></a>Během instalace sady Visual Studio

Pokud jste ještě nenainstalovali Visual Studio, můžete získat instalační program z [webu sady Visual Studio][vs-install].
Při spuštění se zobrazí možnosti instalace pro vybranou edici sady Visual Studio.

::: moniker range="vs-2019"

![Možnosti instalace](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Možnosti instalace](media/install_ui_17.png)

::: moniker-end

Potom můžete nainstalovat Dotfuscator Společenství jako jednotlivé součásti sady Visual Studio:

1. Vyberte kartu **Jednotlivé součásti.**
2. V části *Nástroje kódu*zkontrolujte položku *PreEmptiv Protection - Dotfuscator.*<br/> <br/> ![Jednotlivé komponenty](media/install_individually_12.png) <br/> <br/>
3. Panel *Souhrn* zobrazuje v části *Jednotlivé součásti* *preemptivní ochranu – dotfuscator.* <br/> <br/> ![Podokno Souhrn](media/install_individually_3.png) <br/> <br/>
4. Nakonfigurujte další nastavení instalace podle potřeby pro vaše prostředí.
5. Až budete připraveni k instalaci sady Visual Studio, klepněte na tlačítko *Instalovat.*

Po dokončení instalace můžete začít používat Dotfuscator Community. Podrobnosti najdete na [stránce Getting Started (Začínáme) v kompletní uživatelské příručce k nástroji Dotfuscator Community][get-started].

## <a name="see-also"></a>Viz také

[Toto téma v úplné uživatelské příručce komunity Dotfuscator](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
