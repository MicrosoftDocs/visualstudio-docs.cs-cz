---
title: 'Příkazový řádek profileru: Nástroj dynamický ASP.NET aplikace, získat paměťová data'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 3378a45ebace942bb8696f2f67962365b5f57796
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778879"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postup: Instrumentujte dynamicky kompilované ASP.NET webové aplikace a shromažďujte data paměti pomocí příkazového řádku profileru
Toto téma popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku Nástroje profilování shromažďovat podrobné alokace paměti .NET a data životnosti objektu pro dynamicky kompilované [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace pomocí metody instrumentace profilování.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] údaje o výkonu z webové aplikace, upravte soubor *web.config* cílové aplikace tak, aby nástroj [VSInstr.exe](../profiling/vsinstr.md) instrumentoval dynamicky kompilované soubory aplikací. Potom pomocí nástroje [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nakonfigurujte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] server, který je hostitelem webové aplikace, a povolte profilování paměti .NET nastavením příslušných proměnných prostředí a restartujte počítač.

 Chcete-li shromažďovat data, spusťte profiler a spusťte cílovou aplikaci. Zatímco profiler je připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Po shromáždění příslušných dat zavřete aplikaci, ukončete pracovní proces Internetové informační služby (IIS) a potom vypněte profiler.

 Po dokončení profilování obnovte soubor *web.config* a webový server do původního stavu.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurace ASP.NET webové aplikace a webového serveru

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurace ASP.NET webové aplikace a webového serveru

1. Upravte soubor *web.config* cílové aplikace. Viz [Postup: Úprava souborů web.config na nástroj a profil dynamicky kompilované ASP.NET webových aplikací](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otevřete okno příkazového řádku v počítači, který je hostitelem webové aplikace.

3. Inicializovat proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv /globaltracegc**

     -nebo-

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** umožňuje shromažďování dat přidělení paměti.

    - **/globaltracegclife** umožňuje shromažďování dat přidělení paměti a data životnosti objektu.

4. Restartujte počítač.

## <a name="run-the-profiling-session"></a>Spuštění relace profilování

#### <a name="to-profile-the-aspnet-web-application"></a>Profilování webové aplikace ASP.NET

1. Spusťte profiler. Zadejte:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Možnost **/start:trace** inicializuje profiler.

   - Možnost **/output:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění profilovacích dat (.* vsp*).

     Můžete použít některou z následujících možností s **parametrem /start:trace.**

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro ASP.NET aplikace.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, který vlastní [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Název je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. ID relace je uvedeno ve **sloupci ID relace** na kartě **Procesy** ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Spustí profiler s pozastavenou kolekcí dat. Použití [/globalon](../profiling/globalon-and-globaloff.md) obnovit profilování. |
   | [/counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače `Config`výkonu procesoru určeného v . Informace o čítači jsou přidány k datům shromážděným při každé události profilování. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

2. Spusťte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci typickým způsobem.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat`TID`pro vlákno určené ID vlákna ( ).|

- Můžete také použít **Možnost VSPerfCmd.exe**[/mark](../profiling/mark.md) vložit profilování značku do datového souboru. Příkaz **/mark** přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze filtrovat data v sestavách profileru a zobrazeních dat.

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zavřete cílovou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, ukončete internetovou informační službu (IIS), ukončete profilovaný proces a potom vypněte profiler. Potom restartujte službu IIS.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci.

2. Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces resetováním Internetové informační služby (IIS). Zadejte:

    **IISReset /stop**

3. Vypněte profileru. Zadejte:

    **VSPerfCmd** [/vypnutí](../profiling/shutdown.md)

4. Restartujte službu IIS. Zadejte:

    **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Obnovení konfigurace aplikace a počítače
 Po dokončení veškerého profilování nahraďte soubor *web.config,* zrušte proměnné prostředí profilování a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] restartujte počítač, abyste obnovili server a aplikaci do původního stavu.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Obnovení konfigurace aplikace a počítače

1. Nahraďte soubor *web.config* kopií původního souboru.

2. (Nepovinné). Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfCmd /globaloff**

3. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
