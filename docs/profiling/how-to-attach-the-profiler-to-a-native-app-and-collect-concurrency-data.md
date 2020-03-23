---
title: Připojení profileru k nativní aplikaci a shromažďování dat souběžnosti
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 367c91035f5d37bd8b0c20f1df84c7a2ee2d487a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776924"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Postup: Připojení profileru k nativní samostatné aplikaci a shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku profilování připojit profiler ke spuštěné nativní (C/C++) samostatné aplikace a shromažďovat data tvrzení podprocesu.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Zatímco profiler je připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, profiler již nesmí být připojen k aplikaci a profiler musí být explicitně vypnut.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Připojení profileru ke spuštěné nativní aplikaci

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Připojení profileru ke spuštěné nativní aplikaci

1. Do příkazového řádku zadejte následující příkaz:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:souběžnost**

     Můžete použít některou z možností v následující tabulce s parametrem **/start:concurrency.**

    |Možnost|Popis|
    |------------|-----------------|
    |[/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain\`[ ]`Username`|Určuje volitelnou doménu a uživatelské jméno účtu, kterému má být udělen přístup k profileru.|
    |[/crosssession](../profiling/crosssession.md)|Umožňuje profilování procesů v jiných přihlašovacích relacích.|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilování.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500.|
    |[/události](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru.|

2. Připojte profiler k cílové aplikaci zadáním následujícího příkazu:

     **VSPerfCmd**[/attach](../profiling/attach.md) `PID` **:**{&#124;`ProcName`}  

     `PID`určuje ID procesu cílové aplikace. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízením shromažďování dat můžete shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Dvojice možností v následující tabulce spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování`PID`dat pro proces, který určuje ID procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces, který`PID`určuje ID procesu ( ) nebo název procesu (*ProcName).* **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace, která je profilována metodou vzorkování, můžete zastavit zavřením aplikace nebo vyvoláním možnosti **VSPerfCmd /detach.** Potom vyvolat **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Odpojte profiler od cílové aplikace jeho zavřením nebo zadáním následujícího příkazu:

     **VSPerfCmd /odpojit**

2. Vypněte profiler zadáním následujícího příkazu:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)
