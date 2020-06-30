---
title: Spuštění Nástroje pro profilaci s ladicím programem nebo bez něj | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fb07e9bc6c308e27e3ad054c5aeb0b12c092054
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534001"
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio teď nabízí možnost zvolit si nástroje pro výkon, některé z nich (například **využití procesoru** a **využití paměti**) je možné spustit s ladicím programem nebo bez něj. Nástroje pro sledování výkonu bez ladicího programu mají běžet na konfiguracích vydaných verzí, zatímco nástroje integrované v ladicím programu jsou určené ke spuštění v konfiguracích ladění.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Mám spustit nástroj s ladicím programem nebo bez něj?  
 Nástroje pro integrované ladění v ladicím programu umožňují provádět spoustu věcí, které neprogramují ladicí nástroje, například nastavit zarážky a kontrolovat hodnoty proměnných. Nástroje bez ladicího programu poskytují prostředí, které je bližší, co uvidí uživatelé vydané aplikace.  
  
 Tady jsou některé otázky, které vám pomohou rozhodnout, jaký druh nástroje je pro vaše účely nejvhodnější:  
  
1. Byl problém nalezen při vývoji aplikace nebo byl nalezen v vydané verzi?  
  
     Pokud se během vývoje zjistil problém, který se týká, pravděpodobně nemusíte spouštět nástroje pro sledování výkonu v sestavení pro vydání. Pokud byl nalezen ve vydané verzi, měli byste problém s konfigurací vydané verze reprodukován a pak se rozhodnout, zda bude ladicí program pomáhat s dalším šetřením.  
  
2. Je problém způsobený zpracováním náročným na procesor?  
  
     Mnohé problémy jsou způsobeny externími problémy s výkonem, jako jsou vstupně-výstupní operace se soubory nebo rychlost odezvy sítě, takže by neměl být mnohem rozdíl bez ohledu na to, zda spouštíte nástroje výkonu s ladicím programem nebo bez něj. Pokud se problém týká volání s náročnou na procesor, může být rozdíl mezi konfigurací vydaných verzí a ladění značný a pravděpodobně byste měli ověřit, zda problém existuje v buildu pro vydání před použitím nástrojů integrovaných v ladicím programu.  
  
3. Potřebujete změřit výkon přesně, nebo je přibližné množství přijatelné?  
  
     V sestaveních pro ladění chybí určitá optimalizace, kterou sestavení vydává, například volání funkcí a konstanty, vyřazení nepoužitých cest kódu a ukládání proměnných způsobem, který nelze použít v ladicím programu. Ladicí program změní dobu výkonu, protože provádí určité operace, které jsou nezbytné pro ladění (například zachycení událostí výjimky a načtení modulu). Hodnoty výkonu v nástrojích integrovaných s ladicím programem jsou proto přesné pouze v desítkách milisekund. V případě konfigurací vydaných verzí pomocí nástrojů bez ladicího programu jsou počty výkonu mnohem přesnější.  
  
## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Shromažďování dat profilace během ladění  
 Následující část se zabývá laděním místně. V dalších částech se dozvíte o ladění v zařízení nebo vzdáleném ladění.  
  
1. Otevřete projekt, který chcete ladit, klikněte na tlačítko **ladění/spustit ladění** (nebo **Spusťte** na panelu nástrojů nebo **F5**).  
  
2. Okno **Diagnostické nástroje** se zobrazí automaticky (pokud jste ho nevypnuli). Pokud ho chcete znovu zobrazit, klikněte na **Ladit / Okna / Zobrazit diagnostické nástroje**.  
  
