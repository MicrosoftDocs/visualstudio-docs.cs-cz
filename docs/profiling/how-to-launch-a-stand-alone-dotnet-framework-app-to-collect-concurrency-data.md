---
title: Příkazový řádek profileru – otevření klientské aplikace .NET, získání dat souběžnosti
description: Naučte se, jak pomocí nástrojů příkazového řádku sady Visual Studio Nástroje pro profilaci spustit samostatnou aplikaci .NET a shromažďovat data procesu a souběžnosti vláken.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 01356e2fe8693e39ef06fc1620cabbb2cb608a43
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883449"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: spuštění samostatné .NET Framework aplikace s profilerem za účelem shromáždění dat souběžnosti pomocí příkazového řádku
Toto téma popisuje způsob používání nástrojů příkazového řádku balíku nástrojů pro profilaci sady [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ke spuštění samostatné (klientské) aplikace rozhraní .NET Framework a shromažďování dat procesu a souběžnosti vláken.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 I když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, nesmí být profiler již připojen k aplikaci a musí být explicitně vypnut.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci .NET Framework s profilerem, použijte *VSPerfClrEnv.exe* k nastavení proměnných pro .NET Framework profilování. Pak použijete možnosti VSPerfCmd **/Start** a **/Lauch** k inicializaci profileru a spuštění aplikace. V jednom příkazovém řádku můžete zadat **/Start** a **/Lauch** a jejich příslušné možnosti. Můžete také přidat možnost **/globaloff** do příkazového řádku pro pozastavení sběru dat při spuštění cílové aplikace. Pak použijete **/GlobalOn** na samostatném příkazovém řádku ke spuštění shromažďování dat.

#### <a name="to-start-an-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: Concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:** `OutputFile` [ `Options` ]

   - Možnost [/Start](../profiling/start.md) inicializuje Profiler.

     | | |
     |-------------------------------------| - |
     | **/Start: souběžnost** | Umožňuje shromažďovat kolize prostředků a data spouštění vlákna. |
     | **/Start: Concurrency, resourceonly** | Umožňuje shromažďovat pouze data kolize prostředků. |
     | **/Start: Concurrency, threadonly** | Umožňuje shromažďovat pouze data spouštění vlákna. |

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Concurrency** můžete použít kteroukoli z následujících možností.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `domain\` ]`username` | Určuje volitelnou doménu a uživatelské jméno účtu, kterému má být udělen přístup k profileru. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.*ETL*). |

3. Spusťte cílovou aplikaci. Zadejte:

    **VSPerfCmd**  [/Lauch](../profiling/launch.md) **:** `AppName` [ `Options` ] [ `Sample Event` ]

    S možností **/Lauch** můžete použít kteroukoli z následujících možností.

   |Možnost|Popis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
   |[/Console](../profiling/console.md)|Spustí cílovou aplikaci příkazového řádku v samostatném okně.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

1. Následující páry *VSPerfCmd.exe* možností spustit a zastavit shromažďování dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** spustí shromažďování dat pro proces určený identifikátorem procesu ( `PID` ) nebo názvem procesu (ProcName). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat souběžnosti můžete zastavit zavřením profilované aplikace nebo vyvoláním možnosti **VSPerfCmd/detach** . Potom vyvoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/off.** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících postupů.

    - Zavřete cílovou aplikaci.

         -nebo-

    - Typ **VSPerfCmd/detach**

2. Ukončete profiler.

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také
- [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
