---
title: 'Postupy: připojení Profiler k nativní službě ke shromažďování dat souběžnosti pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6add1c0837e9a1d1308f61112540d00f42617a92
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731441"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru k nativní službě ke shromažďování dat souběžnosti pomocí příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci k připojení profileru k nativní (C/C++), služby a shromažďování dat souběžnosti procesů a vláken pomocí metody vzorkování.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
>  Nástroje příkazového řádku balíku nástrojů pro profilaci jsou umístěny v podadresáři \Team Tools\Performance Tools instalačního adresáře sady Visual Studio. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Chcete-li využívat profiler na příkazového řádku, musíte přidat cestu k nástrojům do proměnné prostředí PATH **příkazového řádku** okno nebo do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Zatímco je profiler připojen ke službě, lze pozastavit a obnovit sběr dat. Chcete-li ukončit relaci profilování, musí Profiler již připojen ke službě a Profiler musí být explicitně vypnut.  

## <a name="attaching-the-profiler"></a>Připojuje Profiler  
 Připojení profileru k nativní službě, můžete použít **VSPerfCmd/start** a **/ attach** možnosti pro inicializaci profileru a pro připojení k cílové aplikaci. Můžete zadat **/start** a **/ attach** a jejich příslušné volby v jednom příkazovém řádku. Můžete také přidat **/globaloff** možnost pozastavit shromažďování dat na začátku cílové aplikace. Pak použijete **globalon** Chcete-li začít shromažďovat data.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Připojit Profiler k nativní službě  

1. Pokud služba není spuštěná, spusťte službu.  

2. Spusťte profiler zadáním následujícího příkazového řádku:  

    [Nástroj VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/output:** `OutputFile` [`Options`]  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     V následující tabulce můžete použít jakoukoli možnost **/start** možnost.  

   > [!NOTE]
   >  Většina služeb vyžaduje **/User** a **/crosssession** možnost.  

   |                               Možnost                               |                                                                     Popis                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` |                           Určuje volitelnou doménu a uživatelské jméno účtu, který má být udělen přístup k profileru.                           |
   |           [/ crosssession](../profiling/crosssession.md)            |                                               Umožňuje profilování procesů v jiných přihlašovacích relacích.                                                |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                      Určuje čítač výkonu Windows má být shromážděn během profilování.                                       |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:** `Config`     |       Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.       |


3. Připojení profileru ke službě zadáním následujícího příkazu na příkazovém řádku:  

    **Nástroj VSPerfCmd / připojit:** `PID`  

    `PID` Určuje ID procesu nebo název procesu cílové aplikace. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Dokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s možností VSPerfCmd.exe. Řízením sběru dat může shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností v následující tabulce spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces, který ID procesu (`PID`) určuje.|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces, který ID procesu (`PID`) nebo názvem procesu (*ProcName*) určuje. **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, profiler nesmí pokračovat ve shromažďování dat. Zastavit shromažďování dat z nativní služby, která je právě profilována metodou souběžnosti zastavením služby nebo vyvoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí vyvolat **VSPerfCmd/Shutdown** možnost se profiler vypne a uzavře soubor dat profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Odpojte profiler od cílové aplikace zastavením služby nebo zadáním následujícího příkazu na příkazovém řádku:  

     Typ **VSPerfCmd / odpojení**  

2.  Vypněte profiler zadáním následujícího příkazu na příkazovém řádku:  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)



