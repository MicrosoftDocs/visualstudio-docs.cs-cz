---
title: 'VSPerfCmd: Připojte profiler k nativní službě, abyste získali data souběžnosti.'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 705e55363f4f8657da20fe66cd4369188f133cdb
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776605"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru k nativní službě ke shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje, jak pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci připojit profiler k nativní službě (C/C++) a shromažďovat data o souběžnosti procesů a vláken pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 I když je profiler připojen ke službě, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, nesmí být profiler již připojen ke službě a musí být explicitně vypnut.

## <a name="attach-the-profiler"></a>Připojení profileru
 K připojení profileru k nativní službě použijte možnosti **VSPerfCmd/Start** a **/Attach** pro inicializaci profileru a připojte ho k cílové aplikaci. V jednom příkazovém řádku můžete zadat **/Start** a **/Attach** a jejich příslušné možnosti. Můžete také přidat možnost **/globaloff** pro pozastavení sběru dat na začátku cílové aplikace. Pak můžete pomocí **/GlobalOn** začít shromažďovat data.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Připojení profileru k nativní službě

1. Pokud služba není spuštěná, spusťte ji.

2. Spusťte profiler zadáním následujícího příkazu na příkazovém řádku:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start:/Output pro Concurrency** : `OutputFile` [`Options`]

   - Parametr [/Output](../profiling/output.md) **:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     V následující tabulce můžete použít libovolnou možnost s možností **/Start** .

   > [!NOTE]
   > Většina služeb vyžaduje možnost **/User** a **/CrossSession** .

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`UserName` | Určuje volitelnou doménu a uživatelské jméno účtu, kterému má být udělen přístup k profileru. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL). |

3. Připojte profiler ke službě zadáním následujícího příkazu na příkazovém řádku:

    **VSPerfCmd/attach:** `PID`

    `PID` Určuje ID procesu nebo název procesu cílové aplikace. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd. exe* . Řízením shromažďování dat můžete shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Dvojice možností v následující tabulce začátek a zastavení shromažďování dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí ( **/GlobalOn**) nebo zastaví shromažďování dat ( **/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí ( **/ProcessOn**) nebo zastaví shromažďování dat ( **/ProcessOff**) pro proces, který určuje ID procesu (`PID`).|
    |[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/Attach** začne shromažďovat data pro proces, který určuje ID procesu (`PID`) nebo název procesu (*ProcName*). **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z nativní služby, která je profilovaná s metodou souběžnosti, můžete zastavit zastavením služby nebo vyvoláním možnosti **VSPerfCmd/detach** . Potom vyvoláte možnost **VSPerfCmd/shutdown** pro vypnutí profileru a zavření souboru dat profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Odpojte Profiler od cílové aplikace zastavením služby nebo zadáním následujícího příkazu na příkazovém řádku:

     Typ **VSPerfCmd/detach**

2. Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
