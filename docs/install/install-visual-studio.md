---
title: Instalace sady Visual Studio
titleSuffix: ''
description: Přečtěte si, jak nainstalovat Visual Studio, krok za krokem.
ms.date: 12/13/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d8e6e3a857c9bbf5577cf395f698f64cfb11bddc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302992"
---
# <a name="install-visual-studio"></a>Instalace sady Visual Studio

::: moniker range="vs-2019"

Vítáme vás v Visual Studiu 2019! V této verzi je snadné vybrat a nainstalovat pouze funkce, které potřebujete. A díky snížené minimální půdorysu se instaluje rychle a s menším dopadem na systém.

::: moniker-end

::: moniker range="vs-2017"

Vítá vás nový způsob instalace sady Visual Studio! V této verzi jsme vám usnadnili výběr a instalaci pouze funkcí, které potřebujete. Také jsme snížili minimální nároky na nároky sady Visual Studio, takže se instaluje rychleji a s menším dopadem na systém než kdykoli předtím.

::: moniker-end

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Instalace Visual Studia pro Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Chcete se dozvědět více o tom, co dalšího je v této verzi nového? Podívejte se na naše [poznámky k verzi](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

Chcete se dozvědět více o tom, co dalšího je v této verzi nového? Podívejte se na naše [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

Jste připraveni k instalaci? Provedeme vás tím krok za krokem.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 – Ujistěte se, že je počítač připravený pro Visual Studio.

Než začnete instalovat Visual Studio:

::: moniker range="vs-2017"

1. Zkontrolujte [systémové požadavky](/visualstudio/productinfo/vs2017-system-requirements-vs). Tyto požadavky vám pomohou zjistit, jestli váš počítač podporuje Visual Studio 2017.

1. Použijte nejnovější aktualizace systému Windows. Tyto aktualizace zajišťují, že počítač obsahuje nejnovější aktualizace zabezpečení a požadované systémové součásti sady Visual Studio.

1. Restartování. Restartování zajišťuje, že všechny čekající instalace nebo aktualizace nebrání instalaci sady Visual Studio.

1. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z %SystemDrive % například spuštěním aplikace Vyčištění disku.

::: moniker-end

::: moniker range="vs-2019"

1. Zkontrolujte [systémové požadavky](/visualstudio/releases/2019/system-requirements). Tyto požadavky vám pomohou zjistit, jestli váš počítač podporuje Visual Studio 2019.

1. Použijte nejnovější aktualizace systému Windows. Tyto aktualizace zajišťují, že počítač obsahuje nejnovější aktualizace zabezpečení a požadované systémové součásti sady Visual Studio.

1. Restartování. Restartování zajišťuje, že všechny čekající instalace nebo aktualizace nebrání instalaci sady Visual Studio.

1. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z %SystemDrive % například spuštěním aplikace Vyčištění disku.

::: moniker-end

::: moniker range="vs-2017"

Dotazy týkající se spuštění předchozích verzí sady Visual Studio vedle Visual Studia 2017 najdete v [tématu Podrobnosti o kompatibilitě sady Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Dotazy týkající se spuštění předchozích verzí Visual Studia vedle Visual Studia 2019 najdete na stránce [Cílení a kompatibilita platformy Visual Studia 2019.](/visualstudio/releases/2019/compatibility/)

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Krok 2 – stažení sady Visual Studio

Dále stáhněte soubor zaváděcího nástroje sady Visual Studio.

::: moniker range="vs-2017"

Pokud chcete získat zaváděcí nástroj pro Visual Studio 2017, podívejte se na stránku pro stažení [předchozích verzí Visual Studia,](https://visualstudio.microsoft.com/vs/older-downloads/) kde najdete podrobnosti o tom, jak to udělat.

::: moniker-end

::: moniker range="vs-2019"

Chcete-li tak učinit, zvolte následující tlačítko, zvolte požadovanou edici sady Visual Studio, zvolte **Uložit**a pak zvolte **Otevřít složku**.

 > [!div class="button"]
 > [Stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 – Instalace instalačního programu sady Visual Studio

Spusťte soubor zaváděcího nástroje a nainstalujte instalační program sady Visual Studio. Tento nový odlehčený instalační program obsahuje vše, co potřebujete k instalaci a přizpůsobení sady Visual Studio.

1. Ve složce **Soubory ke stažení** poklepejte na zaváděcí nástroj, který odpovídá jednomu z následujících souborů nebo je podobný:

   * **vs_community.exe** pro komunitu sady Visual Studio
   * **vs_professional.exe** pro Visual Studio Professional
   * **vs_enterprise.exe** pro Visual Studio Enterprise

   Pokud obdržíte oznámení o řízení uživatelských účtů, zvolte **Ano**.

2. Požádáme vás o potvrzení [licenčních podmínek společnosti](https://visualstudio.microsoft.com/license-terms/) Microsoft a [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement). Zvolte **Pokračovat**.

   ![Licenční podmínky a prohlášení o zásadách ochrany osobních údajů](media/privacy-and-license-terms.png "Licenční podmínky společnosti Microsoft a prohlášení o zásadách ochrany osobních údajů")

## <a name="step-4---choose-workloads"></a>Krok 4 – výběr úloh

Po instalaci instalačního programu ji můžete použít k přizpůsobení instalace výběrem požadovaných sad funkcí nebo úloh. Jak na to:

 ::: moniker range="vs-2017"

1. Najděte požadované úlohy v **Instalační službě sady Visual Studio**.

   ![Visual Studio 2017: Instalace úlohy](../install/media/vs-installer-installing-workloads.png)

     Vyberte například úlohu "Vývoj plochy.NET". Dodává se s výchozím editorem jádra, který zahrnuje základní podporu úprav kódu pro více než 20 jazyků, možnost otevřít a upravit kód z libovolné složky bez nutnosti projektu a integrovanou správu zdrojového kódu.

1. Po výběru pracovního vytížení, které chcete, zvolte **Instalovat**.

    Dále se zobrazí stavové obrazovky, které zobrazují průběh instalace sady Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. Najděte požadované úlohy v **Instalační službě sady Visual Studio**.

   ![Visual Studio 2019: Instalace úlohy](../install/media/vs-2019/vs-installer-workloads.png)

     Můžete například zvolit úlohu "ASP.NET a vývoj webových aplikací". Dodává se s výchozím editorem jádra, který zahrnuje základní podporu úprav kódu pro více než 20 jazyků, možnost otevřít a upravit kód z libovolné složky bez nutnosti projektu a integrovanou správu zdrojového kódu.

1. Po výběru pracovního vytížení, které chcete, zvolte **Instalovat**.

    Dále se zobrazí stavové obrazovky, které zobrazují průběh instalace sady Visual Studio.

 ::: moniker-end

> [!TIP]
> Kdykoli po instalaci můžete nainstalovat úlohy nebo součásti, které jste původně nenainstalovali. Pokud máte otevřenou Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...** která otevře Instalační program sady Visual Studio. Nebo otevřete **Instalační program sady Visual Studio** z nabídky Start. Odtud můžete zvolit úlohy nebo součásti, které chcete nainstalovat. Potom zvolte **Změnit**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5 - Výběr jednotlivých součástí (volitelné)

Pokud nechcete používat funkci Úlohy k přizpůsobení instalace sady Visual Studio nebo chcete přidat více součástí, než nainstaluje pracovní vytížení, můžete tak učinit instalací nebo přidáním jednotlivých součástí na kartě **Jednotlivé součásti.**

::: moniker range="vs-2017"

  ![Visual Studio 2017 – instalace jednotlivých součástí](media/vs-installer-installing-components.png "Instalace jednotlivých součástí sady Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 – instalace jednotlivých součástí](media/vs-2019/vs-installer-individual-components.png "Instalace jednotlivých součástí sady Visual Studio")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Krok 6 – Instalace jazykových sad (volitelné)

Instalační program se ve výchozím nastavení pokusí při prvním spuštění přizpůsobit jazyk operačního systému. Chcete-li aplikaci Visual Studio nainstalovat v jazyce podle vašeho výběru, zvolte kartu **Jazykové balíčky** v instalační službě sady Visual Studio a postupujte podle pokynů.

::: moniker range="vs-2017"

  ![Visual Studio 2017 – instalace jazykových sad](media/vs-installer-installing-language-packs.png "Instalace jazykových sad Sady Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 – instalace jazykových sad](media/vs-2019/vs-installer-language-packs.png "Instalace jazykových sad Sady Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Změna jazyka instalačního programu z příkazového řádku

Dalším způsobem, jak můžete změnit výchozí jazyk, je spuštění instalačního programu z příkazového řádku. Můžete například vynutit spuštění instalačního programu v angličtině `vs_installer.exe --locale en-US`pomocí následujícího příkazu: . Instalační program si toto nastavení zapamatuje při příštím spuštění. Instalátor podporuje následující jazykové tokeny: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru a tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Krok 7 – Vyberte umístění instalace (volitelné)

::: moniker range="vs-2017"

**Novinka v 15.7**: Nyní můžete snížit nároky na instalaci sady Visual Studio na systémové jednotce. Můžete přesunout mezipaměť pro stahování, sdílené součásti, sady SDK a nástroje na různé jednotky a ponechat visual studio na jednotce, která ji spouští nejrychleji.

  ![Visual Studio 2017 – změna umístění instalace](media/installation-options-by-location.png "Změna umístění instalace")

::: moniker-end

::: moniker range="vs-2019"

Můžete snížit nároky na instalaci sady Visual Studio na systémové jednotce. Můžete přesunout mezipaměť pro stahování, sdílené součásti, sady SDK a nástroje na různé jednotky a ponechat visual studio na jednotce, která ji spouští nejrychleji.

  ![Visual Studio 2019 – výběr umístění instalace](media/vs-2019/vs-installer-installation-locations.png "Vyberte umístění instalace")

::: moniker-end

> [!IMPORTANT]
> Jinou jednotku můžete vybrat pouze při první instalaci sady Visual Studio. Pokud jste ji již nainstalovali a chcete změnit jednotky, musíte odinstalovat Visual Studio a znovu ji nainstalovat.

Další informace naleznete na stránce [Vybrat umístění instalace.](change-installation-locations.md)

## <a name="step-8---start-developing"></a>Krok 8 – Začněte vyvíjet

::: moniker range="vs-2017"

1. Po dokončení instalace sady Visual Studio zvolte tlačítko **Spustit** a s ním začít se vyvíjet.

2. Zvolte **Soubor**a pak zvolte **Nový projekt**.

3. Vyberte typ projektu.

   Chcete-li například [vytvořit aplikaci jazyka C++](/cpp/get-started/tutorial-console-cpp), zvolte **Nainstalováno**, rozbalte **visual c++** a pak zvolte typ projektu C++, který chcete vytvořit.

   Chcete-li [vytvořit aplikaci C#](../get-started/csharp/tutorial-console.md), zvolte **Nainstalováno**, rozbalte **visual c#** a pak zvolte typ projektu C#, který chcete sestavit.

::: moniker-end

::: moniker range="vs-2019"

1. Po dokončení instalace sady Visual Studio zvolte tlačítko **Spustit** a s ním začít se vyvíjet.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

1. Do vyhledávacího pole zadejte typ aplikace, kterou chcete vytvořit, abyste viděli seznam dostupných šablon. Seznam šablon závisí na zatížení, které jste zvolili během instalace. Chcete-li zobrazit různé šablony, zvolte různé úlohy.

   Hledání konkrétního programovacího jazyka můžete také filtrovat pomocí rozevíracího seznamu **Jazyk.** Můžete filtrovat pomocí seznamu **Platforma** a seznamu **typů projektu.**

1. Visual Studio otevře nový projekt a jste připraveni ke kódu!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](modify-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Instalace sady Visual Studio pro Mac](/visualstudio/mac/installation)
