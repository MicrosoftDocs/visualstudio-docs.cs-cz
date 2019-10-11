---
title: Instalace sady Visual Studio
titleSuffix: ''
description: Zjistěte, jak nainstalovat sadu Visual Studio, krok za krokem.
ms.date: 10/07/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6cd91fadea397955b756461383ed8e17030b4c3b
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018851"
---
# <a name="install-visual-studio"></a>Instalace sady Visual Studio

::: moniker range="vs-2019"

Vítá vás Visual Studio 2019! V této verzi si snadno zvolíte a nainstalujete jenom ty funkce, které potřebujete. A kvůli jejich menšímu minimálnímu množství je instalace rychle a s menším dopadem na systém.

::: moniker-end

::: moniker range="vs-2017"

Vítá vás nový způsob, jak nainstalovat sadu Visual Studio! V této verzi jsme usnadnili výběr a instalaci jenom těch funkcí, které potřebujete. Také jsme jste snížení nároků sady Visual Studio tak, aby nainstaloval rychleji a s menšími dopady na systém, než kdy dřív.

::: moniker-end

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [instalace sady Visual Studio pro Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Chcete vědět více o tom, co je nového v této verzi? Najdete v našich [poznámky k verzi](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

Chcete vědět více o tom, co je nového v této verzi? Najdete v našich [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

Připraveno k instalaci? Provedeme vás přes něj krok za krokem.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1: Ujistěte se, že váš počítač připravený pro sadu Visual Studio

Před zahájením instalace sady Visual Studio:

::: moniker range="vs-2017"

1. Zkontrolujte, [požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs). Tyto požadavky vám pomohli určit, jestli počítač podporuje Visual Studio 2017.

1. Použijte nejnovější aktualizace Windows. Tyto aktualizace zkontrolujte, zda má počítač nejnovější aktualizace zabezpečení a požadované systémové komponenty pro sadu Visual Studio.

1. Restartování počítače. Restartování zajistí, že instalaci sady Visual Studio nebudou bránit probíhající instalace nebo aktualizace.

1. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z % SystemDrive %, například spuštěním aplikace Vyčištění disku.

::: moniker-end

::: moniker range="vs-2019"

1. Zkontrolujte, [požadavky na systém](/visualstudio/releases/2019/system-requirements). Tyto požadavky vám pomůžou zjistit, jestli váš počítač podporuje Visual Studio 2019.

1. Použijte nejnovější aktualizace Windows. Tyto aktualizace zkontrolujte, zda má počítač nejnovější aktualizace zabezpečení a požadované systémové komponenty pro sadu Visual Studio.

1. Restartování počítače. Restartování zajistí, že instalaci sady Visual Studio nebudou bránit probíhající instalace nebo aktualizace.

1. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z % SystemDrive %, například spuštěním aplikace Vyčištění disku.

::: moniker-end

::: moniker range="vs-2017"

Dotazy týkající se spouštění předchozích verzí sady Visual Studio souběžně se sadou Visual Studio 2017, najdete v článku [informace o kompatibilitě sady Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Dotazy týkající se spouštění předchozích verzí sady Visual Studio vedle sebe se sadou Visual Studio 2019 naleznete na stránce [cílení a kompatibilita platformy Visual studio 2019](/visualstudio/releases/2019/compatibility/) .

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Krok 2: stažení sady Visual Studio

Dále si stáhněte soubor zaváděcího nástroje sady Visual Studio.

::: moniker range="vs-2017"

Další informace o tom, jak to udělat, najdete na stránce pro stažení [předchozích verzí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , kde můžete získat zaváděcí nástroj pro visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Chcete-li to provést, zvolte následující tlačítko, zvolte požadovanou verzi sady Visual Studio, zvolte možnost **Uložit**a pak zvolte možnost **Otevřít složku**.

 > [!div class="button"]
 > [Stáhnout Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3: instalace instalační program sady Visual Studio

Spuštěním souboru zaváděcího nástroje nainstalujte Instalační program pro Visual Studio. Tento nový odlehčený instalační program zahrnuje všechno, co potřebujete k instalaci i přizpůsobení sady Visual Studio.

1. Z vaší **stáhne** složky, dvakrát klikněte na panel zaváděcí nástroj, který odpovídá nebo se podobá následující soubory:

   * **vs_community.exe** pro Visual Studio Community
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_enterprise.exe** pro Visual Studio Enterprise

   Pokud se zobrazí upozornění na řízení uživatelských účtů, vyberte **Ano**.

2. Požádáme vás potvrďte Microsoft [licenční podmínky](https://visualstudio.microsoft.com/license-terms/) a Microsoft [prohlášení o zásadách](https://privacy.microsoft.com/privacystatement). Zvolte **pokračovat**.

   ![Licenční podmínky a prohlášení o zásadách](media/privacy-and-license-terms.png "licenční podmínky společnosti Microsoft a prohlášení o ochraně osobních údajů")

## <a name="step-4---choose-workloads"></a>Krok 4 – Výběr úloh

Po dokončení instalace instalační program vám pomůže ho svou instalaci přizpůsobit výběrem sady funkcí, nebo úlohy –, který chcete. Tady je způsob.

 ::: moniker range="vs-2017"

1. Najít úlohu, kterou chcete v **instalaci sady Visual Studio** obrazovky.

   ![Visual Studio 2017: Instalace úlohy](../install/media/vs-installer-installing-workloads.png)

     Například zvolte úlohu "Vývoj desktopových aplikací .NET". Obsahuje výchozí základní editor, který obsahuje základní podporu pro více než 20 jazycích, schopnost otevírat a upravovat kód z libovolné složky bez nutnosti vytvářet projekt, editaci kódu a integrované správy zdrojového kódu.

1. Po výběru úloh, které chcete zvolit, klikněte na **nainstalovat**.

    V dalším kroku stav obrazovek, které zobrazí průběh instalace sady Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. Po instalaci nové úlohy a komponenty, zvolte **spuštění**.

   ![Visual Studio 2019: Instalace úlohy](../install/media/vs-2019/vs-installer-workloads.png)

     Například vyberte úlohu vývoj pro ASP.NET a Web. Obsahuje výchozí základní editor, který obsahuje základní podporu pro více než 20 jazycích, schopnost otevírat a upravovat kód z libovolné složky bez nutnosti vytvářet projekt, editaci kódu a integrované správy zdrojového kódu.

1. Po výběru úloh, které chcete zvolit, klikněte na **nainstalovat**.

    V dalším kroku stav obrazovek, které zobrazí průběh instalace sady Visual Studio.

 ::: moniker-end

> [!TIP]
> Kdykoli po instalaci můžete nainstalovat úlohy nebo komponenty, které nenainstaloval původně. Pokud máte Visual Studio otevřete, přejděte na **nástroje** > **získat nástroje a funkce...**  tím se otevře instalačního programu sady Visual Studio. Nebo otevřete **instalační program sady Visual Studio** z nabídky Start. Odtud můžete zvolit úlohy nebo komponenty, které chcete nainstalovat. Pak zvolte **Upravit**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5 – výběr jednotlivých komponent (volitelné)

Pokud nechcete použít funkci úlohy k přizpůsobení instalace sady Visual Studio nebo chcete přidat více součástí, než kolik jich je potřeba, můžete to udělat tak, že nainstalujete nebo přidáte jednotlivé komponenty z karty **jednotlivé komponenty** . Zvolte, co chcete, a pak postupujte podle pokynů.

::: moniker range="vs-2017"

  ![Visual Studio 2017 – instalace jednotlivých součástí](media/vs-installer-installing-components.png "jednotlivých součástí instalace sady Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 – instalace jednotlivých komponent](media/vs-2019/vs-installer-individual-components.png "nainstaluje jednotlivé součásti sady Visual Studio") .

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Krok 6 – instalace jazykových sad (volitelné)

Ve výchozím nastavení instalační program pokusí tak, aby odpovídala jazyku operačního systému při prvním spuštění. Chcete-li nainstalovat sadu Visual Studio v jazyce podle vašeho výběru, zvolte kartu **jazykové sady** z instalační program pro Visual Studio a potom postupujte podle pokynů.

::: moniker range="vs-2017"

  ![Visual Studio 2017 – instalace jazykových sad](media/vs-installer-installing-language-packs.png "jazykové sady Nainstalujte Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual studio 2019 – instalace jazykových sad], které(media/vs-2019/vs-installer-language-packs.png "instalují jazykové sady Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Změnit jazyk instalačního programu z příkazového řádku

Dalším způsobem, že můžete změnit výchozí jazyk je spuštění instalačního programu z příkazového řádku. Například můžete vynutit instalační program pro spuštění v anglickém jazyce pomocí následujícího příkazu: `vs_installer.exe --locale en-US`. Instalační program bude mějte na paměti Toto nastavení při příštím spuštění. Instalační program podporuje následující klíčová slova jazyka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru a tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Krok 7 – výběr umístění instalace (volitelné)

::: moniker range="vs-2017"

**Novinka v 15,7**: Nyní můžete omezit nároky na instalaci sady Visual Studio na systémové jednotce. Můžete se rozhodnout, zda budou přesunuty mezipaměť pro stahování, sdílených komponent, sady SDK a nástrojů na jiné jednotky a sady Visual Studio na disku, na kterém běží nejrychlejší.

  ![Visual Studio 2017 – Změna umístění instalace](media/installation-options-by-location.png "Změna umístění instalace")

::: moniker-end

::: moniker range="vs-2019"

Nároky na instalaci sady Visual Studio můžete snížit na systémové jednotce. Můžete se rozhodnout, zda budou přesunuty mezipaměť pro stahování, sdílených komponent, sady SDK a nástrojů na jiné jednotky a sady Visual Studio na disku, na kterém běží nejrychlejší.

  ![Visual Studio 2019 – výběr]umístění instalace(media/vs-2019/vs-installer-installation-locations.png "Výběr umístění instalace")

::: moniker-end

> [!IMPORTANT]
> Můžete vybrat jinou jednotku pouze při první instalaci sady Visual Studio. Pokud jste ho už nainstalovali a chcete změnit jednotky, musíte odinstalovat sadu Visual Studio a pak ji znovu nainstalovat.

Další informace najdete na stránce [Výběr umístění instalace](change-installation-locations.md) .

## <a name="step-8---start-developing"></a>Krok 8: začít s vývojem

::: moniker range="vs-2017"

1. Po dokončení instalace sady Visual Studio klikněte na tlačítko **Spustit** a začněte s vývojem v aplikaci Visual Studio.

2. Zvolte **soubor**a pak zvolte **Nový projekt**.

3. Vyberte typ projektu.

   Chcete-li například [sestavit C++ aplikaci](/cpp/get-started/tutorial-console-cpp), zvolte možnost **nainstalováno**, rozbalte položku **vizuál C++** a pak zvolte C++ typ projektu, který chcete sestavit.

   Chcete-li [sestavit C# aplikaci](../get-started/csharp/tutorial-console.md), zvolte možnost **nainstalováno**, rozbalte položku **vizuál C#** a C# pak zvolte typ projektu, který chcete sestavit.

::: moniker-end

::: moniker range="vs-2019"

1. Po dokončení instalace sady Visual Studio klikněte na tlačítko **Spustit** a začněte s vývojem v aplikaci Visual Studio.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. Do vyhledávacího pole zadejte typ aplikace, kterou chcete vytvořit, aby se zobrazil seznam dostupných šablon. Seznam šablon závisí na úlohách, které jste si zvolili během instalace. Pokud chcete zobrazit různé šablony, vyberte jiné úlohy.

   Hledání konkrétního programovacího jazyka můžete filtrovat také pomocí rozevíracího seznamu **jazyk** . Filtrovat můžete také pomocí seznamu **platforem** a seznamu **typ projektu** .

1. Visual Studio otevře nový projekt a Vy jste připravení na kód!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](modify-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Instalace sady Visual Studio pro Mac](/visualstudio/mac/installation)
