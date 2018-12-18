---
title: Analýza spotřeby energie v aplikacích pro UWP | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 08723f30957ece57af0f666a5464907a686ad604
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220733"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analýza spotřeby energie v aplikacích pro UWP
Visual Studio **spotřeba energie** profileru pomáhá analyzovat spotřebu energie v aplikacích pro UWP v s nízkou spotřebou, na kterých běží všechny nebo část času, na vlastní baterie. Na zařízení napájeném z baterie může aplikace s příliš vysokou spotřebou energie způsobit tak velkou nespokojenost zákazníka, že ji může dokonce i odinstalovat. Optimalizace využití energie můžete rozšířit uživatelskou základnu vaší aplikace a používat zákazníky.  
  
## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Co je profiler Spotřeba energie, jak funguje a co měří  
 Profiler Spotřeba energie shromažďuje údaje o činnosti displeje, procesoru a síťových připojení zařízení během relace profilování. Poté vygeneruje odhady množství energie použité pro tyto činnosti a celkové množství energie použité pro relaci profilování.  
  
> [!NOTE]
>  Energetický profiler provádí odhad výkonu a spotřeby energie pomocí softwarového modelu standardního hardwaru referenčního zařízení, jež reprezentuje tablety s nízkou spotřebou, na kterých by vaše aplikace mohla běžet. Pro dosažení co nejlepšího odhadu doporučujeme shromáždit profilová data u tabletů s nízkou spotřebou.  
>   
>  Ačkoliv model poskytuje dobré odhady pro řadu zařízení s nízkou spotřebou, skutečné hodnoty zařízení, která profilujete, budou pravděpodobně odlišné. Použijte tyto hodnoty pro nalezení aktivit displeje, procesoru a sítě, které jsou v porovnání s využitím jiných prostředků náročné, takže by mohly představovat vhodné kandidáty na optimalizaci.  
  
 Profiler spotřeba energie používá tyto definice *power* a *energie*:  
  
- *Napájení* opatření množství síly potřebné se používá k provedení práce, která se provádí v časovém intervalu. Elektrické věd, je standardní jednotkou výkonu *watt*, který je definován jako rychlost, jakou práce provádí, když jeden Ampér – měrná aktuální toků prostřednictvím rozdílem v elektrickém potenciálu o velikosti jednoho voltu. V **spotřeby energie** grafu, jsou jednotky zobrazeny v miliwattech **mW** jsou 1/1 000 wattu.  
  
   Všimněte si, že výkon má směr (množství práce se v čase může zvýšit nebo snížit) a rychlost (velikost zvýšení nebo snížení množství práce).  
  
