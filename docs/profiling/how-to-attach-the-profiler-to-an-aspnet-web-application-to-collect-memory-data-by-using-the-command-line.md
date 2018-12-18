---
title: Připojení profileru k aplikaci ASP.NET ke shromažďování dat paměti
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7f5c592733cc43101cb5cf022caf84892a55af7a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052955"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Postupy: připojení profileru k webové aplikaci ASP.NET ke shromažďování dat paměti pomocí příkazového řádku
Tento článek popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku nástrojů pro profilaci k připojení profileru k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci a shromažďování dat o počtu a velikosti přidělení paměti rozhraní .NET Framework. Může také shromažďovat data o životnosti objektů paměti rozhraní .NET Framework.  

> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* podadresáře [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Ke shromažďování dat výkonu z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, je nutné použít [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj k inicializaci příslušných proměnných prostředí v počítači, který je hostitelem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci. Musíte pak restartujte počítač nakonfigurovat webový server pro profilování.  

 Pak použijete [VSPerfCmd.exe](../profiling/vsperfcmd.md) nástroj pro připojení profileru k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces, který je hostitelem vašeho webu. Když je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat.  

 Chcete-li ukončit relaci profilování, musí profiler již připojen k aplikaci a profiler musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="attach-the-profiler"></a>Připojení profileru  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Připojení profileru k webové aplikaci ASP.NET  

1. Otevřete okno příkazového řádku.  

2. Inicializujte proměnné prostředí profilování. Typ:  

    **Vsperfclrenv –** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]  

   -   Možnosti **/globalsamplegc** a **/globalsamplegclife** zadejte typ shromažďovaných údajů paměti.  

        Zadejte právě jeden z následujících možností.  

       |Možnost|Popis|  
       |------------|-----------------|  
       |**/globalsamplegc**|Povolí shromažďování dat o přidělování paměti.|  
       |**/globalsamplegclife**|Povoluje shromažďování data o přidělování paměti a životnosti objektů.|  

   -   Možnost **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétnímu zdroji řádků kódu. Pokud je tato možnost zadána, je přiřazen data na úrovni funkce.  

3. Restartujte počítač a nastavit novou konfiguraci prostředí.  

4. Otevřete okno příkazového řádku. V případě potřeby nastavte proměnné prostředí path profileru.  

5. Spusťte profiler. Typ:  

    **Nástroj VSPerfCmd**[/start](../profiling/start.md) **: Ukázka**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start:sample** možnost inicializuje profiler.  

   - **/Output:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:sample** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro aplikace ASP.NET.  

   | Možnost | Popis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows. |
   | [/ crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Relace je vypsán ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md) [**:**`Interval`] | Určuje počet sekund čekání na inicializaci předtím, než je vrácena chyba profileru. Pokud `Interval` není zadán, čeká profiler neomezeně dlouho. Ve výchozím nastavení **/start** vrátí hodnotu okamžitě. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor. |


6. Spustit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci obvyklým způsobem.  

7. Připojení profileru k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Typ:  

    **Nástroj VSPerfCmd**[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[targetclr](../profiling/targetclr.md)**:**`Version`]    

   - ID procesu `(PID)` Určuje ID procesu nebo název procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

   - **targetclr:** `Version` Určuje verzi modulu common language runtime (CLR) do profilu je do aplikace načtena více než jedna verze modulu runtime.  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Když je aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do datového souboru profilování pomocí **VSPerfCmd.exe** možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces zadaný pomocí `PID`.|  
    |**/ attach:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;:`ProcName`}]|**/ attach** spustí sběr dat pro proces určený pomocí ID procesu nebo názvem procesu. **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od webové aplikace. Zastavit shromažďování dat z aplikace, která je profilována pomocí metody odběru vzorků restartováním [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu nebo voláním **VSPerfCmd / odpojení** možnost. Poté je zapotřebí zavolat **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost se profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování, ale konfigurace systému není obnovena, až po restartování počítače.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1. Proveďte jeden z následujících kroků-li odpojit profiler od cílové aplikace:  

   - Typ **VSPerfCmd** [/ odpojení](../profiling/detach.md)  

      -nebo-  

   - Zavřít [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Typ:  

     **Příkaz IISReset/stop**  

2. Vypněte profiler. Typ:  

    **/ Shutdown VSPerfCmd**  

3. (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

    **Nástroj VSPerfCmd /globaloff**  

4. Restartujte počítač. V případě potřeby restartování Internetové informační služby (IIS). Typ:  

    **Příkaz IISReset/Start**  

## <a name="see-also"></a>Viz také:  
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)