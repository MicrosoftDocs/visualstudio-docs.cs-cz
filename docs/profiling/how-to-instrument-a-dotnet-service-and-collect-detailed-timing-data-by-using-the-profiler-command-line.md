---
title: Příkazového řádku profileru – instrumentace služby .NET, získání podrobných informací o časování
description: Naučte se používat Nástroje pro profilaci nástroje příkazového řádku sady Visual Studio ke shromažďování podrobných dat časování pro službu .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9f318fc979d4562c355a9613f67a351452b04ddc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942617"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Postupy: instrumentace služby .NET a shromažďování podrobných dat časování pomocí příkazového řádku profileru

Tento článek popisuje, jak pomocí nástrojů příkazového řádku sady Visual Studio Nástroje pro profilaci instrumentovat službu .NET Framework a shromažďovat podrobná data časování.

> [!NOTE]
> Pomocí metody instrumentace nelze profilovat službu, pokud po spuštění počítače nelze službu restartovat. taková služba se spustí pouze při spuštění operačního systému.
>
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.
>
> Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní postupy s nástroji pro profilaci z příkazového řádku. Viz [shromáždění dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Chcete-li shromažďovat podrobná data časování z .NET Framework služby pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) k vygenerování instrumentované verze komponenty. Potom nahraďte neinstrumentované verze služby pomocí instrumentované verze a ujistěte se, že je služba nakonfigurovaná tak, aby se spouštěla ručně. Použijte nástroj [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) pro inicializaci globálních proměnných profilování a pak restartujte hostitelský počítač. Pak spustíte Profiler.

Po spuštění služby se data časování automaticky shromažďují do datového souboru. Během relace profilace můžete shromažďování dat pozastavit a obnovit.

Chcete-li ukončit relaci profilování, vypněte službu a pak explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Otevřete okno příkazového řádku.

2. Pomocí nástroje **VSInstr** vygenerujte instrumentované verze binárního souboru služby.

3. Nahraďte původní binární soubor pomocí instrumentované verze. Ve Správci řízení služeb systému Windows se ujistěte, že typ spuštění služby je nastaven na ruční.

4. Inicializace proměnných prostředí profilování rozhraní .NET Framework. Zadejte:

     **VSPerfClrEnv/globaltraceon**

5. Restartujte počítač.

6. Otevřete okno příkazového řádku.

7. Spusťte profiler. Zadejte:

     **VSPerfCmd/Start: Trace/output:** `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md)**: Trace** inicializuje Profiler.

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění dat profilování (.*VSP*) soubor.

     S možností **/Start: Trace** můžete použít jednu z následujících možností.

     > [!NOTE]
     > Pro služby profilování jsou obvykle vyžadovány možnosti **/User** a **/CrossSession** .

     | Možnost | Popis |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilový proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows. |
     | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud aplikace běží v jiné relaci. ID relace je uvedeno ve sloupci **ID relace** na kartě **procesy** ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
     | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Určuje počet sekund, po který se má čekat na inicializaci profileru, než vrátí chybu. Pokud `Interval` parametr není zadán, bude Profiler čekat po neomezenou dobu. Ve výchozím nastavení funkce **/Start** vrátí hodnotu hned. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit Profiler s pozastaveným shromažďováním dat, přidejte možnost **/globaloff** do příkazového řádku **/Start** . Obnovte profilování pomocí **/GlobalOn** . |
     | [/Counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru určeného v konfiguraci. Informace čítače jsou přidány do shromažďovaných dat v každé události profilace. |
     | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
     | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.*ETL*). |

8. Spusťte službu ve Správci řízení služeb systému Windows.

## <a name="control-data-collection"></a>Řízení shromažďování dat

Když je služba spuštěná, můžete použít možnosti *VSPerfCmd.exe* pro spuštění a zastavení zápisu dat do datového souboru profileru. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování služby.

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/ThreadOn**) nebo zastaví shromažďování dat (**/ThreadOff**) pro vlákno určené ID vlákna ( `TID` ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování

Chcete-li ukončit relaci profilování, zastavte službu, ve které je spuštěna instrumentovaná součást, a poté zavolejte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) , vypněte profiler a zavřete soubor dat profilování. Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování.

Chcete-li použít nové nastavení prostředí, je nutné restartovat počítač.

1. Zastavte službu ve Správci řízení služeb.

2. Vypněte profiler. Zadejte:

     **VSPerfCmd/shutdown**

3. Po dokončení všech profilování vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv/globaloff**

4. Nahraďte instrumentované modul původní. V případě potřeby překonfigurujte typ spouštění služby.

5. Restartujte počítač.

## <a name="see-also"></a>Viz také

[Profilovací služby](../profiling/command-line-profiling-of-services.md) 
 [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
