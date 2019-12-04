---
title: Připojení profileru ke službě .NET ke shromažďování dat souběžnosti
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a95e907379db19d88fd7204e8410038ddb881d3b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779113"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru ke službě .NET ke shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, jak pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci připojit profiler ke službě .NET Framework a shromažďovat data o souběžnosti procesů a vláken pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromáždit data souběžnosti, Připojte profiler k procesu služby. I když je profiler připojen ke službě, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, nesmí být profiler již připojen ke službě a musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="attach-the-profiler"></a>Připojení profileru

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Připojení profileru k .NET Framework službě

1. Nainstalujte službu.

2. Otevřete příkazové okno.

3. Inicializujte proměnné prostředí pro profilování. Typ:

     [VSPerfCLREnv](../profiling/vsperfclrenv.md) **/globalsampleon** [ **/samplelineoff**]

    - **/globalsampleon** umožňuje vzorkování.

    - **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétním řádkům zdrojového kódu. Je-li tato možnost zadána, jsou data přiřazena pouze funkcím.

4. Restartujte počítač.

5. Spusťte profiler. Typ:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start:/Output pro Concurrency** : `OutputFile` [`Options`]

     Parametr [/Output](../profiling/output.md) **:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     S možností **/Start** můžete použít kteroukoli z následujících možností.

    > [!NOTE]
    > Pro služby jsou obvykle vyžadovány možnosti **/User** a **/CrossSession** .

    |Možnost|Popis|
    |------------|-----------------|
    |[/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName`|Určuje doménu a uživatelské jméno účtu, který vlastní profilový proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows.|
    |[/CrossSession](../profiling/crosssession.md)|Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je služba spuštěna v jiné relaci. ID relace je uvedeno ve sloupci **ID relace** na kartě **procesy** ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**.|
    |[/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilace.|
    |[/AutoMark](../profiling/automark.md) **:** `Interval`|Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (. *ETL*).|

6. V případě potřeby službu spusťte.

7. Připojte profiler ke službě. Typ:

     **VSPerfCmd/attach:** `PID` [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID` Určuje ID procesu nebo název procesu služby. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    - **targetclr:** `Version` určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime. Volitelné.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je služba spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd. exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí ( **/GlobalOn**) nebo zastaví shromažďování dat ( **/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí ( **/ProcessOn**) nebo zastaví sběrdat pro proces určený identifikátorem procesu (`PID`).|
    |**/Attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/Attach** začne shromažďovat data pro proces určený ID procesu nebo názvem procesu. **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

- K vložení značky profilování do datového souboru můžete použít také možnost **VSPerfCmd. exe**[/Mark](../profiling/mark.md) . Příkaz **/Mark** Přidá identifikátor, časové razítko a volitelný uživatelsky definovaný textový řetězec. Značky lze použít k filtrování dat v sestavách a zobrazení dat profileru. Následující páry možností VSPerfCmd spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace profilované s metodou souběžnosti můžete zastavit zastavením služby nebo vyvoláním možnosti **VSPerfCmd/detach** . Potom vyvoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neresetuje, dokud se počítač nerestartuje.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících postupů.

    - Zastavte službu.

         -nebo-

    - Typ **VSPerfCmd/detach.**

2. Vypněte profiler. Typ:

     **VSPerfCmd**  [vypnutí](../profiling/shutdown.md)
