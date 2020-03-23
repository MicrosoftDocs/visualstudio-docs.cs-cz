---
title: Analyzujte spotřebu energie v aplikacích UPW | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
monikerRange: vs-2017
ms.openlocfilehash: 0fc78a84d0c2f86e8db6c4703cc7404a32508d72
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73144742"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analýza spotřeby energie v aplikacích pro UWP

Profiler **visual** studio pro spotřebu energie vám pomůže analyzovat spotřebu energie a spotřeby energie aplikací UPW na tabletových zařízeních s nízkou spotřebou energie, která běží celý čas nebo část času na vlastních bateriích. Na zařízení napájeném z baterie může aplikace s příliš vysokou spotřebou energie způsobit tak velkou nespokojenost zákazníka, že ji může dokonce i odinstalovat. Optimalizace spotřeby energie může zvýšit přijetí a využití vaší aplikace zákazníky.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Co je profiler Spotřeba energie, jak funguje a co měří

Profiler Spotřeba energie shromažďuje údaje o činnosti displeje, procesoru a síťových připojení zařízení během relace profilování. Poté vygeneruje odhady množství energie použité pro tyto činnosti a celkové množství energie použité pro relaci profilování.

> [!NOTE]
> Energetický profiler provádí odhad výkonu a spotřeby energie pomocí softwarového modelu standardního hardwaru referenčního zařízení, jež reprezentuje tablety s nízkou spotřebou, na kterých by vaše aplikace mohla běžet. Pro dosažení co nejlepšího odhadu doporučujeme shromáždit profilová data u tabletů s nízkou spotřebou.
>
> Ačkoliv model poskytuje dobré odhady pro řadu zařízení s nízkou spotřebou, skutečné hodnoty zařízení, která profilujete, budou pravděpodobně odlišné. Použijte tyto hodnoty pro nalezení aktivit displeje, procesoru a sítě, které jsou v porovnání s využitím jiných prostředků náročné, takže by mohly představovat vhodné kandidáty na optimalizaci.

Profiler spotřeba energie používá tyto definice *energie* a *energie*:

- *Moc* měří rychlost, s jakou se síla používá k provádění práce, která se provádí v časovém období. V elektrické vědě je standardní jednotkou výkonu *watt*, který je definován jako rychlost, při které se pracuje, když jeden ampér proudu protéká rozdílem elektrického potenciálu jednoho voltu. V grafu **Využití energie** jsou jednotky zobrazeny jako miliwatty **mW,** které jsou jedna tisícina wattu.

   Všimněte si, že výkon má směr (množství práce se v čase může zvýšit nebo snížit) a rychlost (velikost zvýšení nebo snížení množství práce).

- *Energie* měří celkové množství energie, a to buď jako kapacita nebo potenciál, jako v kapacitě baterie, nebo jako celkový objem energie vynaložené po určitou dobu. Jednotkou energie je watthodina, tedy výkon jednoho wattu konstantně působící po jednu hodinu. V **souhrnném přehledu energie**jsou jednotky zobrazeny jako miliwatthodiny **mW-h**.

![Energetická kapacita, spotřebovávaná energie, celková spotřebovávaná energie](../profiling/media/energyprof_capcitypowerused.png)

Například plně nabitá baterie v tabletu uchovává určité množství energie. Při využívání této energie pro provádění úloh, jako je například komunikace po síti, výpočty hodnot nebo zobrazování grafického obsahu, se výkon spotřebovává různou rychlostí. Pro libovolné časové období se celkové množství spotřebovaného výkonu poměřuje také energií.

