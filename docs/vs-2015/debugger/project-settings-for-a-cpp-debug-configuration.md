---
title: Nastavení pro konfiguraci ladění jazyka C++ projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 404bbc753b2729ad5ec7625fa01803b8a6bdf5c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800793"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit nastavení projektu pro konfiguraci ladění jazyka C nebo Visual C++ v **stránky vlastností** dialogové okno, jak je popsáno v [postupy: nastavení ladění a konfiguraci vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky popisují, kde najít nastavení související s ladicí program v **stránky vlastností** dialogové okno.  
  
> [!WARNING]
>  Nastavení ladění projektu v **konfigurační vlastnosti/ladění** kategorie pro aplikace Windows Store a součásti, které jsou napsané v jazyce C++ se liší. Zobrazit [spustíte relaci ladění (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) ve Windows Development Center.  
  
 Určete, který ladicí program používat v **ladicí program ke spuštění** pole se seznamem. Vaše volba bude mít vliv na vlastnosti, které jsou viditelné.  
  
 Nastavení jednotlivých vlastností ladění automaticky zapíše a uloží do souboru "za user" (. vcxproj.user) pro vaše řešení při každém uložení vašeho řešení.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Složka s vlastnostmi konfigurace (kategorie ladění)  
  
|**Nastavení**|**Popis**|  
|-----------------|---------------------|  
|**Ladicí program ke spuštění**|Určuje ladicí program ke spuštění, s následujícími možnostmi:<br /><br /> -   **Ladicí program místní Windows**<br />-   **Windows vzdáleného ladicího programu**<br />-   **Ladicí program webového prohlížeče**<br />-   **Ladicí program webové služby**|  
|**Příkaz** (ladicí program místní Windows)|Určuje příkaz pro spuštění programu, který právě ladíte v místním počítači.|  
|**Vzdálený příkaz** (Windows vzdálený ladicí program)|Cesta k .exe ve vzdáleném počítači. Zadejte cestu stejně, jako byste ji zadávali ve vzdáleném počítači.|  
|**Argumenty příkazového** (ladicí program místní Windows a Windows vzdálený ladicí program)|-Určuje argumenty pro příkaz zadaný dříve.<br /><br /> V tomto poli můžete použít následující operátory přesměrování:<br /><br /> < `file`<br /> Čte stdin ze souboru.<br /><br /> > `file`<br /> Zapíše hodnotu stdout do souboru.<br /><br /> >> `file`<br /> Připojí stdout do souboru.<br /><br /> 2> `file`<br /> Zapíše hodnotu stderr do souboru.<br /><br /> 2>> `file`<br /> Připojí stderr do souboru.<br /><br /> 2> &1<br /> Odešle výstup stderr (2) do stejného umístění jako stdout (1).<br /><br /> 1> &2<br /> Odešle stdout (1) výstup do stejného umístění jako stderr (2).<br /><br /> Ve většině případů jsou tyto operátory použitelné pouze pro konzolové aplikace.|  
|**Pracovní adresář**|Určuje pracovní adresář laděného programu, relativně vzhledem k adresáři projektu, kde je umístěn váš soubor EXE. Pokud toto pole ponecháte prázdné, pracovní adresář je adresář projektu. Pro vzdálené ladění bude adresář projektu na vzdáleném serveru.|  
|**Připojit** (ladicí program místní Windows a Windows vzdálený ladicí program)|Určuje, zda chcete spustit nebo připojit k aplikaci. Výchozí nastavení je Ne.|  
|**Název vzdáleného severu** (Windows vzdálený ladicí program)|Určuje název počítače (kromě vašeho), na kterém chcete ladit aplikace.<br /><br /> Makro sestavení RemoteMachine je nastavena na hodnotu této vlastnosti; Další informace najdete v tématu [Macros for Build Commands and Properties](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Připojení** (Windows vzdálený ladicí program)|Umožňuje přepínat mezi typy standard a bez ověřování připojení pro vzdálené ladění. Zadejte název vzdáleného počítače v **název vzdáleného serveru** pole. Typy připojení patří:<br /><br /> -   **Vzdálený s ověřováním Windows**<br />-   **Vzdálený bez ověřování (pouze nativní)**<br /><br /> **Poznámka:** vzdálené ladění bez ověřování může zanechat vzdálený počítač zranitelné vůči narušení zabezpečení. Režim ověřování Windows je bezpečnější.<br /><br /> Další informace najdete v tématu [nastavení vzdáleného ladění](../debugger/remote-debugging.md).|  
|**Adresa URL operace HTTP** (Web ladicí program služby a ladicí program webového prohlížeče)|Určuje adresu URL, kde je umístěn projekt, který ladíte.|  
|**Typ ladicího programu**|Určuje typ ladicího programu, který se má použít: **pouze nativní**, **pouze spravované**, **pouze GPU**, **smíšený**, **automaticky**(výchozí), nebo **skript**.<br /><br /> -   **Pouze nativní** je pro nespravovaný kód jazyka C++.<br />-   **Režim pouze spravovaný** je pro kód, který běží v rámci common language runtime (spravovaný kód).<br />-   **Smíšené** vyvolá ladicí programy pro spravovaný i nespravovaný kód.<br />-   **Automatické** Určuje typ ladicího programu na základě kompilátoru a informací souboru EXE.<br />-   **Skript** vyvolá ladicí program skriptů.<br />-   **Pouze GPU** je pro kód C++ AMP, který běží na GPU zařízení nebo v rasterizéru referenčního rozhraní DirectX. Zobrazit [ladění kódu GPU](../debugger/debugging-gpu-code.md).|  
|**Prostředí** (ladicí program místní Windows)|Určuje proměnné prostředí pro program, který ladíte. Použijte syntaxi proměnných standardního prostředí (například `PATH="%SystemRoot%\..."`). Tyto proměnné přepisují prostředí systému nebo jsou sloučeny s prostředím systému v závislosti na tom **sloučit prostředí** nastavení. Po kliknutí na sloupec nastavení "Upravit..." zobrazí. Kliknutím na tento odkaz upravíte proměnné prostředí.|  
|**Sloučit prostředí** (ladicí program místní Windows)|Určuje, zda proměnné, které jsou určené v **prostředí** pole se sloučí s prostředím, který je definován v operačním systému. Výchozí nastavení je Ano.|  
|**Ladění SQL** (všechny kromě ladicího programu clusteru MPI)|Umožňuje ladění procedur SQL z vašich [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] aplikace. Výchozí nastavení je Ne.|  
|**Typ akcelerátoru ladění** (pouze ladění GPU)|Určuje zařízení GPU používané pro ladění. Instalace ovladačů pro kompatibilní zařízení GPU přidá další možnosti. Ve výchozím nastavení je "GPU - softwarový emulátor."|  
|**Výchozí chování zarážky GPU** (pouze ladění GPU)|Určuje, zda by měla být zvýšena událost zarážky pro každý podproces v křivce SIMD. Ve výchozím nastavení je pro vyvolání události zarážky pouze jednou na každý svazek.|  
|**Výchozí akcelerátor amp** (pouze ladění GPU)|Určuje výchozí akcelerátor AMP při ladění kódu GPU. Zvolte **softwarový akcelerátor WARP** pro zjištění, zda problém způsoben hardwarem nebo ovladačem namísto kódu.|  
|**Adresář nasazení** (Windows vzdálený ladicí program)|Určuje cestu ve vzdáleném počítači, kde bude výstup projektu zkopírovaný před spuštěním. Cesta může být síťová sdílená položka vzdáleného počítače, nebo může být cesta ke složce ve vzdáleném počítači. Ve výchozím nastavení je prázdný, což znamená, že výstup projektu není zkopírován do sdílené síťové složky. Pokud chcete povolit nasazení souborů, musíte také vybrat **nasadit** zaškrtávací políčko v dialogovém okně nástroje Configuration Manager. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md).|  
|**Další soubory k nasazení** (Windows vzdálený ladicí program)|Pokud je nastavena vlastnost adresáře nasazení, toto je seznam oddělený středníkem další soubory ke zkopírování do adresáře nasazení. Ve výchozím nastavení je prázdný, což znamená, že žádné další soubory nejsou zkopírovány do adresáře nasazení. Pokud chcete povolit nasazení souborů, musíte také vybrat **nasadit** zaškrtávací políčko v dialogovém okně nástroje Configuration Manager. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md).|  
|**Nasadit běhové knihovny pro ladění jazyka Visual C++** (Windows vzdálený ladicí program)|Pokud je nastavena vlastnost adresáře nasazení, určuje, zda mají být běhové knihovny ladicího programu Visual C++ pro aktuální platformu zkopírovány do sdílené síťové složce. Ve výchozím nastavení je Ano.|  
  
