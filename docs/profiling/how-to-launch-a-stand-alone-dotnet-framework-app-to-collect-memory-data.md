---
title: Příkazový řádek profileru – otevření klientské .NET Framework aplikace, získání dat paměti
description: Naučte se používat Nástroje pro profilaci nástroje příkazového řádku sady Visual Studio ke spuštění .NET Framework samostatné aplikace a shromažďování dat o aktivitách paměti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: acfa657552cb070fe8b98ff4dc761ab6913a6c93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860812"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Postupy: spuštění samostatné .NET Framework aplikace s profilerem za účelem shromáždění dat paměti pomocí příkazového řádku
Toto téma popisuje, jak použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástroje příkazového řádku ke spuštění .NET Framework samostatné (klientské) aplikace a shromažďování dat paměti.

 Relace profilace má tři části:

- Spuštění aplikace pomocí profileru.

- Shromažďují se data profilace.

- Ukončuje se relace profilování.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci pomocí profileru, použijte možnosti **VSPerfCmd.exe/Start** a **/Lauch** pro inicializaci profileru a spuštění aplikace. Na jednom příkazovém řádku můžete zadat **/Start** a **/Lauch** a jejich příslušné možnosti.

 Můžete také přidat možnosti **/globaloff** pro pozastavení sběru dat na začátku cílové aplikace. Pak použijete **/GlobalOn** ke spuštění shromažďování dat.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

    **VSPerfCmd/Start: Sample/output:** `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md)**: Sample** inicializuje Profiler.

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít kteroukoli z následujících možností.

   | Možnost | Popis |
   | - | - |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |

3. Spusťte cílovou aplikaci. Zadejte:

    **VSPerfCmd**  [/Lauch](../profiling/launch.md) **:** `appName` **/GC:**{**alokace**&#124;**Doba života**} [ `Options` ]

   - [](../profiling/gc-vsperfcmd.md) `Keyword` Pro shromažďování dat .NET Framework paměti se vyžaduje možnost/GC:. Parametr klíčového slova určuje, zda shromažďovat data o přidělování paměti nebo shromažďovat data o životnosti objektů.

     |Klíčové slovo|Description|
     |-------------|-----------------|
     |**vyhrazen**|Shromažďovat pouze data o přidělování paměti.|
     |**platné**|Shromážděte jak přidělování paměti, tak data o životnosti objektů.|

     S možností **/Lauch** můžete použít kteroukoli z následujících možností.

   |Možnost|Popis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
   |[/Console](../profiling/console.md)|Spustí cílovou aplikaci příkazového řádku v samostatném okně.|
   |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL).|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Je-li cílová aplikace spuštěna, lze shromažďování dat řídit spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví sběrdat pro proces určený identifikátorem procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/Attach** začne shromažďovat data pro proces, který je určen `PID` (ID procesu). **/detach** zastaví sběr dat pro všechny procesy.|

- K vložení značky profilování do datového souboru můžete použít také možnost **VSPerfCmd.exe** [/Mark](../profiling/mark.md) . Příkaz **/Mark** Přidá identifikátor, časové razítko a volitelný uživatelsky definovaný textový řetězec. Značky lze použít k filtrování dat.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilových procesů a Profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilovaná pomocí metody vzorkování, ukončením aplikace nebo zavoláním možnosti **VSPerfCmd/detach** . Pak zavoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/off.** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

    - Zavřete cílovou aplikaci.

         -nebo-

    - Typ **VSPerfCmd/detach**

2. Vypněte profiler. Zadejte:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
