---
title: Připojení profileru k ASP.NET jsme aplikaci ke shromažďování statistik aplikace
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 32197d50bbc9826261584ba18b5b83f8519b7a38
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063820"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Postupy: připojení profileru k webové aplikaci ASP.NET ke shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku nástrojů pro profilaci k připojení profileru k webové aplikaci ASP.NET a shromáždit statistiky výkonu pomocí metody vzorkování.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
>  Přidání dat interakce vrstvy do běhu profilování vyžaduje zvláštní procedury s nástroji pro profilaci příkazového řádku. Zobrazit [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
> 
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* podadresáře [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Ke shromažďování dat výkonu z webové aplikace ASP.NET, je nutné inicializovat příslušné proměnné prostředí a restartování počítače, který je hostitelem aplikace technologie ASP.NET do konfigurace webového serveru pro profilování.  

 Poté připojíte profiler k pracovnímu procesu ASP.NET, který je hostitelem vašeho webu. Když je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat.  

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od profilované aplikace a profiler musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Spusťte profiler a připojení k webové aplikaci ASP.NET  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>K připojení profileru k webové aplikaci ASP.NET  

1. Otevřete okno příkazového řádku.  

2. Inicializujte proměnné prostředí profilování. Typ:  

    **Vsperfclrenv – /globalsampleon** [**/samplelineoff**]  

   -   **/globalsampleon** umožňuje vzorkování.  

   -   **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétnímu zdroji řádků kódu. Pokud je tato možnost zadána, data přiřazena pouze funkcí.  

3. Restartujte počítač.  

4. Spusťte profiler. Typ:**VSPerfCmd** [/start](../profiling/start.md)**: Ukázka** [/output](../profiling/output.md)**:**`OutputFile`[`Options`]  

   - **/Start:sample** možnost inicializuje profiler.  

   - **/Output:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některou z následujících možností s **/start:sample** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro aplikace ASP.NET.  

   | Možnost | Popis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uveden v **uživatelské jméno** sloupec **procesy** karty ve Správci úloh Windows. |
   | [/ crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Relace je vypsán ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor. |


5. Spusťte webovou aplikaci ASP.NET obvyklým způsobem.  

6. Připojte profiler k pracovnímu procesu ASP.NET. Typ:**VSPerfCmd** [/ attach](../profiling/attach.md)**:**{`PID`&#124;`ProcName`} [`Sample Event`] [[targetclr](../profiling/targetclr.md) **:**`Version`]  

   -   `PID` Určuje ID procesu pracovního procesu ASP.NET; `ProcName` Určuje název pracovního procesu. ID procesů a názvy všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

   -   Ve výchozím nastavení, data výkonu vzorkována každých procesoru 10 000 000 nepřerušených hodinových cyklů. To je přibližně 100krát za sekundu u procesoru s frekvencí 1 GHz. Můžete určit jednu z následujících **VSPerfCmd** možnosti změnit intervalu hodinových cyklů nebo změnu událostí vyvolávajících.  

   |Událost vzorku|Popis|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:** `Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů, které jsou určeny `Interval`.|  
   |[/PF](../profiling/pf.md)[**:**`Interval`]|Změní událost odběru vzorků na chyby stránek. Pokud `Interval` je určen, nastaví počet chyb stránek mezi vzorky. Výchozí hodnota je 10.|  
   |[/ sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Změní událost odběru vzorků na volání systému z procesu do jádra operačního systému (syscalls). Pokud `Interval` je určen, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|  
   |[/ Čítač](../profiling/counter.md) **:** `Config`|Změní událost odběru vzorků a interval na čítač výkonu procesoru a interval, ve stanoveném `Config`.|  
   |[targetclr](../profiling/targetclr.md) **:** `Version`|Určuje verzi modulu common language runtime (CLR), která má být profilována je do aplikace načtena více než jedna verze modulu runtime.|  

   -   **targetclr:** `Version` Určuje verzi modulu CLR do profilu je do aplikace načtena více než jedna verze modulu runtime. Volitelné.  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Když je aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s použitím *VSPerfCmd.exe* možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces, který je určen `PID`.|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces určený pomocí `PID` nebo názvem procesu (ProcName). **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, zavřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci a pak pomocí Internetové informační služby (IIS) **IISReset** příkaz pro zavření [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Volání **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost se profiler vypne a uzavře soubor dat profilování.  

 **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování. Po restartování počítače-li použít nové nastavení prostředí.  

 **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování, ale konfigurace systému není obnovena, až po restartování počítače.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1. Proveďte jednu z následujících-li odpojit profiler od cílové aplikace:  

   - Typ **VSPerfCmd / odpojení**  

      -nebo-  

   - Zavřít [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces.  

2. Vypněte profiler. Typ:**VSPerfCmd**  [ /Shutdown](../profiling/shutdown.md)  

3. (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

    **Nástroj VSPerfCmd /globaloff**  

4. Restartujte počítač.  

## <a name="see-also"></a>Viz také:  
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Zobrazení dat metod vzorkování](../profiling/profiler-sampling-method-data-views.md)