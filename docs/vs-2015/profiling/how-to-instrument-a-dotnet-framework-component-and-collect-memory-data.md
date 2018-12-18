---
title: 'Postupy: instrumentace součásti samostatné rozhraní .NET Framework a shromažďování dat paměti Profiler příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: febdaf1396755a05acce2bb8d82cb4af69ed46bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753794"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Postupy: Instrumentace samostatné součásti rozhraní .NET Framework a shromažďování dat paměti pomocí příkazového řádku profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci k instrumentaci komponenty rozhraní .NET Framework samostatné aplikace, například .exe nebo .dll soubor a shromažďovat informace o paměti pomocí profileru.  

> [!NOTE]
>  Nástroje příkazového řádku balíku nástrojů pro profilaci jsou umístěny v podadresáři \Team Tools\Performance Tools instalačního adresáře sady Visual Studio. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Ke shromažďování dat paměti pomocí metody instrumentace z komponenty rozhraní .NET Framework, můžete použít [VSInstr.exe](../profiling/vsinstr.md) Nástroj generuje instrumentovanou verzi komponenty a [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) Nástroj pro inicializaci proměnné prostředí profilování. Potom spusťte pomocí profileru **VSPerfCmd.exe** nástroj.  

 Po spuštění instrumentované komponenty jsou data paměti automaticky uložena do datového souboru. Můžete pozastavit a obnovit sběr dat. během relace profilování.  

 Chcete-li ukončit relaci profilování, ukončete cílovou aplikaci a explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="starting-the-application-with-the-profiler"></a>Spuštění aplikace se Profiler  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojit Profiler k běžící aplikaci rozhraní .NET Framework  

1. Otevřete okno příkazového řádku.  

2. Použití **VSInstr** Nástroj generuje instrumentovanou verzi cílové aplikace.  

3. Inicializace proměnných prostředí profilování rozhraní .NET Framework. Typ:  

    **Vsperfclrenv –** {**/tracegc** &#124; **/tracegclife**}  

   -   **/Tracegc** a **/tracegclife** možnosti inicializace proměnných prostředí, které chcete shromažďovat pouze data o přidělování paměti nebo získat informace o přidělování paměti a životnosti objektů.  

       |Možnost|Popis|  
       |------------|-----------------|  
       |**/tracegc**|Povolí shromažďování data o přidělování paměti pouze.|  
       |**/tracegclife**|Povolí shromažďování přidělení paměti a životnosti objektů.|  

4. Spusťte profiler. Typ:  

    **/Start:trace VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: trasování** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:trace** možnost.  

   |                                 Možnost                                  |                                                                                                                                                Popis                                                                                                                                                 |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |            Určuje doménu a uživatelské jméno účtu vlastnícího profilovaný proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows.             |
   |              [/ crosssession](../profiling/crosssession.md)              | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. Relace je vypsán ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                          Chcete-li spustit profiler s shromažďování dat pozastaveno, přidejte **/globaloff** umožňuje **/start** příkazového řádku. Použití **globalon** obnovu profilování provedete.                                                                           |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                 Určuje čítač výkonu Windows má být shromážděn během profilování.                                                                                                                  |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                               Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.                                                                                |
   |           [/ Čítač](../profiling/counter.md) **:** `Config`            |                                                                Shromažďuje informace z čítače výkonu procesoru, který je zadaný v konfiguraci. Informace čítače se přidají do dat shromážděných při každé události profilování.                                                                |
   |        [Události](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                  Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.                                                                                  |


5. Spusťte cílovou aplikaci z okna příkazového řádku.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Dokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s použitím **VSPerfCmd.exe** možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat pro vlákno, který je určen pomocí ID vlákna (`TID`).|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, ukončete aplikaci, která je spuštěna instrumentovaná komponenta a následně zavolat **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost se profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv / off** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Ukončete cílovou aplikaci.  

2.  Vypněte profiler. Typ:  

     **/ Shutdown VSPerfCmd**  

3.  (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

     **Nástroj VSPerfCmd / vypnuté**  

## <a name="see-also"></a>Viz také  
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)



