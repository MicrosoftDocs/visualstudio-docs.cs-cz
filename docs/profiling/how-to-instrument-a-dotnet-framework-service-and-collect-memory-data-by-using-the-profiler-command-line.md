---
title: Profiler příkazového řádku – instrumentace služby .NET, získání dat paměti
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 8ff00f9a8a79dadc0cc037b707db057610b904e8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809606"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postupy: Instrumentace služby rozhraní .NET Framework a shromažďování dat paměti pomocí příkazového řádku profileru

Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů příkazového řádku instrumentovat službu .NET Framework a shromažďovat data o využití paměti. Můžete shromažďovat data o přidělování paměti, nebo můžete shromažďovat jak přidělování paměti, tak data o životnosti objektů.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Pomocí metody instrumentace nelze profilovat službu, pokud po spuštění počítače nelze službu restartovat, například službu, která se spouští při spuštění operačního systému.
>
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

## <a name="start-the-profiling-session"></a>Spustit relaci profilace
 Chcete-li shromažďovat údaje o výkonu z .NET Framework služby, použijte nástroj [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí a nástroje [VSInstr.exe](../profiling/vsinstr.md) k vytvoření instrumentované kopie binárního souboru služby.

 Počítač, který je hostitelem služby, se musí restartovat, aby se nakonfiguroval pro profilování. Službu musíte také spustit ručně ze Správce řízení služeb. Poté spusťte Profiler a potom spusťte službu .NET Framework.

 Po spuštění instrumentované komponenty jsou data paměti automaticky shromažďována do datového souboru. Během relace profilace můžete shromažďování dat pozastavit a obnovit.

 Chcete-li ukončit relaci profilování, zavřete službu a explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Zahájení profilování služby .NET Framework

1. Otevřete okno příkazového řádku.

2. Pomocí nástroje **VSInstr** vygenerujte instrumentované verze binárního souboru služby.

3. Pomocí Správce řízení služeb nahraďte původní binární soubor pomocí instrumentované verze. Ujistěte se, že typ spouštění služby je nastavený na ruční.

4. Inicializujte proměnné prostředí pro profilování. Zadejte:

    **VSPerfCLREnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** a **/globaltracegclife** umožňují shromažďování dat o přidělení paměti a životnosti objektů.

       |Možnost|Popis|
       |------------|-----------------|
       |**/globaltracegc**|Shromažďuje pouze data o přidělování paměti.|
       |**/globaltracegclife**|Shromažďuje data o přidělování paměti a životnosti objektů.|

5. Restartujte počítač.

6. Otevřete okno příkazového řádku.

7. Spusťte profiler. Zadejte:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Možnost **/Start: spor** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít kteroukoli z následujících možností.

   > [!NOTE]
   > Pro služby jsou obvykle vyžadovány možnosti **/User** a **/CrossSession** .

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě procesy ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud aplikace ASP.NET běží v jiné relaci. ID relace je uvedeno ve sloupci **ID relace** na kartě **procesy** ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Určuje počet sekund, po který se má čekat na inicializaci profileru, než vrátí chybu. Pokud `Interval` parametr není zadán, bude Profiler čekat po neomezenou dobu. Ve výchozím nastavení funkce **/Start** vrátí hodnotu hned. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit Profiler s pozastaveným shromažďováním dat, přidejte možnost **/globaloff** do příkazového řádku **/Start** . Obnovte profilování pomocí **/GlobalOn** . |
   | [/Counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru určeného v konfiguraci. Informace čítače jsou přidány do shromažďovaných dat v každé události profilace. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.* ETL*). |

8. V případě potřeby službu spusťte.

9. Připojte profiler ke službě. Zadejte:

     **VSPerfCmd/attach:** `PID`&#124;`ProcessName`

    - Zadejte ID procesu nebo název procesu služby. ID procesů a názvy všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je služba spuštěná, můžete shromažďování dat řídit spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/ThreadOn**) nebo zastaví shromažďování dat (**/ThreadOff**) pro vlákno určené ID vlákna ( `TID` ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, ukončete aplikaci, ve které je spuštěna instrumentovaná součást, a poté spusťte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) a vypněte profiler a zavřete soubor dat profilování. Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zastavte službu ve Správci řízení služeb.

2. Vypněte profiler. Zadejte:

     **VSPerfCmd/shutdown**

3. Po dokončení všech profilování vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv/globaloff**

     Nahraďte instrumentované modul původní. V případě potřeby překonfigurujte typ spouštění služby.

4. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
