---
title: Spuštění nástrojů profilování s ladicím programem nebo bez něj | Dokumenty společnosti Microsoft
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 273dc6770f2928ed65d6a473b7f1986bc353687e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999465"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj

Visual Studio nabízí výběr nástrojů pro měření výkonu a profilování. Některé nástroje, jako **je využití procesoru** a **využití paměti**, lze spustit s ladicím programem nebo bez něj a na release nebo debug sestavení konfigurace. **Nástroje profileru výkonu,** jako je **časová osa aplikace,** lze spustit v sestaveních Ladění nebo Vydání. Nástroje integrované s ladicím programem, jako je okno **Diagnostické nástroje** a **události,** se spouštějí pouze během ladicích relací.

>[!NOTE]
>Nástroje výkonu bez ladicího programu můžete používat se systémem Windows 7 a novějším. Windows 8 nebo novější je nutné spustit nástroje profilování integrované ladicí program.

Profilování **výkonu** bez ladicího programu a **diagnostické nástroje** integrované v ladicím programu poskytují různé informace a prostředí. Nástroje integrované s ladicími programy zobrazují zarážky a hodnoty proměnných. Nástroje bez ladicího programu poskytují výsledky blíže k prostředí koncového uživatele.

Chcete-li se rozhodnout, které nástroje a výsledky použít, zvažte následující body:

- Problémy s externím výkonem, jako jsou problémy se vstupně-ru nebo odezvou v síti, nebudou v ladicím programu nebo v nástrojích bez ladicího programu vypadat příliš odlišně.
- Pro problémy způsobené volání náročné na procesor může být značné rozdíly výkonu mezi sestavení verze a ladění. Zkontrolujte, zda problém existuje v sestavení verze.
- Pokud k problému dochází pouze během ladění sestavení, pravděpodobně není nutné spouštět nástroje bez ladicího programu. V části Problémy s sestavením verze rozhodněte, zda nástroje ladicího programu pomohou k dalšímu šetření.
- Vydání sestavení poskytují optimalizace, jako je vkládání volání funkce a konstanty, prořezávání nevyužité cesty kódu a ukládání proměnných způsoby, které nelze použít ladicí program. Čísla výkonu v nástrojích integrované ladicí program jsou méně přesné, protože ladění sestavení chybí tyto optimalizace.
- Samotný ladicí program mění dobu výkonu, stejně jako nezbytné operace ladicího programu, jako je zachycení událostí výjimky a zatížení modulu.
- Čísla výkonu sestavení uvolněte v nástrojích **Profiler výkonu** jsou nejpřesnější a nejpřesnější. Výsledky nástrojů integrované s ladicími programy jsou nejužitečnější pro porovnání s jinými měřeními souvisejícími s laděním.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Shromažďování dat profilování při ladění

Když začnete ladění v sadě Visual Studio výběrem **ladění začít** > ladění nebo stisknutím**klávesy** **F5**, zobrazí se ve výchozím nastavení okno **Diagnostické nástroje.** Chcete-li jej otevřít ručně, vyberte **možnost Ladění** > **diagnostických nástrojů služby****Windows** > Show . V okně **Diagnostické nástroje** se zobrazují informace o událostech, paměti procesu a využití procesoru.

![Diagnostické nástroje](../profiling/media/diagnostictools-update1.png "Diagnostické nástroje")

- Pomocí ikony **Nastavení** na panelu nástrojů vyberte, zda chcete zobrazit **využití paměti**, **analýzu ui**a **využití procesoru**.

- V **Settings** rozevíracím okně **Nastavení** otevřete **stránky vlastností Nástroje diagnostiky** s dalšími možnostmi.

- Pokud používáte Visual Studio Enterprise, můžete povolit nebo zakázat IntelliTrace v části Visual Studio **Tools** > **Options** > **IntelliTrace**.

Diagnostická relace končí, když zastavíte ladění.

Můžete také zobrazit **diagnostické nástroje** pro vzdálené ladění cílů. Pro vzdálené ladění a profilování visual studio vzdálený ladicí program musí být nainstalován a spuštěn na vzdáleném cíli.
- Vzdálené ladění a profilování projektů aplikací plochy naleznete [v tématu Vzdálené ladění](../debugger/remote-debugging.md).
- Vzdálené ladění a profilování aplikací UPW naleznete v tématu [Ladění aplikací UPW na vzdálených počítačích](../debugger/run-windows-store-apps-on-a-remote-machine.md).

### <a name="the-events-tab"></a>Karta Události

Během relace ladění události kartu **události** **diagnostické nástroje** okno uvádí diagnostické události, ke kterým dochází. Předpony kategorií: **Zarážka**, **Soubor**a další umožňují rychle prohledat seznam pro kategorii nebo přeskočit kategorie, které vás nezajímají.

