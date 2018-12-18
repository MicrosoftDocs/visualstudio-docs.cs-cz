---
title: Spustit profilování nástroje s nebo bez ladicího programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8d088978e166f24f624b8ae05cdeb04137d8135
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948709"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj

Visual Studio nabízí celou řadu měření výkonu a nástroje pro profilaci. Některé nástroje, jako je **využití procesoru** a **využití paměti**, můžete spustit s nebo bez ladicího programu a na verze nebo konfigurace sestavení pro ladění. **Profiler výkonu** nástroje, jako je **časová osa aplikace** můžete spustit na ladění nebo vydání verze sestavení. Integrované v ladicím programu nástroje, jako je **diagnostické nástroje** okno a **události** kartu spustit jenom během relace ladění.  

>[!NOTE]
>Můžete použít nástroje pro sledování výkonu bez ladicího programu s Windows 7 a novější. Je potřeba spustit profilování nástroje integrované v ladicím programu systému Windows 8 nebo novější.

Jiné – ladicí program **Profiler výkonu** a integrovaný ladicí program **diagnostické nástroje** poskytují různé informace a prostředí. Nástroje integrované v ladicím programu ukazují, zarážky a hodnoty proměnných. Bez ladicího programu nástroje vám poskytnou výsledky blíž k činnosti koncového uživatele. 

Abychom pomohli, rozhodněte, které nástroje a výsledky použití, zvažte následující body:

- Problémy s výkonem externí, jako je soubor vstupně-výstupních operací nebo problémů se sítí rychlost odezvy, nebude hledat v ladicím programu nebo ladicího programu nástroje mnohem liší. 
- Pro potíže způsobené službou volání náročnou na procesor může být značné výkonu rozdíly mezi sestaveními pro vydání a ladění. Zkontrolujte, jestli existuje problém ve verzi sestavení. 
- Pokud k problému dochází pouze během sestavení pro ladění, pravděpodobně není nutné ke spuštění nástroje bez ladicího programu. Problémy sestavení pro vydání, rozhodněte, zda ladicí program tools pomůže o pomoc. 
- Sestavení pro vydání poskytují optimalizaci, jako je vkládání volání funkce a konstanty, vyřazování cesty nevyužité kódu a uložení proměnné takovým způsobem, který nelze použít pro ladicí program. Čísla výkon v nástrojích pro integrované v ladicím programu jsou méně přesný, protože ladicí sestavení chybí tyto optimalizace. 
- Stejně jako operace nezbytné ladicí program jako zachycení výjimky a události načtení modulu se změní na samotný ladicí program doby výkonu. 
- Sestavení pro vydání údaje o výkonu **Profiler výkonu** nástroje jsou přesné a přesné. Výsledky nástroje integrované v ladicím programu jsou zvláště užitečná pro porovnání s další měření spojené s laděním.

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Shromažďování dat profilace během ladění  

Při spuštění ladění v sadě Visual Studio tak, že vyberete **ladění** > **spustit ladění** nebo stiskněte **F5**, **Diagnostickénástroje** ve výchozím nastavení se zobrazí okno. Chcete-li jej spustit ručně, vyberte **ladění** > **Windows** > **zobrazit diagnostické nástroje**. **Diagnostické nástroje** okno s informacemi o událostech, proces, využití paměti a procesoru.  

![Diagnostické nástroje](../profiling/media/diagnostictools-update1.png "diagnostické nástroje")  

- Použití **nastavení** ikonu na panelu nástrojů vyberte, jestli se má zobrazit **využití paměti**, **Analýza uživatelského prostředí**, a **využití procesoru**. 
  
- Vyberte **nastavení** v **nastavení** rozevírací nabídku, která otevře **diagnostických stránky vlastností nástroje** víc možností. 
  
- Pokud používáte Visual Studio Enterprise, můžete povolit nebo zakázat nástroje IntelliTrace v sadě Visual Studio **nástroje** > **možnosti** > **IntelliTrace**.  
  
Diagnostické relace končí, když zastavíte ladění.  
  
Můžete také zobrazit **diagnostické nástroje** pro vzdálené ladění cíle. Pro vzdálené ladění a profilování musí být vzdálený ladicí program sady Visual Studio nainstalované a spuštěné na vzdálené cílové. 
- Pro vzdálené ladění a profilování aplikace klasické pracovní plochy projektů, naleznete v tématu [vzdálené ladění](../debugger/remote-debugging.md). 
- Vzdálené ladění a profilování aplikací pro UWP, naleznete v tématu [aplikací pro UWP ladění na vzdálených počítačích](../debugger/run-windows-store-apps-on-a-remote-machine.md). 

### <a name="the-events-tab"></a>Na kartě události

Během relace ladění **události** karty **diagnostické nástroje** okně zobrazí diagnostické události, ke kterým dochází. Předpony kategorií: **zarážku**, **souboru**, a jiné, vám umožní rychle vyhledat v seznamu kategorie, nebo přeskočit kategorie nezáleží.  
  
Použití **filtr** rozevírací seznam můžete filtrovat události a zobrazení výběrem nebo zrušením výběru konkrétní kategorie události. 

![Filtr diagnostických událostí](../profiling/media/diagnosticeventfilter.png "filtr diagnostických událostí")  

Pomocí vyhledávacího pole najít konkrétní řetězec v seznamu událostí. Tady jsou výsledky hledání pro řetězec "name", který odpovídá čtyři události:  

