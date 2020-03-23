---
title: 'Příkazový řádek Profiler: Otevřít nativní klientskou aplikaci, získat data souběžnosti'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb8baed0d9154c02f23738944de2d3e84b7402b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76726032"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Spuštění samostatné nativní aplikace s profilerem za účelem shromáždění dat souběžnosti pomocí příkazového řádku
Toto téma popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje profilování spustit nativní samostatnou (klientskou) aplikaci a shromažďovat data souběžnosti procesů a vláken.

 Relace profilování má následující části:

- Spuštění aplikace pomocí profileru

- Řízení sběru dat

- Ukončení relace profilování

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci s profilerem, použijte možnosti [VSPerfCmd.exe](../profiling/vsperfcmd.md)**/start** a **/launch** k inicializaci profileru a spuštění aplikace. Můžete zadat **/start** a **/launch** a jejich příslušné možnosti. Můžete také přidat **/globaloff** možnost pozastavit shromažďování dat na začátku cílové aplikace. Potom pomocí **/globalon** začít shromažďovat data.

#### <a name="to-start-an-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Do příkazového řádku zadejte následující příkaz:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:souběžnost /výstup:** `OutputFile` [`Options`]

     [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z možností v následující tabulce s parametrem **/start:concurrency.**

    |Možnost|Popis|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilování.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500.|
    |[/události](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru.|

2. Spusťte cílovou aplikaci zadáním:

     **VSPerfCmd**[/spuštění](../profiling/launch.md) `Options` **:** `AppName` [ ]  

     Můžete použít některou z možností v následující tabulce s **možností /launch.**

    |Možnost|Popis|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
    |[/konzole](../profiling/console.md)|Spustí aplikaci cílového příkazového řádku v samostatném okně.|
    |[/targetclr](../profiling/targetclr.md) **:**`CLRVersion`|Určuje verzi clr (COMMON Language runtime) pro profil, pokud aplikace načte více než jednu verzi CLR.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízením shromažďování dat můžete shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Dvojice možností v následující tabulce spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování`PID`dat pro proces, který určuje ID procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces, který`PID`určuje ID procesu ( ) nebo název procesu (*ProcName).* **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

- Můžete také použít **Možnost VSPerfCmd.exe**[/mark](../profiling/mark.md) vložit profilování značku do datového souboru. Příkaz **/mark** přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze filtrovat data v sestavách profileru a zobrazeních dat.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat souběžnosti můžete ukončit zavřením profilované aplikace nebo vyvoláním možnosti **VSPerfCmd /detach.** Potom vyvolat **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Odpojte profiler od cílové aplikace jeho zavřením nebo zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd /odpojit**

2. Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)