Rozevírací **seznam Filtr** slouží k filtrování událostí v zobrazení a mimo ně výběrem nebo zrušením výběru určitých kategorií událostí.

![Filtr diagnostických událostí](../profiling/media/diagnosticeventfilter.png "Filtr diagnostických událostí")

Pomocí vyhledávacího pole vyhledejte konkrétní řetězec v seznamu událostí. Zde jsou výsledky hledání řetězce "název", který odpovídal čtyřem událostem:

![Hledání diagnostických událostí](../profiling/media/diagnosticseventsearch.png "Hledání diagnostických událostí")

Další informace naleznete v [tématu Hledání a filtrování karty Události v okně Diagnostické nástroje](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Shromažďování dat profilování bez ladění

Chcete-li shromažďovat data o výkonu bez ladění, můžete spustit nástroje **Profiler výkonu.** Některé nástroje profilování vyžadují ke spuštění oprávnění správce. Visual Studio můžete otevřít jako správce nebo můžete spustit nástroje jako správce při spuštění diagnostické relace.

1. S otevřeným projektem v sadě Visual Studio vyberte **ladit** > **profilování výkonu**nebo stiskněte **alt**+**F2**.

1. Na stránce spuštění diagnostiky vyberte jeden nebo více nástrojů, které chcete spustit. Zobrazí se pouze nástroje, které jsou použitelné pro typ projektu, operační systém a programovací jazyk. Vyberte **Zobrazit všechny nástroje,** chcete-li zobrazit také nástroje, které jsou pro tuto diagnostickou relaci zakázány. Tady je postup, jak můžou vaše volby vypadat pro aplikaci C# UWP:

   ![Výběr diagnostických nástrojů](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Chcete-li zahájit diagnostickou relaci, vyberte **možnost Spustit**.

   Během spuštění relace některé nástroje zobrazují grafy dat v reálném čase na stránce diagnostických nástrojů.

    ![Shromažďování dat o centru pro výkon a diagnostiku](../profiling/media/pdhub_collectdata.png "Centrum shromažďuje data")

1. Chcete-li ukončit diagnostickou relaci, vyberte **možnost Zastavit shromažďování**.

   Analyzovaná data se zobrazí na stránce **Sestava.**

Sestavy můžete uložit a otevřít je ze seznamu **Naposledy otevřené relace** na stránce spuštění diagnostických nástrojů.

![Otevření uloženého souboru relace diagnostiky](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Sestava profilování
 ![Sestava diagnostických nástrojů](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Každý diagnostický nástroj zobrazí jeden nebo více hlavních grafů. Pokud vaše diagnostická relace měla více než jeden nástroj, zobrazí se všechny jejich hlavní grafy.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Jednotlivé grafy jednotlivých nástrojů můžete sbalit a rozbalit.|
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Pokud data obsahují více než jeden nástroj, podrobnosti o nástroji jsou shromažďovány pod záložkami.|
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|V dolní polovině sestavy se zobrazí jedno nebo více podrobných pohledů pro každý nástroj. Zobrazení můžete filtrovat výběrem oblastí časové osy.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Spuštění diagnostických relací na nainstalovaných nebo spuštěných aplikacích

 Kromě spuštění aplikace z projektu Visual Studio můžete také spouštět diagnostické relace na alternativní cíle. Můžete například diagnostikovat problémy s výkonem v aplikaci, která byla nainstalovaná z Windows App Storu.

 ![Zvolit cíl analýzy diagnostických nástrojů](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

 Můžete spustit aplikace, které jsou již nainstalovány, nebo připojit diagnostické nástroje k aplikacím a procesům, které jsou již spuštěny. Když vyberete **Spuštěná aplikace** nebo **Nainstalovaná aplikace**, vyberete aplikaci ze seznamu, který vyhledá aplikace v zadaném cíli nasazení. Tento cíl může být místní nebo vzdálený počítač.

 ![Výběr spuštěné nebo nainstalované aplikace pro diagnostiku](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

## <a name="see-also"></a>Viz také

Níže jsou blogové příspěvky a články MSDN od vývojového týmu diagnostiky:
- [Časopis MSDN: Analýza výkonu při ladění v sadě Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [Časopis MSDN: Rychlejší diagnostika problémů pomocí funkce IntelliTrace](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [Příspěvek blogu: Diagnostika nevracení obslužné rutiny událostí pomocí nástroje využití paměti v sadě Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)

- [Video: Historické ladění pomocí technologie IntelliTrace v aplikaci Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)

- [Video: Ladění problémů s výkonem pomocí Visual Studia 2015](https://channel9.msdn.com/Events/Build/2015/3-731)

- [Tipy pro perftips: Informace o výkonu na první pohled při ladění pomocí sady Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

- [Okno ladicího programu diagnostické nástroje v sadě Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [IntelliTrace v sadě Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
