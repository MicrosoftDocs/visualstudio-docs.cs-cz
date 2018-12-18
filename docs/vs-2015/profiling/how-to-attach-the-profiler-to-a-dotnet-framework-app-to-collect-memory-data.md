---
title: 'Postupy: připojení Profiler k samostatné aplikaci .NET Framework ke shromažďování dat paměti pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de9753b1471cfe90259ab552b38239a2d92a3c67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766962"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Postupy: Připojení profileru k samostatné aplikaci .NET Framework ke shromažďování dat paměti pomocí příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] příkazového řádku nástrojů pro profilaci k připojení profileru k běžící samostatné (klientské) aplikaci rozhraní .NET Framework a shromažďování dat paměti.  

> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v podadresáři nástroje \Team Tools\Performance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Připojit k aplikaci rozhraní .NET Framework a shromažďovat paměťová data, je nutné použít [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj k inicializaci příslušných proměnných prostředí před spuštěním cílové aplikace. Když je profiler připojen k aplikaci, můžete **VSPerfCmd.exe** má pozastavit a obnovit sběr dat. nástroj.  

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="attaching-the-profiler"></a>Připojuje Profiler  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojit Profiler k běžící aplikaci rozhraní .NET Framework  

1. Otevřete okno příkazového řádku.  

2. Inicializujte proměnné prostředí profilování. Typ:  

    **Vsperfclrenv –** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]  

   -   **/Samplegc** a **/samplegclife** možnosti určují, jestli se má shromažďovat pouze data o přidělování paměti nebo získat informace o přidělování paměti a životnosti objektů. Musí být zadána pouze jedna možnost.  

       |Možnost|Popisy|  
       |------------|------------------|  
       |**/samplegc**|Shromážděte pouze data o přidělování paměti.|  
       |**/samplegclife**|Shromážděte o přidělování paměti a životnosti objektů.|  

   -   **/Samplelineoff** možnost zakáže kolekci čísel datového řádku zdrojového kódu.  

3. Spusťte profiler. Typ:  

    **/Start:sample VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Ukázka** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:sample** možnost.  

   |                                 Možnost                                  |                                                                                                                                                Popis                                                                                                                                                 |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |            Určuje doménu a uživatelské jméno účtu vlastnícího profilovaný proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows.             |
   |        [/ crosssession &#124; protokolovacímu](../profiling/crosssession.md)         | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. Relace je vypsán ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                 Určuje čítač výkonu Windows má být shromážděn během profilování.                                                                                                                  |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                               Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.                                                                                |


4. V případě potřeby spusťte cílovou aplikaci standardním způsobem.  

5. Připojení profileru k cílové aplikaci. Typ:  

    **Nástroj VSPerfCmd**[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[targetclr](../profiling/targetclr.md)**:**`Version`]    

   -   `PID` Určuje ID procesu cílové aplikace. `ProcessName` Určuje název procesu. Všimněte si, že pokud zadáte `ProcessName` a běží víc procesů, které mají stejný název, výsledky nepředvídatelné. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

   -   **targetclr:** `Version` Určuje verzi modulu common language runtime (CLR) do profilu je do aplikace načtena více než jedna verze modulu runtime. Volitelné.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Pokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s použitím **VSPerfCmd.exe** možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces, který je určen `PID`.|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces určený pomocí `PID` nebo názvem procesu (ProcName). **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Je-li odpojit profiler od aplikace profilované za použití metody vzorkování ukončením aplikace nebo zavoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí zavolat **VSPerfCmd/Shutdown** možnost se profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv / off** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Proveďte jeden z následujících kroků-li odpojit profiler od cílové aplikace:  

    -   Typ **VSPerfCmd / odpojení**  

         -nebo-  

    -   Ukončete cílovou aplikaci.  

2.  Vypněte profiler. Typ:  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

3.  (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

     **Nástroj VSPerfCmd / vypnuté**  

## <a name="see-also"></a>Viz také  
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)



