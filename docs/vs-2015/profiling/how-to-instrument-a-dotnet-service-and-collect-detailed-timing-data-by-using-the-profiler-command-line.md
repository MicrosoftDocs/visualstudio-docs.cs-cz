---
title: 'Postupy: instrumentace služby rozhraní .NET a shromažďování podrobných dat časování pomocí příkazového řádku Profiler | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc95a776713876f559bf3d72b50dc6f24e055dc8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737658"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Postupy: Instrumentace služby rozhraní .NET a shromažďování podrobných dat časování pomocí příkazového řádku profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] příkazového řádku nástrojů pro profilaci k instrumentaci [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] služby a shromažďování podrobných dat časování.  

> [!NOTE]
>  Metodou instrumentace nelze Profilovat službu, je-li nelze po spuštění počítače restartovat službu, například Služba spouštěná pouze spolu s operačním systémem.  
>   
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v podadresáři nástroje \Team Tools\Performance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalační adresář. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Přidání dat interakce vrstvy do běhu profilování vyžaduje zvláštní procedury s nástroji pro profilaci příkazového řádku. Zobrazit [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Shromažďování podrobných dat časování z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] službu pomocí metody instrumentace, můžete použít [VSInstr.exe](../profiling/vsinstr.md) Nástroj generuje instrumentovanou verzi komponenty. Pak nahradíte neinstrumentovanou verzi služby instrumentovanou verzí, a ujistěte se, že je služba nastavena na Manuální spuštění. Můžete použít [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) nástroj k inicializaci globálních proměnných prostředí profilování a poté restartujte hostitelský počítač. Potom spusťte profiler.  

 Když je služba spuštěna, data o časování jsou automaticky shromažďována do datového souboru. Můžete pozastavit a obnovit sběr dat. během relace profilování.  

 Chcete-li ukončit relaci profilování, vypněte službu a explicitně vypněte profiler. Ve většině případů doporučujeme na konci relace vyčistit proměnné prostředí profilování.  

## <a name="starting-the-application-with-the-profiler"></a>Spuštění aplikace se Profiler  

#### <a name="to-start-profiling-a-net-framework-service"></a>Spuštění profilování služby .NET Framework  

1. Otevřete okno příkazového řádku.  

2. Použití **VSInstr** Nástroj generuje instrumentovanou verzi binárního souboru služby.  

3. Nahraďte původní binární soubor instrumentovanou verzí. Ve Windows správce řízení služeb, ujistěte se, že služby Typ spouštění je nastaven na ručně.  

4. Inicializovat [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] proměnných prostředí profilování. Typ:  

    **Vsperfclrenv – /globaltraceon**  

5. Restartujte počítač.  

6. Otevřete okno příkazového řádku.  

7. Spusťte profiler. Typ:  

    **/Start:trace VSPerfCmd/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: trasování** možnost inicializuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` možnost je vyžadována s **/start**. `OutputFile` Určuje název a umístění souboru dat profilování (.vsp).  

     Můžete použít některou z následujících možností s **/start:trace** možnost.  

   > [!NOTE]
   >  **/User** a **/crosssession** možnosti jsou obvykle vyžadovány pro profilovací služby.  

   |                                 Možnost                                  |                                                                                                                                            Popis                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |        Určuje doménu a uživatelské jméno účtu vlastnícího profilovaný proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn pod jiným než přihlášeným uživatelem. Vlastník procesu je uvedena ve sloupci uživatelské jméno na záložce procesy ve Správci úloh Windows.         |
   |              [/ crosssession](../profiling/crosssession.md)              | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. Id relace je uvedeno ve sloupci ID relace na záložce procesy ve Správci úloh Windows. **Protokolovacímu** může být zadán jako zkratka pro **/crosssession**. |
   |        [/waitstart](../profiling/waitstart.md)[**:**`Interval`]         |                                          Určuje počet sekund čekání na inicializaci předtím, než je vrácena chyba profileru. Pokud `Interval` není zadán, čeká profiler neomezeně dlouho. Ve výchozím nastavení **/start** vrátí hodnotu okamžitě.                                           |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                      Chcete-li spustit profiler s shromažďování dat pozastaveno, přidejte **/globaloff** umožňuje **/start** příkazového řádku. Použití **globalon** obnovu profilování provedete.                                                                       |
   |           [/ Čítač](../profiling/counter.md) **:** `Config`            |                                                                    Shromažďuje informace z čítače výkonu procesoru zadaného v konfiguraci. Informace čítače se přidají do dat shromážděných při každé události profilování.                                                                    |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                             Určuje čítač výkonu Windows má být shromážděn během profilování.                                                                                                              |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                           Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500 ms.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                              Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.                                                                              |


8. Spusťte službu z modulu snap-in Správce řízení služeb Windows.  

## <a name="controlling-data-collection"></a>Řízení kolekce dat  
 Pokud je služba spuštěna, můžete použít **VSPerfCmd.exe** možnosti spuštění a zastavení zápisu dat do datového souboru profilování. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění či ukončování služby.  

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  

-   Následující páry **VSPerfCmd** možností spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces určený identifikátorem procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) sběr dat pro vlákno určené pomocí ID vlákna (`TID`).|  

## <a name="ending-the-profiling-session"></a>Ukončení relace profilování  
 Chcete-li ukončit relaci profilování, zastavte službu, která je spuštěna instrumentovaná komponenta a následně zavolat **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) možnost profiler vypne a uzavře soubor dat profilování. **VSPerfClrEnv /globaloff** příkaz vymaže proměnné prostředí profilování.  

 Po restartování počítače-li použít nové nastavení prostředí.  

#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  

1.  Zastavte službu ze Správce řízení služeb.  

2.  Vypněte profiler. Typ:  

     **/ Shutdown VSPerfCmd**  

3.  Po dokončení veškerého profilování vyčistěte proměnné prostředí profilování. Typ:  

     **Vsperfclrenv – /globaloff**  

4.  Nahraďte instrumentovaný modul původní. V případě potřeby znovu nakonfigurujte typ spouštění služby.  

5.  Restartujte počítač.  

## <a name="see-also"></a>Viz také  
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)   
 [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)



