---
title: 'Postupy: připojení Profiler ke službě .NET ke shromažďování dat souběžnosti pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4f4d940f2bb65fe27c826e4ce06d1ead6626d37
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756431"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Postupy: Připojení profileru ke službě .NET ke shromažďování dat souběžnosti pomocí příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci připojit Profiler k [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] služby a shromažďování dat souběžnosti pro procesů a vláken pomocí metody vzorkování.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Nástroje příkazového řádku balíku nástrojů pro profilaci jsou umístěny v podadresáři \Team Tools\Performance Tools instalačního adresáře sady Visual Studio. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Ke shromažďování dat souběžnosti, připojte profiler k procesu služby. Zatímco je profiler připojen ke službě, lze pozastavit a obnovit sběr dat. Chcete-li ukončit relaci profilování, musí Profiler již připojen ke službě a Profiler musí být explicitně vypnut. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  
  
## <a name="attaching-the-profiler"></a>Připojuje Profiler  
  
#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>K připojení Profiler ke službě rozhraní .NET Framework  
  
1.  Nainstalujte službu.  
  
2.  Otevřete okno příkazového řádku.  
  
3.  Inicializujte proměnné prostředí profilování. Typ:  
  
     [Vsperfclrenv –](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]  
  
    -   **/globalsampleon** umožňuje vzorkování.  
  
    -   **/samplelineoff** zakáže přiřazení shromážděných dat ke konkrétnímu zdroji řádků kódu. Pokud je tato možnost zadána, data přiřazena pouze funkcí.  
  
4.  Restartujte počítač.  
  
5.  Spusťte profiler. Typ:  
  
     [Nástroj VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/output:** `OutputFile` [`Options`]  
  
     [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  
  
     Můžete použít některý z těchto možností s **/start** možnost.  
  
    > [!NOTE]
    >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro služby.  
  
    |Možnost|Popis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Určuje doménu a uživatelské jméno účtu vlastnícího profilovaný proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows.|  
    |[/ crosssession](../profiling/crosssession.md)|Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud služba běží v jiné relaci. Id relace je uvedeno ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Určuje čítač výkonu Windows má být shromážděn během profilování.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.|  
  
6.  V případě potřeby spusťte službu.  
  
7.  Připojení profileru ke službě. Typ:  
  
     **Nástroj VSPerfCmd / připojit:** `PID` [[targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   `PID` Určuje ID procesu nebo názvem procesu služby. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  
  
    -   **targetclr:** `Version` Určuje verzi modulu common language runtime (CLR) do profilu je do aplikace načtena více než jedna verze modulu runtime. Volitelné.  
  
## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Zatímco je služba spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru použitím možností VSPerfCmd.exe. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  
  
#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  
  
-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  
  
    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |**/ attach:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces určený pomocí ID procesu nebo názvem procesu. **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud konkrétní proces není zadán.|  
  
-   Můžete také použít **VSPerfCmd.exe**[/mark](../profiling/mark.md) možnost k vložení profilovací značky do datového souboru. **/Mark** příkaz přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze použít k filtrování dat v zobrazení data a sestavy profileru. Následující páry možností VSPerfCmd spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  
  
## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, profiler nesmí pokračovat ve shromažďování dat. Zastavit shromažďování dat od aplikace profilované za použití metody souběžnosti zastavením služby nebo vyvoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí vyvolat **VSPerfCmd/Shutdown** možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování, ale konfigurace systému není obnovena, až po restartování počítače.  
  
#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  
  
1.  Proveďte jednu z následujících-li odpojit profiler od cílové aplikace.  
  
    -   Zastavte službu.  
  
         -nebo-  
  
    -   Typ **VSPerfCmd / odpojit.**  
  
2.  Vypněte profiler. Typ:  
  
     **Nástroj VSPerfCmd**[vypnutí](../profiling/shutdown.md)