## <a name="identify-scenarios-with-user-marks"></a>Scénáře s uživatelskými značkami
 Do dat profilování můžete přidat *uživatelské značky,* které vám pomohou identifikovat oblasti v pravítku časové osy.

 ![Uživatelské značky na časové ose](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 Značka se zobrazí jako oranžový trojúhelník umístěný na časové ose v čase spuštění metody. Zpráva a čas se zobrazí jako popisek, jakmile na značku umístíte ukazatel myší. Pokud jsou dvě nebo více uživatelských značek blízko u sebe, značky i popisky se sloučí. Značky od sebe rozlišíte přiblížením časové osy.

 **Přidání značek do kódu Jazyka C#, Visual Basic, C++**

 Chcete-li přidat značku uživatele do jazyka C#, Visual <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> Basic, kód Jazyka C++, nejprve vytvořte objekt. Pak vložte <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> volání metod v bodech v kódu, které chcete označit. Použijte [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) ve volání.

 Jakmile se metoda spustí, uživatelská značka je spolu se zprávou přidána do profilových dat.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType>implementuje <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> rozhraní (promítané jako <xref:System.IDisposable?displayProperty=nameWithType> v C# a VB). Chcete-li se vyhnout úniku prostředků operačního systému, volání <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> (v<xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> C# a VB) po dokončení kanálu protokolování.
> - Každý otevřený protokolovací kanál musí mít jedinečný název. Pokud se pokusíte vytvořit nový kanál protokolování se stejným názvem jako nedisponovaný kanál, je vyvolána výjimka.

Například kód, naleznete v ukázkové [ukázkové ukázkové logování sady](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)Windows SDK .

::: moniker range="vs-2017"
**Přidání značek do kódu JavaScriptu**

Chcete-li přidat uživatelské značky, přidejte do míst v kódu, které chcete označit, následující kód:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription* je řetězec, který obsahuje zprávu, která se má zobrazit v popisku uživatelské značky.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Konfigurace prostředí pro profilaci
 Chcete-li získat dobré odhady, budete chtít profilovat spotřebu energie aplikace na zařízení s nízkým výkonem, které je napájeno bateriemi. Vzhledem k tomu, že Visual Studio neběží na většině těchto zařízení, budete muset připojit počítač Sady Visual Studio k zařízení pomocí vzdálených nástrojů sady Visual Studio. Pro připojení ke vzdálenému zařízení je třeba nakonfigurovat jak projekt aplikace Visual Studio, tak vzdálené zařízení. Další informace najdete [v tématu Spuštění aplikací UPW na vzdáleném počítači.](../debugger/run-windows-store-apps-on-a-remote-machine.md)

> [!TIP]
> - Nedoporučujeme profilování energie na simulátoru UPW nebo v počítači Visual Studio. Profilace přímo na příslušném zařízení poskytuje mnohem realističtější data.
> - Provádějte profilaci na cílovém zařízení v době, kdy je zařízení napájeno bateriemi.
> - Zavřete ostatní aplikace, které by mohly využívat stejné prostředky (síť, procesor nebo displej).

## <a name="collect-energy-profile-data-for-your-app"></a>Shromažďování dat o energetickém profilu vaší aplikace

1. V nabídce **Ladění** zvolte **Spustit diagnostiku bez ladění**.

     ![Zvolte spotřebu energie v diagnostickém rozbočovači](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. Zvolte **Spotřeba energie** a pak zvolte **Start**.

    > [!NOTE]
    > Při spuštění profileru **spotřeba energie** se může zobrazit okno **Řízení uživatelských účtů** požadující vaše oprávnění ke spuštění souboru *VsEtwCollector.exe*. Zvolte **Ano**.

3. Spusťte v aplikaci shromažďování dat.

4. Chcete-li profilování ukončit, přepněte zpět do sady Visual Studio (Alt + Tab) a na stránce centra Diagnostika zvolte **Zastavit kolekci.**

     ![Ukončení shromažďování dat](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Shromažďování dat o energetickém profilu nainstalované aplikace
 Nástroj Spotřeba energie lze spustit pouze v aplikacích UPW, které jsou spuštěny z řešení sady Visual Studio nebo jsou nainstalovány z obchodu Microsoft Store. Pokud je řešení otevřené v sadě Visual Studio, je výchozím cílem **projekt po spuštění**. Zacílení nainstalované aplikace:

1. Zvolte **Změnit cíl** a pak zvolte **Nainstalovaná aplikace**.

2. V seznamu **Vybrat balíček nainstalovaných aplikací** zvolte cíl.

3. Na stránce diagnostického centra zvolte **Spotřeba energie.**

4. Chcete-li začít profilování, zvolte **Začít.**

   Chcete-li profilování ukončit, přepněte zpět do sady Visual Studio (Alt + Tab) a na stránce centra Diagnostika zvolte **Zastavit kolekci.**

## <a name="analyze-energy-profile-data"></a>Analýza dat energetického profilu
 Data energetického profilu se zobrazují v okně dokumentu aplikace Visual Studio:

 ![Stránka sestavy energetického profileru](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Soubor sestavy se nazývá Sestava*YYYMMDD-HHMM*.diagsession. Pokud se rozhodnete sestavu uložit, můžete název změnit.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Graf **využití energie** je víceřádkový graf, který zobrazuje změnu výstupu napájení, která je způsobena prostředkem zařízení během relace profilování. Profiler Spotřeba energie sleduje výkon využívaný procesorem, síťovou aktivitou a displejem.|
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Graf **Zdroje (Zapnuto/Vypnuto)** obsahuje podrobnosti o nákladech na energii v síti. **Panel Síť** představuje čas otevření síťového připojení. Podřízený panel **Přenos dat** je čas, kdy aplikace přijímala nebo odesílá data po síti.|
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Souhrn využití energie** zobrazuje poměrné množství celkové energie, která byla použita ve vybrané časové ose procesorem, aktivitou sítě a zobrazením na obrazovce.|

 **Analýza údajů o energetickém profilu**

 Najděte oblast, kde výkon prostředku dosáhl vrcholu. Přiřaďte tuto oblast k funkci vaší aplikace. Pomocí ovládacích panelů časové osy můžete tuto oblast přiblížit. Pokud se zaměřujete na využití sítě, rozbalte uzel **sítě** v grafu **Prostředky (Zapnuto/Vypnuto)** a porovnejte dobu, po kterou bylo síťové připojení otevřeno, s časem, kdy aplikace přijímala nebo přenášela data přes připojení. Zkrácení doby, po kterou je síť zbytečně otevřená, představuje velmi efektivní optimalizaci.

## <a name="optimize-energy-use"></a>Optimalizace spotřeby energie
 Kromě přenosu dat vynakládají síťová připojení energii také na inicializaci, udržování a ukončování připojení. Některé sítě udržují připojení po určitou dobu po odeslání nebo přijetí dat, aby umožnily přenos většího množství dat v rámci jednoho připojení. Podokno **Prostředky (Zapnuto/Vypnuto)** můžete použít ke kontrole způsobu, jakým vaše aplikace spolupracuje s připojením.

 ![Podokno &#40;zdroje&#47;vypnuto&#41;](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 Pokud panely **Síťový** a **datový přenos** ukazují, že připojení je otevřeno po dlouhou dobu, aby přerušovaně přenášelo řadu malých datových paketů, můžete data dávkově odeslat jedním přenosem, zkrátit dobu otevření sítě a tím ušetřit náklady na energii.

 ![Podokno Souhrn spotřeby energie](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Spotřebu energie displeje lze ovlivnit hůře. Většina obrazovek potřebuje více energie k zobrazení světlých barev než tmavších barev, takže jedním ze způsobů, jak snížit spotřebu, je použití tmavého pozadí.

## <a name="other-resources"></a>Další prostředky

- Části **Stav připojení a správa nákladů** pro [c#/VB/C++ a XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) popisují windows api, které poskytují informace o připojení k síti, které vaše aplikace můžete použít k minimalizaci nákladů na síťový provoz.

   Simulátor Visual Studia pro aplikace UPW umožňuje simulovat vlastnosti datového připojení rozhraní API síťových informací. Viz [Spuštění aplikací UPW v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md)

- Nástroje **pro využití procesoru** vám mohou pomoci snížit zatížení procesoru, když je způsobeno neefektivními funkcemi. Viz [Analýza využití procesoru](../profiling/beginners-guide-to-performance-profiling.md).

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)