---
title: Připojení profileru k .NET ke shromažďování dat paměti
description: Naučte se používat Nástroje pro profilaci nástroje příkazového řádku sady Visual Studio k připojení profileru ke spuštěné .NET Framework samostatné (klientské) aplikaci a k získání dat paměti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1a80e4201f04565aaa163d58bca8e13ae715b09f
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801100"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Postupy: Připojení profileru k .NET Framework samostatné aplikaci ke shromažďování dat paměti pomocí příkazového řádku

Tento článek popisuje, jak pomocí nástrojů příkazového řádku sady Visual Studio Nástroje pro profilaci připojit profiler ke spuštěné .NET Framework samostatné (klientské) aplikace a shromažďovat data o paměti.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

Chcete-li se připojit k aplikaci .NET Framework a shromažďovat data paměti, je nutné použít nástroj [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí před spuštěním cílové aplikace. Když je profiler připojen k aplikaci, můžete použít nástroj *VSPerfCmd.exe* k pozastavení a obnovení sběru dat.

Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilových procesů a Profiler musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="attach-the-profiler"></a>Připojení profileru

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru k běžící .NET Framework aplikaci

1. Otevřete okno příkazového řádku.

2. Inicializujte proměnné prostředí pro profilování. Zadejte:

     **VSPerfCLREnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - Možnosti **/samplegc** a **/samplegclife** určují, zda mají být shromažďována pouze data o přidělování paměti nebo jak shromažďovat data o životnosti objektů. Je nutné zadat pouze jednu možnost.

        |Možnost|Označení|
        |------------|------------------|
        |**/samplegc**|Shromažďovat pouze data o přidělování paměti.|
        |**/samplegclife**|Shromážděte jak přidělování paměti, tak data o životnosti objektů.|

    - Možnost **/samplelineoff** zakáže shromažďování dat o číslech řádků zdrojového kódu.

3. Spusťte profiler. Zadejte:

     **VSPerfCmd/Start: Sample/output:** `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md)**: Sample** inicializuje Profiler.

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít kteroukoli z následujících možností.

     | Možnost | Popis |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilový proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě procesy ve Správci úloh systému Windows. |
     | [/CrossSession &#124;/cs](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud aplikace běží v jiné relaci. Vypsán relace je uvedena ve sloupci ID relace na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
     | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |

4. V případě potřeby spusťte cílovou aplikaci obvyklým způsobem.

5. Připojte profiler k cílové aplikaci. Zadejte:

     **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

    - `PID` Určuje ID procesu cílové aplikace. `ProcessName` Určuje název procesu. Všimněte si, že pokud zadáte `ProcessName` a více procesů, které mají stejný název, budou výsledky nepředvídatelné. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    - **/targetclr:** `Version` Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat

Je-li cílová aplikace spuštěna, lze shromažďování dat řídit spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví sběrdat pro proces, který je určen v `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** začne shromažďovat data pro proces, který je určený `PID` názvem procesu nebo názvem procesu (ProcName). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování

Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilových procesů a Profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilovaná pomocí metody vzorkování, ukončením aplikace nebo zavoláním možnosti **VSPerfCmd/detach** . Pak zavoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/off.** vymaže proměnné prostředí profilování.

### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

    - Typ **VSPerfCmd/detach**

         -nebo-

    - Zavřete cílovou aplikaci.

2. Vypněte profiler. Zadejte:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. Volitelné Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfCmd/off.**

## <a name="see-also"></a>Viz také

[Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md) 
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
