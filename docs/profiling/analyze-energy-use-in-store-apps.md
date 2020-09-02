---
title: Analýza využití energie v aplikacích pro UWP | Microsoft Docs
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
ms.openlocfilehash: 524eb76696414cbbdba72266cc732ccb7e089f86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537238"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analýza spotřeby energie v aplikacích pro UWP

Profiler **spotřeby energie** v programu Visual Studio pomáhá analyzovat výkon a spotřebu energie aplikací pro UWP na zařízeních s nízkým výkonem, které běží na svých vlastních bateriích po celou dobu provozu nebo jejich části. Na zařízení napájeném z baterie může aplikace s příliš vysokou spotřebou energie způsobit tak velkou nespokojenost zákazníka, že ji může dokonce i odinstalovat. Optimalizace využití energie může zvýšit přijetí a používání vaší aplikace zákazníky.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Co je profiler Spotřeba energie, jak funguje a co měří

Profiler Spotřeba energie shromažďuje údaje o činnosti displeje, procesoru a síťových připojení zařízení během relace profilování. Poté vygeneruje odhady množství energie použité pro tyto činnosti a celkové množství energie použité pro relaci profilování.

> [!NOTE]
> Energetický profiler provádí odhad výkonu a spotřeby energie pomocí softwarového modelu standardního hardwaru referenčního zařízení, jež reprezentuje tablety s nízkou spotřebou, na kterých by vaše aplikace mohla běžet. Pro dosažení co nejlepšího odhadu doporučujeme shromáždit profilová data u tabletů s nízkou spotřebou.
>
> Ačkoliv model poskytuje dobré odhady pro řadu zařízení s nízkou spotřebou, skutečné hodnoty zařízení, která profilujete, budou pravděpodobně odlišné. Použijte tyto hodnoty pro nalezení aktivit displeje, procesoru a sítě, které jsou v porovnání s využitím jiných prostředků náročné, takže by mohly představovat vhodné kandidáty na optimalizaci.

Profiler spotřeby energie používá tyto definice *energie* a *energie*:

- Hodnota *napájení* měří sazbu, která je využívána k provedení práce, která se provádí v časovém intervalu. V oblasti elektrotechniky má standardní jednotka spotřeby hodnotu *Watt*, která je definována jako sazba, při které je práce prováděna v případě, že jeden Ampere aktuálního toku prochází v důsledku elektrického potenciálního rozdílu v jedné Volt. V grafu **využití výkonu** se jednotky zobrazují jako miliwattech **MW** , což jsou jedna thousandtha w.

   Všimněte si, že výkon má směr (množství práce se v čase může zvýšit nebo snížit) a rychlost (velikost zvýšení nebo snížení množství práce).

- *Energie* měří celkové množství energie, buď jako kapacitu nebo potenciál, jako v rámci kapacity baterie, nebo jako celkové množství energie vynaložené v časovém intervalu. Jednotkou energie je watthodina, tedy výkon jednoho wattu konstantně působící po jednu hodinu. V **souhrnu energie**se jednotky zobrazují jako miliwatthodinách-hodiny **MW-h**.

![Kapacita energie, využité napájení, celkové využití energie](../profiling/media/energyprof_capcitypowerused.png)

Například plně nabitá baterie v tabletu uchovává určité množství energie. Při využívání této energie pro provádění úloh, jako je například komunikace po síti, výpočty hodnot nebo zobrazování grafického obsahu, se výkon spotřebovává různou rychlostí. Pro libovolné časové období se celkové množství spotřebovaného výkonu poměřuje také energií.

