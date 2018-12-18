---
title: Analýza spotřeby energie v aplikacích pro Store | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 102302a1c14f379745007135593cc039aa9f8836
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742016"
---
# <a name="analyze-energy-use-in-store-apps"></a>Analýza spotřeby energie v aplikacích pro Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **spotřeba energie** profiler pomáhá analyzovat spotřebu energie aplikací pro Windows Store na s nízkou spotřebou, na kterých běží všechny nebo část času, na vlastní baterie. Na zařízení napájeném z baterie může aplikace s příliš vysokou spotřebou energie způsobit tak velkou nespokojenost zákazníka, že ji může dokonce i odinstalovat. Optimalizace využití energie můžete zlepšit přijetí a používání aplikace zákazníky.  
  
##  <a name="BKMK_What_the_Energy_Consumption_tool_is__how_it_works__and_what_it_measures"></a> Co je profiler spotřeba energie, jak to funguje a co měří  
 Profiler Spotřeba energie shromažďuje údaje o činnosti displeje, procesoru a síťových připojení zařízení během relace profilování. Poté vygeneruje odhady množství energie použité pro tyto činnosti a celkové množství energie použité pro relaci profilování.  
  
> [!NOTE]
>  Energetický profiler provádí odhad výkonu a spotřeby energie pomocí softwarového modelu standardního hardwaru referenčního zařízení, jež reprezentuje tablety s nízkou spotřebou, na kterých by vaše aplikace mohla běžet. Pro dosažení co nejlepšího odhadu doporučujeme shromáždit profilová data u tabletů s nízkou spotřebou.  
>   
>  Ačkoliv model poskytuje dobré odhady pro řadu zařízení s nízkou spotřebou, skutečné hodnoty zařízení, která profilujete, budou pravděpodobně odlišné. Použijte tyto hodnoty pro nalezení aktivit displeje, procesoru a sítě, které jsou v porovnání s využitím jiných prostředků náročné, takže by mohly představovat vhodné kandidáty na optimalizaci.  
  
 Profiler spotřeba energie používá tyto definice *power* a *energie*:  
  
- *Napájení* opatření množství síly potřebné se používá k provedení práce, která se provádí v časovém intervalu. Elektrické věd, je standardní jednotkou výkonu *watt*, který je definován jako rychlost, jakou práce provádí, když jeden Ampér – měrná aktuální toků prostřednictvím rozdílem v elektrickém potenciálu o velikosti jednoho voltu. V **spotřeby energie** grafu, jsou jednotky zobrazeny v miliwattech **mW** jsou 1/1 000 wattu.  
  
   Všimněte si, že výkon má směr (množství práce se v čase může zvýšit nebo snížit) a rychlost (velikost zvýšení nebo snížení množství práce).  
  
