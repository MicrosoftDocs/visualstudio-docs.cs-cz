---
title: 'Příkazový řádek Profiler: Otevřít klientskou aplikaci .NET, získat data souběžnosti'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4a52c65f8a53d62edde42c26fafef9940046ba5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775390"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Postup: Spuštění samostatné aplikace rozhraní .NET Framework s profilem pro shromažďování dat souběžnosti pomocí příkazového řádku
Toto téma popisuje způsob používání nástrojů příkazového řádku balíku nástrojů pro profilaci sady [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ke spuštění samostatné (klientské) aplikace rozhraní .NET Framework a shromažďování dat procesu a souběžnosti vláken.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Zatímco profiler je připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, profiler již nesmí být připojen k aplikaci a profiler musí být explicitně vypnut.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci rozhraní .NET Framework s profilerem, použijte *vsperfClrEnv.exe* k nastavení proměnných profilování rozhraní .NET Framework. Potom použijte VSPerfCmd **/start** a **/launch** možnosti inicializovat Profiler a spustit aplikaci. Můžete zadat **/start** a **/launch** a jejich příslušné možnosti na jednom příkazovém řádku. Můžete také přidat **/globaloff** možnost příkazového řádku pozastavit shromažďování dat při spuštění cílové aplikace. Potom pomocí **/globalon** na samostatném příkazovém řádku začít shromažďovat data.

#### <a name="to-start-an-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md) inicializuje profiler.

     | | |
     |-------------------------------------| - |
     | **/start:souběžnost** | Umožňuje shromažďovat kolize prostředků a data spouštění vlákna. |
     | **/start:souběžnost,pouze prostředek** | Umožňuje shromažďovat pouze data kolize prostředků. |
     | **/start:souběžnost,pouze podproces** | Umožňuje shromažďovat pouze data spouštění vlákna. |

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:concurrency.**

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`domain\`[ ]`username` | Určuje volitelnou doménu a uživatelské jméno účtu, kterému má být udělen přístup k profileru. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

3. Spusťte cílovou aplikaci. Zadejte:

    **VSPerfCmd**[/spuštění](../profiling/launch.md) `Options` **:** `AppName` `Sample Event`[ ] [ ]  

    S možností **/launch** můžete použít některou z následujících možností.

   |Možnost|Popis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
   |[/konzole](../profiling/console.md)|Spustí aplikaci cílového příkazového řádku v samostatném okně.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Určuje verzi běžného jazyka runtime (CLR) pro profil, pokud je v aplikaci načtena více než jedna verze runtime.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

1. Následující dvojice možností *VSPerfCmd.exe* spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces určený ID procesu (`PID`) nebo název procesu (ProcName). **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat souběžnosti můžete ukončit zavřením profilované aplikace nebo vyvoláním možnosti **VSPerfCmd /detach.** Potom vyvolat **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Jedním z následujících akcí odpojte profiler od cílové aplikace.

    - Zavřete cílovou aplikaci.

         -nebo-

    - Typ **VSPerfCmd /detach**

2. Ukončete profiler.

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také
- [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
