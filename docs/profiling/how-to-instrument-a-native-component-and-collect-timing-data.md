---
title: Služba příkazového řádku profileru – nativní komponenta instrumentace, získání časových údajů
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 9436487655e04649228a1bdb60c5d48138f13842
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85327829"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Postupy: instrumentace nativní samostatné součásti a shromažďování dat časování pomocí profileru z příkazového řádku
Toto téma popisuje, jak použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástroje příkazového řádku k instrumentaci nativní komponenty, jako je například C++.* exe* nebo. soubor *DLL* a shromažďování podrobných dat časování.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

Chcete-li shromažďovat podrobná data časování ze součásti pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) k vygenerování instrumentované verze součásti. Pak spustíte Profiler. Po spuštění instrumentované komponenty se data časování automaticky shromažďují do datového souboru. Během relace profilace můžete shromažďování dat pozastavit a obnovit.

 Chcete-li ukončit relaci profilování, zavřete cílovou aplikaci a pak explicitně vypněte profiler.

## <a name="start-the-profiling-session"></a>Spustit relaci profilace

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Spuštění profilování pomocí metody instrumentace

1. Otevřete okno příkazového řádku.

2. Pomocí nástroje **VSInstr** vygenerujte instrumentované verze cílové aplikace.

3. Spusťte profiler. Zadejte:

    **VSPerfCmd/Start: Trace/output:** `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md)**: Trace** inicializuje Profiler.

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Trace** můžete použít jednu nebo více z následujících možností.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilový proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud aplikace běží v jiné relaci. Identifikátor relace je uvedena ve sloupci **ID relace** na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Spustí Profiler s pozastaveným shromažďováním dat. Obnovte profilování pomocí [/GlobalOn](../profiling/globalon-and-globaloff.md) . |
   | [/Counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru, který je určen v `Config` . Informace čítače jsou přidány do dat, která jsou shromažďována při každé události profilace. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.* ETL*). |

4. Spusťte cílovou aplikaci obvyklým způsobem.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Je-li cílová aplikace spuštěna, lze shromažďování dat řídit spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví sběr **/processoff**dat pro proces určený identifikátorem procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/ThreadOn**) nebo zastaví shromažďování dat (**/ThreadOff**) pro vlákno určené identifikátorem vlákna ( `TID` ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, ukončete aplikaci, ve které je spuštěna instrumentovaná součást, a poté zavolejte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) a vypněte profiler a zavřete soubor dat profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete cílovou aplikaci.

2. Vypněte profiler. Zadejte:

     **VSPerfCmd/shutdown**

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
