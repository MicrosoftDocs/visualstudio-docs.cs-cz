---
title: VSPerfCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 54
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da82cbd8426b1a9af08e27577cdb76ca4a64d2e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148216"
---
# <a name="vsperfcmd"></a>VSPerfCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj **VSPerfCmd.exe** slouží ke spuštění a zastavení shromažďování dat výkonu. Používá následující syntaxi:  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 Následující tabulky popisují **VSPerfCmd.exe** možnosti nástrojů.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**U**|Přesměrovaný výstup konzoly je zapsaný jako Unicode. Musí se jednat o první zadanou možnost.|  
|[Začátek](../profiling/start.md) **:**`mode`|Spustí službu profilace v zadaném režimu.|  
|[Výstup](../profiling/output.md) **:**`filename`|Určuje název výstupního souboru. Použijte pouze v **nabídce Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Povoluje profilování v relacích systému Windows. Používejte pouze v **nabídce Start**, **připojit** **nebo spustit**.|  
|[Uživatel](../profiling/user-vsperfcmd.md) **:**[ `domain\` ]`username`|Povolí přístup zadaného účtu ke službě profileru. Použijte pouze v **nabídce Start**.|  
|[WaitStart](../profiling/waitstart.md)[**:** `n` ]|Čeká na inicializaci protokolovacího nástroje pro shromažďování dat. `n`Je-li parametr zadán, bude **VSPerfCmd** čekat maximálně `n` sekund. Pokud `n` parametr není zadán, bude **VSPerfCmd** čekat na neomezenou dobu. To usnadňuje použití **VSPerfCmd** jako součást dávkového procesu.|  
|[Čítač](../profiling/counter.md) **:**`cfg`|Když se použije metoda profilace vzorku, určí čítač CPU a počet událostí, které se mají použít jako interval vzorkování. Můžete vzorkovat jenom jednu hodnotu čítače.<br /><br /> Když se použije metoda profilace instrumentace, určí čítač procesoru, který se má shromáždit v každém bodu instrumentace. Používejte pouze v **nabídce Start:** `Trace` , **Attach**nebo **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Zobrazí seznam platných čítačů CPU pro aktuální počítač.|  
|[WinCounter](../profiling/wincounter.md) **:** *cesta*|Určuje událost čítače výkonu systému Windows, která se má zahrnout do dat značek Profile. Použijte pouze v **nabídce Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Určuje časový interval (v milisekundách) mezi událostmi shromažďování dat čítače výkonu systému Windows. Použijte s **WinCounter**.|  
|[Události](../profiling/events-vsperfcmd.md) **:**`option`|Řídí kolekci zadaných událostí trasování událostí pro Windows (ETW). Data ETW se shromažďují do souboru. ITL, který není souborem dat profilování (. vsp).|  
|[Stav](../profiling/status.md)|Zobrazuje stav profileru, informace o procesech, které jsou aktuálně profilované, a účty, které mají oprávnění k řízení profileru.|  
|[Vypnutí](../profiling/shutdown.md)[**:** `n` ]|Zavře soubor dat profilování a vypne Profiler.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Obnoví shromažďování dat po volání **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Zastaví veškerou shromažďování dat, ale neukončí relaci profilování.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:**`pid`|Obnoví sběr dat pro zadaný proces po pozastavení profilování voláním metody **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:**`pid`|Zastaví sběr dat pro zadaný proces.|  
|[ThreadOn a ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Obnoví profilování pro zadaný proces po pozastavení profilování voláním metody **VSPerfCmdThreadOff**. **ThreadOn** použijte pouze v případě profilace s metodou instrumentace.|  
|[ThreadOn a ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Pozastaví profilování v zadaném vlákně. **ThreadOff** použijte pouze v případě profilace s metodou instrumentace.|  
|[Značka](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Vloží do datového souboru profilování značku s volitelným textem.|  
  
## <a name="sampling-method-options"></a>Volby metody vzorkování  
 Následující možnosti jsou k dispozici, pouze pokud používáte metodu profilování vzorkování.  
  
|Možnost|Popis|  
|------------|-----------------|  
|[Spustit](../profiling/launch.md) **:** *spustitelný soubor*|Spustí zadanou aplikaci a spustí profilování.|  
|[Args](../profiling/args.md) **:** *argumenty*|Určuje argumenty příkazového řádku, které se mají předat spuštěné aplikaci.|  
|[Konzola](../profiling/console.md)|Spustí zadaný příkaz v novém okně příkazového řádku.|  
|[Připojit](../profiling/attach.md) **:** *PID*[**,**_PID_]|Spustí profilování zadaných procesů. Procesy lze identifikovat pomocí ID procesu nebo pomocí názvu procesu.|  
|[Detach](../profiling/detach.md)[**:**_PID_[;_PID_]]|Zastaví profilování zadaných procesů. Procesy lze identifikovat pomocí ID procesu nebo pomocí názvu procesu. Pokud není zadán žádný proces, profilování se zastaví pro všechny procesy.|  
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Allocation** `&#124;` **disdoba**přidělení}]|Shromažďuje data o přidělování paměti .NET a o životnosti objektů. Používejte pouze s možností **VSPerfCmdLaunch** .|  
  
### <a name="sampling-interval-options"></a>Možnosti intervalu vzorkování  
 Následující možnosti určují typ a dobu trvání vzorkovacích intervalů. Výchozí hodnota je **Timer**. Čítače procesoru můžete zadat také jako interval pomocí možnosti **čítač** . Tyto možnosti lze zadat pouze pomocí možnosti **Spustit** nebo s prvním **připojením** relace profilování.  
  
|Možnost|Popis|  
|------------|-----------------|  
|[PF](../profiling/pf.md)[**:**_n_]|Ukázky v každé n-tém chybě stránky (výchozí = 10).|  
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Ukázky v každém n-tém systémovém volání (výchozí = 10).|  
|[Časovač](../profiling/timer.md)[**:**_n_]|Ukázky v každém n-tém cyklu procesoru (výchozí = 10000000).|  
  
## <a name="service-component-and-kernel-mode-device-options"></a>Součást služby a možnosti zařízení v režimu jádra  
 Následující možnosti správy podporují součásti služby profilace nebo ovladače zařízení režimu jádra. Možnosti správy nastavily oprávnění profilace a řídí profilované služby nebo ovladače zařízení.  
  
 Na příkazovém řádku, který běží s přihlašovacími údaji správce, je nutné provést možnosti správy.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Správce: zabezpečení** \<**ALLOW&#124;DENY**> *Right*[ *Right*] \<*User*&#124;*Group*>|Povolí nebo zakáže přístup ke službám profilace zadaného uživateli nebo skupině.<br /><br /> `Right` může být:<br /><br /> CrossSession – umožní uživateli přístup k této službě, aby prochází profilaci mezi relacemi.<br /><br /> SampleProfiling – umožní uživateli přístup k ovladači, aby bylo možné profilování vzorkování povolit. Používá se také pro přístup k informacím o přechodu jádra během profilace trasování.<br /><br /> FullAccess – udělí uživateli přístup CrossSession i SampleProfiling.|  
|**Správce: zabezpečení, seznam**|Zobrazí seznam aktuálních stavů služby profilace a seznam uživatelských oprávnění.|  
|**Správce:**\<*Service*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|Spustí, zastaví, nainstaluje nebo odinstaluje součást služby profilace (Service) nebo ovladač zařízení režimu jádra (ovladač).|  
|**Správce:** \<*Service*&#124;*Driver*> **Automatické spuštění**\<**ON**&#124;**OFF**>|Povolí nebo zakáže automatické spuštění služby profilace (Service) nebo ovladače zařízení režimu jádra po restartu.|  
  
## <a name="vsperfcmd-driver"></a>VSPerfCmd/Driver  
 Možnost **VSPerfCmd/Driver** je nyní zastaralá. Pro tuto funkci použijte možnosti **VsPerfCmdAdmin** .  
  
## <a name="see-also"></a>Viz také  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
