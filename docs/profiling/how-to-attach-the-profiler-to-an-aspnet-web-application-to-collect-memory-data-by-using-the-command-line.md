---
title: Připojení profileru k ASP.NET ke shromáždění dat paměti
description: K připojení profileru k webové aplikaci ASP.NET použijte Visual Studio Nástroje pro profilaci a Získejte data o počtu a velikosti .NET Framework přidělení paměti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 918a370df43e2754721dd715ea6e2559e14160f8
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801600"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Postupy: Připojení profileru k webové aplikaci ASP.NET ke shromažďování dat paměti pomocí příkazového řádku
Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů příkazového řádku připojit profiler k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikaci a shromažďovat data o počtu a velikosti .NET Framework přidělení paměti. Můžete také shromažďovat data o životnosti objektů .NET Framework paměti.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromažďovat údaje o výkonu z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace, je nutné použít nástroj [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí v počítači, který je hostitelem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace. Pak musíte restartovat počítač a nakonfigurovat webový server pro profilování.

 Pak použijete nástroj [VSPerfCmd.exe](../profiling/vsperfcmd.md) k připojení profileru k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovnímu procesu, který je hostitelem vašeho webu. Když je profiler připojen k aplikaci, můžete pozastavit a obnovit sběr dat.

 Chcete-li ukončit relaci profilování, nesmí být profiler již připojen k aplikaci a musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="attach-the-profiler"></a>Připojení profileru

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Připojení profileru k webové aplikaci ASP.NET

1. Otevřete okno příkazového řádku.

2. Inicializujte proměnné prostředí pro profilování. Zadejte:

    **VSPerfCLREnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - Možnosti **/globalsamplegc** a **/globalsamplegclife** určují typ dat paměti, která se mají shromáždit.

        Zadejte jednu z následujících možností a jenom jednu z těchto možností.

       |Možnost|Popis|
       |------------|-----------------|
       |**/globalsamplegc**|Povolí shromažďování dat o přidělování paměti.|
       |**/globalsamplegclife**|Povoluje shromažďování dat přidělování paměti a dat o životnosti objektů.|

   - Možnost **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétním řádkům zdrojového kódu. Pokud je tato možnost zadána, data jsou přiřazena na úrovni funkce.

3. Pro nastavení nové konfigurace prostředí restartujte počítač.

4. Otevřete okno příkazového řádku. V případě potřeby nastavte proměnnou vyhledáte cesty k profileru.

5. Spusťte profiler. Zadejte:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Sample**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Možnost **/Start: Sample** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít kteroukoli z následujících možností.

   > [!NOTE]
   > Možnosti **/User** a **/CrossSession** se obvykle vyžadují pro aplikace ASP.NET.

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě procesy ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud aplikace ASP.NET běží v jiné relaci. Identifikátor relace je uvedena ve sloupci ID relace na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/waitstart](../profiling/waitstart.md) [**:** `Interval` ] | Určuje počet sekund, po který se má čekat na inicializaci profileru, než vrátí chybu. Pokud `Interval` parametr není zadán, bude Profiler čekat po neomezenou dobu. Ve výchozím nastavení funkce **/Start** vrátí hodnotu hned. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL). |

6. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Obvyklým způsobem spusťte webovou aplikaci.

7. Připojte profiler k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovnímu procesu. Zadejte:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - ID procesu `(PID)` Určuje ID procesu nebo název procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - **/targetclr:** `Version` Určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností **VSPerfCmd.exe** . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví sběrdat pro proces určený v `PID` .|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;: `ProcName` }]|**/Attach** začne shromažďovat data pro proces, který je určen ID procesu nebo názvem procesu. **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od webové aplikace. Shromažďování dat z aplikace, která je profilovaná pomocí metody vzorkování, můžete zastavit restartováním [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu nebo zavoláním možnosti **VSPerfCmd/detach** . Pak zavoláte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neresetuje, dokud se počítač nerestartuje.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

   - Typ **VSPerfCmd** [/detach](../profiling/detach.md)

      -nebo-

   - Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Zadejte:

     **IISReset/stop**

2. Vypněte profiler. Zadejte:

    **VSPerfCmd/shutdown**

3. Volitelné Vymažte proměnné prostředí profilování. Zadejte:

    **VSPerfCmd/globaloff**

4. Restartujte počítač. V případě potřeby restartujte Internetová informační služba (IIS). Zadejte:

    **IISReset/Start**

## <a name="see-also"></a>Viz také
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
