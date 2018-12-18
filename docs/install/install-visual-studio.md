---
title: Instalace sady Visual Studio
titleSuffix: ''
description: Zjistěte, jak nainstalovat sadu Visual Studio, krok za krokem.
ms.custom: seodec18
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9160a5ebca6efe2cca48a2b8832a51fab3c6ca5a
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159734"
---
# <a name="install-visual-studio-2017"></a>Instalace sady Visual Studio 2017

Vítá vás nový způsob, jak nainstalovat sadu Visual Studio! V naší nejnovější verzi My jsme usnadnili si můžete vybrat a instalace jen těch funkcí, které potřebujete. Také jsme jste snížení nároků sady Visual Studio tak, aby nainstaloval rychleji a s menšími dopady na systém, než kdy dřív.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [instalace sady Visual Studio pro Mac](/visualstudio/mac/installation).

Chcete vědět více o tom, co je nového v této verzi? Najdete v našich [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).

Připraveno k instalaci? Provedeme vás přes něj krok za krokem.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1: Ujistěte se, že váš počítač připravený pro sadu Visual Studio

Před zahájením instalace sady Visual Studio:

1. Zkontrolujte, [požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs). Tyto požadavky vám pomohli určit, jestli počítač podporuje Visual Studio 2017.
2. Použijte nejnovější aktualizace Windows. Tyto aktualizace zkontrolujte, zda má počítač nejnovější aktualizace zabezpečení a požadované systémové komponenty pro sadu Visual Studio.
3. Restartování počítače. Restartování zajistí, že instalaci sady Visual Studio nebudou bránit probíhající instalace nebo aktualizace.
4. Uvolněte místo. Odeberte nepotřebné soubory a aplikace z % SystemDrive %, například spuštěním aplikace Vyčištění disku.

