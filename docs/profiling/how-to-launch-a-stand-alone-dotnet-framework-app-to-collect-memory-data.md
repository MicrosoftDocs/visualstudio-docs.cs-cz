---
title: 'Příkazový řádek Profiler: Otevřete klientskou aplikaci .NET Framework, získejte paměťová data'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c9ee0ae59fd32394e31acc75184d0e55aaae872d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775351"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Postup: Spuštění samostatné aplikace rozhraní .NET Framework s profilerem pro shromažďování paměťových dat pomocí příkazového řádku
Toto téma popisuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] použití nástrojů příkazového řádku Nástroje profilování ke spuštění samostatné (klientské) aplikace rozhraní .NET Framework a ke shromažďování dat paměti.

 Relace profilování má tři části:

- Spuštění aplikace pomocí profileru.

- Shromažďování dat profilování.

- Ukončení relace profilování.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li spustit cílovou aplikaci pomocí profileru, použijte možnosti **VSPerfCmd.exe/start** a **/launch** k inicializaci profileru a spuštění aplikace. Můžete zadat **/start** a **/launch** a jejich příslušné možnosti na jednom příkazovém řádku.

 Můžete také přidat **/globaloff** možnosti pozastavit shromažďování dat na začátku cílové aplikace. Potom pomocí **/globalon** začít shromažďovat data.

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

3. Spusťte cílovou aplikaci. Zadejte:

    **VSPerfCmd**[/launch](../profiling/launch.md) **:** `appName` **/gc:**{`Options`**allocation**&#124;**lifetime**}[ ]  

   - [Možnost /gc](../profiling/gc-vsperfcmd.md)**:** `Keyword` je vyžadována ke shromažďování paměťových dat rozhraní .NET Framework. Parametr klíčového slova určuje, zda má být shromažďování dat přidělení paměti nebo shromažďování dat o přidělení paměti i životnosti objektu.

     |Klíčové slovo|Popis|
     |-------------|-----------------|
     |**Přidělení**|Shromažďujte pouze data přidělení paměti.|
     |**Životnost**|Shromažďujte data přidělení paměti i životnosti objektu.|

     S možností **/launch** můžete použít některou z následujících možností.

   |Možnost|Popis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které mají být předány cílové aplikaci.|
   |[/konzole](../profiling/console.md)|Spustí aplikaci cílového příkazového řádku v samostatném okně.|
   |[/události](../profiling/events-vsperfcmd.md) **:**`Config`|Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Určuje verzi běžného jazyka runtime (CLR) pro profil, pokud je v aplikaci načtena více než jedna verze runtime.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat pro`PID`proces, který je určen ID procesu ( ).|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** začne shromažďovat data pro proces, `PID` který je určen (ID procesu). **/detach** zastaví shromažďování dat pro všechny procesy.|

- Můžete také použít **Možnost VSPerfCmd.exe**[/mark](../profiling/mark.md) vložit profilování značku do datového souboru. Příkaz **/mark** přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze použít k filtrování dat.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler musí být odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilována pomocí metody vzorkování zavřením aplikace nebo voláním **možnosti VSPerfCmd /detach.** Potom volání **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Proveďte jeden z následujících kroků, chcete-li odpojit profiler od cílové aplikace:

    - Zavřete cílovou aplikaci.

         -nebo-

    - Typ **VSPerfCmd /detach**

2. Vypněte profileru. Zadejte:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
