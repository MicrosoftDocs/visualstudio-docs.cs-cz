---
title: Profiler pro nativní službu příkazového řádku profileru, získání dat časování
description: Naučte se používat nástroje příkazového řádku sady Visual Studio Nástroje pro profilaci ke shromažďování podrobných dat časování pro nativní službu C/C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 151811d07468c54232933c6c5b78ecee1391f7f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929144"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Postupy: Instrumentace nativní služby a shromažďování podrobných dat časování pomocí příkazového řádku profileru
Tento článek popisuje, jak používat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástroje příkazového řádku k instrumentaci nativní služby (C/C++) a shromažďování podrobných dat časování.

> [!NOTE]
> Pomocí metody instrumentace nelze profilovat službu, pokud po spuštění počítače nelze službu restartovat, například službu, která se spouští pouze při spuštění operačního systému.
>
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromažďovat podrobná data časování z nativní služby pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) k vygenerování instrumentované verze součásti. Potom nahraďte neinstrumentované verze služby pomocí instrumentované verze a ujistěte se, že je služba nakonfigurovaná tak, aby se spouštěla ručně. Pak spustíte Profiler.

 Po spuštění služby se data časování automaticky shromažďují do datového souboru. Během relace profilace můžete shromažďování dat pozastavit a obnovit.

 Chcete-li ukončit relaci profilování, vypněte službu a pak explicitně vypněte profiler.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

#### <a name="to-start-profiling-a-native-service"></a>Spuštění profilování nativní služby

1. Otevřete okno příkazového řádku.

2. Pomocí nástroje **VSInstr** vygenerujte instrumentované verze binárního souboru služby.

3. Nahraďte původní binární soubor pomocí instrumentované verze. Ve Správci řízení služeb systému Windows se ujistěte, že typ spuštění služby je nastaven na ruční.

4. Spusťte profiler. Zadejte:

    **VSPerfCmd** [/Start](../profiling/start.md) **: Trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Možnost **/Start: Trace** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění dat profilování (.*VSP*) soubor.

     Pomocí možnosti **/Start: Trace** můžete použít kteroukoli z následujících možností.

   > [!NOTE]
   > Možnosti **/User** a **/CrossSession** se obvykle vyžadují pro aplikace ASP.NET.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud aplikace ASP.NET běží v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Určuje počet sekund, po který se má čekat na inicializaci profileru, než vrátí chybu. Pokud `Interval` parametr není zadán, bude Profiler čekat po neomezenou dobu. Ve výchozím nastavení funkce **/Start** vrátí hodnotu hned. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit Profiler s pozastaveným shromažďováním dat, přidejte možnost **/globaloff** do příkazového řádku **/Start** . Obnovte profilování pomocí **/GlobalOn** . |
   | [/Counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru určeného v konfiguraci. Informace čítače jsou přidány do shromažďovaných dat v každé události profilace. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.*ETL*). |

5. Spusťte službu ze Správce řízení služeb.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je služba spuštěná, můžete použít možnosti *VSPerfCmd.exe* pro spuštění a zastavení zápisu dat do datového souboru profileru. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování služby.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/ThreadOn**) nebo zastaví shromažďování dat (**/ThreadOff**) pro vlákno určené ID vlákna ( `TID` ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zastavte službu, ve které je spuštěna instrumentovaná součást, a poté zavolejte možnost **VSPerfCmd**[/shutdown](../profiling/shutdown.md) , vypněte profiler a zavřete soubor dat profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zastavte službu ve Správci řízení služeb.

2. Vypněte profiler. Zadejte:

     **VSPerfCmd/shutdown**

3. Nahraďte instrumentované modul původní. V případě potřeby překonfigurujte typ spouštění služby.

## <a name="see-also"></a>Viz také
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
