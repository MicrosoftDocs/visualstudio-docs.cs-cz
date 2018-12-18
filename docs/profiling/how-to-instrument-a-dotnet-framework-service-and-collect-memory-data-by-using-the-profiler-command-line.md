---
title: 'Postupy: instrumentace rozhraní .NET Framework služby a shromažďování dat paměti pomocí příkazového řádku Profiler | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: eafd91fe97a4e4ceb33b9dc315b8b9d9014d27ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914694"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Postupy: instrumentace služby rozhraní .NET Framework a shromažďování dat paměti pomocí příkazového řádku profileru
Tento článek popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku nástrojů pro profilaci k instrumentaci [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] služby a shromažďování dat o využití paměti. Můžete shromažďovat data o přidělování paměti, nebo můžete shromažďovat přidělení paměti a životnosti objektů.  

> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
> [!NOTE]
>  Metodou instrumentace nelze Profilovat službu, je-li nelze po spuštění počítače restartovat službu, například Služba spouštěná spolu s operačním systémem.  
> 
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* podadresáře [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástroji příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="start-the-profiling-session"></a>Spuštění relace profilování  
 Ke shromažďování dat výkonu z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] služby, můžete použít [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj k inicializaci příslušných proměnných prostředí a [VSInstr.exe](../profiling/vsinstr.md) nástroj k vytvoření instrumentované kopie binárního souboru služby.  

 Konfigurace pro profilaci po restartování počítače, který je hostitelem služby. Je nutné také spustit službu ručně ze Správce řízení služeb. Spusťte profiler a poté spusťte [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] služby.  

 Po spuštění instrumentované komponenty jsou data paměti automaticky uložena do datového souboru. Můžete pozastavit a obnovit sběr dat. během relace profilování.  

 Chcete-li ukončit relaci profilování, ukončete službu a explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

#### <a name="to-begin-profiling-a-net-framework-service"></a>Spuštění profilování služby .NET Framework  

1. Otevřete okno příkazového řádku.  

2. Použití **VSInstr** Nástroj generuje instrumentovanou verzi binárního souboru služby.  

3. Pomocí Správce řízení služeb nahraďte původní binární soubor instrumentovanou verzí. Ujistěte se, že služby Typ spouštění je nastaven na ručně.  

4. Inicializujte proměnné prostředí profilování. Typ:  

    **Vsperfclrenv –** {**/globaltracegc** &#124; **/globaltracegclife**}  

   -   **/globaltracegc** a **/globaltracegclife** Povolit shromažďování dat paměti přidělení a objekt životnosti.  

       |Možnost|Popis|  
       |------------|-----------------|  
       |**/globaltracegc**|Shromažďuje data o přidělování paměti pouze.|  
       |**/globaltracegclife**|Shromažďuje data o přidělování a objekt životním cyklu paměti.|  

5. Restartujte počítač.  

6. Otevřete okno příkazového řádku.  

7. Spusťte profiler. Typ:  

    **Nástroj VSPerfCmd**[/start](../profiling/start.md) **: trasování**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start: kolize** možnost inicializuje profiler.  

   - **/Output:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některý z těchto možností s **/start:sample** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro služby.  

   | Možnost | Popis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Určuje doménu a uživatelské jméno účtu vlastnícího pracovní proces ASP.NET. Tato možnost je vyžadována, pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows. |
   | [/ crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných přihlašovacích relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Id relace je uvedeno v **ID relace** sloupec **procesy** karty ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Určuje počet sekund čekání na inicializaci předtím, než je vrácena chyba profileru. Pokud `Interval` není zadán, čeká profiler neomezeně dlouho. Ve výchozím nastavení **/start** vrátí hodnotu okamžitě. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit profiler s shromažďování dat pozastaveno, přidejte **/globaloff** umožňuje **/start** příkazového řádku. Použití **globalon** obnovu profilování provedete. |
   | [/ Čítač](../profiling/counter.md) **:** `Config` | Shromažďuje informace z čítače výkonu procesoru zadaného v konfiguraci. Informace čítače se přidají do dat shromážděných při každé události profilování. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Určuje čítač výkonu Windows má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (. *ETL*) soubor. |


8. V případě potřeby spusťte službu.  

9. Připojení profileru ke službě. Typ:  

     **Nástroj VSPerfCmd / připojit:**`PID`&#124;`ProcessName`  

    -   Zadejte ID procesu nebo názvem procesu služby. ID procesů a názvy všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  

## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Zatímco je služba spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s *VSPerfCmd.exe* možnosti. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) sběr dat pro vlákno určené pomocí ID vlákna (`TID`).|  

## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, ukončete aplikaci používající instrumentovanou komponentu, spusťte **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Zastavte službu ze Správce řízení služeb.  

2.  Vypněte profiler. Typ:  

     **/ Shutdown VSPerfCmd**  

3.  Po dokončení veškerého profilování vyčistěte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – /globaloff**  

     Nahraďte instrumentovaný modul původní. V případě potřeby znovu nakonfigurujte typ spouštění služby.  

4.  Restartujte počítač.  

## <a name="see-also"></a>Viz také:  
 [Profil služby](../profiling/command-line-profiling-of-services.md)   
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)