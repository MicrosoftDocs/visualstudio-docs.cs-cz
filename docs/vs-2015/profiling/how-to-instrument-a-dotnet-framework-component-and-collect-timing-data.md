---
title: 'Postupy: instrumentace součásti samostatné rozhraní .NET Framework a shromažďování dat Profiler z příkazového řádku časování | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 857818dac0b1cf1cd394d69aa322d9c2a0bbbe77
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810147"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Postupy: Instrumentace samostatné součásti rozhraní .NET Framework a shromažďování dat časování z příkazového řádku profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci k instrumentaci komponenty rozhraní .NET Framework, jako například souboru .exe nebo .dll a shromažďování podrobných dat časování.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v podadresáři nástroje \Team Tools\Performance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Přidání dat interakce vrstvy do běhu profilování vyžaduje zvláštní procedury s nástroji pro profilaci příkazového řádku. Zobrazit [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Ke shromažďování podrobných dat časování z komponenty rozhraní .NET Framework pomocí metody instrumentace, můžete použít [VSInstr.exe](../profiling/vsinstr.md) Nástroj generuje instrumentovanou verzi komponenty a [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj k inicializaci proměnné prostředí profilování. Potom spusťte profiler.  

 Po spuštění instrumentované komponenty jsou data časování jsou automaticky shromažďována do datového souboru. Můžete pozastavit a obnovit sběr dat. během relace profilování.  

 Chcete-li ukončit relaci profilování, ukončete cílovou aplikaci a explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="starting-the-profiling-session"></a>Spuštění relace profilování  

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Spuštění profilování pomocí metody instrumentace  

1. Otevřete okno příkazového řádku. V případě potřeby přidejte adresář nástrojů profilování do proměnné prostředí PATH. Tato cesta není při instalaci přidána.  

2. Použití **VSInstr** Nástroj generuje instrumentovanou verzi cílové aplikace.  

3. Inicializace proměnných prostředí profilování rozhraní .NET Framework. Typ:  

    **Vsperfclrenv – /traceon**  

4. Spusťte profiler. Typ:  

    **/Start:trace VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: trasování** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některou z následujících možností s **/start:trace** možnost.  

   |                                 Možnost                                  |                                                                                                                                                     Popis                                                                                                                                                     |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |                 Určuje doménu a uživatelské jméno účtu vlastnícího profilovaný proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows.                 |
   |              [/ crosssession](../profiling/crosssession.md)              | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Relace je vypsán ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                                            Spuštění, které se shromažďováním dat profileru pozastaveno. Použití [globalon](../profiling/globalon-and-globaloff.md) obnovu profilování provedete.                                                                                            |
   |           [/ Čítač](../profiling/counter.md) **:** `Config`            |                                                                   Shromažďuje informace z čítače výkonu procesoru, který je zadán v `Config`. Informace čítače se přidají do dat shromážděných při každé události profilování.                                                                    |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                      Určuje čítač výkonu Windows má být shromážděn během profilování.                                                                                                                      |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                    Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.                                                                                    |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                      Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.                                                                                       |


5. Spusťte cílovou aplikaci z okna příkazového řádku.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Pokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do datového souboru profilování pomocí **VSPerfCmd.exe** možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) sběr dat pro vlákno určené pomocí ID vlákna (`TID`).|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, ukončete aplikaci, ve které běží instrumentovaná komponenta. Volání **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost se profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv / off** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Ukončete cílovou aplikaci.  

2.  Vypněte profiler. Typ:  

     **/ Shutdown VSPerfCmd**  

3.  (Volitelné) Vyčistěte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – / vypnuté**  

## <a name="see-also"></a>Viz také  
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)



