---
title: Využití CPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f699666216d38c34583ebeb15e2bb6ba4953b671
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300754"
---
# <a name="cpu-usage"></a>Využití procesoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud potřebujete prozkoumat problémy s výkonem ve vaší aplikaci, je dobrým místem, kde začít, je porozumění tomu, jak využívá procesor. Nástroj **využití CPU** vám ukáže, kde CPU stráví čas prováděním kódu Visual C++, Visual C#webový Basic a JavaScript Code.  
  
 Počínaje verzí Visual Studio 2015 Update 1 se můžete podívat na rozdělení funkcí procesoru, aniž byste museli opustit ladicí program. Můžete zapnout nebo vypnout profilaci procesoru při ladění a zobrazit výsledky při zastavení spuštění, například na zarážce. Další informace najdete v tématu [profilace procesoru v ladicím programu v aplikaci Visual Studio 2015](https://devblogs.microsoft.com/devops/profile-your-cpu-in-the-debugger-in-visual-studio-2015/).  
  
 Návod, který analyzuje výkon aplikace pro Windows Store, najdete v tématu [Analýza využití procesoru v aplikacích pro Store](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 Centrum pro výkon a diagnostiku nabízí spoustu dalších možností, jak spustit a spravovat diagnostickou relaci. Například můžete spustit nástroj **využití CPU** na místních nebo vzdálených počítačích nebo na simulátoru nebo emulátoru. Můžete analyzovat výkon otevřeného projektu v aplikaci Visual Studio, připojit se ke spuštěné aplikaci nebo spustit aplikaci, která je nainstalována z Windows Storu. Další informace najdete v tématu [spuštění nástrojů pro profilaci bez ladění](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01) .  
  
## <a name="BKMK_Collect_CPU_usage_data"></a>Shromažďování dat o využití procesoru  
  
1. V sadě Visual Studio nastavte konfiguraci řešení na **vydaná** a vyberte cíl nasazení.  
  
    ![Vybrat vydanou verzi a místní počítač](../profiling/media/cpuuse-selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
   - Spuštění aplikace v režimu **vydání** nabízí lepší pohled na skutečný výkon vaší aplikace.  
  
   - Spuštění aplikace na místním počítači nejlépe replikuje spuštění nainstalované aplikace.  
  
   - Pokud shromažďujete data ze vzdáleného zařízení, spusťte aplikaci přímo na zařízení a ne pomocí Připojení ke vzdálené ploše.  
  
   - V případě aplikací Windows Phone aplikace shromažďují data přímo ze **zařízení** a poskytují nejpřesnější data.  
  
2. V nabídce **ladění** vyberte možnost **Profiler výkonnosti...** .  
  
3. Zvolte **využití procesoru** a pak zvolte **Spustit**.  
  
    ![Zvolit využití CPU](../profiling/media/cpuuse-lib-choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4. Po spuštění aplikace klikněte na **získat maximální počet**. Po zobrazení výstupu počkat o sekundu a pak zvolte **získat Max Number Async**. Čekání mezi kliknutím na tlačítko usnadňuje izolaci rutin kliknutí na tlačítko v diagnostické sestavě.  
  
5. Po zobrazení druhé výstupní čáry vyberte možnost **Zastavit shromažďování** v centru výkonu a diagnostiky.  
  
   ![Zastavit shromažďování dat CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Nástroj využití CPU analyzuje data a zobrazí sestavu.  
  
   ![Sestava CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analýza sestavy využití procesoru  
  
### <a name="BKMK_The_CPU_Usage_call_tree"></a> Využití procesoru strom volání  
 Chcete-li začít pochopit informace o stromu volání, vyberte segment `GetMaxNumberButton_Click` a podívejte se na podrobnosti o stromu volání.  
  
#### <a name="BKMK_Call_tree_structure"></a> Struktura stromu volání  
 ![GetMaxNumberButton&#95;kliknout na strom volání](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Nejvyšší uzel ve stromech volání Využití procesoru je fiktivní.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Ve většině aplikací, ve kterých zakážete možnost **Zobrazit externí kód**, je v druhé úrovni uzel **[Externí kód]** , který obsahuje systémový kód a kód architektury, který spouští a zastavuje aplikaci, vykresluje uživatelské rozhraní, řídí plánování podprocesů a na nejnižší úrovni zajišťuje pro aplikaci další služby.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Podřízené uzly metody obsahují jenom data pro volání nadřízené metody. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]** .|  
  
#### <a name="BKMK_External_Code"></a>Externí kód  
 Externí kód jsou funkce v komponentách systému a rozhraní, které jsou spouštěny kódem, který píšete. Externí kód zahrnuje funkce, které spouštějí a zastavují aplikaci, vykreslují uživatelské rozhraní, řídí dělení na podprocesy a na nejnižší úrovni zajišťuje pro aplikaci další služby. Ve většině případů nebudete mít zájem o externí kód, takže strom volání využití CPU shromáždí externí funkce uživatelské metody do jednoho uzlu **[externí kód]** .  
  
 Chcete-li zobrazit cesty volání externího kódu, zvolte možnost **Zobrazit externí kód** ze seznamu **zobrazení filtru** a pak zvolte možnost **použít**.  
  
 ![Zvolte možnost zobrazení filtru a pak zobrazit externí kód.](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Myslete na to, že řetězy volání externího kódu je většinou hluboko vnořené, takže šířka sloupce Název funkce může na většině počítačových monitorů – s výjimkou těch největších – přesáhnout šířku zobrazení. Pokud k tomu dojde, názvy funkcí se zobrazí jako **[...]** :  
  
 ![Vnořený externí kód ve stromu volání](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Pomocí vyhledávacího pole vyhledejte uzel, který hledáte, a pak pomocí vodorovného posuvníku přepněte data do zobrazení:  
  
 ![Hledání vnořeného externího kódu](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="BKMK_Call_tree_data_columns"></a>Sloupce dat stromu volání  
  
|||  
|-|-|  
|**Celkový čas procesoru (%)**|![Total% data Equation – rovnice](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Procentuální podíl aktivity procesoru aplikace ve vybraném časovém rozsahu, který byl použit voláním funkce a funkcemi, které funkce volá. Všimněte si, že se liší od grafu časové osy **využití procesoru** , který porovnává celkovou aktivitu aplikace v časovém rozsahu s celkovou dostupnou kapacitou procesoru.|  
|**Samotný procesor (%)**|![% Rovnice sebe](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Procentuální podíl aktivity procesoru aplikace ve vybraném časovém rozsahu, který byl použit voláním funkce, s výjimkou aktivity funkcí volaných funkcí.|  
|**Celkový čas procesoru (MS)**|Počet milisekund strávených voláním funkce ve vybraném časovém rozsahu a funkcemi, které byly volány funkcí.|  
|**Samotný procesor (MS)**|Počet milisekund strávených voláním funkce ve vybraném časovém rozsahu a funkcemi, které byly volány funkcí.|  
|**Modul**|Název modulu obsahujícího funkci nebo počet modulů, které obsahují funkce v uzlu [externí kód].|  
  
### <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>Asynchronní funkce ve stromu volání využití CPU  
 Když kompilátor narazí na asynchronní metodu, vytvoří skrytou třídu pro řízení provádění metody. V koncepční úrovni je třída Stavový počítač, který obsahuje seznam funkcí generovaných kompilátorem, které volají asynchronní operace původní metody a zpětná volání, Scheduler a iterátory, které jsou pro ně požadovány. Pokud je původní metoda volána nadřazenou metodou, modul runtime odstraní metodu z kontextu spuštění nadřazeného objektu a spustí metody skryté třídy v kontextu systému a kódu rozhraní, který řídí provádění aplikace. Asynchronní metody jsou často, ale ne vždy spouštěny na jeden nebo více různých vláken. Tento kód je zobrazen ve stromu volání využití CPU jako podřízené objekty v uzlu **[External Code]** bezprostředně pod horním uzlem stromu.  
  
 Pokud to chcete vidět v našem příkladu, znovu vyberte segment `GetMaxNumberAsyncButton_Click` na časové ose.  
  
 ![GetMaxNumberAsyncButton&#95;kliknout na výběr sestavy](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 První dva uzly v **[External Code]** jsou metody generované kompilátorem třídy stavového stroje. Třetí je volání původní metody. Rozbalením vygenerovaných metod se dozvíte, co se chystá.  
  
 ![Rozbalený&#95;GetMaxNumberAsyncButton klikněte na strom volání.](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` je velmi málo; spravuje seznam hodnot úkolů, vypočítá maximum výsledků a zobrazí výstup.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` ukazuje aktivit potřebných k naplánování a spuštění 48 úkoly, které obalují volání `GetNumberAsync`.  
  
- `MainPage::<GetNumberAsync>b__b` zobrazuje aktivitu úloh, které volají `GetNumber`.
