---
title: Nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e02ce9a9ef06574de999620017b96d470a76e6c9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767535"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 požadované významných změnách v nástroji Sledování výkonu sady Visual Studio způsob, jak shromažďovat data na těchto platformách. Aplikace Windows Store také vyžadují nové techniky kolekce. Toto téma popisuje změny pro nástroje pro měření výkonu na platformách systému Windows 8 a Windows Server 2012.  
  
> [!NOTE]
>  Sada Performance tools for ostatní podporované verze Windows (Windows 7, Windows Server 2008 R2) se nezměnily.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Shromažďování dat pro aplikace z Windows Store z integrovaného vývojového prostředí sady Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Shromažďování dat na aplikace, které běží na ploše systému Windows 8 nebo Windows serveru 2012 z integrovaného vývojového prostředí sady Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Shromažďování dat na aplikace, které běží na ploše systému Windows 8 nebo Windows Server 2012 s použitím vzorkování z integrovaného vývojového prostředí sady Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Profilace z příkazového řádku](#BKMK_Profiling_from_the_command_line)  
  
  [Shromažďování dat (TIP) interakce vrstev](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Shromažďování dat pro aplikace z Windows Store z integrovaného vývojového prostředí sady Visual Studio  
 Při profilování aplikace Windows Store, který je napsán v jazyce JavaScript a HTML 5, shromažďování dat instrumentace pro kód jazyka JavaScript. Při profilování aplikace Windows Store nebo součásti, která je napsána v jazyce Visual C++, Visual C# nebo Visual Basic, shromažďování dat vzorkování pro nativního a spravovaného kódu. Aplikace můžete Profilovat, místně nebo ve vzdáleném počítači.  
  
 Tyto profilování funkce a možnosti nejsou podporovány při profilování aplikací Windows Store:  
  
- Profilace aplikací jazyka JavaScript pomocí metody odběru vzorků.  
  
- Profilace spravovaného a nativního kódu pomocí metody instrumentace.  
  
- Profilace souběžnosti  
  
- Profilování paměti .NET  
  
- Interakce vrstev (TIP) pro profilaci  
  
- Možnosti vzorkování, například nastavit událost odběru vzorků a interval časování nebo shromažďování dat čítače výkonu Další.  
  
- Instrumentace možnosti, jako je shromažďování dat čítačů windows a výkonu nebo zadání další možnosti příkazového řádku.  
  
  Další informace o profilování aplikací Windows Store naleznete v následujících tématech na webu Windows Dev Center:  
  
  [Spouštění aplikací pro Windows Store v místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Spouštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Analýza výkonu aplikace](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [Časování funkcí jazyka JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Časování funkcí jazyka JavaScript na vzdáleném zařízení](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [Analýza dat časování funkcí jazyka JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Kód profilu Visual C++, Visual C# a Visual Basic v aplikacích pro Windows Store v místním počítači](http://msdn.microsoft.com/en-us/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Kód profilu Visual C++, Visual C# a Visual Basic v aplikacích pro Windows Store na vzdáleném zařízení](http://msdn.microsoft.com/en-us/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Analýza výkonnostních dat pro kód jazyka Visual C++, Visual C# a Visual Basic v aplikacích pro Windows Store](http://msdn.microsoft.com/en-us/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Shromažďování dat na aplikace, které běží na ploše systému Windows 8 nebo Windows serveru 2012 z integrovaného vývojového prostředí sady Visual Studio  
 Profilace pomocí metody instrumentace nedošlo ke změně pro systém Windows 8.  
  
 Interakce vrstev (TIP) profilace není podporováno pomocí metody vzorkování.  
  
###  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Shromažďování dat na aplikace, které běží na ploše systému Windows 8 nebo Windows Server 2012 s použitím vzorkování z integrovaného vývojového prostředí sady Visual Studio  
 Tyto profilování funkce a možnosti nejsou podporovány při profilování desktopových aplikací Windows 8 nebo Windows Server 2012 aplikace pomocí metody vzorkování:  
  
-   Profilace sledováním interakce vrstev (TIP). Shromažďování dat TIP je podporován pomocí instrumentace.  
  
-   Možnosti, jako je nastavení událost odběru vzorků a interval časování nebo shromažďování dat čítače výkonu Další vzorkování.  
  
##  <a name="BKMK_Profiling_from_the_command_line"></a> Profilace z příkazového řádku  
 Ke shromažďování dat profilace na zařízeních s Windows 8 a Windows Server 2012, včetně zařízení, která není nutné instalaci sady Visual Studio, použijte dva nástroje příkazového řádku:  
  
|Název nástroje|Popis|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Shromažďuje data profilace z aplikace Windows Store a shromažďuje data profilace vzorku z aplikací klasické pracovní plochy systému Windows 8 a Windows Server 2012 aplikace...|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Shromažďuje instrumentace, souběžnost a data z aplikací, které jsou spuštěny na ploše sadě Windows 8 nebo Windows Server 2012 profilace interakce vrstev. Shromažďuje všechny typy dat profilování z předchozích verzí Windows.|  
  
 Oba nástroje jsou nainstalovány se sadou Visual Studio pro použití v místním počítači.  
  
 Do profilu aplikace na zařízeních, které nemají nainstalované, Visual Studio proveďte jednu z následujících akcí:  
  
-   Stáhněte si nástroje jako součást nástrojů Remote Tools for Visual Studio z [webu MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).  
  
-   Kopírování a spusťte instalační program nástroje samostatného profileru z počítače Visual Studio. Instalační programy jsou v *VSInstallDir %* **\Team Tools\Performance Tools\Setups** složky. Zvolte instalační program pro operační systém (x86/x64) vzdáleného počítače.  
  
> [!NOTE]
>  Chcete-li shromažďovat data profilování TIP, musí instalace samostatného profileru z vašeho počítače Visual Studio na vzdáleném počítači.  
  
 Tyto profilování funkce a možnosti nejsou podporovány při profilování aplikací Windows 8 a Windows Server 2012 z příkazového řádku:  
  
-   Shromažďování dat z webových aplikací systému Windows 8 a Windows Server 2012 pomocí režimu vzorkování s [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
-   Shromažďování dat vzorkování pomocí VsPerfCmd.exe.  
  
-   Možnosti, jako je nastavení událost odběru vzorků a interval časování nebo shromažďování dat čítače výkonu Další vzorkování.  
  
##  <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Shromažďování dat (TIP) interakce vrstev  
 Profilování interakce vrstev poskytuje další informace o spuštění s úspěšností funkce víceúrovňových aplikací, které komunikují s databázemi prostřednictvím služeb ADO.NET. Data se shromažďují pouze pro synchronní volání.  
  
 **Edice sady Visual Studio**  
  
 Data profilace interakce vrstev lze shromažďovat pomocí [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Nicméně data profilace interakce vrstev lze zobrazit pouze v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Windows 8 a Windows Server 2012**  
  
1. Ke shromažďování dat interakce vrstev z aplikací, které jsou spuštěny na ploše systému Windows 8 nebo Windows Server 2012, musíte použít metody instrumentace.  
  
2. Nelze shromažďování dat interakce vrstev pro aplikace Windows Store.  
  
3. Dat interakce vrstev můžete zahrnout všechny metody profilování na ostatní podporované verze systému Windows.  
  
   **Průvodce výkonu a prohlížeč výkonu**  
  
   Je nutné přidat možnost kolekce dat interakce vrstvy do běhu profilování z prohlížeče výkonu. Musíte také přidat projekt, spustitelný soubor nebo web na cílový uzel prohlížeč výkonu. Zobrazit [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md).  
  
   **Shromažďování dat TIP na vzdáleném počítači**  
  
   Ke shromažďování dat interakce vrstev ve vzdáleném počítači, je nutné zkopírovat **vs\_profiler\_**_\<platformy >_ **\_**  _\<Jazyk >_**.exe** soubor _VSInstallDir %_**\Team Tools\Performance Tools\Setups**složky sady Visual Studio počítače ke vzdálenému počítači a nainstalujte ho. Nelze použít v nástrojů pro profilaci [Visual Studio Remote Tools](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) stažení balíčku.  
  
   Můžete použít [VSPerfCmd](../profiling/vsperfcmd.md) nebo [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) ke shromažďování dat profilování.  
  
   **TIP sestavy**  
  
   Dat interakce vrstev lze zobrazit pouze v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] nebo [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] integrovaného vývojového prostředí. Interakce vrstev souborovému sestavy prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)   
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)



