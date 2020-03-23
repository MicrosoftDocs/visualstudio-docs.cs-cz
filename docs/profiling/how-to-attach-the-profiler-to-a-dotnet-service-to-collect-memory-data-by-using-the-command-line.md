---
title: Připojení profileru ke službě .NET ke shromažďování paměťových dat
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 94ea4f38ccebc1015419e2254b06033fa17a09a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777015"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Postupy: Připojení profileru ke službě .NET ke shromažďování dat paměti pomocí příkazového řádku
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje profilování připojit profiler ke službě rozhraní .NET Framework a shromažďovat data paměti. Můžete shromažďovat data o počtu a velikosti přidělení paměti a můžete také shromažďovat data o životnosti paměťových objektů.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat paměťová data ze služby .NET Framework, použijte nástroj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí v počítači, který je hostitelem služby. Počítač musí být restartován, aby byl nakonfigurován pro profilování.

 Potom pomocí nástroje [VSPerfCmd](../profiling/vsperfcmd.md) připojit profiler k procesu služby. Zatímco profiler je připojen ke službě, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a poté explicitně ukončen. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="attach-the-profiler"></a>Připojte profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Připojení profileru ke službě rozhraní .NET Framework

1. V případě potřeby nainstalujte službu.

2. Otevřete okno příkazového řádku.

3. Inicializovat proměnné prostředí profilování. Zadejte:

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]

   - Možnosti **/globalsamplegclife** a **/globalsamplegclife** určují typ dat paměti, která mají být shromažďována. Zadejte jednu a pouze jednu z následujících možností.

     **/globalsamplegc** Umožňuje shromažďování dat přidělení paměti.

     **/globalsamplegclife** Umožňuje shromažďování dat přidělení paměti i dat životnosti objektu.

   - Možnost **/samplelineoff** zakáže shromažďování dat čísla řádku zdrojového kódu.

4. Chcete-li nastavit novou konfiguraci prostředí, restartujte počítač.

5. V případě potřeby spusťte službu.

6. Otevřete okno příkazového řádku. V případě potřeby přidejte cestu profileru do proměnné prostředí PATH.

7. Spusťte profiler. Zadejte:

    **VSPerfCmd**  [/start](../profiling/start.md) **:vzorek**  [/výstup](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Možnost **/start:sample** inicializuje profiler.

   - Možnost **/output:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     S možností **/start:sample** můžete použít jednu nebo více z následujících možností.

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro služby.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který proces vlastní. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel jiný než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě Procesy ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje volitelnou doménu a uživatelské jméno přihlašovacího účtu, pod kterým je služba spuštěna. Přihlašovací účet je uveden ve sloupci Přihlásit se jako služby ve Správci řízení služeb systému Windows. |
   | [/crosssession&#124;cs](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru. |

8. Připojte profiler ke službě. Zadejte:

    **VSPerfCmd**[/attach](../profiling/attach.md) **:**`PID` {&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   - Zadejte ID procesu nebo název procesu služby. ID procesů a názvy všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - **targetclr:** `Version` určuje verzi clr (COMMON Language runtime) pro profil, když je v aplikaci načtena více než jedna verze runtime. Nepovinný parametr.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco služba je spuštěna, můžete použít *VSPerfCmd.exe* možnosti zastavit a spustit zápis dat do datového souboru profileru. Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |**/attach:**`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces určený ID procesu nebo název procesu. **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace profilované metodou vzorkování můžete zastavit zastavením služby nebo voláním možnosti **VSPerfCmd /detach.** Potom volání **VSPerfCmd** [/shutdown](../profiling/shutdown.md) možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neobnoví, dokud není počítač restartován.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Jedním z následujících akcí odpojte profiler od cílové aplikace:

    - Zastavte službu.

         -nebo-

    - Typ **VSPerfCmd /detach**

2. Vypněte profileru. Zadejte:

     **VSPerfCmd /vypnutí**

3. (Nepovinné) Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv /globaloff**

4. Restartujte počítač.

## <a name="see-also"></a>Viz také
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
