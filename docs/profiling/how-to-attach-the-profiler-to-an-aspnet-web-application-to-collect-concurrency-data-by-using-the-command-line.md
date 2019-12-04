---
title: Připojení profileru k aplikaci ASP.NET ke shromažďování dat souběžnosti
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 04745140c3f92b3d601a03ddbcd68259b3959364
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776467"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru k webové aplikaci ASP.NET ke shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, jak pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci připojit profiler k aplikaci ASP.NET a shromažďovat data o procesech a souběžnosti vláken.

Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromáždit data souběžnosti, Připojte profiler k pracovnímu procesu ASP.NET, který je hostitelem vašeho webu. I když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, nesmí být profiler již připojen k aplikaci a musí být explicitně vypnut. Ve většině případů byste měli na konci relace vymazat proměnné prostředí profilování.

## <a name="attach-the-profiler"></a>Připojení profileru

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Připojení profileru k aplikaci ASP.NET

1. Spusťte profiler zadáním následujícího příkazu:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start:/Output pro Concurrency** : `OutputFile` [`Options`]

   - Možnost [/Start](../profiling/start.md) inicializuje profiler pro shromažďování dat o kolizí prostředků.

   - Parametr [/Output](../profiling/output.md) **:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     V následující tabulce můžete použít libovolnou možnost s možností **/Start** .

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, kterému má být udělen přístup k profileru. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány samostatně (. *ETL*). |

2. Obvyklým způsobem spusťte aplikaci ASP.NET.

3. Připojte profiler k pracovnímu procesu ASP.NET zadáním následujícího příkazu:**VSPerfCmd/attach:** `PID` [ **/targetclr:** `Version`]

   - `PID` Určuje ID nebo název pracovního procesu ASP.NET. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime. Tento parametr je volitelný.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd. exe* . Řízením shromažďování dat můžete shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Páry možností VSPerfCmd v následující tabulce začátek a zastavení shromažďování dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí ( **/GlobalOn**) nebo zastaví shromažďování dat ( **/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID`[ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí ( **/ProcessOn**) nebo zastaví shromažďování dat ( **/ProcessOff**) pro proces, který určuje ID procesu (`PID`).|
    |[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/Attach** začne shromažďovat data pro proces, který určuje ID procesu (`PID`) nebo název procesu (*ProcName*). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace, která je profilovaná metodou souběžnosti, můžete zastavit restartováním pracovního procesu ASP.NET nebo vyvoláním možnosti **VSPerfCmd/detach** . Potom vyvoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neresetuje, dokud se počítač nerestartuje.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Odpojte Profiler z cílové aplikace jeho zavřením nebo zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd/detach**

2. Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také:
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