- *Energie* opatření dosáhl celkové množství výkonu, smyslu kapacity nebo potenciálu, jako v případě kapacity baterií, nebo smyslu celkového množství výkonu vynaloženého za určitou dobu. Jednotkou energie je watthodina, tedy výkon jednoho wattu konstantně působící po jednu hodinu. V **souhrn energie**, jsou jednotky zobrazeny v miliwatthodinách **MWh**.  
  
  ![Kapacita energie výkon použít, celkového množství energie použité](../profiling/media/energyprof-capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Například plně nabitá baterie v tabletu uchovává určité množství energie. Při využívání této energie pro provádění úloh, jako je například komunikace po síti, výpočty hodnot nebo zobrazování grafického obsahu, se výkon spotřebovává různou rychlostí. Pro libovolné časové období se celkové množství spotřebovaného výkonu poměřuje také energií.  
  
##  <a name="BKMK_Identify_scenarios_with_user_marks"></a> Určit scénáře s uživatelskými značkami  
 Můžete přidat *uživatelské značky* do vlastních profilovacích dat. Chcete-li usnadníte identifikaci oblastí na časové ose.  
  
 ![Značky uživatele na časové ose](../profiling/media/profilers-usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 Značka se zobrazí jako oranžový trojúhelník umístěný na časové ose v čase spuštění metody. Zpráva a čas se zobrazí jako popisek, jakmile na značku umístíte ukazatel myší. Pokud jsou dvě nebo více uživatelských značek blízko u sebe, značky i popisky se sloučí. Značky od sebe rozlišíte přiblížením časové osy.  
  
 **Přidání značek do C#, Visual Basic, kód jazyka C++**  
  
 Chcete-li přidat uživatelskou značku do jazyka C#, Visual Basic, kód jazyka C++, nejprve vytvořit [Windows.Foundation.Diagnostics LoggingChannel](http://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) objektu. Pak vložte volání [LoggingChannel.LogMessage](http://msdn.microsoft.com/library/windows/apps/dn264210.aspx) metod v kódu, které chcete označit. Použití [LoggingLevel.Information](http://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) ve volání.  
  
 Jakmile se metoda spustí, uživatelská značka je spolu se zprávou přidána do profilových dat.  
  
> [!NOTE]
> - Obor názvů Windows.Foundation.Diagnostics.loggingchannel implementuje [Windows.Foundation.IClosable](http://msdn.microsoft.com/library/windows/apps/windows.foundation.iclosable.aspx) rozhraní (předpokládané podobě [rozhraní System.IDisposable](http://msdn.microsoft.com/library/System.IDisposable.aspx) v C# a VB). Aby se zabránilo nevrácení prostředků operačního systému, volejte [LoggingChannel.Close](http://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.close.aspx)() (Windows.Foundation.Diagnostics.LoggingChannel.Dispose() v C# a VB) po dokončení protokolovacího kanálu.  
>   -   Každý otevřený protokolovací kanál musí mít jedinečný název. Pokus o vytvoření nového protokolovacího kanálu se stejným názvem, jaké má jiný kanál, způsobil výjimku.  
  
 Viz ukázku Windows SDK [ukázka LoggingSession](http://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336) příklady.  
  
 **Přidání značek do kódu jazyka JavaScript**  
  
 Chcete-li přidat uživatelské značky, přidejte do míst v kódu, které chcete označit, následující kód:  
  
```  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* je řetězec, který obsahuje zprávu zobrazíte v popisu uživatelské značky.  
  
##  <a name="BKMK_Configure_your_environment_for_profiling"></a> Konfigurace prostředí pro profilaci  
 Pro získání kvalitních odhadů je vhodné provést profilaci využití energie aplikací na zařízení s nízkou spotřebou, které je napájeno bateriemi. Protože aplikaci Visual Studio nelze na většině z těchto zařízení spustit, bude třeba k tomuto zařízení pomocí nástrojů Visual Studio Remote Tools připojit počítač, na kterém aplikace Visual Studio běží. Pro připojení ke vzdálenému zařízení je třeba nakonfigurovat jak projekt aplikace Visual Studio, tak vzdálené zařízení. Zobrazit [aplikace Windows Store spustit ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md) Další informace.  
  
> [!TIP]
> - Nedoporučujeme provádět energetickou profilaci na simulátoru Windows Store ani na počítači, na kterém běží aplikace Visual Studio. Profilace přímo na příslušném zařízení poskytuje mnohem realističtější data.  
>   -   Provádějte profilaci na cílovém zařízení v době, kdy je zařízení napájeno bateriemi.  
>   -   Zavřete ostatní aplikace, které by mohly využívat stejné prostředky (síť, procesor nebo displej).  
  
##  <a name="BKMK_Collect_energy_profile_data_for_your_app"></a> Shromažďování dat o energetickém profilu vaší aplikace  
  
1.  Na **ladění** nabídce zvolte **spustit diagnostické nástroje bez ladění**.  
  
     ![Zvolte spotřebu energie v centra diagnostiky](../profiling/media/energyprof-diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2.  Zvolte **spotřeba energie** a klikněte na tlačítko **Start**.  
  
    > [!NOTE]
    >  Při spuštění **spotřeba energie** profiler, může se zobrazit **řízení uživatelských účtů** okno povolení ke spuštění VsEtwCollector.exe. Zvolte **Ano**.  
  
3.  Spusťte v aplikaci shromažďování dat.  
  
4.  Pokud chcete profilaci zastavit, přepněte zpět do sady Visual Studio (Alt + Tab) a zvolte **zastavit shromažďování** na stránce centra diagnostiky.  
  
     ![Shromažďování dat ukončit](../profiling/media/xamlprof-stopcollection.png "XAMLProf_StopCollection")  
  
     Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.  
  
##  <a name="BKMK_Collect_energy_profile_data_for_an_installed_app"></a> Shromažďování dat o energetickém profilu nainstalované aplikace  
 Nástroj Spotřeba energie lze spustit pouze v aplikacích pro Windows Store 8.1, které jsou spouštěny z řešení aplikace Visual Studio nebo jsou instalovány z Windows Store. Pokud je řešení otevřené v sadě Visual Studio, je výchozí cíl **spouštěný projekt**. Zacílení nainstalované aplikace:  
  
1. Zvolte **změnit cíl** a klikněte na tlačítko **nainstalovaná aplikace**.  
  
2. Z **vybrat nainstalované balíčky aplikací** , zvolte cíl.  
  
3. Zvolte **spotřeba energie** na stránce Centrum diagnostiky.  
  
4. Zvolte **Start** spuštění profilování.  
  
   Pokud chcete profilaci zastavit, přepněte zpět do sady Visual Studio (Alt + Tab) a zvolte **zastavit shromažďování** na stránce centra diagnostiky.  
  
##  <a name="BKMK_Analyze_energy_profile_data"></a> Analýza dat energetického profilu  
 Data energetického profilu se zobrazují v okně dokumentu aplikace Visual Studio:  
  
 ![Stránka sestavy profileru energie](../profiling/media/energyprof-all.png "ENERGYPROF_All")  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid-1.png "ProcGuid_1")|Soubor sestavy má název sestavy*YYYYMMDD-HHMM*.diagsession. Pokud se rozhodnete sestavu uložit, můžete název změnit.|  
|![2. krok](../profiling/media/procguid-2.png "ProcGuid_2")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|  
|![3. krok](../profiling/media/procguid-3.png "ProcGuid_3")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|  
|![4. krok](../profiling/media/procguid-4.png "ProcGuid_4")|**Spotřeby energie** graf je Víceřádkový graf, který zobrazuje změnu ve výstupu napájení, jež je způsobena prostředkem zařízení během relace profilování. Profiler Spotřeba energie sleduje výkon využívaný procesorem, síťovou aktivitou a displejem.|  
|![Krok 5](../profiling/media/procguid-6.png "ProcGuid_6")|**Prostředky (zapnuto/vypnuto)** graph poskytuje podrobné informace o síti náklady na energii. **Sítě** panelu představuje čas, který bylo otevřeno síťové připojení. **Přenosu dat** podřízený řádek je čas, aby byla aplikace přijímala nebo odesílala data přes síť.|  
|![Krok 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|**Souhrn využití energie** ukazuje poměrné množství celkového množství energie použité ve vybrané časové osy podle Procesorem, síťovou aktivitou a displejem.|  
  
 **Analýza dat energetického profilu**  
  
 Najděte oblast, kde výkon prostředku dosáhl vrcholu. Přiřaďte tuto oblast k funkci vaší aplikace. Pomocí ovládacích panelů časové osy můžete tuto oblast přiblížit. Pokud vás zajímá využití sítě, rozbalte **sítě** uzlu v **prostředky (zapnuto/vypnuto)** grafu se porovnat čas, který byl síťové připojení otevřené, s dobou, která aplikace přijímala nebo přenosu data přes dané připojení. Zkrácení doby, po kterou je síť zbytečně otevřená, představuje velmi efektivní optimalizaci.  
  
##  <a name="BKMK_Optimize_energy_use"></a> Optimalizace spotřeby energie  
 Kromě přenosu dat vynakládají síťová připojení energii také na inicializaci, udržování a ukončování připojení. Některé sítě udržují připojení po určitou dobu po odeslání nebo přijetí dat, aby umožnily přenos většího množství dat v rámci jednoho připojení. Můžete použít **prostředky (zapnuto/vypnuto)** podokně způsobu, jakým aplikace komunikuje s připojením.  
  
 ![Prostředky &#40;na&#47;vypnout&#41; podokně](../profiling/media/energyprof-resources.png "ENERGYPROF_Resources")  
  
 Pokud **sítě** a **přenosu dat** pruhy ukazují, že připojení je otevřeno po dlouhou dobu na přerušovaně přenáší řadu malých datových paketů, můžete dávky dat k odeslání v jednom přenosu zkrátit čas, který je otevřen v síti a tím snížit spotřebu energie.  
  
 ![Podokně Souhrn využití energie](../profiling/media/energyprof-summary.png "ENERGYPROF_Summary")  
  
 Spotřebu energie displeje lze ovlivnit hůře. Většina obrazovek potřebuje více energie k zobrazení světlých barev než tmavších barev, takže jedním ze způsobů, jak snížit spotřebu, je použití tmavého pozadí.  
  
##  <a name="BKMK_Other_resources"></a> Další prostředky  
  
-   **Stav připojení a správa spotřeby** oddíly pro [jazyka C# / VB/C++ a XAML](http://msdn.microsoft.com/en-us/0ee0b706-8432-4d49-9801-306ed90764e1) a [jazyka JavaScript a HTML](http://msdn.microsoft.com/en-us/372afa6a-1c7c-4657-967d-03a77cd8e933) Windows Dev Center popisují rozhraní Windows API, které poskytují informace o síťovém připojení, které vaše aplikace může používat minimalizovat náklady na síťový provoz.  
  
     Simulátor aplikace Visual Studio pro aplikace pro Windows Store umožňuje simulovat vlastnosti datového připojení rozhraní API pro síťové informace. Zobrazit [aplikace spustit Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md)  
  
-   **Časování funkcí jazyka JavaScript** a **využití procesoru** nástroje pomáhá snížit zatížení procesoru při je způsobeno neefektivními funkcemi. Zobrazit [analýza využití procesoru](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).



