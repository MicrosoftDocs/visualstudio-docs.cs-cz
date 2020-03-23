---
title: 'Příkazový řádek profileru: Služba Instrument .NET, získání podrobností o časování'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: af801d2b30c48deb1a88800f67ff4d3efef412b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778892"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Postup: Instrumentujte službu .NET a shromažďujte podrobná časovací data pomocí příkazového řádku profileru

Tento článek popisuje, jak používat nástroje příkazového řádku Nástroje profilování visual studio k instrumentaci služby rozhraní .NET Framework a ke shromažďování podrobných časovacích dat.

> [!NOTE]
> Službu nelze profilovat pomocí metody instrumentace, pokud službu nelze restartovat po spuštění počítače, jako je služba, která se spustí pouze při spuštění operačního systému.
>
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.
>
> Přidání dat interakce vrstvy do spuštění profilování vyžaduje specifické postupy s nástroji profilování příkazového řádku. Viz [Shromáždit data interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Chcete-li shromažďovat podrobná časovací data ze služby rozhraní .NET Framework pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) ke generování instrumentované verze komponenty. Potom nahradit neinstrumented verzi služby s instrumentovanou verzí, ujistěte se, že služba je nakonfigurován a spustit ručně. Nástroj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) slouží k inicializaci proměnných prostředí globálního profilování a restartování hostitelského počítače. Potom spustíte profiler.

Při spuštění služby časování data se automaticky shromažďují do datového souboru. Shromažďování dat můžete pozastavit a obnovit během relace profilování.

Chcete-li ukončit relaci profilování, vypněte službu a potom explicitně vypněte profiler. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Otevřete okno příkazového řádku.

2. Nástroj **VSInstr** slouží ke generování instrumentované verze binární služby.

3. Nahraďte původní binární soubor instrumentolou verzí. Ve Správci řízení služeb systému Windows zkontrolujte, zda je typ spuštění služby nastaven na ruční.

4. Inicializace proměnných prostředí profilování rozhraní .NET Framework. Zadejte:

     **VSPerfClrEnv /globaltraceon**

5. Restartujte počítač.

6. Otevřete okno příkazového řádku.

7. Spusťte profiler. Zadejte:

     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:trace** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění profilovacích dat (.* vsp*).

     S možností **/start:trace** můžete použít některou z následujících možností.

     > [!NOTE]
     > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro profilování služeb.

     | Možnost | Popis |
     | - | - |
     | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows. |
     | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. ID relace je uvedeno ve **sloupci ID relace** na kartě **Procesy** ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
     | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Určuje počet sekund čekání na inicializaci profileru, než vrátí chybu. Pokud `Interval` není zadán, profiler čeká neomezeně dlouho. Ve výchozím nastavení **/start** vrátí okamžitě. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit profiler s pozastavenou kolekcí dat, přidejte možnost **/globaloff** do příkazového řádku **/start.** Použití **/globalon** obnovit profilování. |
     | [/counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru určeného v konfiguraci. Informace o čítači jsou přidány k datům shromážděným při každé události profilování. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
     | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

8. Spusťte službu ze Správce řízení služeb systému Windows.

## <a name="control-data-collection"></a>Řízení shromažďování dat

Když je služba spuštěna, můžete použít *vsPerfCmd.exe* možnosti spustit a zastavit zápis dat do datového souboru profileru. Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí služby.

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat`TID`pro vlákno určené ID vlákna ( ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování

Chcete-li ukončit relaci profilování, zastavte službu, která je spuštěna součást s přístrojovou součástí, a potom zavolejte možnost **VSPerfCmd** [/shutdown,](../profiling/shutdown.md) vypněte profiler a zavřete datový soubor profilování. Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování.

Chcete-li použít nové nastavení prostředí, je nutné restartovat počítač.

1. Zastavte službu ze Správce řízení služeb.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd /vypnutí**

3. Po dokončení všech profilování zrušte zaškrtnutí proměnných prostředí profilování. Zadejte:

     **VSPerfClrEnv /globaloff**

4. Vyměňte přístrojový modul za originální. V případě potřeby překonfigurujte typ spuštění služby.

5. Restartujte počítač.

## <a name="see-also"></a>Viz také

[Profile services](../profiling/command-line-profiling-of-services.md)Zobrazení[dat metody instrumentace profilů](../profiling/instrumentation-method-data-views.md) 