Dotazy týkající se spouštění předchozích verzí sady Visual Studio souběžně se sadou Visual Studio 2017, najdete v článku [informace o kompatibilitě sady Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Krok 2: stažení sady Visual Studio

Dále si stáhněte soubor zaváděcího nástroje sady Visual Studio. Uděláte to tak, klikněte na následující tlačítko, vyberte edici sady Visual Studio 2017, který chcete, klikněte na tlačítko **Uložit**a potom klikněte na tlačítko **otevřít složku**.

 > [!div class="button"]
 > [Stažení sady Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![Ikona filmové kamery pro video](media/video-icon.png "Sledovat video")  |    [Podívejte se na video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) o tom, jak stáhnout soubor zaváděcí nástroj Visual Studio a zvolte edici sady Visual Studio, která je pro vás nejvhodnější. |

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3: instalace instalační program sady Visual Studio

Potom spusťte zaváděcího nástroje sloužící k instalaci instalačního programu sady Visual Studio. Tohoto nového zjednodušeného instalačního programu obsahuje všechno, co je potřeba nainstalovat i přizpůsobení sady Visual Studio 2017.

1. Z vaší **stáhne** složky, dvakrát klikněte na panel zaváděcí nástroj, který odpovídá nebo se podobá následující soubory:

   * **vs_enterprise.exe** pro Visual Studio Enterprise
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_community.exe** pro Visual Studio Community  <br><br>

   Pokud se zobrazí oznámení o řízení uživatelských účtů, klikněte na tlačítko **Ano**.

2. Požádáme vás potvrďte Microsoft [licenční podmínky](https://visualstudio.microsoft.com/license-terms/) a Microsoft [prohlášení o zásadách](https://privacy.microsoft.com/privacystatement). Klikněte na tlačítko **pokračovat**.

   ![Licenční podmínky a prohlášení o zásadách](media/vs2017-privacy-and-license-terms.PNG "licenční podmínky společnosti Microsoft a prohlášení o ochraně osobních údajů")

## <a name="step-4---select-workloads"></a>Krok 4 – vyberte úlohy

Po dokončení instalace instalační program vám pomůže ho svou instalaci přizpůsobit výběrem sady funkcí, nebo úlohy –, který chcete. Tady je způsob.

1. Najít úlohu, kterou chcete v **instalaci sady Visual Studio** obrazovky.

   ![Vyberte úlohu instalačním programu sady Visual Studio 2017](../install/media/install-visual-studio-community.png)

     Například zvolte úlohu "Vývoj desktopových aplikací .NET". Obsahuje výchozí základní editor, který obsahuje základní podporu pro více než 20 jazycích, schopnost otevírat a upravovat kód z libovolné složky bez nutnosti vytvářet projekt, editaci kódu a integrované správy zdrojového kódu.

2. Po výběru workload(s) Chcete kliknutím **nainstalovat**.

    V dalším kroku stav obrazovek, které zobrazí průběh instalace sady Visual Studio.

3. Po instalaci nové úlohy a komponenty, klikněte na tlačítko **spuštění**.

> [!TIP]
> Kdykoli po instalaci můžete nainstalovat úlohy nebo komponenty, které nenainstaloval původně. Pokud máte Visual Studio otevřete, přejděte na **nástroje** > **získat nástroje a funkce...**  tím se otevře instalačního programu sady Visual Studio. Nebo otevřete **instalační program sady Visual Studio** z nabídky Start. Odtud můžete vybrat úlohy nebo komponenty, které chcete nainstalovat a pak klikněte na **změnit**.

|         |         |
|---------|---------|
|  ![Ikona filmové kamery pro video](media/video-icon.png "Sledovat video")  |    [Podívejte se na video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) o tom, jak nainstalovat Instalační program sady Visual Studio a pak nainstalujte úlohu. |

## <a name="step-5---select-individual-components-optional"></a>Krok 5: vyberte jednotlivé komponenty (volitelné)

Pokud už nechcete používat funkci úlohy k přizpůsobení instalace sady Visual Studio, můžete tak učiníte nainstalováním jednotlivé komponenty. Chcete-li vybrat jednotlivé komponenty, klikněte na tlačítko **jednotlivé komponenty** z instalačního programu sady Visual Studio, vyberte, co chcete a pak postupujte podle pokynů.

  ![Visual Studio 2017 – instalace jednotlivých součástí](media/vs2017-components.PNG "jednotlivých součástí instalace sady Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Ikona filmové kamery pro video](media/video-icon.png "Sledovat video")  |   [Podívejte se na video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) o postupu instalace jednotlivých součástí s použitím instalačního programu sady Visual Studio. |

## <a name="step-6---install-language-packs-optional"></a>Krok 6 – instalace jazykových sad (volitelné)

Ve výchozím nastavení instalační program pokusí tak, aby odpovídala jazyku operačního systému při prvním spuštění. Chcete-li nainstalovat Visual Studio 2017 v jazyce podle vašeho výběru, klikněte na tlačítko **jazykových sad** možnost z instalačního programu sady Visual Studio a postupujte podle zobrazených výzev.

  ![Visual Studio 2017 – instalace jazykových sad](media/vs2017-languages.PNG "jazykové sady Nainstalujte Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Ikona filmové kamery pro video](media/video-icon.png "Sledovat video")  |   [Podívejte se na video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) o tom, jak nainstalovat jazykovou sadu pomocí instalačního programu sady Visual Studio. |

### <a name="change-the-installer-language-from-the-command-line"></a>Změnit jazyk instalačního programu z příkazového řádku

Dalším způsobem, že můžete změnit výchozí jazyk je spuštění instalačního programu z příkazového řádku. Například můžete vynutit instalační program pro spuštění v anglickém jazyce pomocí následujícího příkazu: `vs_installer.exe --locale en-US`. Instalační program bude mějte na paměti Toto nastavení při příštím spuštění. Instalační program podporuje následující klíčová slova jazyka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru a tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Krok 7: Změna umístění instalace (volitelné)

**Nové ve verzi 15.7**: Nyní můžete snížit nároky na instalaci sady Visual Studio na systémovou jednotku. Můžete se rozhodnout, zda budou přesunuty mezipaměť pro stahování, sdílených komponent, sady SDK a nástrojů na jiné jednotky a sady Visual Studio na disku, na kterém běží nejrychlejší.

  ![Změna umístění instalace sady Visual Studio 2017 –](media/installation-options-by-location.png "Změna umístění instalace")

Další informace najdete v tématu [změnit umístění instalace v sadě Visual Studio](change-installation-locations.md) stránky.

## <a name="step-8---start-developing"></a>Krok 8: začít s vývojem

1. Po dokončení instalace sady Visual Studio, klikněte na tlačítko **spuštění** tlačítko, abyste mohli začít vyvíjet pomocí sady Visual Studio.

2. Klikněte na tlačítko **souboru**a potom klikněte na tlačítko **nový projekt**.

3. Vyberte typ projektu.

   Například [sestavení aplikace v jazyce C++](../ide/getting-started-with-cpp-in-visual-studio.md), klikněte na tlačítko **nainstalováno**, rozbalte **Visual C++** a pak vyberte typ projektu jazyka C++, který má být sestaveno.

   K [sestavení C# aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), klikněte na tlačítko **nainstalováno**, rozbalte **Visual C#** a pak vyberte C# typ, který chcete sestavit projekt.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Update Visual Studio 2017](update-visual-studio.md)
* [Úpravy sady Visual Studio 2017](modify-visual-studio.md)
* [Odinstalace sady Visual Studio 2017](uninstall-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Použití parametrů příkazového řádku pro instalaci sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Instalace sady Visual Studio pro Mac](/visualstudio/mac/installation)