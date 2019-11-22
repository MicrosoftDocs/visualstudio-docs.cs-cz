---
title: Nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c65561f9a9a2ca287232b7a61bb0e07ca07a769d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299657"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Nástroje pro měření výkonu v aplikacích pro Windows 8 a Windows Server 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým nástroje Visual Studio Performance Tools shromažďují data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Toto téma popisuje změny pro nástroje pro sledování výkonu na platformách Windows 8 a Windows Server 2012.  
  
> [!NOTE]
> Nástroje výkonu pro jiné podporované verze systému Windows (Windows 7, Windows Server 2008 R2) se nezměnily.  
  
## <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Shromažďování dat z aplikací pro Windows Store z integrovaného vývojového prostředí sady Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Shromažďování dat z aplikací běžících na desktopu Windows 8 nebo na Windows Serveru 2012 z integrovaného vývojového prostředí (IDE) sady Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Shromažďování dat na aplikace spuštěné na počítači s Windows 8 nebo na Windows Serveru 2012 pomocí vzorkování z integrovaného vývojového prostředí (IDE) sady Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Profilace z příkazového řádku](#BKMK_Profiling_from_the_command_line)  
  
  [Shromažďování dat o interakcích vrstev (TIP)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
## <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a>Shromažďování dat z aplikací pro Windows Store z integrovaného vývojového prostředí sady Visual Studio  
 Při profilování aplikace pro Windows Store, která je napsaná v JavaScriptu a HTML 5, shromažďujete data instrumentace pro kód JavaScriptu. Při profilování aplikace pro Windows Store nebo součásti, která je napsaná C++v jazyce C#visual, vizuálů nebo Visual Basic, shromažďujete data vzorkování pro nativní a spravovaný kód. Svou aplikaci můžete profilovat lokálně nebo na vzdáleném počítači.  
  
 Při profilování aplikací pro Windows Store se tyto funkce a možnosti profilování nepodporují:  
  
- Profilování aplikací JavaScriptu pomocí metody vzorkování.  
  
- Profilace spravovaného a nativního kódu pomocí metody instrumentace.  
  
- Profilace souběžného zpracování  
  
- Profilace paměti .NET  
  
- Profilace interakce vrstev (TIP)  
  
- Možnosti vzorkování, jako je například nastavení události vzorkování a intervalu časování nebo shromažďování dalších dat čítače výkonu.  
  
- Možnosti instrumentace, jako je například shromažďování výkonu a dat čítače systému Windows nebo určení dalších možností příkazového řádku.  
  
  Další informace o profilování aplikací pro Windows Store naleznete v následujících tématech na stránce Windows Dev Center:  
  
  [Spouštění aplikací pro Windows Store v místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Spouštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Analýza výkonu aplikace](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [Časování funkcí JavaScriptu](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Časování funkcí JavaScriptu na vzdáleném zařízení](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [Analýza dat časování funkcí JavaScriptu](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Profilace C++vizuálu, C#vizuálu a Visual Basic kódu v aplikacích pro Windows Store v místním počítači](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Profilace C++vizuálu, C#vizuálu a Visual Basic kódu v aplikacích pro Windows Store na vzdáleném zařízení](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Analýza údajů o výkonu pro C++vizuál, C#vizuál a Visual Basic kódu v aplikacích pro Windows Store](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [V tomto tématu](#BKMK_In_this_topic)  
  
## <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a>Shromažďování dat z aplikací běžících na desktopu Windows 8 nebo na Windows Serveru 2012 z integrovaného vývojového prostředí (IDE) sady Visual Studio  
 Profilace pomocí metody instrumentace se pro systém Windows 8 nezměnila.  
  
 Profilace interakce vrstev (TIP) není podporována pomocí metody vzorkování.  
  
### <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a>Shromažďování dat na aplikace spuštěné na počítači s Windows 8 nebo na Windows Serveru 2012 pomocí vzorkování z integrovaného vývojového prostředí (IDE) sady Visual Studio  
 Tyto funkce profilování a možnosti se nepodporují při profilování aplikací pro stolní počítače s Windows 8 nebo Windows Server 2012 pomocí metody vzorkování:  
  
- Profilace interakce vrstev (TIP). Shromažďování dat s tipem je podporované pomocí instrumentace.  
  
- Možnosti vzorkování, jako je například nastavení události vzorkování a intervalu časování nebo shromažďování dalších dat čítače výkonu.  
  
## <a name="BKMK_Profiling_from_the_command_line"></a>Profilace z příkazového řádku  
 K shromažďování dat profilování na zařízeních se systémem Windows 8 a Windows Server 2012 můžete použít dva nástroje příkazového řádku, včetně zařízení, která nemají instalaci sady Visual Studio:  
  
|Název nástroje|Popis|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Shromažďuje data profilace z aplikací pro Windows Store a shromažďuje ukázková data profilování z aplikací pro stolní počítače s Windows 8 a aplikací Windows Server 2012.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Shromažďuje data profilace, souběžnosti a interakce vrstev z aplikací, které běží v theWindows 8 Desktop nebo Windows Serveru 2012. Shromažďuje všechny typy dat profilování z předchozích verzí Windows.|  
  
 Oba nástroje jsou nainstalovány se sadou Visual Studio pro použití v místním počítači.  
  
 Chcete-li Profilovat aplikace na zařízeních, ve kterých není nainstalována aplikace Visual Studio, proveďte jednu z následujících akcí:  
  
- Stáhněte si nástroje jako součást Remote Tools for Visual Studio z webu [MSDN](https://go.microsoft.com/fwlink/?LinkID=219549).  
  
- Zkopírujte a spusťte instalační program nástrojů samostatného profileru z počítače se systémem Visual Studio. Instalační programy jsou ve složce *% VSINSTALLDIR%* **\Team Tools\Performance Tools\Setups** . Vyberte instalační program operačního systému (x86/x64) vzdáleného počítače.  
  
> [!NOTE]
> Chcete-li shromáždit data profilování, je nutné nainstalovat samostatný Profiler z počítače se systémem Visual Studio na vzdáleném počítači.  
  
 Tyto funkce a možnosti profilování nejsou podporované při profilování aplikací Windows 8 a Windows Server 2012 z příkazového řádku:  
  
- Shromažďování dat z webových aplikací Windows 8 a Windows Server 2012 pomocí režimu vzorkování s [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md).  
  
- Shromažďování dat vzorkování pomocí VsPerfCmd. exe.  
  
- Možnosti vzorkování, jako je například nastavení události vzorkování a intervalu časování nebo shromažďování dalších dat čítače výkonu.  
  
## <a name="BKMK_Collecting_tier_interaction__TIP__data"></a>Shromažďování dat o interakcích vrstev (TIP)  
 Profilace interakce vrstev poskytuje další informace o době spuštění funkcí vícevrstvých aplikací, které komunikují s databázemi prostřednictvím služby ADO.NET Services. Data jsou shromažďována pouze pro volání synchronních funkcí.  
  
 **Edice sady Visual Studio**  
  
 Data profilování interakce vrstev je možné shromažďovat pomocí [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Data profilování interakce vrstev ale můžete zobrazit jenom v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Windows 8 a Windows Server 2012**  
  
1. Chcete-li shromáždit data interakce vrstev z aplikací, které jsou spuštěny v počítači se systémem Windows 8 nebo Windows Server 2012, je nutné použít metodu instrumentace.  
  
2. Nemůžete shromažďovat data interakce vrstev pro aplikace pro Windows Store.  
  
3. Data interakce vrstev můžete zahrnout do všech metod profilování v jiné podporované verzi systému Windows.  
  
   **Průvodce výkonem a Prohlížeč výkonu**  
  
   Je nutné přidat možnost shromažďování dat interakce vrstev ke spuštění profilace z Prohlížeč výkonu. Také je nutné přidat projekt, spustitelný soubor nebo web do cílového uzlu Prohlížeč výkonu. Viz [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md).  
  
   **Shromažďování dat s tipem na vzdáleném počítači**  
  
   Chcete-li shromažďovat data o interakcích vrstev na vzdáleném počítači, je nutné zkopírovat sadu **vs\_profiler\_** _\<Platform >_ **\_** _\<souboru jazyka >_ **. exe** ze složky _% VSINSTALLDIR%_ **\Team Tools\Performance** v počítači sady Visual Studio do vzdáleného počítače a nainstalovat ji. Nástroje pro profilaci nelze použít v balíčku ke stažení pro [vzdálené nástroje sady Visual Studio](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
   K shromažďování dat profilace můžete použít [VSPerfCmd](../profiling/vsperfcmd.md) nebo [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) .  
  
   **Sestavy tipů**  
  
   Data interakce vrstev se dají zobrazit jenom v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] nebo [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] IDE. Sestavy interakce na úrovni souborů prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)   
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
