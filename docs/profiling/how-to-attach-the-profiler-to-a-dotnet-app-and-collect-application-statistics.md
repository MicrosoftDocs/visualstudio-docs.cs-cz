---
title: Připojit profiler k samostatné aplikaci .NET; získat statistiku aplikace
description: Naučte se používat Nástroje pro profilaci nástroje příkazového řádku sady Visual Studio k připojení profileru ke spuštěné .NET Framework samostatné (klientské) aplikace a získání statistik.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 899a74894e34b43f87a7f45b4c4c90fff60088a1
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801151"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru k samostatné aplikaci .NET Framework a shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů příkazového řádku připojit profiler ke spuštěné .NET Framework samostatné (klientské) aplikaci a shromažďovat statistiku výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.
>
> Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku. Viz [shromáždění dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Chcete-li shromažďovat údaje o výkonu z aplikace .NET Framework, musí být před spuštěním cílové aplikace inicializovány příslušné proměnné prostředí. Když je profiler připojen k aplikaci, můžete pozastavit a obnovit sběr dat.

 Chcete-li ukončit relaci profilování, nesmí být profiler již připojen k aplikaci a musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace profilování vyprázdnit proměnné prostředí profilování.

## <a name="attach-the-profiler"></a>Připojení profileru

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru k běžící .NET Framework aplikaci

1. Otevřete okno příkazového řádku.

2. Inicializujte proměnné prostředí pro profilování. Zadejte:

    **VSPerfCLREnv/sampleon** [**/samplelineoff**]

   - Možnost **/samplelineoff** zakáže shromažďování dat o číslech řádků zdrojového kódu.

3. Spusťte profiler. Zadejte:

    **VSPerfCmd/Start: Sample/output:** `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md)**: Sample** inicializuje Profiler.

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít jednu z následujících možností.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, který vlastní profilový proces. Tato možnost je vyžadována pouze v případě, že profilovaná aplikace byla spuštěna jako jiný uživatel než přihlášený uživatel. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. **/Cs** lze zadat jako zkratku pro **/CrossSession**. Tato možnost je vyžadována, pokud aplikace běží v jiné relaci. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.*ETL*). |

4. V případě potřeby spusťte cílovou aplikaci obvyklým způsobem.

5. Připojte profiler k cílové aplikaci. Zadejte:

    **VSPerfCmd/attach:**{ `PID`&#124;`ProcessName` } [ `Sample Event` ] [**/targetclr:** `Version` ]

   - `PID` Určuje ID procesu cílové aplikace. `ProcessName` Určuje název procesu. Všimněte si, že pokud zadáte `ProcessName` a více procesů, které mají stejný název, budou výsledky nepředvídatelné. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime. Nepovinný parametr.

   - Ve výchozím nastavení jsou data o výkonu Navzorkovaná každých 10 000 000 hodinových cyklů procesoru. To je přibližně jednou za 10 sekund na frekvencí 1 GHz procesoru. Můžete určit jednu z následujících možností pro změnu intervalu hodinových cyklů nebo zadat jinou událost vzorkování. [/targetclr](../profiling/targetclr.md)**:** `Version` Určuje verzi modulu CLR, která se má profilovat, pokud je v aplikaci načtena více než jedna verze modulu runtime. Nepovinný parametr.

   |Ukázková událost|Popis|
   |-|-|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů, které jsou určeny pomocí `Interval` .|
   |[/PF](../profiling/pf.md) [**:** `Interval` ]|Změní událost vzorkování na chyby stránkování. Pokud `Interval` je zadaný, nastaví počet chyb stránek mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (voláním). Pokud `Interval` je zadáno, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Změní událost vzorkování a interval na čítač výkonu procesoru a interval, který je určen v `Config` .|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Je-li cílová aplikace spuštěna, lze shromažďování dat řídit spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví sběrdat pro proces, který je určen v `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** začne shromažďovat data pro proces, který je určený `PID` názvem procesu nebo názvem procesu (ProcName). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilových procesů a Profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilovaná pomocí metody vzorkování, ukončením aplikace nebo zavoláním možnosti **VSPerfCmd/detach** . Potom zavoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/off.** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

    - Typ **VSPerfCmd/detach**

         -nebo-

    - Zavřete cílovou aplikaci.

2. Vypněte profiler. Zadejte:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. Volitelné Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv/off.**

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
