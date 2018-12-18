---
title: Spuštění nástroje pro profilaci s nebo bez ladicího programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb36ad055f126ce034fbb7323877b65aa8e3105c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722239"
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>Spuštění nástroje pro profilaci s nebo bez ladicího programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio nyní nabízí možnost výkonu nástroje, z nichž některé (například **využití procesoru** a **využití paměti**) můžete spustit s nebo bez ladicího programu. Výkon bez ladicího programu nástroje jsou určeny ke spuštění na verzi konfigurace, zatímco integrované v ladicím programu nástroje jsou určeny ke spuštění na konfiguraci ladění.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Má spustit nástroj, s nebo bez ladicího programu?  
 Nástroje integrované v ladicím programu Sledování výkonu umožňují dělat spoustu věcí, které nelze nástroje bez ladicího programu, například nastavit zarážky a zkontrolovat hodnoty proměnných. Bez ladicího programu nástroje vám poskytnou prostředí, který je blíž k uživatelům vydané aplikace zobrazí.  
  
 Tady je pár otázek, které vám můžou pomoct rozhodnout, jaký druh nástroj je nejvhodnější pro vaše účely:  
  
1.  Byl nalezen problém najít, když se vyvinula aplikaci, nebo se jednalo ve vydané verzi?  
  
     Pokud se problém, který se zabývají byl nalezen během vývoje, pravděpodobně není nutné ke spuštění nástroje pro sledování výkonu v sestavení pro vydání. Pokud byl nalezen v prodejní verzi, by měl reprodukujte problém s konfiguraci vydané verze a následně se rozhodnete, zda by ladicí program nápovědy pro další zkoumání.  
  
2.  Zpracování potíže způsobené náročnou na procesor  
  
     Mnoho problémů jsou z důvodu problémů s výkonem externí například soubor vstupně-výstupních operací nebo rychlost odezvy sítě, takže neprovádějte velký rozdíl, ať už spouštíte nástroje Sledování výkonu s nebo bez ladicího programu. Pokud je váš problém způsobený volání náročnou na procesor, rozdíl mezi konfiguracemi vydání a ladění může být značné a měli byste pravděpodobně zkontrolujte-li tento problém existuje před použitím nástroje integrované v ladicím programu v sestavení pro vydání  
  
3.  Je třeba přesně měřit výkon, nebo je přijatelné přibližný počet?  
  
     Ladění sestavení chybí některé optimalizace, které poskytují buildy vydaných verzí, například vkládání volání funkce a konstanty, čištění nevyužitých kódu cesty a ukládání proměnné takovým způsobem, který nelze použít pro ladicí program. Na samotný ladicí program změní časy výkon, protože provede některé operace, které jsou nezbytné pro ladění (například zachycení výjimky a události načtení modulu). Čísla výkon v nástrojích pro integrované v ladicím programu jsou tak přesné pouze v rámci desítky milisekund. Jsou mnohem přesnější čísla výkonu pro konfiguraci vydání nástroje bez ladicího programu.  
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Shromažďování dat profilace během ladění  
 Následující část se zabývá místním ladění. Můžete získat informace o ladění na zařízení nebo vzdálené ladění, v dalších částech.  
  
1. Otevřete projekt, který chcete ladit, pak klikněte na **ladění / spuštění ladění** (nebo **Start** na panelu nástrojů nebo **F5**).  
  
2. Okno **Diagnostické nástroje** se zobrazí automaticky (pokud jste ho nevypnuli). Pokud ho chcete znovu zobrazit, klikněte na **Ladit / Okna / Zobrazit diagnostické nástroje**.  
  
3. Scénáře, pro které chcete shromažďovat data pro spuštění.  
  
    Při spuštění relace, zobrazí se informace o události, proces, využití paměti a procesoru.  
  
    Následující grafické ukazuje **diagnostické nástroje** okna v aplikaci Visual Studio 2015 Update 1:  
  
    ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
4. Můžete zvolit, zda chcete zobrazit **využití paměti** nebo **využití procesoru** (nebo obojí) se **vyberte nástroje** nastavení na panelu nástrojů. Pokud používáte Visual Studio Enterprise, můžete povolit nebo zakázat nástroje IntelliTrace v **nástroje / Možnosti / IntelliTrace**.  
  
5. Diagnostické relace končí, když zastavíte ladění.  
  
   Visual Studio 2015 Update 1 **diagnostické nástroje** okno usnadňuje pro soustředit na události, které vás zajímají.   Názvy událostí se teď zobrazují s předponami kategorie (**gesta**, **výstup programu**, **zarážku**, **souboru** atd.) tak, aby se rychle Vyhledejte v seznamu pro danou kategorii nebo přeskočit kategorie, které vám nezáleží.  
  
   V okně nyní obsahuje pole pro hledání, abyste našli konkrétní řetězec kdekoli v seznamu událostí. Například následující obrázek znázorňuje výsledky hledání řetězce "instalaci", který odpovídá čtyři události:  
  
   ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
   Můžete také filtrovat události a zobrazení v okně. V **filtr** rozevírací seznam, dokáže kontrolovat nebo zrušte zaškrtnutí políčka konkrétní kategorie události:. Názvy kategorií jsou stejné jako názvy předponu.  
  
   ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
   Další informace najdete v tématu [vyhledávání a filtrování na kartě události okna diagnostické nástroje](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx).  
  
