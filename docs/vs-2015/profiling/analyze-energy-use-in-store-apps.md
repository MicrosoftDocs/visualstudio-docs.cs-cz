---
title: Analýza využití energie v aplikacích pro Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82f5e6401ba65a0dfaffc268890ece0166432c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532948"
---
# <a name="analyze-energy-use-in-store-apps"></a>Analýza spotřeby energie v aplikacích pro Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler **spotřeby energie** v programu Visual Studio pomáhá analyzovat spotřebu energie a energie aplikací pro Windows Store na zařízeních s nízkým výkonem, na kterých běží celá nebo část času na svých vlastních bateriích. Na zařízení napájeném z baterie může aplikace s příliš vysokou spotřebou energie způsobit tak velkou nespokojenost zákazníka, že ji může dokonce i odinstalovat. Optimalizace využití energie můžete zlepšit přijetí a používání aplikace zákazníky.  
  
## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a><a name="BKMK_What_the_Energy_Consumption_tool_is__how_it_works__and_what_it_measures"></a> Co je profiler spotřeba energie, jak funguje a co měří  
 Profiler Spotřeba energie shromažďuje údaje o činnosti displeje, procesoru a síťových připojení zařízení během relace profilování. Poté vygeneruje odhady množství energie použité pro tyto činnosti a celkové množství energie použité pro relaci profilování.  
  
> [!NOTE]
> Energetický profiler provádí odhad výkonu a spotřeby energie pomocí softwarového modelu standardního hardwaru referenčního zařízení, jež reprezentuje tablety s nízkou spotřebou, na kterých by vaše aplikace mohla běžet. Pro dosažení co nejlepšího odhadu doporučujeme shromáždit profilová data u tabletů s nízkou spotřebou.  
>   
> Ačkoliv model poskytuje dobré odhady pro řadu zařízení s nízkou spotřebou, skutečné hodnoty zařízení, která profilujete, budou pravděpodobně odlišné. Použijte tyto hodnoty pro nalezení aktivit displeje, procesoru a sítě, které jsou v porovnání s využitím jiných prostředků náročné, takže by mohly představovat vhodné kandidáty na optimalizaci.  
  
 Profiler spotřeby energie používá tyto definice *energie* a *energie*:  
  
- Hodnota *napájení* měří sazbu, která je využívána k provedení práce, která se provádí v časovém intervalu. V oblasti elektrotechniky má standardní jednotka spotřeby hodnotu *Watt*, která je definována jako sazba, při které je práce prováděna v případě, že jeden Ampere aktuálního toku prochází v důsledku elektrického potenciálního rozdílu v jedné Volt. V grafu **využití výkonu** se jednotky zobrazují jako miliwattech **MW** , což jsou jedna thousandtha w.  
  
   Všimněte si, že výkon má směr (množství práce se v čase může zvýšit nebo snížit) a rychlost (velikost zvýšení nebo snížení množství práce).  
  