- *Energie* opatření dosáhl celkové množství výkonu, smyslu kapacity nebo potenciálu, jako v případě kapacity baterií, nebo smyslu celkového množství výkonu vynaloženého za určitou dobu. Jednotkou energie je watthodina, tedy výkon jednoho wattu konstantně působící po jednu hodinu. V **souhrn energie**, jsou jednotky zobrazeny v miliwatthodinách **MWh**.  
  
  ![Kapacita energie výkon použít, celkového množství energie použité](../profiling/media/energyprof_capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Například plně nabitá baterie v tabletu uchovává určité množství energie. Při využívání této energie pro provádění úloh, jako je například komunikace po síti, výpočty hodnot nebo zobrazování grafického obsahu, se výkon spotřebovává různou rychlostí. Pro libovolné časové období se celkové množství spotřebovaného výkonu poměřuje také energií.  
  
## <a name="identify-scenarios-with-user-marks"></a>Scénáře s uživatelskými značkami  
 Můžete přidat *uživatelské značky* do vlastních profilovacích dat. Chcete-li usnadníte identifikaci oblastí na časové ose.  
  
 ![Značky uživatele na časové ose](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 Značka se zobrazí jako oranžový trojúhelník umístěný na časové ose v čase spuštění metody. Zpráva a čas se zobrazí jako popisek, jakmile na značku umístíte ukazatel myší. Pokud jsou dvě nebo více uživatelských značek blízko u sebe, značky i popisky se sloučí. Značky od sebe rozlišíte přiblížením časové osy.  
  
 **Přidání značek do C#, Visual Basic, kód jazyka C++**  
  
 Chcete-li přidat uživatelskou značku do jazyka C#, Visual Basic, kód jazyka C++, nejprve vytvořit [Windows.Foundation.Diagnostics LoggingChannel](xref:Windows.Foundation.Diagnostics.LoggingChannel) objektu. Pak vložte volání [LoggingChannel.LogMessage](xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A) metod v kódu, které chcete označit. Použití [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) ve volání.  
  
 Jakmile se metoda spustí, uživatelská značka je spolu se zprávou přidána do profilových dat.  
  
> [!NOTE]
> - Obor názvů Windows.Foundation.Diagnostics.loggingchannel implementuje [Windows.Foundation.IClosable](/uwp/api/windows.foundation.iclosable) rozhraní (předpokládané podobě [rozhraní System.IDisposable](/dotnet/api/system.idisposable) v C# a VB). Aby se zabránilo nevrácení prostředků operačního systému, volejte [LoggingChannel.Close](/uwp/api/Windows.Foundation.Diagnostics.LoggingChannel) ([Windows.Foundation.Diagnostics.LoggingChannel.Dispose](/uwp/api/Windows.Foundation.Diagnostics.LoggingChannel) v C# a VB) po dokončení protokolování kanál.  
>   -   Každý otevřený protokolovací kanál musí mít jedinečný název. Pokus o vytvoření nového protokolovacího kanálu se stejným názvem, jaké má jiný kanál, způsobil výjimku.  
  
 Viz ukázku Windows SDK [ukázka LoggingSession](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336) příklady.  
  
 **Přidání značek do kódu jazyka JavaScript**  
  
 Chcete-li přidat uživatelské značky, přidejte do míst v kódu, které chcete označit, následující kód:  
  
```JavaScript  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* je řetězec, který obsahuje zprávu zobrazíte v popisu uživatelské značky.  
  
## <a name="configure-your-environment-for-profiling"></a>Konfigurace prostředí pro profilaci  
 Pro získání kvalitních odhadů, bude potřeba profilaci využití energie aplikací na zařízení s nízkou spotřebou, které je napájeno bateriemi. Vzhledem k tomu, že Visual Studio se nespouští na většině z těchto zařízení, musíte připojit počítač Visual Studio k zařízení pomocí nástroje Visual Studio remote tools. Pro připojení ke vzdálenému zařízení je třeba nakonfigurovat jak projekt aplikace Visual Studio, tak vzdálené zařízení. Zobrazit [aplikací pro UWP spuštění na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md) Další informace.  
  
> [!TIP]
> - Nedoporučujeme provádět energetickou profilaci na simulátoru UPW nebo na počítači aplikace Visual Studio. Profilace přímo na příslušném zařízení poskytuje mnohem realističtější data.  
>   -   Provádějte profilaci na cílovém zařízení v době, kdy je zařízení napájeno bateriemi.  
>   -   Zavřete ostatní aplikace, které by mohly využívat stejné prostředky (síť, procesor nebo displej).  
  
## <a name="collect-energy-profile-data-for-your-app"></a>Shromažďování dat o energetickém profilu vaší aplikace  
  
1.  Na **ladění** nabídce zvolte **spustit diagnostické nástroje bez ladění**.  
  
     ![Zvolte spotřebu energie v centra diagnostiky](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2.  Zvolte **spotřeba energie** a klikněte na tlačítko **Start**.  
  
    > [!NOTE]
    >  Při spuštění **spotřeba energie** profiler, může se zobrazit **řízení uživatelských účtů** okno ke spuštění *VsEtwCollector.exe*. Zvolte **Ano**.  
  
3.  Spusťte v aplikaci shromažďování dat.  
  
4.  Pokud chcete profilaci zastavit, přepněte zpět do sady Visual Studio (Alt + Tab) a zvolte **zastavit shromažďování** na stránce centra diagnostiky.  
  
     ![Shromažďování dat ukončit](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")  
  
     Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.  
  
## <a name="collect-energy-profile-data-for-an-installed-app"></a>Shromažďování dat o energetickém profilu nainstalované aplikace  
 Nástroj spotřeba energie lze spustit pouze v aplikacích pro UWP, které jsou spouštěny z řešení sady Visual Studio nebo jsou instalovány z Microsoft Store. Pokud je řešení otevřené v sadě Visual Studio, je výchozí cíl **spouštěný projekt**. Zacílení nainstalované aplikace:  
  
1. Zvolte **změnit cíl** a klikněte na tlačítko **nainstalovaná aplikace**.  
  
2. Z **vybrat nainstalované balíčky aplikací** , zvolte cíl.  
  
3. Zvolte **spotřeba energie** na stránce Centrum diagnostiky.  
  
4. Zvolte **Start** spuštění profilování.  
  
   Pokud chcete profilaci zastavit, přepněte zpět do sady Visual Studio (Alt + Tab) a zvolte **zastavit shromažďování** na stránce centra diagnostiky.  
  
## <a name="analyze-energy-profile-data"></a>Analýza dat energetického profilu  
 Data energetického profilu se zobrazují v okně dokumentu aplikace Visual Studio:  
  
 ![Stránka sestavy profileru energie](../profiling/media/energyprof_all.png "ENERGYPROF_All")  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid_1.png "ProcGuid_1")|Soubor sestavy má název sestavy*YYYYMMDD-HHMM*.diagsession. Pokud se rozhodnete sestavu uložit, můžete název změnit.|  
|![2. krok](../profiling/media/procguid_2.png "ProcGuid_2")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|  
|![3. krok](../profiling/media/procguid_3.png "ProcGuid_3")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|  
|![4. krok](../profiling/media/procguid_4.png "ProcGuid_4")|**Spotřeby energie** graf je Víceřádkový graf, který zobrazuje změnu ve výstupu napájení, jež je způsobena prostředkem zařízení během relace profilování. Profiler Spotřeba energie sleduje výkon využívaný procesorem, síťovou aktivitou a displejem.|  
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|**Prostředky (zapnuto/vypnuto)** graph poskytuje podrobné informace o síti náklady na energii. **Sítě** panelu představuje čas, který bylo otevřeno síťové připojení. **Přenosu dat** podřízený řádek je čas, aby byla aplikace přijímala nebo odesílala data přes síť.|  
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Souhrn využití energie** ukazuje poměrné množství celkového množství energie použité ve vybrané časové osy podle Procesorem, síťovou aktivitou a displejem.|  
  
 **Analýza dat energetického profilu**  
  
 Najděte oblast, kde výkon prostředku dosáhl vrcholu. Přiřaďte tuto oblast k funkci vaší aplikace. Pomocí ovládacích panelů časové osy můžete tuto oblast přiblížit. Pokud vás zajímá využití sítě, rozbalte **sítě** uzlu v **prostředky (zapnuto/vypnuto)** grafu se porovnat čas, který byl síťové připojení otevřené, s dobou, která aplikace přijímala nebo přenosu data přes dané připojení. Zkrácení doby, po kterou je síť zbytečně otevřená, představuje velmi efektivní optimalizaci.  
  
## <a name="optimize-energy-use"></a>Optimalizace spotřeby energie  
 Kromě přenosu dat vynakládají síťová připojení energii také na inicializaci, udržování a ukončování připojení. Některé sítě udržují připojení po určitou dobu po odeslání nebo přijetí dat, aby umožnily přenos většího množství dat v rámci jednoho připojení. Můžete použít **prostředky (zapnuto/vypnuto)** podokně způsobu, jakým aplikace komunikuje s připojením.  
  
 ![Prostředky &#40;na&#47;vypnout&#41; podokně](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")  
  
 Pokud **sítě** a **přenosu dat** pruhy ukazují, že připojení je otevřeno po dlouhou dobu na přerušovaně přenáší řadu malých datových paketů, můžete dávky dat k odeslání v jednom přenosu zkrátit čas, který je otevřen v síti a tím snížit spotřebu energie.  
  
 ![Podokně Souhrn využití energie](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")  
  
 Spotřebu energie displeje lze ovlivnit hůře. Většina obrazovek potřebuje více energie k zobrazení světlých barev než tmavších barev, takže jedním ze způsobů, jak snížit spotřebu, je použití tmavého pozadí.  
  
## <a name="other-resources"></a>Další zdroje  
  
-   **Stav připojení a správa spotřeby** oddíly pro [jazyka C# / VB/C++ a XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) a [jazyka JavaScript a HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) Windows Dev Center popisují rozhraní Windows API, které poskytují informace o síťovém připojení, které vaše aplikace může používat minimalizovat náklady na síťový provoz.  
  
     Simulátor aplikace Visual Studio pro aplikace pro UPW umožňuje simulovat vlastnosti datového připojení rozhraní API pro síťové informace. Zobrazit [aplikace spustit UWP v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md)  
  
-   **Časování funkcí jazyka JavaScript** a **využití procesoru** nástroje pomáhá snížit zatížení procesoru při je způsobeno neefektivními funkcemi. Zobrazit [využití procesoru analyzovat](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).

## <a name="see-also"></a>Viz také:
 [Profilace v sadě Visual Studio](../profiling/index.md)  
 [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)