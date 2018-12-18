---
title: 'Postupy: spuštění samostatné rozhraní .NET Framework aplikace s Profiler ke shromažďování dat souběžnosti pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6b95f2f02e68d5b115ea4a04bbc33b78a7c60277
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817857"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: spuštění samostatné aplikace rozhraní .NET Framework s profilerem ke shromažďování dat souběžnosti pomocí příkazového řádku
Toto téma popisuje způsob používání nástrojů příkazového řádku balíku nástrojů pro profilaci sady [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ke spuštění samostatné (klientské) aplikace rozhraní .NET Framework a shromažďování dat procesu a souběžnosti vláken.  

> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* podadresáře [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástroji příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Zatímco je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat. Chcete-li ukončit relaci profilování, musí Profiler již připojen k aplikaci a Profiler musí být explicitně vypnut.  

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace s profilerem  
 Chcete-li spustit cílovou aplikaci rozhraní .NET Framework s Profiler, použijete *VSPerfClrEnv.exe* k nastavení proměnné profilování rozhraní .NET Framework. Potom můžete upgradovat pomocí příkazu vsperfcmd proveďte **/start** a **/spuštění** možnosti, jak inicializovat Profiler a spusťte aplikaci. Můžete zadat **/start** a **/spuštění** a jejich příslušné volby v jednom příkazovém řádku. Můžete také přidat **/globaloff** možnost příkazového řádku se pozastavit shromažďování dat při spuštění cílové aplikace. Pak použijete **globalon** na samostatný příkazový řádek spustit shromažďování data.  

#### <a name="to-start-an-application-with-the-profiler"></a>Spuštění aplikace s profilerem  

1. Otevřete okno příkazového řádku.  

2. Spusťte profiler. Typ:  

    [Nástroj VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/ výstup:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md) možnost inicializuje profiler.  


     | | |
     |-------------------------------------| - |
     | **/Start:Concurrency** | Umožňuje shromažďovat kolize prostředků a data spouštění vlákna. |
     | **/Start:Concurrency resourceonly** | Umožňuje shromažďovat pouze data kolize prostředků. |
     | **/Start:Concurrency threadonly** | Umožňuje shromažďovat pouze data spouštění vlákna. |


   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:concurrency** možnost.  

   | Možnost | Popis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username` | Určuje volitelnou doménu a uživatelské jméno účtu, který má být udělen přístup k profileru. |
   | [/ crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (. *ETL*) soubor. |


3. Spusťte cílovou aplikaci. Typ:  

    **Nástroj VSPerfCmd**[/spuštění](../profiling/launch.md) **:** `AppName` [`Options`] [`Sample Event`]    

    Můžete použít některý z těchto možností s **/spuštění** možnost.  

   |Možnost|Popis|  
   |------------|-----------------|  
   |[/ args](../profiling/args.md) **:** `Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které se mají předat cílové aplikace.|  
   |[/ Console](../profiling/console.md)|Spustí cílovou aplikaci příkazového řádku v samostatném okně.|  
   |[targetclr](../profiling/targetclr.md) **:** `Version`|Určuje verzi modulu common language runtime (CLR), která má být profilována je do aplikace načtena více než jedna verze modulu runtime.|  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Dokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s použitím *VSPerfCmd.exe* možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

1.  Následující páry *VSPerfCmd.exe* možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces určený identifikátorem procesu (`PID`) nebo názvem procesu (ProcName). **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, profiler nesmí pokračovat ve shromažďování dat. Zastavit shromažďování dat souběžnosti zavřením profilované aplikace nebo zavoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí vyvolat **VSPerfCmd/Shutdown** možnost se profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv / off** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Proveďte jednu z následujících-li odpojit profiler od cílové aplikace.  

    -   Ukončete cílovou aplikaci.  

         -nebo-  

    -   Typ **VSPerfCmd / odpojení**  

2.  Ukončete profiler.  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Viz také:  
 [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)