---
title: Připojení profileru k webové aplikaci ASP.NET, aby se získala Statistika aplikace
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 549e43f403b19d8832e00277f826cdc7b276b747
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779074"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru k webové aplikaci ASP.NET ke shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů příkazového řádku připojit profiler k webové aplikaci ASP.NET a shromažďovat statistiku výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku. Viz [shromáždění dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).
>
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromažďovat údaje o výkonu z webové aplikace ASP.NET, musí být inicializovány příslušné proměnné prostředí a počítač, který je hostitelem webové aplikace ASP.NET, musí být restartován, aby bylo možné konfigurovat webový server pro profilování.

 Pak Připojte profiler k pracovnímu procesu ASP.NET, který je hostitelem vašeho webu. Když je profiler připojen k aplikaci, můžete pozastavit a obnovit sběr dat.

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od profilované aplikace a musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Spuštění profileru a připojení k webové aplikaci ASP.NET

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Připojení profileru k webové aplikaci ASP.NET

1. Otevřete okno příkazového řádku.

2. Inicializujte proměnné prostředí pro profilování. Typ:

    **VSPerfCLREnv/globalsampleon** [ **/samplelineoff**]

   - **/globalsampleon** umožňuje vzorkování.

   - **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétním řádkům zdrojového kódu. Je-li tato možnost zadána, jsou data přiřazena pouze funkcím.

3. Restartujte počítač.

4. Spusťte profiler. Typ:**VSPerfCmd** [/Start](../profiling/start.md) **: Sample** [/Output](../profiling/output.md) **:** `OutputFile`[`Options`]

   - Možnost **/Start: Sample** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít jednu z následujících možností.

   > [!NOTE]
   > Možnosti **/User** a **/CrossSession** se obvykle vyžadují pro aplikace ASP.NET.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **uživatelské jméno** na kartě **procesy** ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud aplikace ASP.NET běží v jiné relaci. Identifikátor relace je uvedena ve sloupci ID relace na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL). |

5. Spusťte webovou aplikaci v ASP.NET obvyklým způsobem.

6. Připojte profiler k pracovnímu procesu ASP.NET. Typ:**VSPerfCmd** [/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md) **:** `Version`]

   - `PID` Určuje ID procesu pracovního procesu ASP.NET; `ProcName` Určuje název pracovního procesu. ID procesů a názvy všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - Ve výchozím nastavení jsou data o výkonu Navzorkovaná každých 10 000 000 hodinových cyklů procesoru. To je přibližně 100 časů za sekundu na frekvencí 1 GHz procesoru. Můžete zadat jednu z následujících možností **VSPerfCmd** pro změnu intervalu hodinových cyklů nebo zadání jiné události vzorkování.

   |Ukázková událost|Popis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:** `Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů, které jsou určeny `Interval`.|
   |[/PF](../profiling/pf.md)[ **:** `Interval`]|Změní událost vzorkování na chyby stránkování. Je-li zadán `Interval`, aplikace nastaví počet chyb stránek mezi vzorky. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (voláním). Je-li zadán `Interval`, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/Counter](../profiling/counter.md) **:** `Config`|Změní událost vzorkování a interval na čítač výkonu procesoru a interval, který je určen v `Config`.|
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime.|

   - **targetclr:** `Version` určuje verzi modulu CLR, která se má profilovat, pokud je v aplikaci načtena více než jedna verze modulu runtime. Volitelné.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd. exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí ( **/GlobalOn**) nebo zastaví shromažďování dat ( **/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` **/ProcessOff:** `PID`|Spustí ( **/ProcessOn**) nebo zastaví sběrdat pro proces určený `PID`.|
    |[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/Attach** začne shromažďovat data pro proces určený `PID` nebo názvem procesu (ProcName). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zavřete webovou aplikaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a pak pomocí příkazu Internetová informační služba (IIS) **iisreset** zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Zavolejte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pro vypnutí profileru a zavření souboru dat profilování.

 Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování. Chcete-li použít nové nastavení prostředí, je nutné restartovat počítač.

 Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neresetuje, dokud se počítač nerestartuje.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

   - Typ **VSPerfCmd/detach**

      -nebo-

   - Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces.

2. Vypněte profiler. Typ:**VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. Volitelné Vymažte proměnné prostředí profilování. Typ:

    **VSPerfCmd/globaloff**

4. Restartujte počítač.

## <a name="see-also"></a>Viz také:
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
