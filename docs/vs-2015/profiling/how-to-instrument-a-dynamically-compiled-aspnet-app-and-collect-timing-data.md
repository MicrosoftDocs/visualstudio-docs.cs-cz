---
title: 'Postupy: instrumentace dynamicky kompilované webové aplikace a shromažďování podrobných dat Profiler časování pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c140ae2-ecdd-48c7-bd89-3dc1b88e19b0
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 041385fcda5aa587647752c3e32f933a5674b8aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757117"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Postupy: Instrumentace dynamicky kompilované webové aplikace ASP.NET a shromažďování podrobných dat časování pomocí příkazového řádku profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci ke shromažďování podrobných dat časování pro dynamicky kompilovaných [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace s použitím metoda profilace instrumentace.  

> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v podadresáři nástroje \Team Tools\Performance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Ke shromažďování dat výkonu z [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci, upravte soubor web.config cílové aplikace, aby [VSInstr.exe](../profiling/vsinstr.md) nástroj instrumentace dynamicky kompilované aplikace soubory. Pak použijete [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroje nastavit příslušné proměnné prostředí na webový server a povolit profilaci a pak restartujte počítač.  

 Spusťte profiler a pak spusťte cílovou aplikaci. Zatímco je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat. Po dokončení profilování, ukončete aplikaci, zavřete pracovní proces služby IIS (Internetová informační služba) a poté vypněte profiler. Po dokončení profilování pracovní souboru web.config a webový server obnovte do původního stavu.  

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Konfigurace webové aplikace a webového serveru  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurovat webovou aplikaci ASP.NET a webového serveru  

1.  Upravte soubor web.config cílové aplikace. Zobrazit [postupy: Úprava souborů Web.Config za účelem instrumentace a profilování dynamicky kompilovaných webových aplikací ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).  

2.  Otevřete okno příkazového řádku.  

3.  Inicializujte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – /globaltraceon**  

    -   **/globaltraceon** povolí profilaci pomocí metody instrumentace.  

4.  Restartujte počítač.  

## <a name="running-the-profiling-session"></a>Spuštění relace profilování  

#### <a name="to-profile-the-web-application"></a>Chcete-li profilovat webové aplikace  

1. Otevřete okno příkazového řádku.  

2. Spusťte profiler. Typ:  

    **Nástroj VSPerfCmd**[/start](../profiling/start.md) **: trasování**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start:trace** možnost inicializuje profiler.  

   - **/Output:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:trace** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro aplikace ASP.NET.  

   |                                 Možnost                                  |                                                                                                                                                       Popis                                                                                                                                                        |
   |-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |                   Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows.                   |
   |              [/ crosssession](../profiling/crosssession.md)              | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Identifikátor relace je uvedeno ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                                              Spuštění, které se shromažďováním dat profileru pozastaveno. Použití [globalon](../profiling/globalon-and-globaloff.md) obnovu profilování provedete.                                                                                               |
   |           [/ Čítač](../profiling/counter.md) **:** `Config`            |                                                                      Shromažďuje informace z čítače výkonu procesoru, který je zadán v `Config`. Informace čítače se přidají do dat shromážděných při každé události profilování.                                                                      |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                        Určuje čítač výkonu Windows má být shromážděn během profilování.                                                                                                                         |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                      Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.                                                                                       |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                         Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.                                                                                         |


3. Spustit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci obvyklým způsobem.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Dokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do datového souboru profilování pomocí **VSPerfCmd.exe** možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) sběr dat pro vlákno určené pomocí ID vlákna (`TID`).|  

-   Můžete také použít **VSPerfCmd.exe**[/mark](../profiling/mark.md) možnost k vložení profilovací značky do datového souboru. **/Mark** příkaz přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze použít k filtrování dat v zobrazení data a sestavy profileru.  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, zavřete cíl [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci, restartujte službu IIS zastavte profilovaných procesů a poté vypněte profiler.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Zavřít [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci.  

2.  Zavřít [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovní proces resetováním Internetové informační služby (IIS). Typ:  

     **Příkaz IISReset/stop**  

3.  Vypněte profiler. Typ:  

     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

4.  Restartujte službu IIS. Typ:  

     **Příkaz IISReset/Start**  

## <a name="restoring-the-application-and-computer-configuration"></a>Obnovení aplikace a konfigurace počítače  
 Po dokončení veškerého profilování nahradit v souboru web.config, vyčistěte proměnné prostředí pro profilování a restartujte počítač a obnovit stavy, které se nacházely před profilace aplikace a serveru.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Chcete-li obnovit konfiguraci aplikace a počítače  

1.  Nahraďte soubor web.config kopii původního souboru.  

2.  Vyčistěte proměnné prostředí profilování. Typ:  

     **Nástroj VSPerfCmd /globaloff**  

3.  Restartujte počítač.  

## <a name="see-also"></a>Viz také  
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)



