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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776467"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Postup: Připojení profileru k webové aplikaci ASP.NET ke shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku profilování připojit profiler k ASP.NET aplikaci a shromažďovat data souběžnosti procesů a vláken.

Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat data souběžnosti, připojte profiler k pracovnímu procesu ASP.NET, který hostuje váš web. Zatímco profiler je připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, profiler již nesmí být připojen k aplikaci a profiler musí být explicitně vypnut. Ve většině případů byste měli vymazat proměnné prostředí profilování na konci relace.

## <a name="attach-the-profiler"></a>Připojte profiler

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Připojení profileru k ASP.NET aplikaci

1. Spusťte profiler zadáním následujícího příkazu:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:souběžnost /výstup:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md) inicializuje profiler pro shromažďování dat konfliktů prostředků.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít libovolnou možnost v následující tabulce s **parametrem /start.**

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain\`[ ]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, kterému má být udělen přístup k profileru. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

2. Spusťte aplikaci ASP.NET typickým způsobem.

3. Připojit profiler k pracovnímu procesu ASP.NET zadáním následujícího příkazu:**VSPerfCmd /attach:** `PID` [**/targetclr:**`Version`]

   - `PID`určuje ID nebo název ASP.NET pracovního procesu. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` určuje verzi clr (COMMON Language runtime) pro profil, když je v aplikaci načtena více než jedna verze runtime. Tento parametr je volitelný.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 V době, kdy je aplikace spuštěna, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízením shromažďování dat můžete shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Dvojice možností VSPerfCmd v následující tabulce spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:**  `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování`PID`dat pro proces, který určuje ID procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces, který`PID`určuje ID procesu ( ) nebo název procesu (*ProcName).* **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace, která je profilována metodou souběžnosti, můžete zastavit restartováním pracovního procesu ASP.NET nebo vyvoláním možnosti **VSPerfCmd /detach.** Potom vyvolat **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neobnoví, dokud není počítač restartován.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Odpojte profiler od cílové aplikace jeho zavřením nebo zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd /odpojit**

2. Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)

## <a name="see-also"></a>Viz také
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Rychlé profilování webových stránek s VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