- *Energie* měří celkové množství energie, buď jako kapacitu nebo potenciál, jako v rámci kapacity baterie, nebo jako celkové množství energie vynaložené v časovém intervalu. Jednotkou energie je watthodina, tedy výkon jednoho wattu konstantně působící po jednu hodinu. V **souhrnu energie**se jednotky zobrazují jako miliwatthodinách-hodiny **MW-h**.  
  
  ![Kapacita energie, využité napájení, celkové využití energie](../profiling/media/energyprof-capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Například plně nabitá baterie v tabletu uchovává určité množství energie. Při využívání této energie pro provádění úloh, jako je například komunikace po síti, výpočty hodnot nebo zobrazování grafického obsahu, se výkon spotřebovává různou rychlostí. Pro libovolné časové období se celkové množství spotřebovaného výkonu poměřuje také energií.  
  
## <a name="identify-scenarios-with-user-marks"></a><a name="BKMK_Identify_scenarios_with_user_marks"></a> Identifikace scénářů s uživatelskými značkami  
 Můžete přidat *uživatelské značky* k datům profilace, které vám pomůžou identifikovat oblasti v pravítku časové osy.  
  
 ![Uživatelské značky na časové ose](../profiling/media/profilers-usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 Značka se zobrazí jako oranžový trojúhelník umístěný na časové ose v čase spuštění metody. Zpráva a čas se zobrazí jako popisek, jakmile na značku umístíte ukazatel myší. Pokud jsou dvě nebo více uživatelských značek blízko u sebe, značky i popisky se sloučí. Značky od sebe rozlišíte přiblížením časové osy.  
  
 **Přidání značek do C#, Visual Basic, kódu C++**  
  
 Chcete-li přidat značku uživatele do C#, Visual Basic, kód C++, nejprve vytvořte objekt [Windows. Foundation. Diagnostics LoggingChannel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) . Poté vložte volání metod [LoggingChannel. LogMessage –](https://msdn.microsoft.com/library/windows/apps/dn264210.aspx) v místech v kódu, který chcete označit. Použijte [LoggingLevel. informace](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) v voláních.  
  
 Jakmile se metoda spustí, uživatelská značka je spolu se zprávou přidána do profilových dat.  
  
> [!NOTE]
> - Windows. Foundation. Diagnostics LoggingChannel implementuje rozhraní [Windows. Foundation. IClosable](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iclosable.aspx) (prohlášené jako [System. IDisposable](https://msdn.microsoft.com/library/System.IDisposable.aspx) v jazyce C# a VB). Aby se zabránilo úniku prostředků operačního systému, zavolejte [LoggingChannel. Close](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.close.aspx)() (Windows. Foundation. Diagnostics. LoggingChannel. Dispose () v jazyce C# a VB), až budete hotovi s kanálem protokolování.  
>   - Každý otevřený protokolovací kanál musí mít jedinečný název. Pokus o vytvoření nového protokolovacího kanálu se stejným názvem, jaké má jiný kanál, způsobil výjimku.  
  
 **Přidání značek do kódu JavaScriptu**  
  
 Chcete-li přidat uživatelské značky, přidejte do míst v kódu, které chcete označit, následující kód:  
  
```  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* je řetězec, který obsahuje zprávu, která se má zobrazit v popisu značky uživatele.  
  
## <a name="configure-your-environment-for-profiling"></a><a name="BKMK_Configure_your_environment_for_profiling"></a> Konfigurace prostředí pro profilaci  
 Pro získání kvalitních odhadů je vhodné provést profilaci využití energie aplikací na zařízení s nízkou spotřebou, které je napájeno bateriemi. Protože aplikaci Visual Studio nelze na většině z těchto zařízení spustit, bude třeba k tomuto zařízení pomocí nástrojů Visual Studio Remote Tools připojit počítač, na kterém aplikace Visual Studio běží. Pro připojení ke vzdálenému zařízení je třeba nakonfigurovat jak projekt aplikace Visual Studio, tak vzdálené zařízení. Další informace najdete v tématu [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md) .  
  
> [!TIP]
> - Nedoporučujeme provádět energetickou profilaci na simulátoru Windows Store ani na počítači, na kterém běží aplikace Visual Studio. Profilace přímo na příslušném zařízení poskytuje mnohem realističtější data.  
>   - Provádějte profilaci na cílovém zařízení v době, kdy je zařízení napájeno bateriemi.  
>   - Zavřete ostatní aplikace, které by mohly využívat stejné prostředky (síť, procesor nebo displej).  
  
## <a name="collect-energy-profile-data-for-your-app"></a><a name="BKMK_Collect_energy_profile_data_for_your_app"></a> Shromažďování dat o energetickém profilu vaší aplikace  
  
1. V nabídce **ladění** vyberte možnost **Spustit diagnostiku bez ladění**.  
  
     ![Výběr spotřeby energie v centru diagnostiky](../profiling/media/energyprof-diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2. Zvolte **Spotřeba energie** a pak zvolte **Spustit**.  
  
    > [!NOTE]
    > Když spustíte Profiler **spotřeby energie** , může se zobrazit okno **řízení uživatelských účtů** požadující vaše oprávnění ke spuštění VsEtwCollector.exe. Vyberte **Ano**.  
  
3. Spusťte v aplikaci shromažďování dat.  
  
4. Pokud chcete profilaci zastavit, přepněte zpátky na Visual Studio (ALT + TAB) a na stránce diagnostické centrum klikněte na **Zastavit shromažďování** .  
  
     ![Zastavit shromažďování dat](../profiling/media/xamlprof-stopcollection.png "XAMLProf_StopCollection")  
  
     Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.  
  
## <a name="collect-energy-profile-data-for-an-installed-app"></a><a name="BKMK_Collect_energy_profile_data_for_an_installed_app"></a> Shromažďování dat o energetickém profilu nainstalované aplikace  
 Nástroj Spotřeba energie lze spustit pouze v aplikacích pro Windows Store 8.1, které jsou spouštěny z řešení aplikace Visual Studio nebo jsou instalovány z Windows Store. Když je řešení otevřené v aplikaci Visual Studio, výchozím cílem je **projekt po spuštění**. Zacílení nainstalované aplikace:  
  
1. Zvolte **změnit cíl** a pak zvolte **nainstalovaná aplikace**.  
  
2. V seznamu **Vybrat nainstalovaný balíček aplikace** zvolte cíl.  
  
3. Na stránce Centrum diagnostiky vyberte **Spotřeba energie** .  
  
4. Vyberte **Spustit** pro zahájení profilace.  
  
   Pokud chcete profilaci zastavit, přepněte zpátky na Visual Studio (ALT + TAB) a na stránce diagnostické centrum klikněte na **Zastavit shromažďování** .  
  
## <a name="analyze-energy-profile-data"></a><a name="BKMK_Analyze_energy_profile_data"></a> Analýza dat energetického profilu  
 Data energetického profilu se zobrazují v okně dokumentu aplikace Visual Studio:  
  
 ![Stránka sestavy profilace energie](../profiling/media/energyprof-all.png "ENERGYPROF_All")  
  
|Image|Popis|  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Soubor sestavy má název Report*RRRRMMDD-hhmm*. diagsession. Pokud se rozhodnete sestavu uložit, můžete název změnit.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Graf **využití napájení** je víceřádkový graf, který zobrazuje změnu ve výstupu napájení způsobenou prostředkem zařízení během relace profilování. Profiler Spotřeba energie sleduje výkon využívaný procesorem, síťovou aktivitou a displejem.|  
|![Krok 5](../profiling/media/procguid-6.png "ProcGuid_6")|Graf **prostředky (zapnuto/vypnuto)**  poskytuje podrobné informace o nákladech na energii sítě. Panel **síť** představuje čas, kdy bylo připojení k síti otevřeno. Podřízený panel **přenos dat** je čas, kdy aplikace přijímala nebo odesílala data přes síť.|  
|![Krok 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|**Souhrn využití energie** zobrazuje poměrnou hodnotu celkové energie, která se použila ve vybrané časové ose podle procesoru, síťové aktivity a displeje obrazovky.|  
  
 **Postup analýzy dat energetického profilu**  
  
 Najděte oblast, kde výkon prostředku dosáhl vrcholu. Přiřaďte tuto oblast k funkci vaší aplikace. Pomocí ovládacích panelů časové osy můžete tuto oblast přiblížit. Pokud se zaměřujete na využití sítě, rozbalte uzel **síť** v grafu **prostředky (zapnuto/vypnuto)**  , abyste porovnali čas, kdy se síťové připojení otevřelo v době, kdy aplikace přijímala nebo přenáší data prostřednictvím připojení. Zkrácení doby, po kterou je síť zbytečně otevřená, představuje velmi efektivní optimalizaci.  
  
## <a name="optimize-energy-use"></a><a name="BKMK_Optimize_energy_use"></a> Optimalizovat spotřebu energie  
 Kromě přenosu dat vynakládají síťová připojení energii také na inicializaci, udržování a ukončování připojení. Některé sítě udržují připojení po určitou dobu po odeslání nebo přijetí dat, aby umožnily přenos většího množství dat v rámci jednoho připojení. Podokno **prostředky (zapnuto/vypnuto)** můžete použít k prohlédnutí způsobu, jakým vaše aplikace komunikuje s připojením.  
  
 ![&#40;prostředků&#47;vypnutí&#41; podokně](../profiling/media/energyprof-resources.png "ENERGYPROF_Resources")  
  
 Pokud se v seznamu **síť** a **přenos dat** ukáže, že je připojení otevřeno pro dlouhou dobu, aby bylo možné občasně přenášet řadu malých objemů dat, můžete data dávkovat za účelem jejich odeslání v jednom přenosu, zkrátit dobu, po kterou je síť otevřená, a ušetřit tak náklady na energii.  
  
 ![Podokno Souhrn spotřeby energie](../profiling/media/energyprof-summary.png "ENERGYPROF_Summary")  
  
 Spotřebu energie displeje lze ovlivnit hůře. Většina obrazovek potřebuje více energie k zobrazení světlých barev než tmavších barev, takže jedním ze způsobů, jak snížit spotřebu, je použití tmavého pozadí.  
  
## <a name="other-resources"></a><a name="BKMK_Other_resources"></a> Další zdroje informací  
  
- Oddíly **stav připojení a Správa nákladů** pro [jazyky C#/VB/C + + a XAML](https://msdn.microsoft.com/0ee0b706-8432-4d49-9801-306ed90764e1) a [JavaScript a HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) na stránce Windows Dev Center popisují rozhraní API systému Windows, která poskytují informace o připojení k síti, které může vaše aplikace používat k minimalizaci nákladů na síťový provoz.  
  
     Simulátor aplikace Visual Studio pro aplikace pro Windows Store umožňuje simulovat vlastnosti datového připojení rozhraní API pro síťové informace. Viz [spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md) .  
  
- **Časování funkcí jazyka JavaScript** a nástroje **využití procesoru** vám můžou snížit zatížení procesoru, když je to způsobeno neúčinnými funkcemi. Viz [Analýza využití procesoru](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).
