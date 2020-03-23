---
title: 'Příkazový řádek profileru: Služba Instrument .NET, získání paměťových dat'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 8697f1451e3d528ff27beb2467ff7758e04267cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775493"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postupy: Instrumentace služby rozhraní .NET Framework a shromažďování dat paměti pomocí příkazového řádku profileru
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje nástroje nástroje .NET Framework a shromažďovat data o využití paměti. Můžete shromažďovat data přidělení paměti nebo můžete shromažďovat data přidělení paměti i data životnosti objektu.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Službu nelze profilovat pomocí metody instrumentace, pokud službu nelze restartovat po spuštění počítače, jako je služba, která se spustí při spuštění operačního systému.
>
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

## <a name="start-the-profiling-session"></a>Spuštění relace profilování
 Chcete-li shromažďovat data o výkonu ze služby .NET Framework, použijte nástroj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí a nástroj [VSInstr.exe](../profiling/vsinstr.md) k vytvoření instrumentované kopie binárního souboru služby.

 Počítač, který je hostitelem služby, musí být restartován, aby ji nakonfiguroval pro profilování. Službu je také nutné spustit ručně ze Správce řízení služeb. Potom spusťte profiler a potom spusťte službu rozhraní .NET Framework.

 Při spuštění instrumentované součásti jsou data paměti automaticky shromažďována do datového souboru. Shromažďování dat můžete pozastavit a obnovit během relace profilování.

 Chcete-li ukončit relaci profilování, zavřete službu a explicitně vypněte profiler. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Chcete-li zahájit profilování služby rozhraní .NET Framework

1. Otevřete okno příkazového řádku.

2. Nástroj **VSInstr** slouží ke generování instrumentované verze binární služby.

3. Pomocí Správce řízení služeb nahraďte původní binární soubor instrumentolou verzí. Ujistěte se, že typ spuštění služby je nastaven a manuální.

4. Inicializovat proměnné prostředí profilování. Zadejte:

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** a **/globaltracegclife** umožňují shromažďování dat přidělení paměti a životnosti objektu.

       |Možnost|Popis|
       |------------|-----------------|
       |**/globaltracegc**|Shromažďuje pouze data přidělení paměti.|
       |**/globaltracegclife**|Shromažďuje data přidělení paměti a životnosti objektu.|

5. Restartujte počítač.

6. Otevřete okno příkazového řádku.

7. Spusťte profiler. Zadejte:

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **Možnost /start: contention** inicializuje profiler.

   - Možnost **/output:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:sample.**

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro služby.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě Procesy ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. ID relace je uvedeno ve **sloupci ID relace** na kartě **Procesy** ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Určuje počet sekund čekání na inicializaci profileru, než vrátí chybu. Pokud `Interval` není zadán, profiler čeká neomezeně dlouho. Ve výchozím nastavení **/start** vrátí okamžitě. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit profiler s pozastavenou kolekcí dat, přidejte možnost **/globaloff** do příkazového řádku **/start.** Použití **/globalon** obnovit profilování. |
   | [/counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru určeného v konfiguraci. Informace o čítači jsou přidány k datům shromážděným při každé události profilování. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

8. V případě potřeby spusťte službu.

9. Připojte profiler ke službě. Zadejte:

     **VSPerfCmd /připojit:** `PID`&#124;`ProcessName`

    - Zadejte ID procesu nebo název procesu služby. ID procesů a názvy všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 V době, kdy je služba spuštěna, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat`TID`pro vlákno určené ID vlákna ( ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zavřete aplikaci, která je spuštěna součást s přístrojovou součástí, a spusťte možnost **VSPerfCmd** [/shutdown,](../profiling/shutdown.md) chcete-li vypnout profiler a zavřít datový soubor profilování. Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zastavte službu ze Správce řízení služeb.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd /vypnutí**

3. Po dokončení všech profilování zrušte zaškrtnutí proměnných prostředí profilování. Zadejte:

     **VSPerfClrEnv /globaloff**

     Vyměňte přístrojový modul za originální. V případě potřeby překonfigurujte typ spuštění služby.

4. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
