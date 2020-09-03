---
title: Profiler příkazového řádku – instrumentace dynamické aplikace ASP.NET, získání dat časování
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: f510878c3952cb98bcbee3bfecedf05b87b2658f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85327973"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Postupy: instrumentace dynamicky kompilované webové aplikace ASP.NET a shromažďování podrobných dat časování s použitím profileru pomocí příkazového řádku

Tento článek popisuje, jak pomocí nástrojů příkazového řádku sady Visual Studio Nástroje pro profilaci shromažďovat podrobná data časování pro dynamicky kompilovaná [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace pomocí metody profilace instrumentace.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

Chcete-li shromažďovat údaje o výkonu z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace, upravte *web.config* souboru cílové aplikace tak, aby nástroj [VSInstr.exe](../profiling/vsinstr.md) mohl instrumentovat dynamicky kompilované soubory aplikace. Pak pomocí nástroje [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) nastavte příslušné proměnné prostředí na webovém serveru, abyste mohli profilaci povolit, a pak restartujte počítač.

Spusťte profiler a pak spusťte cílovou aplikaci. I když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Po dokončení profilování ukončete aplikaci, zavřete pracovní proces Internetová informační služba (IIS) a pak vypněte profiler. Po dokončení práce s profilací obnovte soubor *web.config* a webový server do původního stavu.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurace webové aplikace ASP.NET a webového serveru

1. Upravte soubor *web.config* cílové aplikace. Viz [Postupy: změna web.config souborů pro instrumentaci a profilování dynamicky kompilovaných webových aplikací ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otevřete okno příkazového řádku.

3. Inicializujte proměnné prostředí pro profilování. Zadejte:

     **VSPerfClrEnv/globaltraceon**

    - **/globaltraceon** umožňuje profilaci pomocí metody instrumentace.

4. Restartujte počítač.

## <a name="run-the-profiling-session"></a>Spuštění relace profilace

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

     **VSPerfCmd**  [/Start](../profiling/start.md) **: Trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Možnost **/Start: Trace** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění dat profilování (.* VSP*) soubor.

     Pomocí možnosti **/Start: Trace** můžete použít kteroukoli z následujících možností.

     > [!NOTE]
     > Možnosti **/User** a **/CrossSession** se obvykle vyžadují pro aplikace ASP.NET.

     | Možnost | Popis |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows. |
     | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud aplikace ASP.NET běží v jiné relaci. Identifikátor relace je uveden ve sloupci **ID relace** na kartě **procesy** ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Spustí Profiler s pozastaveným shromažďováním dat. Obnovte profilování pomocí [/GlobalOn](../profiling/globalon-and-globaloff.md) . |
     | [/Counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru, který je určen v `Config` . Informace čítače jsou přidány do dat, která jsou shromažďována při každé události profilace. |
     | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
     | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.* ETL*). |

3. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Obvyklým způsobem spusťte webovou aplikaci.

## <a name="control-data-collection"></a>Řízení shromažďování dat

I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/ThreadOn**) nebo zastaví shromažďování dat (**/ThreadOff**) pro vlákno určené ID vlákna ( `TID` ).|

- K vložení značky profilování do datového souboru můžete použít také možnost **VSPerfCmd.exe** [/Mark](../profiling/mark.md) . Příkaz **/Mark** Přidá identifikátor, časové razítko a volitelný uživatelsky definovaný textový řetězec. Značky lze použít k filtrování dat v sestavách a zobrazení dat profileru.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování

Chcete-li ukončit relaci profilování, zavřete cílovou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, obnovte IIS, aby se zastavil profilování, a pak vypněte profiler.

1. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci.

2. Kliknutím na [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] resetování Internetová informační služba (IIS) zavřete pracovní proces. Zadejte:

     **IISReset/stop**

3. Vypněte profiler. Zadejte:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

4. Restartujte službu IIS. Zadejte:

     **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Obnovení konfigurace aplikace a počítače

Po dokončení všech profilování nahraďte soubor *web.config* , vymažte proměnné prostředí profilace a restartujte počítač, aby se aplikace a server obnovily do stavu před profilací.

1. Nahraďte soubor *web.config* kopií původního souboru.

2. Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfCmd/globaloff**

3. Restartujte počítač.

## <a name="see-also"></a>Viz také

[ASP.NET webové aplikace](../profiling/command-line-profiling-of-aspnet-web-applications.md) 
 Profile [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
