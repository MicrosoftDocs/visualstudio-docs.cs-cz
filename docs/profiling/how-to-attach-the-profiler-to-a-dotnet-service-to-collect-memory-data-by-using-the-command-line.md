---
title: Připojení profileru ke službě .NET ke shromažďování dat paměti
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bd51a323ca369b30dcba32d3f480756d3e95f1f6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052725"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Postupy: připojení profileru ke službě .NET ke shromažďování dat paměti pomocí příkazového řádku
Tento článek popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku nástrojů pro profilaci k připojení profileru k [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] služby a shromažďování dat paměti. Můžete shromažďovat data o počtu a velikosti přidělení paměti a může také shromažďovat data o životnosti objektů v paměti.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* podadresáře [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Ke shromažďování dat paměti ze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] služby, můžete použít [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj k inicializaci příslušných proměnných prostředí v počítači, který je hostitelem služby. Počítač musí restartovat ho nakonfigurovat pro profilování.  

 Pak použijete [VSPerfCmd](../profiling/vsperfcmd.md) nástroj připojit profiler k procesu služby. Zatímco je profiler připojen ke službě, lze pozastavit a obnovit sběr dat.  

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a poté explicitně ukončen. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="attach-the-profiler"></a>Připojení profileru  

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Připojení profileru ke službě rozhraní .NET Framework  

1. V případě potřeby nainstalujte službu.  

2. Otevřete okno příkazového řádku.  

3. Inicializujte proměnné prostředí profilování. Typ:  

    **Vsperfclrenv –** {**/globalsamplegc /globalsamplegclife**} [**/samplelineoff**]  

   - Možnosti **/globalsamplegclife** a **/globalsamplegclife** zadejte typ shromažďovaných údajů paměti. Zadejte právě jeden z následujících možností.  

     **/globalsamplegc**  
     Povolí shromažďování dat o přidělování paměti.  

     **/globalsamplegclife**  
     Povoluje shromažďování data o přidělování paměti a životnosti objektů.  

   - **/Samplelineoff** možnost zakáže kolekci čísel datového řádku zdrojového kódu.  

4. Restartujte počítač a nastavit novou konfiguraci prostředí.  

5. V případě potřeby spusťte službu.  

6. Otevřete okno příkazového řádku. V případě potřeby přidáte cestu profileru do proměnné prostředí PATH.  

7. Spusťte profiler. Typ:  

    **Nástroj VSPerfCmd**[/start](../profiling/start.md) **: Ukázka**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start:sample** možnost inicializuje profiler.  

   - **/Output:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít jeden nebo více z následujících možností s **/start:sample** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro služby.  

   | Možnost | Popis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího procesu. Tato možnost je vyžadována, pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows. |
   | [/ crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Id relace je uvedeno ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje volitelný doména a uživatelské jméno pro přihlašovací účet, pod kterým je služba spuštěna. Účet pro přihlášení je uvedena ve sloupci přihlášení jako služby ve správci řízení služeb Windows. |
   | [/ crosssession&#124;cs](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor. |


8. Připojení profileru ke službě. Typ:  

    **Nástroj VSPerfCmd**[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[targetclr](../profiling/targetclr.md)**:**`Version`]    

   -   Zadejte ID procesu nebo název procesu služby. ID procesů a názvy všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

   -   **targetclr:** `Version` Určuje verzi modulu common language runtime (CLR) do profilu je do aplikace načtena více než jedna verze modulu runtime. Volitelné.  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Služba je spuštěná, ale můžete použít *VSPerfCmd.exe* možnosti zastavení a spuštění zápisu dat do datového souboru profilování. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |**/ attach:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces určený pomocí ID procesu nebo názvem procesu. **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, profiler nesmí pokračovat ve shromažďování dat. Zastavit shromažďování dat od aplikace profilované používáním metody vzorkování zastavením služby nebo voláním **VSPerfCmd / detach** možnost. Poté je zapotřebí zavolat **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování, ale konfigurace systému není obnovena, až po restartování počítače.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Proveďte jednu z následujících-li odpojit profiler od cílové aplikace:  

    -   Zastavte službu.  

         -nebo-  

    -   Typ **VSPerfCmd / odpojení**  

2.  Vypněte profiler. Typ:  

     **/ Shutdown VSPerfCmd**  

3.  (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – /globaloff**  

4.  Restartujte počítač.  

## <a name="see-also"></a>Viz také:  
 [Profil služby](../profiling/command-line-profiling-of-services.md)   
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)