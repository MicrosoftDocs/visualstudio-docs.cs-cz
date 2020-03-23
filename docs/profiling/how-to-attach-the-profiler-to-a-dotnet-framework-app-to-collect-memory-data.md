---
title: Připojení profileru k aplikaci .NET ke shromažďování paměťových dat
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 04dcf800074476b285a07e36db5a85fa3a366585
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779126"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Postup: Připojení profileru k samostatné aplikaci rozhraní .NET Framework ke shromažďování dat paměti pomocí příkazového řádku

Tento článek popisuje, jak pomocí nástrojů příkazového řádku Nástroje profilování sady Visual Studio připojit profiler ke spuštěné samostatné (klientské) aplikaci rozhraní .NET Framework a shromažďovat data paměti.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

Chcete-li připojit k aplikaci rozhraní .NET Framework a shromažďovat data paměti, musíte použít nástroj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí před spuštěním cílové aplikace. Když je profiler připojen k aplikaci, můžete použít nástroj *VSPerfCmd.exe* k pozastavení a obnovení shromažďování dat.

Chcete-li ukončit relaci profilování, profiler musí být odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="attach-the-profiler"></a>Připojte profiler

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru ke spuštěné aplikaci rozhraní .NET Framework

1. Otevřete okno příkazového řádku.

2. Inicializovat proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - Možnosti **/samplegc** a **/samplegclife** určují, zda se mají shromažďovat pouze data přidělení paměti nebo shromažďovat data přidělení paměti i životnosti objektu. Je nutné zadat jednu a pouze jednu možnost.

        |Možnost|Popisy|
        |------------|------------------|
        |**/samplegc**|Shromažďujte pouze data přidělení paměti.|
        |**/samplegclife**|Shromažďujte data přidělení paměti i životnosti objektu.|

    - Možnost **/samplelineoff** zakáže shromažďování dat čísla řádku zdrojového kódu.

3. Spusťte profiler. Zadejte:

     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:sample** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:sample.**

     | Možnost | Popis |
     | - | - |
     | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě Procesy ve Správci úloh systému Windows. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. Idenitifer relace je uveden ve sloupci ID relace na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |

4. V případě potřeby spusťte cílovou aplikaci typickým způsobem.

5. Připojte profiler k cílové aplikaci. Zadejte:

     **VSPerfCmd**[/attach](../profiling/attach.md) **:**`PID` {&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

    - `PID`určuje ID procesu cílové aplikace. `ProcessName`určuje název procesu. Všimněte si, `ProcessName` že pokud zadáte a více procesů, které mají stejný název jsou spuštěny, výsledky jsou nepředvídatelné. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    - **/targetclr:** `Version` určuje verzi clr (COMMON Language runtime) pro profil, když je v aplikaci načtena více než jedna verze runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat

Když je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování `PID`dat pro proces, který je určen .|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces, `PID` který je určen názvem nebo procesu (ProcName). **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování

Chcete-li ukončit relaci profilování, profiler musí být odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilována pomocí metody vzorkování zavřením aplikace nebo voláním **možnosti VSPerfCmd /detach.** Potom volání **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Proveďte jeden z následujících kroků, chcete-li odpojit profiler od cílové aplikace:

    - Typ **VSPerfCmd /detach**

         -nebo-

    - Zavřete cílovou aplikaci.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)

3. (Nepovinné) Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfCmd /vypnuto**

## <a name="see-also"></a>Viz také

[Profilová zobrazení](../profiling/command-line-profiling-of-stand-alone-applications.md)
dat s vlastními aplikacemi[.NET](../profiling/dotnet-memory-data-views.md)
