---
title: 'Příkazový řádek profileru: otevřít nativní klientskou aplikaci, získat data souběžnosti'
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
ms.sourcegitcommit: 0c3c4bd38455f7046c5c5a448eaaa5e407ad5bf4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76726032"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: spuštění samostatné nativní aplikace s profilerem za účelem shromáždění dat souběžnosti pomocí příkazového řádku
Toto téma popisuje, jak pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci spustit nativní samostatnou (klientskou) aplikaci a shromažďovat data o procesech a souběžnosti vláken.

 Relace profilace má následující části:

- Spuštění aplikace v profileru

- Řízení shromažďování dat

- Ukončuje se relace profilování.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci s profilerem, použijte možnosti [VSPerfCmd. exe](../profiling/vsperfcmd.md) **/Start** a **/Lauch** pro inicializaci profileru a spuštění aplikace. Můžete zadat **/Start** a **/Lauch** a jejich příslušné možnosti. Můžete také přidat **/globaloff** možnost pozastavit shromažďování dat na začátku cílové aplikace. Pak můžete pomocí **/GlobalOn** začít shromažďovat data.

#### <a name="to-start-an-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Na příkazovém řádku zadejte následující příkaz:

     [Nástroj VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/output:** `OutputFile` [`Options`]

     [/Output](../profiling/output.md) **:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).

     V následující tabulce můžete použít některou z možností **/start:concurrency** možnost.

    |Možnost|Popis|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Určuje čítač výkonu Windows má být shromážděn během profilování.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.|

2. Spusťte cílovou aplikaci zadáním:

     **VSPerfCmd**  [/Lauch](../profiling/launch.md) **:** `AppName` [`Options`]

     Můžete použít kteroukoli z možností v následující tabulce s možností **/Lauch** .

    |Možnost|Popis|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:** `Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
    |[/Console](../profiling/console.md)|Spustí cílovou aplikaci příkazového řádku v samostatném okně.|
    |[targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Určuje verzi modulu CLR (Common Language Runtime) pro profilaci, pokud aplikace načte více než jednu verzi modulu CLR.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd. exe* . Řízením sběru dat může shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností v následující tabulce spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví ( **/globaloff**) sběr dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí ( **/processon**) nebo zastaví ( **/processoff**) sběr dat pro proces, který ID procesu (`PID`) určuje.|
    |[/ attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces, který ID procesu (`PID`) nebo názvem procesu (*ProcName*) určuje. **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

- Můžete také použít **VSPerfCmd.exe**[/mark](../profiling/mark.md) možnost k vložení profilovací značky do datového souboru. **/Mark** příkaz přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze použít k filtrování dat v zobrazení data a sestavy profileru.

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování
 Chcete-li ukončit relaci profilování, profiler nesmí pokračovat ve shromažďování dat. Shromažďování dat souběžnosti můžete zastavit zavřením profilované aplikace nebo vyvoláním možnosti **VSPerfCmd/detach** . Poté je zapotřebí vyvolat **VSPerfCmd/Shutdown** možnost se profiler vypne a uzavře soubor dat profilování.

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování

1. Odpojte Profiler od cílové aplikace, a to tak, že ho zavřete nebo zadáte na příkazovém řádku tento příkaz:

     **Nástroj VSPerfCmd / odpojení**

2. Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)