---
title: 'Příkazový řádek profileru: Nástroj statické ASP.NET aplikace, získat paměťová data'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98fac9f01219cd398f1d5ec462e3f5165f4638d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775428"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postup: Instrumentujte staticky kompilované ASP.NET webové aplikace a sbírat data o paměti pomocí příkazového řádku profileru
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje nástroje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] předkompilovanou webovou komponentu nebo web a shromažďování přidělení paměti .NET, životnostobjektu a podrobná data časování.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] data z webové součásti pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) ke generování instrumentované verze komponenty. V počítači, který je hostitelem součásti, nahradíte neinstrumentolou verzi komponenty instrumentolou verzí. Potom pomocí nástroje [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) inicializovat globální profilování proměnné prostředí a restartovat hostitelský počítač. Potom spustíte profiler.

 Při spuštění instrumentované součásti jsou data časování automaticky shromažďována do datového souboru. Shromažďování dat můžete pozastavit a obnovit během relace profilování.

 Chcete-li ukončit relaci profilování, zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces, který je hostitelem součásti, a potom explicitně vypněte profiler. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="start-to-profile"></a>Začít profilovat

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Instrumentace ASP.NET webové součásti a zahájení profilování

1. Nástroj **VSInstr** slouží ke generování instrumentované verze cílové aplikace. V případě potřeby vyměňte binární soubory aplikace na hostitelském počítači ASP.NET instrumentovanými binárními soubory.

2. Otevření okna příkazového řádku

3. Inicializovat proměnné prostředí profilování .NET. Do okna příkazového řádku zadejte:

    **VSPerfClrEnv /globaltracegc**

    -nebo-

    **VSPerfClrEnv /globaltracegclife**

   - **/globaltracegc** shromažďuje data přidělení a časování paměti .NET.

   - **/globaltracegclife** shromažďuje přidělení paměti .NET, životnost objektu a podrobná data časování.

4. Restartujte počítač.

5. Otevřete okno příkazového řádku.

6. Spusťte profiler. Do okna příkazového řádku zadejte:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:trace** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:trace.**

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro ASP.NET aplikace.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, který vlastní pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel, který je jiný než přihlášený uživatel. Název je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě **Procesy** ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit profiler s pozastavenou kolekcí dat, přidejte možnost **/globaloff** do příkazového řádku **/start.** Použití **/globalon** obnovit profilování. |

7. Otevřete web, který obsahuje instrumentotou komponentu.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat`TID`pro vlákno určené ID vlákna ( ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilování, ukončete webovou aplikaci a potom pomocí příkazu **IISReset** internetové informační služby (IIS) ukončete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Volání **VSPerfCmd** [/shutdown](../profiling/shutdown.md) možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování. Chcete-li použít nové nastavení prostředí, je nutné restartovat počítač.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci.

2. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Zadejte:

    **IISReset /stop**

3. Vypněte profileru. Zadejte:

    **VSPerfCmd /vypnutí**

4. (Nepovinné). Vymažte proměnné prostředí profilování. Zadejte:

    **VSPerfCmd /globaloff**

5. Restartujte počítač. V případě potřeby restartujte službu IIS. Zadejte:

    **IISReset /start**

## <a name="see-also"></a>Viz také
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
