---
title: 'Příkazový řádek profileru: Nástroj statické ASP.NET aplikace, získat časovací data'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 7d743dd854bd11449161c47cc896d0735849e1dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778853"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Postup: Instrumentujte staticky kompilované ASP.NET webové aplikace a shromažďujte podrobná časovací data s profilerem pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nástroje předkompilované webové součásti nebo webu a ke shromažďování podrobných časovacích dat.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.
>
> Přidání dat interakce vrstvy do spuštění profilování vyžaduje specifické postupy s nástroji profilování příkazového řádku. Viz [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Chcete-li shromažďovat podrobná časovací data z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové součásti pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) ke generování instrumentované verze komponenty. V počítači, který je hostitelem součásti, nahradíte neinstrumentolovnou verzi komponenty instrumentolou verzí. Potom pomocí nástroje [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) inicializovat globální profilování proměnné prostředí a restartovat hostitelský počítač. Potom spustíte profiler.

 Při spuštění instrumentované součásti jsou data časování automaticky shromažďována do datového souboru. Shromažďování dat můžete pozastavit a obnovit během relace profilování.

 Chcete-li ukončit relaci profilování, zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces, který je hostitelem součásti, a potom explicitně vypněte profiler. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="start-to-profile"></a>Začít profilovat

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Instrumentace webové komponenty ASP.NET a zahájení profilování

1. Otevřete okno příkazového řádku.

2. Nástroj **VSInstr** slouží ke generování instrumentované verze cílové aplikace. V případě potřeby vyměňte binární soubory aplikace na hostitelském počítači ASP.NET instrumentovanými binárními soubory.

3. Inicializovat proměnné prostředí profilování .NET. Do okna příkazového řádku zadejte:

    **VSPerfClrEnv /globaltraceon**

4. Restartujte počítač.

5. Otevřete okno příkazového řádku. V případě potřeby nastavte cestu nástrojů profileru.

6. Spusťte profiler. Zadejte:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:trace** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:trace.**

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro ASP.NET aplikace.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Idenitifikátor relace je uveden ve sloupci ID relace na kartě **Procesy** ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit profiler s pozastavenou kolekcí dat, přidejte možnost **/globaloff** do příkazového řádku **/start.** Použití **/globalon** obnovit profilování. |

7. Otevřete web, který obsahuje instrumentotou komponentu.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat`TID`pro vlákno určené ID vlákna ( ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilování, ukončete webovou aplikaci a potom pomocí příkazu **IISReset** internetové informační služby (IIS) ukončete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Volání **VSPerfCmd** [/shutdown](../profiling/shutdown.md) možnost vypnout profiler a zavřete profilování datový soubor.

 Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování. Chcete-li použít nové nastavení prostředí, je nutné restartovat počítač.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci.

2. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Zadejte:

    **IISReset /stop**

3. Vypněte profileru. Zadejte:

    **VSPerfCmd /vypnutí**

4. (Nepovinné). Vymažte proměnné prostředí profilování. Zadejte:

    **VSPerfCmd /globaloff**

5. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
