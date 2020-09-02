---
title: Připojení profileru k nativní aplikaci a shromažďování dat souběžnosti
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: dcc125f795a29f53abb07920aa11c9a5e6ee966b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329517"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru k nativní samostatné aplikaci a shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů příkazového řádku připojit profiler ke spuštěné samostatné aplikaci (C/C++) a shromažďovat data kolize vláken.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 I když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, nesmí být profiler již připojen k aplikaci a musí být explicitně vypnut.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Připojení profileru k běžící nativní aplikaci

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Připojení profileru k běžící nativní aplikaci

1. Do příkazového řádku zadejte následující příkaz:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: Concurrency**

     Můžete použít kteroukoli z možností v následující tabulce s možností **/Start: Concurrency** .

    |Možnost|Popis|
    |------------|-----------------|
    |[/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`Username`|Určuje volitelnou doménu a uživatelské jméno účtu, kterému má být udělen přístup k profileru.|
    |[/CrossSession](../profiling/crosssession.md)|Umožňuje profilování procesů v jiných přihlašovacích relacích.|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilace.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL).|

2. Připojte profiler k cílové aplikaci zadáním následujícího příkazu:

     **VSPerfCmd**  [/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` }

     `PID` Určuje ID procesu cílové aplikace. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízením shromažďování dat můžete shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Dvojice možností v následující tabulce začátek a zastavení shromažďování dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces, který určuje ID procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** začne shromažďovat data pro proces, který určuje ID procesu ( `PID` ) nebo název procesu (*ProcName*). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace, která je profilovaná pomocí metody vzorkování, můžete zastavit ukončením aplikace nebo vyvoláním možnosti **VSPerfCmd/detach** . Potom vyvoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Odpojte Profiler od cílové aplikace, a to tak, že ho zavřete nebo zadáte následující příkaz:

     **VSPerfCmd/detach**

2. Vypněte profiler zadáním následujícího příkazu:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
