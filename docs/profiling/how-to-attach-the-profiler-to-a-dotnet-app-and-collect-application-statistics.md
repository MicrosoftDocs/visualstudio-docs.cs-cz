---
title: Připojit profiler k samostatné aplikaci rozhraní .NET Framework; získat statistiky aplikací
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9084f2d1dd784172735c66d38da785dffb74d82c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779178"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru k samostatné aplikaci .NET Framework a shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje profilování připojit profiler ke spuštěné samostatné (klientské) aplikaci rozhraní .NET Framework a shromažďovat statistiky výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.
>
> Přidání dat interakce vrstvy do spuštění profilování vyžaduje specifické postupy s nástroji profilování příkazového řádku. Viz [Shromáždit data interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Chcete-li shromažďovat data o výkonu z aplikace rozhraní .NET Framework, musí být před spuštěním cílové aplikace inicializovány příslušné proměnné prostředí. Když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, profiler již nesmí být připojen k aplikaci a profiler musí být explicitně vypnut. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace profilování.

## <a name="attach-the-profiler"></a>Připojte profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru ke spuštěné aplikaci rozhraní .NET Framework

1. Otevřete okno příkazového řádku.

2. Inicializovat proměnné prostředí profilování. Zadejte:

    **VSPerfClrEnv /sampleon** [**/samplelineoff**]

   - Možnost **/samplelineoff** zakáže shromažďování dat čísla řádku zdrojového kódu.

3. Spusťte profiler. Zadejte:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:sample** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     S možností **/start:sample** můžete použít některou z následujících možností.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že profilovaná aplikace byla spuštěna jako uživatel jiný než přihlášený uživatel. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. **/CS** lze zadat jako zkratku pro **/crosssession**. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

4. V případě potřeby spusťte cílovou aplikaci typickým způsobem.

5. Připojte profiler k cílové aplikaci. Zadejte:

    **VSPerfCmd /attach:**`PID` `ProcessName`{`Sample Event`&#124;} [ ] [**/targetclr:**`Version`]

   - `PID`určuje ID procesu cílové aplikace. `ProcessName`určuje název procesu. Všimněte si, `ProcessName` že pokud zadáte a více procesů, které mají stejný název jsou spuštěny, výsledky jsou nepředvídatelné. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` určuje verzi clr (COMMON Language runtime) pro profil, když je v aplikaci načtena více než jedna verze runtime. Nepovinný parametr.

   - Ve výchozím nastavení jsou data o výkonu vzorkována každých 10 000 000 nezastavených cyklů hodin procesoru. To je přibližně jednou za 10 sekund na procesoru 1GH. Můžete zadat jednu z následujících možností pro změnu intervalu cyklu hodin nebo pro určení jiné události vzorkování. [/targetclr](../profiling/targetclr.md)**:** `Version` určuje verzi CLR pro profil, když je v aplikaci načtena více než jedna verze runtime. Nepovinný parametr.

   |||
   |-|-|
   |Ukázková událost|Popis|
   |[/časovač](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nezastavených hodinových `Interval`cyklů určených aplikací .|
   |[/pf](../profiling/pf.md) [**:**`Interval`]|Změní událost vzorkování na chyby stránky. Pokud `Interval` je zadán, nastaví počet chyb stránky mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (syscalls). Pokud `Interval` je zadán, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Změní událost vzorkování a interval na čítač `Config`výkonu procesoru a interval, které jsou určeny v .|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování `PID`dat pro proces, který je určen .|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces, `PID` který je určen názvem nebo procesu (ProcName). **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler musí být odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilována pomocí metody vzorkování zavřením aplikace nebo voláním **možnosti VSPerfCmd /detach.** Potom volání **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Proveďte jeden z následujících kroků, chcete-li odpojit profiler od cílové aplikace:

    - Typ **VSPerfCmd /detach**

         -nebo-

    - Zavřete cílovou aplikaci.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)

3. (Nepovinné) Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv /vypnuto**

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
