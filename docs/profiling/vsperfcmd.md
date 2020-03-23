---
title: VSPerfCmd | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 53378c3d210ef9666df251d68a3eec570f8caa2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777995"
---
# <a name="vsperfcmd"></a>VSPerfCmd
Nástroj *VSPerfCmd.exe* se používá ke spuštění a zastavení shromažďování dat výkonu. Používá následující syntaxi:

```cmd
VSPerfCmd [/U] [/options]
```

 Následující tabulky popisují volby nástroje *VSPerfCmd.exe.*

|Možnost|Popis|
|------------|-----------------|
|**U**|Přesměrovaný výstup konzoly je zapsán jako Unicode. Musí být zadána první možnost.|
|[Začátek](../profiling/start.md) **:**`mode`|Spustí službu profilování v zadaném režimu.|
|[Výstup](../profiling/output.md) **:**`filename`|Určuje název výstupního souboru. Používejte pouze s **úvodní .**|
|[CrossSession&#124;CS](../profiling/crosssession.md)|Umožňuje profilování v relacích systému Windows. Používejte pouze se **startem**, **připojením** **nebo spuštěním**.|
|[Uživatel](../profiling/user-vsperfcmd.md) **:**:`domain\`[ ]`username`|Povolí zadaný přístup účtu ke službě profiler. Používejte pouze s **úvodní .**|
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Čeká na inicializaci protokolování shromažďování dat. Pokud `n` je zadán, **VSPerfCmd** `n` bude čekat na maximálně sekund. Pokud `n` není zadán, **VSPerfCmd** bude čekat neomezeně dlouho. To usnadňuje použití **VSPerfCmd** jako součást dávkového procesu.|
|[Čítač](../profiling/counter.md) **:**`cfg`|Při použití metody profilování vzorku určuje čítač procesoru a počet událostí, které mají být použity jako interval vzorkování. Můžete vzorkovat pouze jednu hodnotu čítače.<br /><br /> Při použití metody profilování instrumentace určuje čítač procesoru, který má být shromažďován v každém bodě instrumentace. Používejte pouze při **spuštění:**`Trace`, **Připojit**nebo **Spustit**.|
|[QueryCounters](../profiling/querycounters.md)|Zobrazí seznam platných čítačů procesoru pro aktuální počítač.|
|[WinCounter](../profiling/wincounter.md) **:** *cesta*|Určuje událost čítače výkonu systému Windows, která má být zahrnuta s daty značky profilu. Používejte pouze s **úvodní .**|
|[Automatické označení](../profiling/automark.md) **:** *n*|Určuje časový interval (v milisekundách) mezi událostmi shromažďování dat čítače výkonu systému Windows. Použití s **wincounter**.|
|[Události](../profiling/events-vsperfcmd.md) **:**`option`|Řídí kolekci zadaných událostí trasování událostí pro Windows (ETW). Data ETW jsou shromažďována do . *souborit,* který není profilovacími daty (.* vsp*).|
|[Stav](../profiling/status.md)|Zobrazuje stav profileru, informace o procesech, které jsou aktuálně profilovány, a účty, které mají oprávnění k řízení profileru.|
|[Vypnutí](../profiling/shutdown.md)[**:**`n`]|Zavře datový soubor profilování a vypne profiler.|
|[Globální on](../profiling/globalon-and-globaloff.md)|Obnoví shromažďování dat po volání **VSPerfCmdGlobalOff**.|
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Zastaví všechny shromažďování dat, ale neukončí relaci profilování.|
|[Proceson](../profiling/processon-and-processoff.md) **:**`pid`|Obnoví shromažďování dat pro zadaný proces po profilování byl pozastaven volání **VSPerfCmdProcessOff**.|
|[ProcessOff](../profiling/processon-and-processoff.md) **:**`pid`|Zastaví shromažďování dat pro zadaný proces.|
|[ThreadOn a ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Obnoví profilování pro zadaný proces po profilování bylo pozastaveno volání **VSPerfCmdThreadOff**. **ThreadOn** používejte pouze při profilování pomocí metody instrumentace.|
|[ThreadOn a ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Pozastaví profilování pro zadané vlákno. **ThreadOff** používejte pouze při profilování pomocí metody instrumentace.|
|[Označit](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Vloží značku do datového souboru profilování s volitelným textem.|

## <a name="sample-method-options"></a>Možnosti ukázkové metody
 Následující možnosti jsou k dispozici pouze v případě, že používáte metodu profilování vzorkování.

|Možnost|Popis|
|------------|-----------------|
|[Spuštění](../profiling/launch.md) **:** *Spustitelný soubor*|Spustí zadanou aplikaci a zahájí profilování.|
|[Args](../profiling/args.md) **:** *Argumenty*|Určuje argumenty příkazového řádku, které mají být předávány spuštěné aplikaci.|
|[Konzola](../profiling/console.md)|Spustí zadaný příkaz v novém okně příkazového řádku.|
|[Připojit](../profiling/attach.md) **:** *PID*[**,**_PID_]|Začne profilování zadaných procesů. Procesy lze identifikovat podle ID procesu nebo podle názvu procesu.|
|[Odpojit](../profiling/detach.md)[**:**_PID_[,_PID_]]|Zastaví profilování zadaných procesů. Procesy lze identifikovat podle ID procesu nebo podle názvu procesu. Pokud není zadán žádný proces, profilování je zastaveno pro všechny procesy.|
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Doba****přidělení**`&#124;`}]|Shromažďuje data přidělení paměti .NET a životnosti objektu. Používejte pouze s volbou **VSPerfCmdLaunch.**|

### <a name="sample-interval-options"></a>Možnosti intervalu vzorku
 Následující možnosti určují typ a dobu trvání intervalů vzorkování. Výchozí hodnota je **Timer**. Můžete také zadat čítač procesoru jako interval pomocí možnosti **Čítač.** Tyto možnosti lze zadat pouze s **spuštěnínebo** s první **připojit** relace profilování.

|Možnost|Popis|
|------------|-----------------|
|[PF](../profiling/pf.md)[**:**_n_]|Ukázky na každé chybě n-té stránky (default=10).|
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Ukázky při každém n-tém systémovém volání (default=10).|
|[Časovač](../profiling/timer.md)[**:**_n_]|Ukázky na každém cyklu n-tý procesor (default=10000000).|

## <a name="service-component-and-kernel-mode-device-options"></a>Možnosti součásti služby a zařízení režimu jádra
 Následující možnosti správce podporují součásti služby profilování nebo ovladače zařízení režimu jádra. Možnosti správce nastavují oprávnění profilování a řídí profilovanou službu nebo ovladač zařízení.

 Možnosti správce musí být provedeny na příkazovém řádku, který je spuštěn s pověřeními pro správu.

|Možnost|Popis|
|------------|-----------------|
|**Admin:Zabezpečení** \<, **POVOLIT&#124;ODEPŘÍT**>, *Group* *Vpravo*[ *Vpravo*], \<Skupina *&#124;uživatele*>|Povolí nebo odepře zadaný přístup uživatele nebo skupiny ke službám profilování.<br /><br /> `Right`může být:<br /><br /> CrossSession - poskytuje uživateli přístup ke službě provést profilování napříč relacemi.<br /><br /> SampleProfiling - poskytuje uživateli přístup k ovladači, který umožňuje profilování vzorkování. Používá se také pro přístup k informacím o přechodu jádra během sledování profilování.<br /><br /> FullAccess - poskytuje uživateli přístup crosssession a sampleprofiling.|
|**Admin:Zabezpečení, seznam**|Uvádí aktuální stav profilování služeb a seznam uživatelských oprávnění.|
|**Admin:** \< *Service*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|Spustí, zastaví, nainstaluje nebo odinstaluje komponentu služby profilování (službu) nebo ovladač zařízení (ovladač) režimu jádra.|
|**Admin:** \<Automatické**spuštění**\< *ovladače*> *služby*&#124;**zapnuto** **&#124;vypnuto**>|Povolí nebo zakáže automatické spuštění profilovací služby (služby) nebo ovladače zařízení (ovladače) režimu jádra po restartování.|

## <a name="vsperfcmd-driver"></a>VSPerfCmd /Ovladač
 **Možnost VSPerfCmd /Driver** je nyní zastaralá. Pro tuto funkci použijte možnosti **správce VsPerfCmd.**

## <a name="see-also"></a>Viz také
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
