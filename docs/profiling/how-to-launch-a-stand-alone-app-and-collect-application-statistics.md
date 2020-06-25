---
title: Příkazový řádek profileru – spuštění samostatné aplikace, získání statistiky aplikace
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 96838b622171aa3e313dd8c241a5e316f72ff7b2
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85327762"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: Spuštění samostatné aplikace s profilerem a shromáždění statistik aplikace pomocí příkazového řádku
Toto téma popisuje, jak použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástroje příkazového řádku ke spuštění samostatné (klientské) aplikace a shromáždění statistik výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní postupy s nástroji pro profilaci z příkazového řádku. Viz [shromáždění dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) .

 Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do příkazu samotného. Nástroje pro profilaci můžete spustit na počítači, kde je nainstalována aplikace Visual Studio z příkazového okna sady Visual Studio.

1. Pokud používáte nástroje pro profilaci na počítači, kde je nainstalována sada Visual Studio, příkazové okno sady Visual Studio nastaví správné cesty. V nabídce **nástroje** klikněte na **příkaz vs Command Prompt** .

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci pomocí profileru, použijte možnosti VSPerfCmd **/Start** a **/Lauch** pro inicializaci profileru a spuštění aplikace. V jednom příkazovém řádku můžete zadat **/Start** a **/Lauch** a jejich příslušné možnosti.

 Můžete také přidat možnost **/globaloff** pro pozastavení sběru dat na začátku cílové aplikace. Pak použijete **/GlobalOn** ke spuštění shromažďování dat.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

    **VSPerfCmd/Start: Sample/output:** `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md)**: Sample** inicializuje Profiler.

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile`Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít kteroukoli z následujících možností.

   | Možnost | Popis |
   | - | - |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.* ETL*). |

3. Spusťte cílovou aplikaci. Zadejte:**VSPerfCmd/Lauch:** `appName` [ `Options` ] [ `Sample Event` ]

    S možností **/Lauch** můžete použít jednu nebo více z následujících možností.

   |Možnost|Popis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
   |[/Console](../profiling/console.md)|Spustí cílovou aplikaci příkazového řádku v samostatném okně.|

    Ve výchozím nastavení jsou data o výkonu Navzorkovaná každých 10 000 000 hodinových cyklů procesoru. To je přibližně jednou za 10 sekund na 1GHz procesoru. Můžete určit jednu z následujících možností pro změnu intervalu hodinových cyklů nebo zadat jinou událost vzorkování.

   |Ukázková událost|Popis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů, které jsou určeny pomocí `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Změní událost vzorkování na chyby stránkování. Pokud `Interval` je zadaný, nastaví počet chyb stránek mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[**:** `Interval` ]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (voláním). Pokud `Interval` je zadáno, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Změní událost vzorkování a interval na čítač výkonu procesoru a interval, který je určen v `Config` .|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Je-li cílová aplikace spuštěna, lze shromažďování dat řídit spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**  `PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** spustí shromažďování dat pro proces určený `PID` názvem procesu nebo (ProcName). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, nesmí být profiler připojen k žádnému profilované procesu a Profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilovaná pomocí metody vzorkování, ukončením aplikace nebo zavoláním možnosti **VSPerfCmd/detach** . Potom zavoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/off.** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

    - Zavřete cílovou aplikaci.

         -nebo-

    - Typ **VSPerfCmd/detach**

2. Vypněte profiler. Zadejte:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
