---
title: 'Postupy: instrumentace dynamicky zkompilován ASP.NET webovou aplikaci a shromažďování dat paměti pomocí příkazového řádku Profiler | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 9c1d908a29d4255401aaad4567b56be16ce467cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862668"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postupy: instrumentace dynamicky kompilované webové aplikace ASP.NET a shromažďování dat paměti pomocí příkazového řádku profileru
Toto téma popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku nástrojů pro profilaci shromažďovat podrobná data paměti .NET přidělení a objekt doba života pro dynamicky kompilovaných [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci s použitím metoda profilace instrumentace.  

> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* podadresáře [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástroji příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Ke shromažďování dat výkonu z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, můžete upravit *web.config* soubor cílové aplikace umožňující [VSInstr.exe](../profiling/vsinstr.md) nástroj instrumentace dynamicky kompilované soubory aplikace. Pak použijete [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj pro konfiguraci serveru, který hostuje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci a povolit profilování paměti .NET tak, že nastavíte příslušné proměnné prostředí a pak restartujte počítač.  

 Shromažďování dat, spuštění profileru a pak spusťte cílovou aplikaci. Zatímco je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat. Po shromáždění příslušných dat, ukončete aplikaci, zavřete pracovní proces služby IIS (Internetová informační služba) a poté vypněte profiler.  

 Po dokončení profilování práci, obnovte *web.config* souboru a webový server do původního stavu.  

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurace webové aplikace ASP.NET a webového serveru  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurace webové aplikace ASP.NET a webového serveru  

1.  Upravit *web.config* soubor cílové aplikace. Zobrazit [postupy: Úprava souborů web.config za účelem instrumentace a profilování dynamicky kompilovaných webových aplikací ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).  

2.  Otevřete okno příkazového řádku na počítači, který je hostitelem webové aplikace.  

3.  Inicializujte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – /globaltracegc**  

     -nebo-  

     **Vsperfclrenv – /globaltracegclife**  

    -   **/globaltracegc** umožňuje shromažďování data o přidělování paměti.  

    -   **/globaltracegclife** povoluje shromažďování data o přidělování paměti a životnosti objektů.  

4.  Restartujte počítač.  

## <a name="run-the-profiling-session"></a>Spuštění relace profilování  

#### <a name="to-profile-the-aspnet-web-application"></a>Chcete-li profilovat webové aplikace ASP.NET  

1. Spusťte profiler. Typ:  

    **Nástroj VSPerfCmd** [/start](../profiling/start.md) **: trasování** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - **/Start:trace** možnost inicializuje profiler.  

   - **/Output:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění dat profilování (. *Vsp*) soubor.  

     Můžete použít některý z těchto možností s **/start:trace** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro aplikace ASP.NET.  

   | Možnost | Popis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje volitelný doména a uživatelské jméno účtu vlastnícího [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Tato možnost je vyžadována, pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Je uveden v **uživatelské jméno** sloupec **procesy** karty ve Správci úloh Windows. |
   | [/ crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. ID je uvedeno v relaci **ID relace** sloupec na **procesy** karty ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Spuštění, které se shromažďováním dat profileru pozastaveno. Použití [globalon](../profiling/globalon-and-globaloff.md) obnovu profilování provedete. |
   | [/ Čítač](../profiling/counter.md) **:** `Config` | Shromažďuje informace z čítače výkonu procesoru zadaného v `Config`. Informace čítače se přidají do dat shromážděných při každé události profilování. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (. *ETL*) soubor. |


2. Spustit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci obvyklým způsobem.  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Dokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do datového souboru profilování pomocí *VSPerfCmd.exe* možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) sběr dat pro vlákno určené pomocí ID vlákna (`TID`).|  

-   Můžete také použít **VSPerfCmd.exe**[/mark](../profiling/mark.md) možnost k vložení profilovací značky do datového souboru. **/Mark** příkaz přidá identifikátor, časové razítko a volitelný uživatelem definovaný textový řetězec. Značky lze použít k filtrování dat v zobrazení data a sestavy profileru.  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, zavřete cíl [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, zastavte Internetová informační služba () pro profilovaný proces zastavte a poté vypněte profiler. Potom restartujte službu IIS.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1. Zavřít [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci.  

2. Zavřít [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces resetováním Internetové informační služby (IIS). Typ:  

    **Příkaz IISReset/stop**  

3. Vypněte profiler. Typ:  

    **Nástroj VSPerfCmd**  [ /Shutdown](../profiling/shutdown.md)  

4. Restartujte službu IIS. Typ:  

    **Příkaz IISReset/Start**  

## <a name="restore-the-application-and-computer-configuration"></a>Obnovit konfiguraci aplikace a počítače  
 Po dokončení veškerého profilování nahradit *web.config* souboru, vyčistěte proměnné prostředí pro profilování a restartujte počítač a obnovte server a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace do původního stavu.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Chcete-li obnovit konfiguraci aplikace a počítače  

1.  Nahradit *web.config* souboru kopií původního souboru.  

2.  (Volitelné). Vyčistěte proměnné prostředí profilování. Typ:  

     **Nástroj VSPerfCmd /globaloff**  

3.  Restartujte počítač.  

## <a name="see-also"></a>Viz také:  
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
