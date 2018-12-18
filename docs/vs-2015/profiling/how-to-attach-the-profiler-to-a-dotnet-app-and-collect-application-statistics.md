---
title: 'Postupy: připojení Profiler k samostatné aplikaci .NET Framework a shromažďování statistik aplikace pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd0375663882363a1b3379c9a20f2b2042d495b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742356"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru k samostatné aplikaci .NET Framework a shromažďování statistik aplikace pomocí příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci k připojení profileru k běžící samostatné (klientské) aplikaci rozhraní .NET Framework a shromáždit statistiky výkonu pomocí metody vzorkování.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v podadresáři nástroje \Team Tools\Performance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Přidání dat interakce vrstvy do běhu profilování vyžaduje zvláštní procedury s nástroji pro profilaci příkazového řádku. Zobrazit [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Ke shromažďování dat výkonu z aplikace rozhraní .NET Framework, musí inicializovat příslušné proměnné prostředí před spuštěním cílové aplikace. Když je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat.  

 Chcete-li ukončit relaci profilování, musí profiler již připojen k aplikaci a profiler musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace profilování vyčistit proměnné prostředí profilování.  

## <a name="attaching-the-profiler"></a>Připojuje Profiler  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojit Profiler k běžící aplikaci rozhraní .NET Framework  

1. Otevřete okno příkazového řádku.  

2. Inicializujte proměnné prostředí profilování. Typ:  

    **Vsperfclrenv – /sampleon** [**/samplelineoff**]  

   -   **/Samplelineoff** možnost zakáže kolekci čísel datového řádku zdrojového kódu.  

3. Spusťte profiler. Typ:  

    **/Start:sample VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Ukázka** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některou z následujících možností s **/start:sample** možnost.  

   |                                 Možnost                                  |                                                                                                  Popis                                                                                                  |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje volitelný doména a uživatelské jméno účtu vlastnícího profilovaný proces. Tato možnost je vyžadována, pouze pokud profilované aplikace byl spuštěn pod jiným než přihlášeným uživatelem. |
   |              [/ crosssession](../profiling/crosssession.md)              |   Umožňuje profilování procesů v jiných přihlašovacích relacích. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci.    |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                   Určuje čítač výkonu Windows má být shromážděn během profilování.                                                                   |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                 Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.                                 |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                   Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.                                    |


4. V případě potřeby spusťte cílovou aplikaci standardním způsobem.  

5. Připojení profileru k cílové aplikaci. Typ:  

    **Nástroj VSPerfCmd / připojit:**{`PID`&#124;`ProcessName`} [`Sample Event`] [**targetclr:**`Version`]  

   -   `PID` Určuje ID procesu cílové aplikace. `ProcessName` Určuje název procesu. Všimněte si, že pokud zadáte `ProcessName` a běží víc procesů, které mají stejný název, výsledky nepředvídatelné. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

   -   [targetclr](../profiling/targetclr.md) **:** `Version` Určuje verzi modulu common language runtime (CLR) do profilu je do aplikace načtena více než jedna verze modulu runtime. Volitelné.  

   -   Ve výchozím nastavení, data výkonu vzorkována každých procesoru 10 000 000 nepřerušených hodinových cyklů. To je přibližně jednou za 10 sekund u procesoru s frekvencí 1 GHz. Můžete zadat jednu z následujících možností, chcete-li změnit intervalu hodinových cyklů nebo změnu událostí vyvolávajících. [targetclr](../profiling/targetclr.md)**:** `Version` Určuje verzi modulu CLR do profilu je do aplikace načtena více než jedna verze modulu runtime. Volitelné.  

   |||  
   |-|-|  
   |Událost vzorku|Popis|  
   |[/Timer](../profiling/timer.md) **:** `Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů, které jsou určeny `Interval`.|  
   |[/PF](../profiling/pf.md) [**:**`Interval`]|Změní událost odběru vzorků na chyby stránek. Pokud `Interval` je určen, nastaví počet chyb stránek mezi vzorky. Výchozí hodnota je 10.|  
   |[/ sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Změní událost odběru vzorků na volání systému z procesu do jádra operačního systému (syscalls). Pokud `Interval` je určen, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|  
   |[/ Čítač](../profiling/counter.md) **:** `Config`|Změní událost odběru vzorků a interval na čítač výkonu procesoru a interval, ve stanoveném `Config`.|  

   -  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Pokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do datového souboru profilování pomocí **VSPerfCmd.exe** možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces, který je určen `PID`.|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces určený pomocí `PID` nebo názvem procesu (ProcName). **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Je-li odpojit profiler od aplikace profilované za použití metody vzorkování ukončením aplikace nebo zavoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí zavolat **VSPerfCmd/Shutdown** možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv / off** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Proveďte jeden z následujících kroků-li odpojit profiler od cílové aplikace:  

    -   Typ **VSPerfCmd / odpojení**  

         -nebo-  

    -   Ukončete cílovou aplikaci.  

2.  Vypněte profiler. Typ:  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

3.  (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – / vypnuté**  

## <a name="see-also"></a>Viz také  
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)



