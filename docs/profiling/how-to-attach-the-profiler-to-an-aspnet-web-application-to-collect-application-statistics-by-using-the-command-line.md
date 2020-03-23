---
title: Připojení profileru k ASP.NET webové aplikaci za účelem získání statistik aplikací
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779074"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Postup: Připojení profileru k webové aplikaci ASP.NET ke shromažďování statistik aplikací pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje profilování připojit profiler k ASP.NET webové aplikace a shromažďovat statistiky výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Přidání dat interakce vrstvy do spuštění profilování vyžaduje specifické postupy s nástroji profilování příkazového řádku. Viz [Shromáždit data interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md).
>
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat údaje o výkonu z ASP.NET webové aplikace, musí být inicializovány příslušné proměnné prostředí a počítač, který je hostitelem ASP.NET webové aplikace, musí být restartován, aby byl webový server pro profilování nakonfigurován.

 Potom připojte profiler k ASP.NET pracovní proces, který je hostitelem webu. Když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, profiler musí být odpojen od profilované aplikace a profiler musí být explicitně vypnut. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Spuštění profileru a připojení k webové aplikaci ASP.NET

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Připojení profileru k webové aplikaci ASP.NET

1. Otevřete okno příkazového řádku.

2. Inicializovat proměnné prostředí profilování. Zadejte:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** umožňuje vzorkování.

   - **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétním řádkům zdrojového kódu. Pokud je tato možnost zadána, data jsou přiřazena pouze funkcím.

3. Restartujte počítač.

4. Spusťte profiler. Typ:**VSPerfCmd** [/start](../profiling/start.md)**:vzorek** `Options` [/výstup](../profiling/output.md)**:**`OutputFile`[ ]

   - Možnost **/start:sample** inicializuje profiler.

   - Možnost **/output:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     S možností **/start:sample** můžete použít některou z následujících možností.

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro ASP.NET aplikace.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Idenitifikátor relace je uveden ve sloupci ID relace na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru. |

5. Spusťte ASP.NET webovou aplikaci typickým způsobem.

6. Připojte profiler k pracovnímu procesu ASP.NET. Typ:**VSPerfCmd** [/attach](../profiling/attach.md) `ProcName`**:**`Sample Event`{`PID`&#124;} [ ] [[/targetclr](../profiling/targetclr.md)**:**`Version`]

   - `PID`určuje ID procesu pracovního procesu ASP.NET; `ProcName` určuje název pracovního procesu. ID procesů a názvy všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - Ve výchozím nastavení jsou data o výkonu vzorkována každých 10 000 000 nezastavených cyklů hodin procesoru. To je přibližně 100 krát za sekundu na 1GH procesoru. Můžete zadat jednu z následujících možností **VSPerfCmd** pro změnu intervalu cyklu hodin nebo pro určení jiné události vzorkování.

   |Ukázková událost|Popis|
   |------------------|-----------------|
   |[/časovač](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nezastavených hodinových `Interval`cyklů určených aplikací .|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Změní událost vzorkování na chyby stránky. Pokud `Interval` je zadán, nastaví počet chyb stránky mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)`:``Interval`[ ]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (syscalls). Pokud `Interval` je zadán, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Změní událost vzorkování a interval na čítač `Config`výkonu procesoru a interval, které jsou určeny v .|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Určuje verzi běžného jazyka runtime (CLR) pro profil, pokud je v aplikaci načtena více než jedna verze runtime.|

   - **targetclr:** `Version` určuje verzi CLR profilu, když je v aplikaci načtena více než jedna verze runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je aplikace spuštěna, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování `PID`dat pro proces, který je určen .|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces `PID` určený názvem nebo (ProcName). **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilování, ukončete webovou aplikaci a potom pomocí příkazu **IISReset** internetové informační služby (IIS) ukončete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Volání **VSPerfCmd** [/shutdown](../profiling/shutdown.md) možnost vypnout profiler a zavřete profilování datový soubor.

 Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování. Chcete-li použít nové nastavení prostředí, je nutné restartovat počítač.

 Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neobnoví, dokud není počítač restartován.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Jedním z následujících akcí odpojte profiler od cílové aplikace:

   - Typ **VSPerfCmd /detach**

      -nebo-

   - Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces.

2. Vypněte profileru. Typ:**VSPerfCmd** [/vypnutí](../profiling/shutdown.md)

3. (Nepovinné) Vymažte proměnné prostředí profilování. Zadejte:

    **VSPerfCmd /globaloff**

4. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
