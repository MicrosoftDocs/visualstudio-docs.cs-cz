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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779113"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Postup: Připojení profileru ke službě .NET ke shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje profilování připojit profiler ke službě rozhraní .NET Framework a shromažďovat data souběžnosti procesů a vláken pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat data souběžnosti, připojte profiler k procesu služby. Zatímco profiler je připojen ke službě, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, profiler již nesmí být připojen ke službě a profiler musí být explicitně vypnut. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="attach-the-profiler"></a>Připojte profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Připojení profileru ke službě rozhraní .NET Framework

1. Nainstalujte službu.

2. Otevřete příkazové okno.

3. Inicializovat proměnné prostředí profilování. Zadejte:

     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]

    - **/globalsampleon** umožňuje vzorkování.

    - **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétním řádkům zdrojového kódu. Pokud je tato možnost zadána, data jsou přiřazena pouze funkcím.

4. Restartujte počítač.

5. Spusťte profiler. Zadejte:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:souběžnost /výstup:** `OutputFile` [`Options`]

     [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     S možností **/start** můžete použít některou z následujících možností.

    > [!NOTE]
    > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro služby.

    |Možnost|Popis|
    |------------|-----------------|
    |[/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName`|Určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows.|
    |[/crosssession](../profiling/crosssession.md)|Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je služba spuštěna v jiné relaci. ID relace je uvedeno ve **sloupci ID relace** na kartě **Procesy** ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**.|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Určuje čítač výkonu systému Windows, který má být shromážděn během profilování.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms.|
    |[/události](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru.|

6. V případě potřeby spusťte službu.

7. Připojte profiler ke službě. Zadejte:

     **VSPerfCmd /attach:** `PID` [[/targetclr](../profiling/targetclr.md)**:**`Version`]

    - `PID`určuje ID procesu nebo název procesu služby. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    - **targetclr:** `Version` určuje verzi clr (COMMON Language runtime) pro profil, když je v aplikaci načtena více než jedna verze runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 V době, kdy je služba spuštěna, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |**/attach:**`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces určený ID procesu nebo název procesu. **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

- Můžete také použít **Možnost VSPerfCmd.exe**[/mark](../profiling/mark.md) vložit profilování značku do datového souboru. Příkaz **/mark** přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze filtrovat data v sestavách profileru a zobrazeních dat. Následující dvojice možností VSPerfCmd spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace profilované metodou souběžnosti můžete zastavit zastavením služby nebo vyvoláním možnosti **VSPerfCmd /detach.** Potom vyvolat **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neobnoví, dokud není počítač restartován.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Jedním z následujících akcí odpojte profiler od cílové aplikace.

    - Zastavte službu.

         -nebo-

    - Zadejte **VSPerfCmd /detach.**

2. Vypněte profileru. Zadejte:

     **Vypnutí vsperfcmd**[Shutdown](../profiling/shutdown.md)  
