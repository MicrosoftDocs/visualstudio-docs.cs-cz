---
title: Profiler příkazového řádku – instrumentace dynamické aplikace ASP.NET, získání dat paměti
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 7c1fafd3b21dd40da1215e7864c6d66090589d03
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328075"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postupy: instrumentace dynamicky kompilované webové aplikace ASP.NET a shromažďování dat paměti pomocí příkazového řádku profileru
Toto téma popisuje, jak používat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástroje příkazového řádku ke shromažďování podrobných dat o přidělování paměti .NET a o životnosti objektů pro dynamicky kompilované [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace pomocí metody profilace instrumentace.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromažďovat údaje o výkonu z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace, upravte *web.config* souboru cílové aplikace tak, aby nástroj [VSInstr.exe](../profiling/vsinstr.md) mohl instrumentovat dynamicky kompilované soubory aplikace. Pak pomocí nástroje [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) nakonfigurujte server, který je hostitelem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace, a povolte profilaci paměti .NET nastavením příslušných proměnných prostředí a pak restartujte počítač.

 Pokud chcete shromažďovat data, spusťte Profiler a pak spusťte cílovou aplikaci. I když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Pokud jste shromáždili příslušná data, ukončete aplikaci, ukončete pracovní proces Internetová informační služba (IIS) a pak vypněte profiler.

 Po dokončení práce s profilací obnovte soubor *web.config* a webový server do původního stavu.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurace webové aplikace ASP.NET a webového serveru

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurace webové aplikace ASP.NET a webového serveru

1. Upravte soubor *web.config* cílové aplikace. Viz [Postupy: změna web.config souborů pro instrumentaci a profilování dynamicky kompilovaných webových aplikací ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otevřete okno příkazového řádku v počítači, který je hostitelem webové aplikace.

3. Inicializujte proměnné prostředí pro profilování. Zadejte:

     **VSPerfClrEnv/globaltracegc**

     -nebo-

     **VSPerfClrEnv/globaltracegclife**

    - **/globaltracegc** umožňuje shromažďování dat o přidělování paměti.

    - **/globaltracegclife** umožňuje shromažďování dat o přidělení paměti a data o životnosti objektů.

4. Restartujte počítač.

## <a name="run-the-profiling-session"></a>Spuštění relace profilace

#### <a name="to-profile-the-aspnet-web-application"></a>Profilování webové aplikace v ASP.NET

1. Spusťte profiler. Zadejte:

    **VSPerfCmd** [/Start](../profiling/start.md) **: Trace** [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Možnost **/Start: Trace** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile`Určuje název a umístění dat profilování (.* VSP*) soubor.

     Pomocí možnosti **/Start: Trace** můžete použít kteroukoli z následujících možností.

   > [!NOTE]
   > Možnosti **/User** a **/CrossSession** se obvykle vyžadují pro aplikace ASP.NET.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, který vlastní [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Tato možnost je vyžadována, pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Název se zobrazí ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud aplikace běží v jiné relaci. ID relace je uvedeno ve sloupci **ID relace** na kartě **procesy** ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Spustí Profiler s pozastaveným shromažďováním dat. Obnovte profilování pomocí [/GlobalOn](../profiling/globalon-and-globaloff.md) . |
   | [/Counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru určeného v `Config` . Informace čítače jsou přidány do shromažďovaných dat v každé události profilace. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (.* ETL*). |

2. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Obvyklým způsobem spusťte webovou aplikaci.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/ThreadOn**) nebo zastaví shromažďování dat (**/ThreadOff**) pro vlákno určené ID vlákna ( `TID` ).|

- K vložení značky profilování do datového souboru můžete použít také možnost **VSPerfCmd.exe** [/Mark](../profiling/mark.md) . Příkaz **/Mark** Přidá identifikátor, časové razítko a volitelný uživatelsky definovaný textový řetězec. Značky lze použít k filtrování dat v sestavách a zobrazení dat profileru.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zavřete cílovou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, zastavte Internetová informační služba (IIS) a zastavte profilování a pak vypněte profiler. Pak restartujte službu IIS.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci.

2. Kliknutím na [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] resetování Internetová informační služba (IIS) zavřete pracovní proces. Zadejte:

    **IISReset/stop**

3. Vypněte profiler. Zadejte:

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

4. Restartujte službu IIS. Zadejte:

    **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Obnovení konfigurace aplikace a počítače
 Po dokončení všech profilování nahraďte soubor *web.config* , vymažte proměnné prostředí profilace a restartujte počítač, aby se server a aplikace obnovily [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] do jejich původních stavů.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Obnovení konfigurace aplikace a počítače

1. Nahraďte soubor *web.config* kopií původního souboru.

2. (Volitelné). Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfCmd/globaloff**

3. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