3. Spusťte scénáře, pro které chcete shromažďovat data.  
  
    Když spouštíte relaci, můžete zobrazit informace o událostech, paměti procesu a využití procesoru.  
  
    Následující obrázek znázorňuje okno **diagnostické nástroje** v aplikaci Visual Studio 2015 Update 1:  
  
    ![DiagnosticTools&#45;-datum1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-v-datum1")  
  
4. Pomocí nastavení **Nástroje pro výběr** na panelu nástrojů můžete zvolit, zda se má zobrazit **využití paměti** nebo využití **CPU** (nebo obojí). Pokud používáte Visual Studio Enterprise, můžete povolit nebo zakázat IntelliTrace v **nabídce Nástroje/možnosti/IntelliTrace**.  
  
5. Diagnostická relace skončí po zastavení ladění.  
  
   V aplikaci Visual Studio 2015 Update 1 okno **diagnostické nástroje** usnadňuje soustředění na události, které vás zajímají.   Názvy událostí se teď zobrazují s předponami kategorií (**gesto**, **výstupem programu**, **zarážkami**, **soubory** atd.), takže můžete rychle vyhledat seznam pro danou kategorii nebo přeskočit kategorie, o kterých nezáleží.  
  
   Okno nyní obsahuje vyhledávací pole, aby bylo možné najít konkrétní řetězec kdekoli v seznamu událostí. Například následující obrázek znázorňuje výsledky hledání řetězce "Install", který se shoduje se čtyřmi událostmi:  
  
   ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
   Události můžete filtrovat také v okně a mimo zobrazení. V rozevíracím seznamu **filtru** můžete zaškrtnout nebo zrušit kontrolu určitých kategorií událostí:. Názvy kategorií jsou stejné jako názvy předpon.  
  
   ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
   Další informace najdete v tématu [hledání a filtrování událostí diagnostické nástroje okna na kartě události](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).  
  
## <a name="collect-profiling-data-without-debugging"></a>Shromažďování dat profilace bez ladění  
 Některé nástroje pro profilaci vyžadují ke spuštění oprávnění správce. Můžete spustit aplikaci Visual Studio jako správce nebo můžete zvolit spuštění nástrojů jako správce při spuštění diagnostické relace.  
  
1. Otevřete projekt v sadě Visual Studio.  
  
2. V nabídce **ladění** vyberte možnost **Profiler výkonu...** (Klávesová zkratka: Alt + F2).  
  
3. Na stránce spuštění diagnostiky vyberte jeden nebo více nástrojů, které chcete spustit v relaci. Zobrazí se pouze nástroje, které jsou použitelné pro typ projektu, operační systém a programovací jazyk. Když zvolíte diagnostický nástroj, budou zakázány výběry pro nástroje, které nelze spustit ve stejné diagnostické relaci. Tady je postup, jak můžou vaše volby Hledat univerzální aplikaci pro Windows v C#:  
  
    ![Výběr diagnostických nástrojů](../profiling/media/diag-selecttool.png "DIAG_SelectTool")  
  
4. Chcete-li spustit relaci diagnostiky, klikněte na tlačítko **Start**.  
  
5. Spusťte scénáře, pro které chcete shromažďovat data.  
  
    Když spouštíte relaci, některé nástroje zobrazují grafy dat v reálném čase na stránce spuštění diagnostických nástrojů.  
  
    ![Shromažďování dat o úvo výkonu a diagnostiky](../profiling/media/pdhub-collectdata.png "PDHUB_CollectData")  
  
6. Chcete-li ukončit relaci diagnostiky, klikněte na tlačítko **Zastavit shromažďování**.  
  
   Když zastavíte shromažďování dat v relaci diagnostiky, analyzují se data a sestava se zobrazí na stránce diagnostiky.  
  
   Uložené soubory relace diagnostiky můžete otevřít také ze seznamu naposledy otevřených na stránce spuštění diagnostických nástrojů.  
  
   ![Otevřít uložený soubor diagnostické relace](../profiling/media/pdhub-openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Sestava profilace  
 ![Sestava diagnostických nástrojů](../profiling/media/diag-report.png "DIAG_Report")  
  
|Image|Popis|  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Nástroj zobrazí jeden nebo více hlavních grafů. Pokud máte vytvořenou relaci diagnostiky pomocí více nástrojů, zobrazí se všechny hlavní grafy.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Jednotlivé grafy můžete sbalit a rozbalit.|  
|![Krok 5](../profiling/media/procguid-6.png "ProcGuid_6")|Pokud vaše data obsahují informace z více nástrojů, jsou podrobnosti o nástroji shromažďovány na kartách.|  
|![Krok 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|Nástroj může mít jedno nebo více zobrazení podrobností. Zobrazení je filtrováno podle vybrané oblasti časové osy.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>Nastavení cíle analýzy na jiné zařízení  
 Kromě spuštění aplikace z projektu sady Visual Studio můžete také spustit diagnostické relace pro alternativní cíle. Například můžete chtít diagnostikovat problémy s výkonem ve verzi vaší aplikace, která byla nainstalována z Windows App Storu.  
  
 ![Zvolit cíl analýzy diagnostických nástrojů](../profiling/media/pdhub-chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Můžete spustit aplikace, které jsou již nainstalovány v zařízení, nebo můžete připojit diagnostické nástroje k některým aplikacím, které jsou již spuštěny. Když zvolíte **běžící aplikace** nebo **nainstalovaná aplikace**, vyberete aplikaci ze seznamu, který zjistí aplikace v zadaném cíli nasazení.  
  
 ![Zvolit spuštěnou nebo nainstalovanou aplikaci pro diagnostiku](../profiling/media/pdhub-selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Když zvolíte **Internet Explorer**, zadáte adresu URL a můžete změnit cíl nasazení telefonu.  
  
 ![Zadejte adresu URL, která se má zobrazit v Internet Exploreru.](../profiling/media/pdhub-choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Vzdálené ladění  
 Spuštění diagnostické relace na vzdáleném počítači nebo tabletu vyžaduje, aby byly na vzdáleném cíli nainstalovány a spuštěny vzdálené nástroje sady Visual Studio. Pro desktopové aplikace se podívejte na téma [vzdálené ladění](../debugger/remote-debugging.md).  Informace o univerzálních aplikacích pro Windows najdete v tématu [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Blogové příspěvky a články MSDN z vývojového týmu diagnostiky  
 [MSDN Magazine: Analýza výkonu při ladění v aplikaci Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)  
  
 [MSDN Magazine: použití IntelliTrace k rychlejší diagnostice problémů](https://msdn.microsoft.com/magazine/dn973014.aspx)  
  
 [Blogový příspěvek: Diagnostika nevracení obslužných rutin událostí pomocí nástroje využití paměti v aplikaci Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)  
  
 [Video: historické ladění s IntelliTrace v Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Video: ladění problémů s výkonem pomocí sady Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [Tipy pro výkon: informace o výkonu na první pohled při ladění v aplikaci Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)  
  
 [Okno ladicího programu Diagnostické nástroje v aplikaci Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [IntelliTrace v Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
