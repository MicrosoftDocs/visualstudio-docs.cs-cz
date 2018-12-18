---
title: 'Postupy: připojení Profiler k webové aplikaci ASP.NET ke shromažďování dat souběžnosti pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea6f642f3178e06127dc21bc115d70c68525bf0e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750142"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru k webové aplikaci ASP.NET ke shromažďování dat souběžnosti pomocí příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů příkazového řádku nástrojů pro profilaci sady připojení Profiler k aplikaci technologie ASP.NET a shromažďování dat souběžnosti procesů a vláken.  

 Nástroje příkazového řádku balíku nástrojů pro profilaci jsou umístěny v podadresáři \Team Tools\Performance Tools instalačního adresáře sady Visual Studio. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Chcete-li využívat profiler na příkazového řádku, musíte přidat cestu k nástrojům do proměnné prostředí PATH **příkazového řádku** okno nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Ke shromažďování dat souběžnosti, připojte profiler k pracovnímu procesu ASP.NET, který je hostitelem vašeho webu. Zatímco je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat. Chcete-li ukončit relaci profilování, musí Profiler již připojen k aplikaci a Profiler musí být explicitně vypnut. Ve většině případů byste měli na konci relace vymazat proměnné prostředí profilování.  

## <a name="attaching-the-profiler"></a>Připojuje Profiler  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Připojení Profiler k aplikaci ASP.NET  

1. Spusťte profiler zadáním následujícího příkazu:  

    [Nástroj VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md) inicializuje možnost profileru sbírat data kolize prostředků.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     V následující tabulce můžete použít jakoukoli možnost **/start** možnost.  

   |                               Možnost                               |                                                                     Popis                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` |                           Určuje volitelnou doménu a uživatelské jméno účtu, který má být udělen přístup k profileru.                           |
   |           [/ crosssession](../profiling/crosssession.md)            |                                               Umožňuje profilování procesů v jiných přihlašovacích relacích.                                                |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                      Určuje čítač výkonu Windows má být shromážděn během profilování.                                       |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:** `Config`     |       Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.       |


2. Spusťte aplikaci ASP.NET obvyklým způsobem.  

3. Připojit profiler k pracovnímu procesu ASP.NET zadáním následujícího příkazu:**VSPerfCmd / připojit:** `PID` [**targetclr:**`Version`]  

   -   `PID` Určuje ID nebo název pracovního procesu technologie ASP.NET. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

   -   [targetclr](../profiling/targetclr.md) **:** `Version` Určuje verzi modulu common language runtime (CLR) do profilu je do aplikace načtena více než jedna verze modulu runtime. Tento parametr je volitelný.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Zatímco je aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru použitím možností VSPerfCmd.exe. Řízením sběru dat může shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností VSPerfCmd z následující tabulky spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces, který ID procesu (`PID`) určuje.|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces, který ID procesu (`PID`) nebo názvem procesu (*ProcName*) určuje. **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, profiler nesmí pokračovat ve shromažďování dat. Zastavit shromažďování dat z aplikace, která je profilována metodou souběžnosti restartování pracovního procesu technologie ASP.NET nebo vyvoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí vyvolat **VSPerfCmd/Shutdown** možnost se profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování, ale konfigurace systému není obnovena, až po restartování počítače.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Pomocí následujícího příkazu na příkazovém řádku nebo ukončením odpojte profiler od cílové aplikace:  

     **Nástroj VSPerfCmd / odpojení**  

2.  Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Viz také  
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Pohotová profilace webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)



