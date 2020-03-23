---
title: 'Příkazový řádek Profileru: Spusťte samostatnou aplikaci, získejte statistiky aplikací'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fb6228592115091dc538dbe59c227a180e75aa10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775412"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: Spuštění samostatné aplikace s profilerem a shromáždění statistik aplikace pomocí příkazového řádku
Toto téma popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje profilování spustit samostatnou (klientskou) aplikaci a shromažďovat statistiky výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Přidání dat interakce vrstvy do spuštění profilování vyžaduje specifické postupy s nástroji profilování příkazového řádku. Viz [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu k proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu. Profilování nástrojů můžete spustit v počítači, kde je nainstalována Visual Studio z příkazového okna sady Visual Studio.

1. Pokud používáte nástroje profilování v počítači, ve kterém je nainstalována sada Visual Studio příkaz okno nastaví správné cesty. V nabídce **Nástroje** zvolte **příkazový řádek VS.**

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci pomocí profileru, použijte možnosti VSPerfCmd **/start** a **/launch** k inicializaci profileru a spuštění aplikace. Můžete zadat **/start** a **/launch** a jejich příslušné možnosti na jednom příkazovém řádku.

 Můžete také přidat **/globaloff** možnost pozastavit shromažďování dat na začátku cílové aplikace. Potom pomocí **/globalon** začít shromažďovat data.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Spuštění aplikace pomocí profileru

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:sample** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:sample.**

   | Možnost | Popis |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

3. Spusťte cílovou aplikaci. Typ:**VSPerfCmd /launch:** `appName` [`Options`] [`Sample Event`]

    S možností **/launch** můžete použít jednu nebo více z následujících možností.

   |Možnost|Popis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
   |[/konzole](../profiling/console.md)|Spustí aplikaci cílového příkazového řádku v samostatném okně.|

    Ve výchozím nastavení jsou data o výkonu vzorkována každých 10 000 000 nezastavených cyklů hodin procesoru. To je přibližně jednou za 10 sekund na procesoru 1GHz. Můžete zadat jednu z následujících možností pro změnu intervalu cyklu hodin nebo pro určení jiné události vzorkování.

   |Ukázková událost|Popis|
   |------------------|-----------------|
   |[/časovač](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nezastavených hodinových `Interval`cyklů určených aplikací .|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Změní událost vzorkování na chyby stránky. Pokud `Interval` je zadán, nastaví počet chyb stránky mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[**:**`Interval`]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (syscalls). Pokud `Interval` je zadán, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Změní událost vzorkování a interval na čítač `Config`výkonu procesoru a interval, které jsou určeny v .|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**  `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces `PID` určený názvem nebo (ProcName). **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí být připojen k žádnému procesu profilovaného a profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilována pomocí metody vzorkování zavřením aplikace nebo voláním **možnosti VSPerfCmd /detach.** Potom volání **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Proveďte jeden z následujících kroků, chcete-li odpojit profiler od cílové aplikace:

    - Zavřete cílovou aplikaci.

         -nebo-

    - Typ **VSPerfCmd /detach**

2. Vypněte profileru. Zadejte:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
