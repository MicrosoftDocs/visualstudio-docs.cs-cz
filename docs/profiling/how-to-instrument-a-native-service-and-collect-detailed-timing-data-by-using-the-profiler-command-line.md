---
title: 'Příkazový řádek profileru: Nativní služba nástroje, získání časovacích dat'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: c738a5183a7708c967192cf201e38a4f9384710e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778866"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Postupy: Instrumentace nativní služby a shromažďování podrobných dat časování pomocí příkazového řádku profileru
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak používat nástroje příkazového řádku nástroje nástroje profilování (C/C++) služby a shromažďovat podrobná data časování.

> [!NOTE]
> Službu nelze profilovat pomocí metody instrumentace, pokud službu nelze restartovat po spuštění počítače, jako je služba, která se spustí pouze při spuštění operačního systému.
>
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat podrobná časovací data z nativní služby pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) ke generování instrumentované verze komponenty. Potom nahradit neinstrumented verzi služby s instrumentovanou verzí, ujistěte se, že služba je nakonfigurován a spustit ručně. Potom spustíte profiler.

 Při spuštění služby časování data se automaticky shromažďují do datového souboru. Shromažďování dat můžete pozastavit a obnovit během relace profilování.

 Chcete-li ukončit relaci profilování, vypněte službu a potom explicitně vypněte profiler.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

#### <a name="to-start-profiling-a-native-service"></a>Spuštění profilování nativní služby

1. Otevřete okno příkazového řádku.

2. Nástroj **VSInstr** slouží ke generování instrumentované verze binární služby.

3. Nahraďte původní binární soubor instrumentolou verzí. Ve Správci řízení služeb systému Windows zkontrolujte, zda je typ spuštění služby nastaven na ruční.

4. Spusťte profiler. Zadejte:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Možnost **/start:trace** inicializuje profiler.

   - Možnost **/output:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění profilovacích dat (.* vsp*).

     Můžete použít některou z následujících možností s **parametrem /start:trace.**

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro ASP.NET aplikace.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Určuje počet sekund čekání na inicializaci profileru, než vrátí chybu. Pokud `Interval` není zadán, profiler čeká neomezeně dlouho. Ve výchozím nastavení **/start** vrátí okamžitě. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit profiler s pozastavenou kolekcí dat, přidejte možnost **/globaloff** do příkazového řádku **/start.** Použití **/globalon** obnovit profilování. |
   | [/counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru určeného v konfiguraci. Informace o čítači jsou přidány k datům shromážděným při každé události profilování. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

5. Spusťte službu ze Správce řízení služeb.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je služba spuštěna, můžete použít *vsPerfCmd.exe* možnosti spustit a zastavit zápis dat do datového souboru profileru. Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí služby.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat`TID`pro vlákno určené ID vlákna ( ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zastavte službu, která je spuštěna součást s přístrojovou součástí, a potom zavolejte možnost **VSPerfCmd**[/shutdown,](../profiling/shutdown.md) vypněte profiler a zavřete datový soubor profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zastavte službu ze Správce řízení služeb.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd /vypnutí**

3. Vyměňte přístrojový modul za originální. V případě potřeby překonfigurujte typ spuštění služby.

## <a name="see-also"></a>Viz také
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
