---
title: Připojení profileru k nativní aplikaci a shromažďování statistik aplikace
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d304e74d9480404e768789ffa0000c35da4f66ce
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063626"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: připojení profileru k nativní samostatné aplikaci a shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku nástrojů pro profilaci k připojení profileru k běžící nativní samostatné (klientské) aplikaci a shromáždit statistiky výkonu pomocí metody vzorkování.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* podadresáře [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Když je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat. Chcete-li ukončit relaci profilování, musí profiler již připojen k aplikaci a profiler musí být explicitně vypnut.  

## <a name="attach-the-profiler"></a>Připojení profileru  
 Připojení profileru k cílové aplikaci pomocí profileru, je použít **VSPerfCmd/start** a **/ attach** možnosti pro inicializaci profileru a pro připojení k cílové aplikaci. Můžete zadat **/start** a **/ attach** a jejich příslušné volby v jednom příkazovém řádku. Můžete také přidat **/globaloff** možnost pozastavit shromažďování dat na začátku cílové aplikace. Pak použijete **globalon** spustit shromažďování data.  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru k běžící aplikaci rozhraní .NET Framework  

1. Otevřete okno příkazového řádku.  

2. Spusťte profiler. Typ:  

    **/Start:sample VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Ukázka** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:sample** možnost.  

   | Možnost | Popis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího profilovaný proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows. |
   | [/ crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Relace je vypsán ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (. *ETL*) soubor. |


3. Připojení profileru k cílové aplikaci. Typ:  

    **Nástroj VSPerfCmd**[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [`Sample Event`]    

    `PID` Určuje ID procesu cílové aplikace. `ProcessName` Určuje název procesu. Všimněte si, že pokud zadáte `ProcessName` a běží víc procesů, které mají stejný název, výsledky nepředvídatelné. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

    Ve výchozím nastavení, data výkonu vzorkována každých procesoru 10 000 000 nepřerušených hodinových cyklů. To je přibližně 100krát za sekundu u procesoru s frekvencí 1 GHz. Můžete zadat jednu z následujících možností, chcete-li změnit intervalu hodinových cyklů nebo změnu událostí vyvolávajících.  

   |Událost vzorku|Popis|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:** `Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů, které jsou určeny `Interval`.|  
   |[/PF](../profiling/pf.md)[**:**`Interval`]|Změní událost odběru vzorků na chyby stránek. Pokud `Interval` je určen, nastaví počet chyb stránek mezi vzorky. Výchozí hodnota je 10.|  
   |[/ sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Změní událost odběru vzorků na volání systému z procesu do jádra operačního systému (syscalls). Pokud `Interval` je určen, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|  
   |[/ Čítač](../profiling/counter.md) **:** `Config`|Změní událost odběru vzorků a interval na čítač výkonu procesoru a interval, který je zadán v `Config`.|  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Pokud je cílová aplikace spuštěna, můžete použít *VSPerfCmd.exe* možnosti spuštění a zastavení zápisu dat do datového souboru profilování. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený pomocí `PID`.|  
    |[/ attach](../profiling/attach.md) **:** `PID` [/ odpojení](../profiling/detach.md)|**/ attach** spustí sběr dat pro proces určený pomocí `PID`. **/ detach** zastaví sběr dat pro všechny procesy.|  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Je-li odpojit profiler od aplikace profilované za použití metody vzorkování ukončením aplikace nebo zavoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí zavolat **VSPerfCmd/Shutdown** možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv / off** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Proveďte jeden z následujících kroků-li odpojit profiler od cílové aplikace.  

    -   Typ **VSPerfCmd / odpojení**  

         -nebo-  

    -   Ukončete cílovou aplikaci.  

2.  Vypněte profiler. Typ:  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

3.  (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – / vypnuté**  

## <a name="see-also"></a>Viz také:  
 [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Zobrazení dat metod vzorkování](../profiling/profiler-sampling-method-data-views.md)