## <a name="identify-scenarios-with-user-marks"></a>Scénáře s uživatelskými značkami
 Můžete přidat *uživatelské značky* k datům profilace, které vám pomůžou identifikovat oblasti v pravítku časové osy.

 ![Uživatelské značky na časové ose](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 Značka se zobrazí jako oranžový trojúhelník umístěný na časové ose v čase spuštění metody. Zpráva a čas se zobrazí jako popisek, jakmile na značku umístíte ukazatel myší. Pokud jsou dvě nebo více uživatelských značek blízko u sebe, značky i popisky se sloučí. Značky od sebe rozlišíte přiblížením časové osy.

 **Přidání značek do C#, Visual Basic, kódu C++**

 Chcete-li přidat značku uživatele do C#, Visual Basic, kód jazyka C++, nejprve vytvořte <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> objekt. Pak vložte volání <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> metod v místech v kódu, který chcete označit. Použijte [LoggingLevel. informace](xref:Windows.Foundation.Diagnostics.LoggingLevel) v voláních.

 Jakmile se metoda spustí, uživatelská značka je spolu se zprávou přidána do profilových dat.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType> implementuje <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> rozhraní (projekt jako <xref:System.IDisposable?displayProperty=nameWithType> v jazyce C# a VB). Chcete-li zabránit úniku prostředků operačního systému, zavolejte <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> ( <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> v jazyce C# a VB), až budete hotovi s kanálem protokolování.
> - Každý otevřený protokolovací kanál musí mít jedinečný název. Pokud se pokusíte vytvořit nový kanál protokolování se stejným názvem jako neuvolněný kanál, vyvolá se výjimka.

Příklad kódu naleznete v ukázce Windows SDK Sample [LoggingSession](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)Sample.

::: moniker range="vs-2017"
**Přidání značek do kódu JavaScriptu**

Chcete-li přidat uživatelské značky, přidejte do míst v kódu, které chcete označit, následující kód:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription* je řetězec, který obsahuje zprávu, která se má zobrazit v popisu značky uživatele.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Konfigurace prostředí pro profilaci
 Chcete-li získat dobré odhady, budete chtít profilovat využití energie aplikace na zařízení s nízkou spotřebou, které je napájené z baterií. Vzhledem k tomu, že Visual Studio neběží na většině těchto zařízení, budete muset připojit počítač se systémem Visual Studio k zařízení pomocí nástrojů Visual Studio Remote Tools. Pro připojení ke vzdálenému zařízení je třeba nakonfigurovat jak projekt aplikace Visual Studio, tak vzdálené zařízení. Další informace najdete v tématu [spuštění aplikací pro UWP na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md) .

> [!TIP]
> - Nedoporučujeme profilaci energie v simulátoru UWP ani na počítači se systémem Visual Studio. Profilace přímo na příslušném zařízení poskytuje mnohem realističtější data.
> - Provádějte profilaci na cílovém zařízení v době, kdy je zařízení napájeno bateriemi.
> - Zavřete ostatní aplikace, které by mohly využívat stejné prostředky (síť, procesor nebo displej).

## <a name="collect-energy-profile-data-for-your-app"></a>Shromažďování dat o energetickém profilu vaší aplikace

1. V nabídce **ladění** vyberte možnost **Spustit diagnostiku bez ladění**.

     ![Výběr spotřeby energie v centru diagnostiky](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. Zvolte **Spotřeba energie** a pak zvolte **Spustit**.

    > [!NOTE]
    > Když spustíte Profiler **spotřeby energie** , může se zobrazit okno **řízení uživatelských účtů** požadující vaše oprávnění ke spuštění *VsEtwCollector.exe*. Vyberte **Ano**.

3. Spusťte v aplikaci shromažďování dat.

4. Pokud chcete profilaci zastavit, přepněte zpátky na Visual Studio (ALT + TAB) a na stránce diagnostické centrum klikněte na **Zastavit shromažďování** .

     ![Zastavit shromažďování dat](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Shromažďování dat o energetickém profilu nainstalované aplikace
 Nástroj spotřeba energie se dá spustit jenom u aplikací pro UWP, které se spouštějí z řešení sady Visual Studio, nebo se instalují z Microsoft Store. Když je řešení otevřené v aplikaci Visual Studio, výchozím cílem je **projekt po spuštění**. Zacílení nainstalované aplikace:

1. Zvolte **změnit cíl** a pak zvolte **nainstalovaná aplikace**.

2. V seznamu **Vybrat nainstalovaný balíček aplikace** zvolte cíl.

3. Na stránce Centrum diagnostiky vyberte **Spotřeba energie** .

4. Vyberte **Spustit** pro zahájení profilace.

   Pokud chcete profilaci zastavit, přepněte zpátky na Visual Studio (ALT + TAB) a na stránce diagnostické centrum klikněte na **Zastavit shromažďování** .

## <a name="analyze-energy-profile-data"></a>Analýza dat energetického profilu
 Data energetického profilu se zobrazují v okně dokumentu aplikace Visual Studio:

 ![Stránka sestavy profilace energie](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|Image|Popis|
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Soubor sestavy má název Report*RRRRMMDD-hhmm*. diagsession. Pokud se rozhodnete sestavu uložit, můžete název změnit.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Časová osa ukazuje délku relace profilace, aktivační události životního cyklu aplikace a uživatelské značky.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Přetažením modrých panelů můžete vybrat určitou oblast časové osy a omezit tak sestavu jen na tuto část časové osy.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Graf **využití napájení** je víceřádkový graf, který zobrazuje změnu ve výstupu napájení způsobenou prostředkem zařízení během relace profilování. Profiler Spotřeba energie sleduje výkon využívaný procesorem, síťovou aktivitou a displejem.|
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Graf **prostředky (zapnuto/vypnuto)**  poskytuje podrobné informace o nákladech na energii sítě. Panel **síť** představuje čas, kdy bylo připojení k síti otevřeno. Podřízený panel **přenos dat** je čas, kdy aplikace přijímala nebo odesílala data přes síť.|
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Souhrn využití energie** zobrazuje poměrnou hodnotu celkové energie, která se použila ve vybrané časové ose podle procesoru, síťové aktivity a displeje obrazovky.|

 **Postup analýzy dat energetického profilu**

 Najděte oblast, kde výkon prostředku dosáhl vrcholu. Přiřaďte tuto oblast k funkci vaší aplikace. Pomocí ovládacích panelů časové osy můžete tuto oblast přiblížit. Pokud se zaměřujete na využití sítě, rozbalte uzel **síť** v grafu **prostředky (zapnuto/vypnuto)**  , abyste porovnali čas, kdy se síťové připojení otevřelo v době, kdy aplikace přijímala nebo přenáší data prostřednictvím připojení. Zkrácení doby, po kterou je síť zbytečně otevřená, představuje velmi efektivní optimalizaci.

## <a name="optimize-energy-use"></a>Optimalizace spotřeby energie
 Kromě přenosu dat vynakládají síťová připojení energii také na inicializaci, udržování a ukončování připojení. Některé sítě udržují připojení po určitou dobu po odeslání nebo přijetí dat, aby umožnily přenos většího množství dat v rámci jednoho připojení. Podokno **prostředky (zapnuto/vypnuto)** můžete použít k prohlédnutí způsobu, jakým vaše aplikace komunikuje s připojením.

 ![&#40;prostředků&#47;vypnutí&#41; podokně](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 Pokud se v seznamu **síť** a **přenos dat** ukáže, že je připojení otevřeno pro dlouhou dobu, aby bylo možné občasně přenášet řadu malých objemů dat, můžete data dávkovat za účelem jejich odeslání v jednom přenosu, zkrátit dobu, po kterou je síť otevřená, a ušetřit tak náklady na energii.

 ![Podokno Souhrn spotřeby energie](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Spotřebu energie displeje lze ovlivnit hůře. Většina obrazovek potřebuje více energie k zobrazení světlých barev než tmavších barev, takže jedním ze způsobů, jak snížit spotřebu, je použití tmavého pozadí.

## <a name="other-resources"></a>Další prostředky

- Části **stav připojení a Správa nákladů** pro [C#/VB/C + + a XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) popisují rozhraní API systému Windows, která poskytují informace o připojení k síti, které vaše aplikace může použít k minimalizaci nákladů na síťový provoz.

   Simulátor sady Visual Studio pro aplikace pro UWP umožňuje simulovat vlastnosti datového připojení rozhraní API pro informace o síti. Viz [spouštění aplikací pro UWP v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md)

- Nástroje **využití procesoru** vám můžou snížit zatížení procesoru, když je to způsobeno neúčinnými funkcemi. Viz [Analýza využití procesoru](../profiling/beginners-guide-to-performance-profiling.md).

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)