## <a name="collect-profiling-data-without-debugging"></a>Shromažďování dat profilace bez ladění  
 Některé nástroje pro profilaci vyžadují oprávnění správce pro spuštění. Visual Studio můžete spustit jako správce, nebo můžete spustit nástroje jako správce, když spustíte diagnostické relace.  
  
1. Otevřete projekt v sadě Visual Studio.  
  
2. Na **ladění** nabídce zvolte **Profiler výkonu...** (Klávesová zkratka: Alt + F2).  
  
3. Na stránce diagnostiky spuštění zvolte jeden nebo víc nástrojů ke spuštění v relaci. Zobrazí se pouze nástroje, které platí pro typ projektu, operační systém a programovací jazyk. Pokud si zvolíte diagnostický nástroj, jsou zakázané výběry pro nástroje, které nemůže běžet ve stejné relaci diagnostiky. Zde je, jak může vypadat vaše volby jazyka C# Windows univerzální aplikace:  
  
    ![Vyberte diagnostické nástroje](../profiling/media/diag-selecttool.png "DIAG_SelectTool")  
  
4. Chcete-li spustit diagnostické relace, klikněte na tlačítko **Start**.  
  
5. Spuštění scénářů, pro které chcete shromažďovat data.  
  
    Při spuštění relace, některé nástroje grafy dat v reálném čase zobrazit na stránce spustit diagnostické nástroje.  
  
    ![Shromažďovat data o výkonu a Diagnostika Úvo](../profiling/media/pdhub-collectdata.png "PDHUB_CollectData")  
  
6. Chcete-li ukončit relaci diagnostiky, klikněte na tlačítko **zastavit shromažďování**.  
  
   Když zastavíte shromažďování dat v relaci diagnostiky, data se analyzují a sestavy se zobrazí na stránce diagnostiky.  
  
   Můžete také otevřít relaci .diagnostic uložené soubory ze seznamu posledních otevřených na diagnostických nástrojů úvodní stránka.  
  
   ![Otevřete soubor uloženou diagnostiku relace](../profiling/media/pdhub-openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Sestava profilace  
 ![Diagnostické nástroje sestavy](../profiling/media/diag-report.png "DIAG_Report")  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid-1.png "ProcGuid_1")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|  
|![2. krok](../profiling/media/procguid-2.png "ProcGuid_2")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|  
|![3. krok](../profiling/media/procguid-3.png "ProcGuid_3")|Nástroj zobrazí jeden nebo více hlavní grafy. Pokud diagnostické relace je vytvořena pomocí různých nástrojů, jsou zobrazeny všechny hlavní grafy.|  
|![4. krok](../profiling/media/procguid-4.png "ProcGuid_4")|Můžete rozbalovat a sbalovat jednotlivé grafy.|  
|![Krok 5](../profiling/media/procguid-6.png "ProcGuid_6")|Pokud data obsahují informace z různých nástrojů, podrobnosti o nástroj je shromažďovat v rámci karty.|  
|![Krok 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|Nástroj může mít jeden nebo více zobrazení podrobností. Zobrazení se filtruje podle vybrané oblasti na časové ose.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>Nastavení cílové analýzy na jiném zařízení  
 Kromě spuštění vaší aplikace z projektu sady Visual Studio, můžete také spustit diagnostické relace na alternativní cíle. Můžete například chtít diagnostikovat problémy s výkonem na verzi aplikace, která byla nainstalovaná z App Store Windows.  
  
 ![Zvolte cíl analýzy diagnostické nástroje](../profiling/media/pdhub-chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Můžete spustit aplikace, které jsou na zařízení nainstalovaná, nebo diagnostické nástroje můžete připojit k některé aplikace, které jsou již spuštěny. Pokud zvolíte **spuštění aplikace** nebo **nainstalovaná aplikace**, vyberte aplikaci ze seznamu, který zjistí aplikace na cíli zadané nasazení.  
  
 ![Zvolte spuštěné nebo nainstalovanou aplikaci pro účely diagnostiky](../profiling/media/pdhub-selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Pokud zvolíte **aplikace Internet Explorer**, zadejte adresu URL a můžete změnit cíl nasazení telefon.  
  
 ![Zadejte adresu url pro zobrazení v aplikaci Internet Explorer](../profiling/media/pdhub-choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Vzdálené ladění  
 Spouštění diagnostické relace na vzdálené počítače nebo tabletu vyžaduje, aby Visual Studio Remote Tools na vzdálené cílové nainstalovaná a spuštěná. Aplikace klasické pracovní plochy, naleznete v tématu [vzdálené ladění](../debugger/remote-debugging.md).  Windows Universal apps, najdete v části [aplikace Windows Store spustit ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Blogy a články MSDN od vývojového týmu diagnostiky  
 [Zpravodaj MSDN Magazine: Analýza výkonu při ladění v sadě Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)  
  
 [Zpravodaj MSDN Magazine: Dokážete rychleji diagnostikovat problémy pomocí IntelliTrace](https://msdn.microsoft.com/magazine/dn973014.aspx)  
  
 [Blogový příspěvek: Diagnostika nevrácené obslužné rutiny události pomocí nástroje využití paměti v sadě Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/04/29/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015.aspx)  
  
 [Video: Historické ladění pomocí nástroje IntelliTrace v sadě Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Video: Ladění problémů s výkonem pomocí sady Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [Tipy pro výkon: Informace o výkonu v přehledem při ladění se sadou Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)  
  
 [Ladicí program okně diagnostické nástroje v sadě Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [Nástroj IntelliTrace v sadě Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)



