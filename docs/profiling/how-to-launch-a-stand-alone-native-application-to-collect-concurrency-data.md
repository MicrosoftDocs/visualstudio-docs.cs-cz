---
title: Příkazový řádek profileru – otevřít nativní klientskou aplikaci, získat data souběžnosti
description: Naučte se používat Nástroje pro profilaci nástroje příkazového řádku sady Visual Studio ke spuštění nativní samostatné klientské aplikace a shromažďování dat o souběžnosti procesů a vláken.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: da71c5bb714a50c70cbefcd2a2987a48c14eb4b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928963"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Spuštění samostatné nativní aplikace s profilerem za účelem shromáždění dat souběžnosti pomocí příkazového řádku
Toto téma popisuje, jak použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástroje příkazového řádku ke spuštění nativní samostatné (klientské) aplikace a shromáždění dat procesu a souběžnosti vláken.

 Relace profilace má následující části:

- Spuštění aplikace v profileru

- Řízení shromažďování dat

- Ukončuje se relace profilování.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci s profilerem, použijte možnosti [VSPerfCmd.exe](../profiling/vsperfcmd.md) **/Start** a **/Lauch** pro inicializaci profileru a spuštění aplikace. Můžete zadat **/Start** a **/Lauch** a jejich příslušné možnosti. Můžete také přidat možnost **/globaloff** pro pozastavení sběru dat na začátku cílové aplikace. Pak můžete pomocí **/GlobalOn** začít shromažďovat data.

#### <a name="to-start-an-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Do příkazového řádku zadejte následující příkaz:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start:/Output souběžného zpracování:** `OutputFile` [ `Options` ]

     Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Můžete použít kteroukoli z možností v následující tabulce s možností **/Start: Concurrency** .

    |Možnost|Popis|
    |------------|-----------------|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilace.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL).|

2. Spusťte cílovou aplikaci zadáním:

     **VSPerfCmd**  [/Lauch](../profiling/launch.md) **:** `AppName` [ `Options` ]

     Můžete použít kteroukoli z možností v následující tabulce s možností **/Lauch** .

    |Možnost|Popis|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
    |[/Console](../profiling/console.md)|Spustí cílovou aplikaci příkazového řádku v samostatném okně.|
    |[/targetclr](../profiling/targetclr.md) **:**`CLRVersion`|Určuje verzi modulu CLR (Common Language Runtime) pro profilaci, pokud aplikace načte více než jednu verzi modulu CLR.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěna, lze shromažďování dat řídit spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízením shromažďování dat můžete shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Dvojice možností v následující tabulce začátek a zastavení shromažďování dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces, který určuje ID procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** začne shromažďovat data pro proces, který určuje ID procesu ( `PID` ) nebo název procesu (*ProcName*). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

- K vložení značky profilování do datového souboru můžete použít také možnost **VSPerfCmd.exe** [/Mark](../profiling/mark.md) . Příkaz **/Mark** Přidá identifikátor, časové razítko a volitelný uživatelsky definovaný textový řetězec. Značky lze použít k filtrování dat v sestavách a zobrazení dat profileru.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat souběžnosti můžete zastavit zavřením profilované aplikace nebo vyvoláním možnosti **VSPerfCmd/detach** . Potom vyvoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Odpojte Profiler od cílové aplikace, a to tak, že ho zavřete nebo zadáte na příkazovém řádku tento příkaz:

     **VSPerfCmd/detach**

2. Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)