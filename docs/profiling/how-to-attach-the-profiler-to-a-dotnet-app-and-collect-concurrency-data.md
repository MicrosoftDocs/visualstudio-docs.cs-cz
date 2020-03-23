---
title: Připojení profileru k aplikaci .NET ke shromažďování dat souběžnosti | Dokumenty společnosti Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f44213bf7356d499f852b53335698c701bf03eb7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779152"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Postup: Připojení profileru k samostatné aplikaci rozhraní .NET Framework ke shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje profilování připojit profiler ke spuštěné samostatné (klientské) aplikaci rozhraní .NET Framework a shromažďovat data souběžnosti procesů a vláken.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, [přečtěte si návod: Použití souborů API profileru](../profiling/walkthrough-using-profiler-apis.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu. Další informace naleznete [v tématu Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

 Zatímco profiler je připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, profiler již nesmí být připojen k aplikaci a profiler musí být explicitně vypnut.

## <a name="attach-the-profiler"></a>Připojte profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru ke spuštěné aplikaci rozhraní .NET Framework

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:souběžnost /výstup:** `OutputFile` [`Options`]

     [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:concurrency.**

    |Možnost|Popis|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilování.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms.|
    |[/události](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru.|

3. Spusťte cílovou aplikaci typickým způsobem.

4. Připojte profiler k cílové aplikaci. Zadejte:

     **VSPerfCmd /attach:** `PID` [**/lineoff**] [**/targetclr:**`Version`]

    - `PID`určuje ID procesu cílové aplikace. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    - [/lineoff](../profiling/lineoff.md) zakáže shromažďování dat čísla řádku.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` určuje verzi clr (COMMON Language runtime) pro profil, když je v aplikaci načtena více než jedna verze runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností *VSPerfCmd.exe* spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces určený ID procesu (`PID`) nebo název procesu (ProcName). **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace profilované metodou souběžnosti můžete zastavit zavřením aplikace nebo vyvoláním možnosti **VSPerfCmd /detach.** Potom vyvolat **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Jedním z následujících akcí odpojte profiler od cílové aplikace.

    - Typ **VSPerfCmd /detach**

         -nebo-

    - Zavřete cílovou aplikaci.

2. Vypněte profileru. Zadejte:

     VSPerfCmd[/vypnutí](../profiling/shutdown.md)
