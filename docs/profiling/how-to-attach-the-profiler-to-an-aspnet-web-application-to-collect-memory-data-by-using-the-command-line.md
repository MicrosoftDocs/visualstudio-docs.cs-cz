---
title: Připojení profileru k aplikaci ASP.NET ke shromažďování paměťových dat
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: f2b9ea7799656b0dd7dacd35bde62dc84aea08dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779061"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Postup: Připojení profileru k ASP.NET webové aplikaci ke shromažďování paměťových dat pomocí příkazového řádku
Tento článek popisuje použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů příkazového řádku Nástroje profilování k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] připojení profileru k webové aplikaci a shromažďování dat o počtu a velikosti přidělení paměti rozhraní .NET Framework. Můžete také shromažďovat data o životnosti objektů paměti rozhraní .NET Framework.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] údaje o výkonu z webové aplikace, je nutné použít nástroj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] inicializaci příslušných proměnných prostředí v počítači, který je hostitelem webové aplikace. Potom je nutné restartovat počítač a nakonfigurovat webový server pro profilování.

 Potom pomocí nástroje [VSPerfCmd.exe](../profiling/vsperfcmd.md) připojit profiler [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] k pracovnímu procesu, který je hostitelem webu. Když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, profiler již nesmí být připojen k aplikaci a profiler musí být explicitně vypnut. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="attach-the-profiler"></a>Připojte profiler

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Připojení profileru k webové aplikaci ASP.NET

1. Otevřete okno příkazového řádku.

2. Inicializovat proměnné prostředí profilování. Zadejte:

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - Možnosti **/globalsamplegc** a **/globalsamplegclife** určují typ dat paměti, která mají být shromažďována.

        Zadejte jednu a pouze jednu z následujících možností.

       |Možnost|Popis|
       |------------|-----------------|
       |**/globalsamplegc**|Umožňuje shromažďování dat přidělení paměti.|
       |**/globalsamplegclife**|Umožňuje shromažďování dat přidělení paměti i dat životnosti objektu.|

   - Možnost **/samplelineoff** zakáže přiřazení shromážděných dat na určité řádky zdrojového kódu. Pokud je tato možnost zadána, data jsou přiřazena na úrovni funkce.

3. Chcete-li nastavit novou konfiguraci prostředí, restartujte počítač.

4. Otevřete okno příkazového řádku. V případě potřeby nastavte proměnnou prostředí dráhy profileru.

5. Spusťte profiler. Zadejte:

    **VSPerfCmd**  [/start](../profiling/start.md) **:vzorek**  [/výstup](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Možnost **/start:sample** inicializuje profiler.

   - Možnost **/output:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:sample.**

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro ASP.NET aplikace.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě Procesy ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Idenitifikátor relace je uveden ve sloupci ID relace na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md) [**:**`Interval`] | Určuje počet sekund čekání na inicializaci profileru, než vrátí chybu. Pokud `Interval` není zadán, profiler čeká neomezeně dlouho. Ve výchozím nastavení **/start** vrátí okamžitě. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru. |

6. Spusťte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci typickým způsobem.

7. Připojte profiler k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovnímu procesu. Zadejte:

    **VSPerfCmd**[/attach](../profiling/attach.md) **:**`PID` {&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   - ID `(PID)` procesu určuje ID procesu nebo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] název procesu pracovního procesu. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - **/targetclr:** `Version` určuje verzi clr (COMMON Language runtime) pro profil, když je v aplikaci načtena více než jedna verze runtime.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 V době, kdy je aplikace spuštěna, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do datového souboru profileru pomocí možností **VSPerfCmd.exe.** Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) `PID`shromažďování dat pro proces určený .|
    |**/attach:**`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)`ProcName`[**:**{`PID`&#124;: }]|**/attach** začne shromažďovat data pro proces, který je určen ID procesu nebo název procesu. **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od webové aplikace. Shromažďování dat z aplikace, která je profilována metodou vzorkování, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] můžete zastavit restartováním pracovního procesu nebo voláním možnosti **VSPerfCmd /detach.** Potom volání **VSPerfCmd** [/shutdown](../profiling/shutdown.md) možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neobnoví, dokud není počítač restartován.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Proveďte jeden z následujících kroků, chcete-li odpojit profiler od cílové aplikace:

   - Typ **VSPerfCmd** [/detach](../profiling/detach.md)

      -nebo-

   - Zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Zadejte:

     **IISReset /stop**

2. Vypněte profileru. Zadejte:

    **VSPerfCmd /vypnutí**

3. (Nepovinné) Vymažte proměnné prostředí profilování. Zadejte:

    **VSPerfCmd /globaloff**

4. Restartujte počítač. V případě potřeby restartujte Internetovou informační službu (IIS). Zadejte:

    **IISReset /start**

## <a name="see-also"></a>Viz také
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
