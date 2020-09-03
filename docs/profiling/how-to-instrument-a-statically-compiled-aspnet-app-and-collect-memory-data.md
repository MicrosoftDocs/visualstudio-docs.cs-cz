---
title: Profiler příkazového řádku – instrumentace statické aplikace ASP.NET, načtení dat paměti
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 427ece50dc2e8add6cc05e944907a9e0e1a890ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85327934"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postupy: Instrumentace staticky kompilované webové aplikace ASP.NET a shromažďování dat paměti pomocí příkazového řádku profileru
Tento článek popisuje, jak používat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástroje příkazového řádku k instrumentaci předkompilované [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové komponenty nebo webu a shromažďování přidělování paměti .NET, životnosti objektů a podrobných dat časování.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromažďovat data z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové komponenty pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) k vygenerování instrumentované verze součásti. V počítači, který je hostitelem komponenty, nahraďte neinstrumentované verze komponenty pomocí instrumentované verze. Pak použijte nástroj [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) k inicializaci globálních proměnných profilování a restartujte hostitelský počítač. Pak spustíte Profiler.

 Po spuštění instrumentované komponenty se data časování automaticky shromažďují do datového souboru. Během relace profilace můžete shromažďování dat pozastavit a obnovit.

 Chcete-li ukončit relaci profilování, zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces, který je hostitelem komponenty, a pak explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="start-to-profile"></a>Začít profilovat

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Instrumentace webové komponenty ASP.NET a spuštění profilování

1. Pomocí nástroje **VSInstr** vygenerujte instrumentované verze cílové aplikace. V případě potřeby nahraďte binární soubory aplikace v hostitelském počítači s ASP.NET pomocí instrumentované binární soubory.

2. Otevření okna příkazového řádku

3. Inicializujte proměnné prostředí pro profilování .NET. V okně příkazového řádku zadejte:

    **VSPerfClrEnv/globaltracegc**

    -nebo-

    **VSPerfClrEnv/globaltracegclife**

   - **/globaltracegc** shromažďuje data o přidělování paměti .NET a časování.

   - **/globaltracegclife** shromažďuje přidělování paměti .NET, životnost objektů a podrobná data časování.

4. Restartujte počítač.

5. Otevřete okno příkazového řádku.

6. Spusťte profiler. V okně příkazového řádku zadejte:

    **VSPerfCmd/Start: Trace/output:** `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md)**: Trace** inicializuje Profiler.

   - Parametr [/Output](../profiling/output.md)**:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Trace** můžete použít kteroukoli z následujících možností.

   > [!NOTE]
   > Možnosti **/User** a **/CrossSession** se obvykle vyžadují pro aplikace ASP.NET.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel, který je jiný než přihlášený uživatel. Název se zobrazí ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud aplikace běží v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě **procesy** ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL). |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit Profiler s pozastaveným shromažďováním dat, přidejte možnost **/globaloff** do příkazového řádku **/Start** . Obnovte profilování pomocí **/GlobalOn** . |

7. Otevřete web, který obsahuje instrumentované komponenty.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/ThreadOn**) nebo zastaví shromažďování dat (**/ThreadOff**) pro vlákno určené ID vlákna ( `TID` ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci a poté pomocí příkazu Internetová informační služba (IIS) **iisreset** zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Pro vypnutí profileru a zavření souboru dat profilování použijte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) . Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování. Chcete-li použít nové nastavení prostředí, je nutné restartovat počítač.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci.

2. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Zadejte:

    **IISReset/stop**

3. Vypněte profiler. Zadejte:

    **VSPerfCmd/shutdown**

4. (Volitelné). Vymažte proměnné prostředí profilování. Zadejte:

    **VSPerfCmd/globaloff**

5. Restartujte počítač. V případě potřeby restartujte službu IIS. Zadejte:

    **IISReset/Start**

## <a name="see-also"></a>Viz také
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
