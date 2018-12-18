---
title: 'Postupy: instrumentace staticky kompilované webové technologie ASP.NET aplikaci a shromažďování dat paměti pomocí příkazového řádku Profiler | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f1ffce16632d0daceaf5e917dbbe62dadd29cc2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750158"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postupy: Instrumentace staticky kompilované webové aplikace ASP.NET a shromažďování dat paměti pomocí příkazového řádku profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci k instrumentaci předkompilované [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové komponenty nebo webu a shromažďovat alokaci paměti .NET, doba života objektu a podrobných dat časování.  

> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v podadresáři nástroje \Team Tools\Performance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Pro shromáždění dat z [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové komponenty pomocí metody instrumentace, je použít [VSInstr.exe](../profiling/vsinstr.md) Nástroj generuje instrumentovanou verzi komponenty. Na počítači, který je hostitelem součásti nahradíte neinstrumentovanou verzi součásti instrumentovanou verzí. Pak použijete [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj k inicializaci globálních proměnných prostředí profilování a restartujte hostitelský počítač. Potom spusťte profiler.  

 Po spuštění instrumentované komponenty jsou data časování jsou automaticky shromažďována do datového souboru. Můžete pozastavit a obnovit sběr dat. během relace profilování.  

 Chcete-li ukončit relaci profilování, zavřete [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovní proces, který je hostitelem komponentu a potom explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="starting-to-profile"></a>Spuštění do profilu  

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Nástroje webového komponentu ASP.NET a spustit profilování  

1. Použití **VSInstr** Nástroj generuje instrumentovanou verzi cílové aplikace. V případě potřeby nahraďte binární soubory aplikace ASP.NET hostitelského počítače instrumentovanými binárními soubory.  

2. Otevřete okno příkazového řádku  

3. Inicializujte proměnné prostředí profilování rozhraní .NET. V okně příkazového řádku zadejte:  

    **Vsperfclrenv – /globaltracegc**  

    -nebo-  

    **Vsperfclrenv – /globaltracegclife**  

   -   **/globaltracegc** shromažďuje alokaci paměti .NET a údaje o načasování.  

   -   **/globaltracegclife** shromažďuje alokaci paměti .NET, dobu života objektu a podrobných dat časování.  

4. Restartujte počítač.  

5. Otevřete okno příkazového řádku.  

6. Spusťte profiler. V okně příkazového řádku zadejte:  

    **/Start:trace VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: trasování** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:trace** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro aplikace ASP.NET.  

   |                                 Možnost                                  |                                                                                                                                            Popis                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |  Určuje volitelnou doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn jako uživatel, který se liší od přihlášeného uživatele. Název je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows.   |
   |              [/ crosssession](../profiling/crosssession.md)              | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. Id relace je uvedeno ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                             Určuje čítač výkonu Windows má být shromážděn během profilování.                                                                                                              |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                           Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                              Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.                                                                              |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                      Chcete-li spustit profiler s shromažďování dat pozastaveno, přidejte **/globaloff** umožňuje **/start** příkazového řádku. Použití **globalon** obnovu profilování provedete.                                                                       |


7. Otevřete web, který obsahuje instrumentovanou komponentu.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Dokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s použitím **VSPerfCmd.exe** možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) sběr dat pro vlákno určené pomocí ID vlákna (`TID`).|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, zavřete [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci a pak pomocí Internetové informační služby (IIS) **IISReset** příkaz pro zavření [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovní proces. Volání **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování. Po restartování počítače-li použít nové nastavení prostředí.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Zavřít [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci.  

2.  Zavřít [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovní proces. Typ:  

     **Příkaz IISReset/stop**  

3.  Vypněte profiler. Typ:  

     **/ Shutdown VSPerfCmd**  

4.  (Volitelné). Vyčistěte proměnné prostředí profilování. Typ:  

     **Nástroj VSPerfCmd /globaloff**  

5.  Restartujte počítač. V případě potřeby restartujte službu IIS. Typ:  

     **Příkaz IISReset/Start**  

## <a name="see-also"></a>Viz také  
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)



