---
title: Připojení profileru ke službě .NET ke shromažďování statistik aplikace
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ac59e0e08894ca143df6a68c49e5f5f8b24ebc50
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328712"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru ke službě .NET ke shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů příkazového řádku připojit profiler ke službě .NET Framework a shromažďovat statistiku výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.
>
> Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku. Viz [shromáždění dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Chcete-li shromažďovat údaje o výkonu z .NET Framework služby, je nutné použít nástroj [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí. Poté je nutné restartovat počítač, který je hostitelem služby, a nakonfigurovat tento počítač pro profilování. Poté profiler připojte k procesu služby. Pokud je profiler připojen ke službě, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a poté explicitně ukončen. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="attach-the-profiler"></a>Připojení profileru

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Připojení profileru k .NET Framework službě

1. Nainstalujte službu.

2. Otevřete okno příkazového řádku.

3. Inicializujte proměnné prostředí pro profilování. Zadejte:

    **VSPerfCLREnv/globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** umožňuje vzorkování.

   - **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétním řádkům zdrojového kódu. Je-li tato možnost zadána, jsou data přiřazena pouze funkcím.

4. Restartujte počítač.

5. Otevřete okno příkazového řádku.

6. Spusťte profiler. Zadejte:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Sample**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Možnost **/Start: Sample** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile`Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít kteroukoli z následujících možností.

   > [!NOTE]
   > Pro služby jsou obvykle vyžadovány možnosti **/User** a **/CrossSession** .

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilový proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě procesy ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je služba spuštěna v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL). |

7. V případě potřeby službu spusťte.

8. Připojte profiler ke službě. Zadejte:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:** { `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Zadejte identifikátor ID procesu (`PID`) nebo název procesu (ProcName) služby. ID procesů a názvy všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

     Ve výchozím nastavení jsou data o výkonu Navzorkovaná každých 10 000 000 hodinových cyklů procesoru. V případě procesoru s frekvencí 1 GHz jde o přibližně 100 vzorků za sekundu. Můžete určit jednu z následujících možností pro změnu intervalu hodinových cyklů nebo zadat jinou událost vzorkování.

   |Událost vzorku|Popis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů určených parametrem `Interval`.|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Změní událost vzorkování na chyby stránkování. Pokud `Interval` je zadaný, nastaví počet chyb stránek mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (voláním). Pokud `Interval` je zadáno, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Změní událost a interval vzorkování na čítač výkonu a interval procesoru určený parametrem `Config`.|

   - **targetclr:** `Version` Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je služba spuštěná, můžete použít možnosti *VSPerfCmd.exe* pro spuštění a zastavení zápisu dat do datového souboru profileru. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** začne shromažďovat data pro proces určený ID procesu nebo názvem procesu. **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilových procesů a Profiler musí být explicitně vypnut. Můžete odpojit od aplikace profilované pomocí metody vzorkování ukončením aplikace nebo zavoláním možnosti **VSPerfCmd/detach** . Potom zavoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování.

 Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neresetuje, dokud se počítač nerestartuje.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

    - Zastavte službu.

         -nebo-

    - Typ **VSPerfCmd/detach**

2. Vypněte profiler. Zadejte:

     **VSPerfCmd/shutdown**

3. Volitelné Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv/globaloff**

4. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
