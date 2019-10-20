---
title: Instalace Dotfuscatoru Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, nepřesné, bezplatná řešení, bezplatná ochrana, ochrana, Community Edition, zmatene, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio, instalace
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
description: Přečtěte si, jak nainstalovat bezplatnou kopii Dotfuscator komunity zahrnuté v aplikaci Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4ff951ee202f706ab3b8553cff83519e36c86ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652422"
---
# <a name="install-dotfuscator-community"></a>Instalace Dotfuscatoru Community

Dotfuscator Community je volitelná součást sady Visual Studio.
Tyto pokyny vysvětlují, jak ji nainstalovat.

> [!NOTE]
> Kromě verzí Dotfuscator Community dodaných s vydáním sady Visual Studio pravidelně poskytuje řešení s bezkontaktní verzí aktualizované verze na svém webu.
> Pokud chcete stáhnout **nejnovější verzi** přímo místo instalace ze sady Visual Studio, **[klikněte sem a přejděte na stránku Dotfuscator ke stažení][download]** .

## <a name="within-visual-studio"></a>V sadě Visual Studio

::: moniker range="vs-2019"

Komunitu Dotfuscator můžete nainstalovat z integrovaného vývojového prostředí sady Visual Studio:

1. Do **vyhledávacího pole** (CTRL + Q) zadejte `dotfuscator`. <br/> <br/> ![Search box ](media/install_in_vs19_12.png) <br/> <br/>

2. V zobrazených výsledcích hledání pod nadpisem *součásti* vyberte možnost **instalovat neDotfuscatorelné ochrany –** .
   * Pokud se místo toho zobrazí, v části nabídky s názvem *Nabídka* s možností **přerušení ochrany – Dotfuscator komunita**je Dotfuscator komunita již nainstalována. [Začněte][get-started]tím, že tuto možnost vyberete.

3. Spustí se Instalační program pro Visual Studio okno, které je předem nakonfigurované pro instalaci komunity Dotfuscator.
   > [!NOTE]
   > Může být nutné zadat přihlašovací údaje správce, aby bylo možné pokračovat.

4. V okně Instalační program pro Visual Studio klikněte na *nainstalovat*. <br/> <br/> ![Click instalaci ](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Komunitu Dotfuscator můžete nainstalovat z integrovaného vývojového prostředí sady Visual Studio:

1. Na panelu hledání **snadného spuštění** (CTRL + Q) zadejte `dotfuscator`. <br/> <br/> ![Quick spuštění ](media/install_from_vs_12.png) <br/> <br/>

2. V zobrazených výsledcích snadného spuštění vyberte v části *instalace* možnost Dotfuscatorá **ochrana – (samostatná součást)** .
   * Pokud se místo toho zobrazí, v části *nabídky* pro položku **nástroje-inDotfuscator Protection-** je už nainstalovaná Dotfuscator CE. [Začněte][get-started]tím, že tuto možnost vyberete.

3. Spustí se Instalační program pro Visual Studio okno, předem nakonfigurované pro instalaci Dotfuscator CE.
   > [!NOTE]
   > Může být nutné zadat přihlašovací údaje správce, aby bylo možné pokračovat.

4. V okně Instalační program pro Visual Studio klikněte na *nainstalovat*. <br/> <br/> ![Click instalaci ](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Po dokončení instalace můžete [začít používat komunitu Dotfuscator][get-started].

## <a name="during-visual-studio-installation"></a>Během instalace sady Visual Studio

Pokud jste ještě nenainstalovali Visual Studio, můžete získat instalační program z [webu sady Visual Studio][vs-install].
Po spuštění se zobrazí možnosti instalace pro vybranou edici sady Visual Studio.

::: moniker range="vs-2019"

![Možnosti instalace](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Možnosti instalace](media/install_ui_17.png)

::: moniker-end

Pak můžete nainstalovat komunitu Dotfuscator jako samostatnou součást sady Visual Studio:

1. Vyberte kartu **jednotlivé součásti** .
2. V části *nástroje kódu*ověřte položku *Dotfuscator s možností přerušení ochrany* .<br/> <br/> ![Individual komponenty ](media/install_individually_12.png) <br/> <br/>
3. Panel *Souhrn* zobrazuje v části *jednotlivé komponenty* *Dotfuscator s možností přerušení ochrany* . <br/> <br/> podokno ![Summary ](media/install_individually_3.png) <br/> <br/>
4. Nakonfigurujte všechna další nastavení instalace, jak je to vhodné pro vaše prostředí.
5. Až budete připraveni k instalaci sady Visual Studio, klikněte na tlačítko *nainstalovat* .

Po dokončení instalace můžete začít používat komunitu Dotfuscator. Podrobnosti najdete [na stránce Začínáme v úplné příručce pro uživatele komunity Dotfuscator][get-started].

## <a name="see-also"></a>Viz také:

[Toto téma v úplné příručce pro uživatele komunity Dotfuscator](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html