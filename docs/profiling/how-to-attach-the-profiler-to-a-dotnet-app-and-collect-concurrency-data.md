---
title: Připojení profileru k .NET ke shromažďování dat souběžnosti
description: Naučte se získat data o souběžnosti procesů a vláken pomocí nástrojů příkazového řádku sady Visual Studio Nástroje pro profilaci k připojení profileru k běžící .NET Framework aplikaci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4d584d9d6cecc4d5df0f3c32172d4aeec9c02c97
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801130"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru k .NET Framework samostatné aplikace ke shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů příkazového řádku připojit profiler ke spuštěné .NET Framework samostatné (klientské) aplikaci a shromažďovat data o procesech a souběžnosti vláken.

> [!NOTE]
> Informace o tom, jak získat cestu k nástrojům pro profilaci, najdete v tématu [Návod: použití rozhraní API profileru](../profiling/walkthrough-using-profiler-apis.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu. Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

 I když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, nesmí být profiler již připojen k aplikaci a musí být explicitně vypnut.

## <a name="attach-the-profiler"></a>Připojení profileru

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru k běžící .NET Framework aplikaci

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start:/Output souběžného zpracování:** `OutputFile` [ `Options` ]

     Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Concurrency** můžete použít kteroukoli z následujících možností.

    |Možnost|Popis|
    |------------|-----------------|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilace.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL).|

3. Spusťte cílovou aplikaci obvyklým způsobem.

4. Připojte profiler k cílové aplikaci. Zadejte:

     **VSPerfCmd/attach:** `PID` [**/LineOff**] [**/targetclr:** `Version` ]

    - `PID` Určuje ID procesu cílové aplikace. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    - [/LineOff](../profiling/lineoff.md) zakáže shromažďování dat o číslech řádků.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry *VSPerfCmd.exe* možností spustit a zastavit shromažďování dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** spustí shromažďování dat pro proces určený identifikátorem procesu ( `PID` ) nebo názvem procesu (ProcName). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace profilované s metodou souběžnosti můžete zastavit ukončením aplikace nebo vyvoláním možnosti **VSPerfCmd/detach** . Potom vyvoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/off.** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících postupů.

    - Typ **VSPerfCmd/detach**

         -nebo-

    - Zavřete cílovou aplikaci.

2. Vypněte profiler. Zadejte:

     VSPerfCmd[/shutdown](../profiling/shutdown.md)