![Vyhledávání diagnostických událostí](../profiling/media/diagnosticseventsearch.png "prohledávání diagnostických událostí")  

Další informace najdete v tématu [vyhledávání a filtrování na kartě události okna diagnostické nástroje](https://blogs.msdn.microsoft.com/devops/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).  

## <a name="collect-profiling-data-without-debugging"></a>Shromažďování dat profilace bez ladění  

Pokud chcete shromažďovat data o výkonu bez ladění, můžete spustit **Profiler výkonu** nástroje. Některé z nástrojů pro profilaci vyžadují oprávnění správce pro spuštění. Visual Studio můžete spustit jako správce nebo nástroje můžete spustit jako správce, když spustíte diagnostické relace.  
   
1. Projekt otevřít v sadě Visual Studio, vyberte **ladění** > **Profiler výkonu**, nebo stiskněte klávesu **Alt**+**F2**.  
   
1. Na stránce diagnostiky spouštění vyberte jeden nebo víc nástrojů ke spuštění. Zobrazí se pouze nástroje, které platí pro typ projektu, operační systém a programovací jazyk. Vyberte **zobrazit všechny nástroje** také zobrazit nástroje, které jsou pro tuto relaci diagnostiky zakázáno. Zde je, jak může vypadat vaše volby pro aplikace pro UPW v jazyce C#:  
   
   ![Vyberte diagnostické nástroje](../profiling/media/diag_selecttool.png "DIAG_SelectTool")  
   
1. Chcete-li spustit diagnostické relace, vyberte **Start**.  
   
   Je spuštěna relace některé nástroje grafy dat v reálném čase zobrazit na stránce diagnostické nástroje.  
   
    ![Shromažďování dat o výkonu a diagnostiky](../profiling/media/pdhub_collectdata.png "centra shromažďování dat")  
   
1. Chcete-li ukončit relaci diagnostiky, vyberte **zastavit shromažďování**.  
   
   Analyzovaná data zobrazí na **sestavy** stránky.  
  
Můžete uložit sestavy a otevřete je z **naposledy otevřené relace** seznamu na stránce spustit diagnostické nástroje.  

![Otevřete soubor uloženou diagnostiku relace](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
### <a name="the-profiling-report"></a>Sestava profilace  
 ![Diagnostické nástroje sestavy](../profiling/media/diag_report.png "DIAG_Report")  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid_1.png "ProcGuid_1")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|  
|![2. krok](../profiling/media/procguid_2.png "ProcGuid_2")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|  
|![3. krok](../profiling/media/procguid_3.png "ProcGuid_3")|Každý nástroj pro diagnostiku zobrazuje jeden nebo více hlavní grafy. Pokud diagnostické relace má více než jeden nástroj, jsou zobrazeny všechny jejich hlavní grafy.|  
|![4. krok](../profiling/media/procguid_4.png "ProcGuid_4")|Můžete rozbalovat a sbalovat jednotlivých nástrojích jednotlivé grafy.|  
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Pokud data obsahují více než jeden nástroj, jsou podrobnosti k nástroji shromažďovat v rámci karty.|  
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|Dolní polovinu sestavy zobrazuje podrobná zobrazení pro jednotlivé nástroje. Zobrazení můžete filtrovat výběrem oblastí na časové ose.|  
  
## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Spouštět aplikace nainstalována nebo spuštěna relace diagnostiky 

 Kromě spuštění vaší aplikace z projektu sady Visual Studio, můžete také spustit diagnostické relace na alternativní cíle. Můžete například chtít diagnostikovat problémy s výkonem v aplikaci, která byla nainstalovaná z App Store Windows.  
  
 ![Zvolte cíl analýzy diagnostické nástroje](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Můžete spustit aplikace, které jsou již nainstalovány nebo připojit diagnostické nástroje pro aplikace a procesy, které jsou již spuštěny. Když vyberete **spuštěná aplikace** nebo **nainstalovaná aplikace**, vyberte aplikaci ze seznamu, který najde v zadaném nasazení cílové aplikace. Tento cíl může být místní nebo vzdáleném počítači. 
  
 ![Zvolte spuštěné nebo nainstalovanou aplikaci pro účely diagnostiky](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")  
  
## <a name="see-also"></a>Viz také:

Následují blogy a články MSDN od vývojového týmu diagnostiky:  
 [Zpravodaj MSDN Magazine: Analýza výkonu při ladění v sadě Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)
  
 [Zpravodaj MSDN Magazine: Dokážete rychleji diagnostikovat problémy pomocí IntelliTrace](https://msdn.microsoft.com/magazine/dn973014.aspx)
  
 [Blogový příspěvek: Diagnostika nevrácené obslužné rutiny události pomocí nástroje využití paměti v sadě Visual Studio 2015](https://blogs.msdn.microsoft.com/devops/2015/04/29/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)
  
 [Video: Historické ladění pomocí nástroje IntelliTrace v sadě Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)
  
 [Video: Ladění problémů s výkonem pomocí sady Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)
  
 [Tipy pro výkon: Informace o výkonu v přehledem při ladění se sadou Visual Studio](https://blogs.msdn.microsoft.com/devops/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)
  
 [Ladicí program okně diagnostické nástroje v sadě Visual Studio 2015](https://blogs.msdn.microsoft.com/devops/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015/)
  
 [Nástroj IntelliTrace v sadě Visual Studio Enterprise 2015](https://blogs.msdn.microsoft.com/devops/2015/01/16/intellitrace-in-visual-studio-ultimate-2015/)
