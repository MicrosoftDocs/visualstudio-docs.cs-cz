---
title: Spuštění nástrojů pro profilaci s ladicím programem nebo bez něj | Microsoft Docs
description: Další informace o rozdílech mezi různými režimy dostupnými pro nástroje pro profilaci
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13fd616e9ec596bfcdeb3718a62dc1a3a1bc8137
ms.sourcegitcommit: 172aaf05596a9d8ded298b7b104569c1cce6160e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/13/2020
ms.locfileid: "92007162"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj

Visual Studio nabízí možnost měření výkonu a nástrojů pro profilaci. Některé nástroje, jako je využití CPU a využití paměti, můžou běžet s ladicím programem nebo bez něj, a to na vydaných nebo ladicích konfiguracích sestavení. Nástroje, které se zobrazí v [okně diagnostické nástroje](../profiling/profiling-feature-tour.md#measure-performance-while-debugging) , se spouštějí pouze během relace ladění. Nástroje, které se zobrazí v [profileru výkonu](../profiling/profiling-feature-tour.md#post_mortem) , se spouštějí bez ladicího programu a výsledky se analyzují po zvolení zastavení a shromažďování dat (pro analýzu po porážce).

>[!NOTE]
>Nástroje pro sledování výkonu bez ladicího programu můžete používat se systémem Windows 7 nebo novějším. Pro spuštění nástrojů pro profilaci integrovaných s ladicím programem je vyžadován systém Windows 8 nebo novější.

Profiler výkonu bez ladicího programu a Diagnostické nástroje integrované s ladicím programem poskytují různé informace a prostředí. Nástroje integrované v ladicím programu ukazují proměnné hodnoty a umožňují používat zarážky. Nástroje bez ladicího programu poskytují výsledky směrem k prostředí koncových uživatelů.

Chcete-li se rozhodnout, které nástroje a výsledky použít, vezměte v úvahu tyto informace:

- Nástroj integrovaný v ladicím programu vs. nástroj bez ladicího programu
  - Problémy s externím výkonem, jako jsou vstupně-výstupní operace se soubory nebo problémy s odezvou sítě, se v ladicím programu nebo v neladicích nástrojích neliší.
  - Ladicí program změní dobu výkonu, protože vyžaduje operace ladicího programu, jako je zachycení výjimek a událostí načtení modulu.
  - Čísla výkonu sestavení verze v profileru výkonu jsou nejpřesnější a přesná. Výsledky nástroje integrované v ladicím programu jsou nejužitečnější pro porovnání s ostatními měřeními souvisejícími s laděním nebo pro použití funkcí ladicího programu.
- Ladění vs. sestavení pro vydání
  - Pro problémy způsobené voláními náročnými na procesor mohou nastat výrazné rozdíly ve výkonu mezi sestaveními vydaných verzí a ladění. Zkontrolujte, zda problém existuje v sestavení vydaných verzí.
  - Pokud k problému dochází pouze během sestavení ladění, pravděpodobně nemusíte spouštět nástroje bez ladicího programu. V případě problémů se sestavením verze se rozhodněte, jestli funkce poskytované nástroji integrovaným ladicím programem pomůžou problém identifikovat.
  - Sestavení vydaných verzí poskytují optimalizace, jako jsou volání funkcí a konstanty, vyřazení nepoužitých cest kódu a ukládání proměnných způsobem, který nelze použít v ladicím programu. Čísla výkonu v sestaveních ladění jsou méně přesná, protože sestavení pro ladění nemají tyto optimalizace.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Shromažďování dat profilace během ladění

Když spustíte ladění v aplikaci Visual Studio tak, že vyberete **ladění**  >  **Spustit ladění**nebo stisknete klávesu **F5**, ve výchozím nastavení se zobrazí okno **diagnostické nástroje** . Pokud ho chcete otevřít ručně, vyberte **ladit**  >  **Windows**  >  **Zobrazit diagnostické nástroje**. V okně **diagnostické nástroje** se zobrazují informace o událostech, paměti procesu a využití procesoru.

![Snímek obrazovky okna Diagnostické nástroje](../profiling/media/diagnostictoolswindow.png " Okno Diagnostické nástroje")

- Pomocí ikony **Nastavení** na panelu nástrojů vyberte, jestli se má zobrazit **využití paměti**, **Analýza uživatelského rozhraní**a **využití procesoru**.

- V rozevíracím seznamu **Nastavení** vyberte **Nastavení** a otevřete **stránku vlastností diagnostické nástroje** s dalšími možnostmi.

- Pokud používáte Visual Studio Enterprise, můžete povolit nebo zakázat IntelliTrace tak, že kliknete na **nástroje**  >  **Možnosti**  >  **IntelliTrace**.

Diagnostická relace skončí po zastavení ladění.

Další informace naleznete v tématech:

- [Měření výkonu aplikace analýzou využití CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Měření paměti profilu v sadě Visual Studio](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>Karta události

Během relace ladění vypíše karta události v okně Diagnostické nástroje diagnostické události, ke kterým dojde. Kategorie *zarážky*, *soubory*a další v této kategorii vám umožní rychle vyhledat seznam pro kategorii nebo přeskočit kategorie, o kterých nezáleží.

Pomocí rozevíracího seznamu **Filtr** můžete filtrovat události v zobrazení a mimo ně výběrem nebo zrušením určitých kategorií událostí.

![Snímek obrazovky s filtrem diagnostických událostí](../profiling/media/diagnosticeventfilter.png "Filtr diagnostické události")

Pomocí vyhledávacího pole vyhledejte konkrétní řetězec v seznamu událostí. Tady jsou výsledky hledání *názvu* řetězce, který se shoduje se čtyřmi událostmi:

![Snímek obrazovky s vyhledáváním diagnostických událostí](../profiling/media/diagnosticseventsearch.png "Hledání diagnostické události")

Další informace najdete v tématu [hledání a filtrování událostí diagnostické nástroje okna na kartě události](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Shromažďování dat profilace bez ladění

Chcete-li shromažďovat data o výkonu bez ladění, můžete spustit nástroje profileru výkonu.

1. Otevřete projekt v sadě Visual Studio, nastavte konfiguraci řešení na **release**a jako cíl nasazení vyberte **místní ladicí program systému Windows**   (nebo **místní počítač**).

1. Vyberte **ladit**  >  **Performance Profiler**nebo stiskněte **ALT** + **F2**.

1. Na stránce spuštění diagnostických nástrojů vyberte jeden nebo více nástrojů, které chcete spustit. Zobrazují se jenom nástroje, které platí pro typ projektu, operační systém a programovací jazyk. Vyberte **Zobrazit všechny nástroje** a zobrazí se také nástroje, které jsou pro tuto diagnostickou relaci zakázané.

   ![Snímek obrazovky diagnostických nástrojů](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Chcete-li spustit relaci diagnostiky, vyberte možnost **Spustit**.

   Když je relace spuštěná, některé nástroje zobrazují grafy dat v reálném čase na stránce diagnostické nástroje a také ovládací prvky pro pozastavení a obnovení sběru dat.

    ![Snímek obrazovky shromažďování dat v profileru výkonu](../profiling/media/diaghubcollectdata.png "Shromáždění dat z centra")

1. Chcete-li ukončit relaci diagnostiky, vyberte **Zastavit shromažďování**.

   Analyzovaná data se zobrazí na stránce **sestavy** .

Sestavy můžete uložit a otevřít je ze seznamu **naposledy otevřených relací** na stránce spuštění diagnostické nástroje.

![Snímek obrazovky se seznamem Diagnostické nástroje naposledy otevřené relace](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

Další informace naleznete v tématech:

- [Analýza využití procesoru](../profiling/cpu-usage.md)
- [Analýza využití paměti pro kód .NET](../profiling/dotnet-alloc-tool.md)
- [Analýza využití paměti](../profiling/memory-usage-without-debugging2.md)
- [Analýza výkonu asynchronního kódu .NET](../profiling/analyze-async.md)
- [Analýza výkonu databáze](../profiling/analyze-database.md)
- [Analýza využití GPU](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>Shromažďování dat profilace z příkazového řádku

Chcete-li změřit údaje o výkonu z příkazového řádku, můžete použít VSDiagnostics.exe, který je součástí sady Visual Studio nebo nástrojů Remote Tools. To je užitečné pro zachytávání trasování výkonu v systémech, kde není nainstalovaná sada Visual Studio, nebo pro skriptování kolekce trasování výkonu. Podrobné pokyny najdete v tématu [měření výkonu aplikace z příkazového řádku](../profiling/profile-apps-from-command-line.md).