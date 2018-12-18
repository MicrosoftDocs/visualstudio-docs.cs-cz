---
title: 'Postupy: spuštění samostatné aplikace s Profiler a shromáždění statistik aplikace pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a57d56564b7be9051efb1a5d153a2a797fcc2211
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820002"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: spuštění samostatné aplikace s profilerem a shromáždění statistik aplikace pomocí příkazového řádku
Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku nástrojů pro profilaci spuštění samostatné (klientské) aplikaci a shromáždit statistiky výkonu pomocí metody vzorkování.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Přidání dat interakce vrstvy do běhu profilování vyžaduje zvláštní procedury s nástroji pro profilaci příkazového řádku. Zobrazit [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)  

 Chcete-li využívat nástroje příkazového řádku profileru, musí přidat cestu do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Spuštění nástrojů pro profilaci na počítači nainstalovanou aplikaci Visual Studio z příkazového okna sady Visual Studio.  

1.  Pokud používáte nástroje pro profilaci nainstalované na počítači, kde je aplikace Visual Studio okno sady Visual Studio příkazů správné cesty. Na **nástroje** nabídce zvolte **VS příkazového řádku**  

> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* jedná o podadresář adresáře instalace sady Visual Studio. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Chcete-li využívat nástroje příkazového řádku profileru, musí přidat cestu do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástroji příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace s profilerem  
 Chcete-li spustit cílovou aplikaci pomocí profileru, je použít příkazu vsperfcmd proveďte **/start** a **/spuštění** možnosti pro inicializaci profileru a spuštění aplikace. Můžete zadat **/start** a **/spuštění** a jejich příslušné volby v jednom příkazovém řádku.  

 Můžete také přidat **/globaloff** možnost pozastavit shromažďování dat na začátku cílové aplikace. Pak použijete **globalon** spustit shromažďování data.  

#### <a name="to-start-an-application-by-using-the-profiler"></a>Spusťte aplikaci pomocí profileru  

1. Otevřete okno příkazového řádku.  

2. Spusťte profiler. Typ:  

    **/Start:sample VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Ukázka** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:sample** možnost.  

   | Možnost | Popis |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (. *ETL*) soubor. |


3. Spusťte cílovou aplikaci. Typ:**VSPerfCmd/lauch:** `appName` [`Options`] [`Sample Event`]  

    Můžete použít jeden nebo více z následujících možností s **/spuštění** možnost.  

   |Možnost|Popis|  
   |------------|-----------------|  
   |[/ args](../profiling/args.md) **:** `Arguments`|Určuje řetězec, který obsahuje argumenty příkazového řádku, které se mají předat cílové aplikace.|  
   |[/ Console](../profiling/console.md)|Spustí cílovou aplikaci příkazového řádku v samostatném okně.|  

    Ve výchozím nastavení, data výkonu vzorkována každých procesoru 10 000 000 nepřerušených hodinových cyklů. To je přibližně jednou za 10 sekund u procesor 1GHz. Můžete zadat jednu z následujících možností, chcete-li změnit intervalu hodinových cyklů nebo změnu událostí vyvolávajících.  

   |Událost vzorku|Popis|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:** `Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů, které jsou určeny `Interval`.|  
   |[/PF](../profiling/pf.md)[**:**`Interval`]|Změní událost odběru vzorků na chyby stránek. Pokud `Interval` je určen, nastaví počet chyb stránek mezi vzorky. Výchozí hodnota je 10.|  
   |[/ sys](../profiling/sys-vsperfcmd.md)[**:**`Interval`]|Změní událost odběru vzorků na volání systému z procesu do jádra operačního systému (syscalls). Pokud `Interval` je určen, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|  
   |[/ Čítač](../profiling/counter.md) **:** `Config`|Změní událost odběru vzorků a interval na čítač výkonu procesoru a interval, ve stanoveném `Config`.|  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Pokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do datového souboru profilování pomocí *VSPerfCmd.exe* možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces určený pomocí `PID` nebo názvem procesu (ProcName). **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, nesmí být profiler připojen k žádné profilovaný proces a profiler musí být explicitně vypnut. Je-li odpojit profiler od aplikace profilované za použití metody vzorkování ukončením aplikace nebo zavoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí zavolat **VSPerfCmd/Shutdown** možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv / off** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Proveďte jeden z následujících kroků-li odpojit profiler od cílové aplikace:  

    -   Ukončete cílovou aplikaci.  

         -nebo-  

    -   Typ **VSPerfCmd / odpojení**  

2.  Vypněte profiler. Typ:  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Viz také:  
 [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Zobrazení dat metod vzorkování](../profiling/profiler-sampling-method-data-views.md)