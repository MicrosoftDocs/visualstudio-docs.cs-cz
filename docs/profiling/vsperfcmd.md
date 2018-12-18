---
title: Nástroj VSPerfCmd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23abc362b3c91579585272e4ebf1b190cab55dde
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320979"
---
# <a name="vsperfcmd"></a>VSPerfCmd
*VSPerfCmd.exe* nástroj se používá ke spuštění a zastavení shromažďování dat o výkonu. Používá následující syntaxi:  
  
```cmd  
VSPerfCmd [/U] [/options]  
```  
  
 Následující tabulky popisují *VSPerfCmd.exe* nástroj možnosti.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**U**|Přesměrovaný výstup konzoly je zapsán jako Unicode. První možnost je povinná.|  
|[Spustit](../profiling/start.md) **:** `mode`|Spuštění služby profilace v zadaný režim.|  
|[Výstup](../profiling/output.md) **:** `filename`|Určuje název výstupního souboru. Používejte pouze s **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Umožňuje profilace napříč relacemi Windows. Používejte pouze s **Start**, **připojit**, **, nebo spusťte**.|  
|[Uživatel](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Povolí zadaný účet přístup ke službě profileru. Používejte pouze s **Start**.|  
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Počká na inicializaci protokolovače sběru dat. Pokud `n` není zadána, **VSPerfCmd** počká nejvýše `n` sekund. Pokud `n` není zadán, **VSPerfCmd** bude čekat bez omezení. To usnadňuje použití nástroje **VSPerfCmd** jako součást dávkového procesu.|  
|[Čítač](../profiling/counter.md) **:** `cfg`|Když se používá ukázková metoda profilace, určuje čítače procesoru a počet událostí, který se použije jako interval vzorkování. Vzorkovat pouze jednu hodnotu čítače.<br /><br /> Když se používá metoda profilace instrumentace, určuje čítačů procesoru, které se mají shromažďovat u každého bodu instrumentace. Používejte pouze s **Start:**`Trace`, **připojit**, nebo **spuštění**.|  
|[QueryCounters](../profiling/querycounters.md)|Zobrazí seznam platný čítače CPU pro aktuální počítač.|  
|[WinCounter](../profiling/wincounter.md) **:** *cesta*|Určuje události čítače výkonu Windows mají zahrnout do profilu označit data. Používejte pouze s **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Určuje časový interval (v milisekundách) mezi událostmi sběru dat čítače výkonu Windows. Použití s **WinCounter**.|  
|[Události](../profiling/events-vsperfcmd.md) **:** `option`|Kolekci ovládacích prvků konkrétní události trasování událostí pro Windows (ETW). Shromažďovaných dat trasování událostí pro Windows do. *itl* soubor, který není dat profilování (. *Vsp*) soubor.|  
|[Status](../profiling/status.md)|Zobrazí stav profileru, informace o procesy, které jsou právě profilována a účty, které mají oprávnění k řízení profileru.|  
|[Vypnutí](../profiling/shutdown.md)[**:**`n`]|Zavření souboru dat profilování a profiler vypne.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Obnoví shromažďování dat po volání **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Zastaví shromažďování všech dat, ale nemá na konci relace profilování.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Obnoví shromažďování dat pro zadaný proces po profilace byla pozastavena voláním **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Zastaví sběr dat pro zadaný proces.|  
|[ThreadOn a ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid.*|Obnoví profilace pro zadaný proces po profilace byla pozastavena voláním **VSPerfCmdThreadOff**. Použití **ThreadOn** jenom v případě, že profilace pomocí metody instrumentace.|  
|[ThreadOn a ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid.*|Pozastaví profilace pro zadaný podproces. Použití **ThreadOff** jenom v případě, že profilace pomocí metody instrumentace.|  
|[Označit](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Vloží znak do souboru dat profilování, s volitelným textem.|  
  
## <a name="sample-method-options"></a>Ukázka možnosti – metoda  
 Tyto možnosti jsou k dispozici pouze při použití metoda profilování vzorkování.  
  
|Možnost|Popis|  
|------------|-----------------|  
|[Spuštění](../profiling/launch.md) **:** *spustitelný soubor*|Zadaná aplikace spustí a začne profilace.|  
|[Args](../profiling/args.md) **:** *argumenty*|Určuje argumenty příkazového řádku k předání do aplikace.|  
|[Console](../profiling/console.md)|V novém okně Příkazový řádek spustí zadaný příkaz.|  
|[Připojit](../profiling/attach.md) **:** *PID*[**,**_PID_]|Zahájení profilace konkrétních procesů. Procesy lze identifikovat podle ID procesu nebo název procesu.|  
|[Odpojit](../profiling/detach.md)[**:**_PID_[,_PID_]]|Zastaví profilaci konkrétních procesů. Procesy lze identifikovat podle ID procesu nebo název procesu. Pokud není zadán žádný proces, profilace je zastaveno pro všechny procesy.|  
|[Uvolňování paměti](../profiling/gc-vsperfcmd.md)[**:**{**přidělení**`&#124;`**životnost**}]|Shromažďuje data paměti .NET přidělení a objekt životnost. Použít pouze **VSPerfCmdLaunch** možnost.|  
  
### <a name="sample-interval-options"></a>Možnosti intervalu vzorku  
 Následující možnosti určit typ a doba trvání vzorkování intervalech. Výchozí hodnota je **časovače**. Čítače CPU může také zadáte jako interval pomocí **čítač** možnost. Tyto možnosti lze zadat pouze s **spuštění** nebo s prvním **připojit** z relace profilování.  
  
|Možnost|Popis|  
|------------|-----------------|  
|[PF](../profiling/pf.md)[**:**_n_]|Vzorkuje při každé n tém stránkování (výchozí = 10).|  
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Ukázky při každém n tém systému volání (výchozí = 10).|  
|[Časovač](../profiling/timer.md)[**:**_n_]|Cyklus vzorkuje při každém n tém procesoru (výchozí = 10000000).|  
  
## <a name="service-component-and-kernel-mode-device-options"></a>Možnosti zařízení režimu služby pro komponenty a jádra  
 Následující možnosti správy podporovat profilování součásti služby nebo ovladače zařízení režimu jádra. Možnosti Správce nastavení oprávnění profilace a řídit profilované služby nebo ovladače zařízení.  
  
 Možnosti správce je třeba spustit na příkazovém řádku, na kterém běží s přihlašovacími údaji správce.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Admin:Security**, \< **povolit&#124;ODEPŘÍT**>, *vpravo*[ *vpravo*], \< *uživatele* &#124; *Skupiny*>|Povoluje nebo zakazuje zadaného uživatele nebo skupiny přístup k profilovací služby.<br /><br /> `Right` může být:<br /><br /> CrossSession – umožní uživateli přístup ke službě pro různé relace profilování.<br /><br /> SampleProfiling – umožní uživateli přístup k ovladači povolit profilaci vzorkování. Také umožňuje přístup k informacím o přechodu jádra během profilace trasování.<br /><br /> FullAccess – umožňuje uživateli CrossSession a SampleProfiling přístup.|  
|**Admin:Security seznamu**|Zobrazí aktuální stav služeb profilace a zobrazí seznam oprávnění uživatele.|  
|**Správce:** \< *služby*&#124;*ovladač*>\<**START**&#124;**zastavit**  &#124; **Nainstalovat**&#124;**odinstalace**>|Spustí, zastaví, nainstaluje nebo odinstaluje komponentu služeb profilace (service) nebo ovladač zařízení režimu jádra (driver).|  
|**Správce:** \< *služby*&#124;*ovladač*>**AutoStart**\<**na** &#124; **Vypnuto**>|Povolí nebo zakáže automatické spuštění služby profilace (service) nebo ovladač zařízení režimu jádra (driver) po restartu.|  
  
## <a name="vsperfcmd-driver"></a>Nástroj VSPerfCmd Driver/Driver  
 **Driver/Driver VSPerfCmd** možnost je nyní zastaralá. Použití **VsPerfCmdAdmin** možnosti pro tuto funkci.  
  
## <a name="see-also"></a>Viz také:  
 [Nástroj VSInstr](../profiling/vsinstr.md)   
 [Vsperfmon –](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)