### <a name="cc-folder-general-category"></a>Složka C/C++ (obecná kategorie)  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Formát ladicích informací** ([/Z7, / Zd, Zi, /ZI](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Určuje typ ladicích informací vytvářených pro projekt.<br /><br /> Výchozí možnost (/ZI) vytvoří databázi programu (PDB) ve formátu kompatibilním upravit a pokračovat. Další informace najdete v tématu [/Z7, / Zd, / zi, /ZI (formát informací o ladění)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Složka C/C++ (optimalizační kategorie)  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Optimalizace**|Určuje, zda by měl kompilátor optimalizovat kód, který vytvoří. Optimalizace změní kód, který se spouští. Optimalizovaný kód již neodpovídá zdrojovému kódu. Ladění je proto obtížné.<br /><br /> Výchozí možnost (**zakázáno (/ 0d**) potlačí optimalizaci. Můžete vyvíjet s potlačenou optimalizací a potom zapnout, když vytváříte výrobní verzi kódu.|  
  
### <a name="linker-folder-debugging-category"></a>Složka linkeru (kategorie ladění)  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Generovat ladicí informace** ([/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Přikáže linkeru, aby zahrnul informace o ladění, který bude mít formát určený pomocí/Z7, / Zd, Zi nebo/zi.|  
|**Generovat soubor databáze programu** ([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|Zadejte název souboru PDB do tohoto pole. Je nutné vybrat ZI nebo /Zi pro formát informací o ladění.|  
|**Odstranit privátní symboly** ([/PDBSTRIPPED:filename](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|Pokud nechcete zahrnout privátní symboly do souboru PDB, zadejte název souboru PDB do tohoto pole. Tato volba vytvoří druhý soubor databáze (PDB) programu při vytváření bitové kopie programu s žádným z kompilátoru nebo linkeru, které vytvářejí soubor PDB, např. / Debug, / Z7, / zd. Nebo/zi. Tento druhý soubor PDB vynechává symboly, které není vhodné k odeslání vašich zákazníků. Další informace najdete v tématu [/PDBSTRIPPED (odstranění privátních symbolů)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Generovat soubor mapy** ([/MAP](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Přikáže linkeru, aby generoval soubor mapy během propojení. Výchozí nastavení je Ne. Další informace najdete v tématu [parametr/map (generování souboru mapování)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Název souboru mapy** ([/MAP:](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*název*)|Pokud vyberete možnost Generovat soubor mapy, můžete zadat soubor mapy v tomto poli. Další informace najdete v tématu [parametr/map (generování souboru mapování)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Mapovat exporty** ([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Obsahuje exportované funkce v souboru mapy. Výchozí nastavení je Ne. Další informace najdete v tématu [parametr/MapInfo (zahrnout informace do souboru mapování)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Laditelné sestavení** ([/assemblydebug](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Určuje nastavení pro Linker/assemblydebug – možnost. Možné hodnoty jsou následující:<br /><br /> -   **Nevysílat žádný laditelný atribut**.<br />-   **Modul runtime sledování a zakázat optimalizace (/ ASSEMBLYDEBUG)**. Toto je výchozí nastavení<br />-   **Žádný modul runtime sledování a povolit optimizations(/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<Zdědit z nadřazené nebo projektu výchozích nastavení >**.<br />-Další informace najdete v tématu [/assemblydebug (přidání atributu DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Můžete změnit tato nastavení ve složce vlastnosti konfigurace (kategorie ladění) programově pomocí rozhraní Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)   
 [Vytváření a spravování projektů Visual C++](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ ASSEMBLYDEBUG (přidání atributu DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Běžná makra pro příkazy a vlastnosti sestavení](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)



