---
title: Připojení profileru ke službě .NET ke shromažďování dat paměti
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777015"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Postupy: Připojení profileru ke službě .NET ke shromažďování dat paměti pomocí příkazového řádku
Tento článek popisuje, jak pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci připojit profiler ke službě .NET Framework a shromažďovat data paměti. Můžete shromažďovat data o počtu a velikosti přidělení paměti a můžete také shromažďovat data o životnosti paměťových objektů.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 Chcete-li shromažďovat data o paměti z .NET Framework služby, použijte nástroj [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) k inicializaci příslušných proměnných prostředí v počítači, který je hostitelem služby. Počítač je třeba restartovat, aby bylo možné ho nakonfigurovat pro profilaci.

 Pak použijete nástroj [VSPerfCmd](../profiling/vsperfcmd.md) k připojení profileru k procesu služby. I když je profiler připojen ke službě, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a poté explicitně ukončen. Ve většině případů doporučujeme na konci relace vymazat proměnné prostředí pro profilování.

## <a name="attach-the-profiler"></a>Připojení profileru

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Připojení profileru k .NET Framework službě

1. V případě potřeby nainstalujte službu.

2. Otevřete okno příkazového řádku.

3. Inicializujte proměnné prostředí pro profilování. Typ:

    **VSPerfCLREnv** { **/globalsamplegc/globalsamplegclife**} [ **/samplelineoff**]

   - Možnosti **/globalsamplegclife** a **/globalsamplegclife** určují typ dat paměti, která se mají shromáždit. Zadejte jednu z následujících možností a jenom jednu z těchto možností.

     **/globalsamplegc** Povolí shromažďování dat o přidělování paměti.

     **/globalsamplegclife** Povoluje shromažďování dat přidělování paměti a dat o životnosti objektů.

   - Možnost **/samplelineoff** zakáže shromažďování dat o číslech řádků zdrojového kódu.

4. Pro nastavení nové konfigurace prostředí restartujte počítač.

5. V případě potřeby službu spusťte.

6. Otevřete okno příkazového řádku. V případě potřeby přidejte cestu profileru do proměnné prostředí PATH.

7. Spusťte profiler. Typ:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Sample**  [/Output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Možnost **/Start: Sample** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile` Určuje název a umístění souboru dat profilování (. vsp).

     Pomocí možnosti **/Start: Sample** můžete použít jednu nebo více z následujících možností.

   > [!NOTE]
   > Pro služby jsou obvykle vyžadovány možnosti **/User** a **/CrossSession** .

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní proces. Tato možnost je vyžadována, pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě procesy ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud aplikace ASP.NET běží v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Určuje volitelnou doménu a uživatelské jméno přihlašovacího účtu, pod kterým se služba spouští. Přihlašovací účet se zobrazí ve sloupci přihlásit se jako služba ve Správci řízení služeb systému Windows. |
   | [/CrossSession&#124;cs](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL). |

8. Připojte profiler ke službě. Typ:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md) **:** `Version`]

   - Zadejte buď ID procesu, nebo název procesu služby. ID procesů a názvy všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

   - **targetclr:** `Version` určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu runtime. Volitelné.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je služba spuštěná, můžete k zastavení a spuštění zápisu dat do datového souboru profileru použít možnosti *VSPerfCmd. exe* . Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí ( **/GlobalOn**) nebo zastaví shromažďování dat ( **/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí ( **/ProcessOn**) nebo zastaví sběrdat pro proces určený identifikátorem procesu (`PID`).|
    |**/Attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/Attach** začne shromažďovat data pro proces určený ID procesu nebo názvem procesu. **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán konkrétní proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler nesmí shromažďovat data. Shromažďování dat z aplikace profilované pomocí metody vzorkování můžete zastavit zastavením služby nebo zavoláním možnosti **VSPerfCmd/detach** . Potom zavoláte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pro vypnutí profileru a zavření souboru dat profilování. Příkaz **VSPerfCLREnv/globaloff** vymaže proměnné prostředí profilování, ale konfigurace systému se neresetuje, dokud se počítač nerestartuje.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

    - Zastavte službu.

         -nebo-

    - Typ **VSPerfCmd/detach**

2. Vypněte profiler. Typ:

     **VSPerfCmd/shutdown**

3. Volitelné Vymažte proměnné prostředí profilování. Typ:

     **VSPerfClrEnv/globaloff**

4. Restartujte počítač.

## <a name="see-also"></a>Viz také:
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
