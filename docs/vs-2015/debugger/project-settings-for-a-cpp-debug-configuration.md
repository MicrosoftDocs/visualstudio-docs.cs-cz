---
title: Nastavení projektu pro konfiguraci ladění C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ca9ff0678ba2c7abafa0d988efa09437ccd27dca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687561"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit nastavení projektu pro konfiguraci ladění C nebo Visual C++ v dialogovém okně **stránky vlastností** , jak je popsáno v tématu [Postupy: nastavení ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky ukazují, kde najít nastavení související s ladicím programem v dialogovém okně **stránky vlastností** .  
  
> [!WARNING]
> Nastavení projektu ladění v kategorii **Vlastnosti konfigurace/ladění** pro aplikace pro Windows Store a součásti, které jsou napsané v jazyce C++, se liší. Viz [Spustit ladicí relaci (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) ve vývojářském centru pro Windows.  
  
 Určete, který ladicí program se má použít v poli se seznamem **pro spuštění ladicího programu** . Vaše volba bude mít vliv na to, které vlastnosti jsou viditelné.  
  
 Každé nastavení vlastnosti ladění je automaticky zapisováno a uloženo do souboru pro jednotlivé uživatele (. vcxproj. User) pro vaše řešení, kdykoli uložíte řešení.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Složka vlastností konfigurace (kategorie ladění)  
  
|**Nastavení**|**Popis**|  
|-----------------|---------------------|  
|**Spuštění ladicího programu**|Určuje ladicí program, který se má spustit, s následujícími možnostmi:<br /><br /> -   **Místní ladicí program systému Windows**<br />-   **Vzdálený ladicí program systému Windows**<br />-   **Ladicí program webového prohlížeče**<br />-   **Ladicí program webové služby**|  
|– **Příkaz** (místní ladicí program systému Windows)|Určuje příkaz pro spuštění programu, který ladíte v místním počítači.|  
|**Vzdálený příkaz** (vzdálený ladicí program systému Windows)|Cesta k souboru. exe na vzdáleném počítači. Zadejte cestu stejně, jako byste ji zadali na vzdáleném počítači.|  
|**Argumenty příkazu** (místní ladicí program systému Windows a vzdálený ladicí program systému Windows)|– Určuje argumenty pro příkaz, který jste zadali dříve.<br /><br /> V tomto poli můžete použít následující operátory přesměrování:<br /><br /> < `file`<br /> Čte stdin ze souboru.<br /><br /> > `file`<br /> Zapíše stdout do souboru.<br /><br /> >> `file`<br /> Připojí stdout do souboru.<br /><br /> 2> `file`<br /> Zapíše stderr do souboru.<br /><br /> 2>> `file`<br /> Připojí stderr do souboru.<br /><br /> 2> &1<br /> Odešle výstup stderr (2) do stejného umístění jako stdout (1).<br /><br /> 1> &2<br /> Odešle výstup stdout (1) do stejného umístění jako stderr (2).<br /><br /> Ve většině případů se tyto operátory vztahují pouze na konzolové aplikace.|  
|**Pracovní adresář**|Určuje pracovní adresář laděného programu, který je relativní vzhledem k adresáři projektu, ve kterém je umístěn váš soubor EXE. Necháte-li toto pole prázdné, bude pracovním adresářem adresář projektu. Pro vzdálené ladění se adresář projektu bude na vzdáleném serveru.|  
|**Připojit** (místní ladicí program systému Windows a vzdálený ladicí program systému Windows)|Určuje, jestli se má aplikace spustit nebo připojit. Výchozí nastavení je ne.|  
|**Název vzdáleného serveru** (vzdálený ladicí program systému Windows)|Určuje název počítače (jiný než váš), na kterém chcete aplikaci ladit.<br /><br /> Makro sestavení RemoteMachine je nastaveno na hodnotu této vlastnosti; Další informace naleznete v tématu [makra pro příkazy a vlastnosti sestavení](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Připojení** (vzdálený ladicí program systému Windows)|Umožňuje přepínat mezi typy připojení Standard a No-Authentication pro vzdálené ladění. Do pole **název vzdáleného serveru** zadejte název vzdáleného počítače. Typy připojení zahrnují následující:<br /><br /> -   **Vzdálený s ověřováním systému Windows**<br />-   **Vzdálený bez ověřování (jenom nativní)**<br /><br /> **Poznámka:** Vzdálené ladění bez ověřování může způsobit ohrožení vzdáleného počítače vůči narušení zabezpečení. Režim ověřování systému Windows je bezpečnější.<br /><br /> Další informace najdete v tématu [Nastavení vzdáleného ladění](../debugger/remote-debugging.md).|  
|**Http URL** (ladicí program webové služby a ladicí program webového prohlížeče)|Určuje adresu URL, kde se nachází projekt, který ladíte.|  
|**Typ ladicího programu**|Určuje typ ladicího programu, který se má použít: **jenom nativní**, **jenom spravované**, **jenom GPU**, **smíšený**, **automaticky** (výchozí) nebo **skript**.<br /><br /> -   **Pouze nativní** je pro nespravovaný kód jazyka C++.<br />-   **Pouze spravované** je pro kód, který běží v modulu CLR (Common Language Runtime) (spravovaný kód).<br />-   **Smíšené** vyvolá ladicí programy pro spravovaný i nespravovaný kód.<br />-   **Automaticky** určuje typ ladicího programu na základě informací o kompilátoru a exe.<br />-   **Skript** vyvolá ladicí program pro skripty.<br />-   **Pouze GPU** je určena pro C++ amp kód, který běží na zařízení GPU nebo v rastrovém odkazu rozhraní DirectX. Viz [ladění kódu GPU](../debugger/debugging-gpu-code.md).|  
|**Prostředí** (místní ladicí program systému Windows)|Určuje proměnné prostředí pro program, který ladíte. Použijte syntaxi proměnné prostředí Standard (například `PATH="%SystemRoot%\..."` ). Tyto proměnné přepíšou prostředí systému nebo jsou sloučeny se systémovým prostředím v závislosti na nastavení **prostředí sloučení** . Když kliknete na sloupec nastavení, upravíte. uvedeny. Kliknutím na tento odkaz upravíte proměnné prostředí.|  
|**Sloučit prostředí** (místní ladicí program systému Windows)|Určuje, zda proměnné, které jsou zadány v poli **prostředí** , budou sloučeny s prostředím, které je definováno operačním systémem. Výchozí nastavení je Ano.|  
|**Ladění SQL** (všechny kromě ladicího programu clusteru MPI)|Povolí ladění procedur SQL z vaší [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] aplikace. Výchozí nastavení je ne.|  
|**Typ akcelerátoru ladění** (pouze ladění GPU)|Určuje zařízení GPU, které se má použít pro ladění. Při instalaci ovladačů zařízení pro kompatibilní zařízení GPU budou přidány další možnosti. Výchozí nastavení je "GPU-software emulátor".|  
|**Výchozí chování zarážky GPU** (jenom ladění GPU)|Určuje, zda má být pro každé vlákno v SIMD křivce vyvolána událost zarážky. Výchozím nastavením je vyvolat událost zarážky pouze jednou pro pokřivení.|  
|**Výchozí akcelerátor amp** (pouze ladění GPU)|Určuje výchozí akcelerátor AMP při ladění kódu GPU. Chcete-li zjistit, zda je problém způsoben hardwarem nebo ovladačem namísto kódu, vyberte možnost **pokřivit softwarový akcelerátor** .|  
|**Adresář nasazení** (vzdálený ladicí program systému Windows)|Určuje cestu na vzdáleném počítači, kde bude zkopírován výstup projektu před spuštěním. Cestou může být síťová sdílená složka na vzdáleném počítači nebo může se jednat o cestu ke složce na vzdáleném počítači. Výchozí nastavení je prázdné, což znamená, že výstup projektu není zkopírován do sdílené síťové složky. Chcete-li povolit nasazení souborů, je nutné také zaškrtnout políčko **nasadit** v dialogovém okně Configuration Manager. Další informace najdete v tématu [Postup: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md).|  
|**Další soubory k nasazení** (vzdálený ladicí program systému Windows)|Pokud je nastavená vlastnost adresáře nasazení, jedná se o středníkem oddělený seznam dalších souborů, které se zkopírují do adresáře nasazení. Výchozí nastavení je prázdné, což znamená, že do adresáře nasazení nejsou zkopírovány žádné další soubory. Chcete-li povolit nasazení souborů, je nutné také zaškrtnout políčko **nasadit** v dialogovém okně Configuration Manager. Další informace najdete v tématu [Postup: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md).|  
|**Nasazení ladicích knihoven modulu Runtime Visual C++** (vzdálený ladicí program systému Windows)|Pokud je nastavena vlastnost adresáře nasazení, určuje, zda má být Visual C++ běhové knihovny pro ladění pro aktuální platformu zkopírovány do sdílené síťové složky. Výchozí nastavení je Ano.|  
  
### <a name="cc-folder-general-category"></a>Složka C/C++ (obecná kategorie)  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Formát ladicích informací** ([/Z7,/zd, Zi,/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Určuje typ ladicích informací, které mají být vytvořeny pro projekt.<br /><br /> Výchozí možnost (/ZI) vytvoří databázi programu (PDB) ve formátu kompatibilním s úpravou a pokračováním. Další informace naleznete v tématu [/Z7,/zd,/Zi,/Zi (formát ladicích informací)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Složka C/C++ (kategorie optimalizace)  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Optimalizace**|Určuje, zda má kompilátor optimalizovat kód, který vytváří. Optimalizace změní kód, který je spuštěn. Optimalizovaný kód již neodpovídá zdrojovému kódu. Proto je ladění obtížné.<br /><br /> Výchozí možnost (**disabled (/0d**) potlačí optimalizaci. Můžete vyvíjet s potlačením optimalizace a pak je zapnout při vytváření produkční verze kódu.|  
  
### <a name="linker-folder-debugging-category"></a>Složka Linkeru (kategorie ladění)  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Generovat ladicí informace** ([/Debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Instruuje linkeru, aby zahrnoval informace o ladění, které budou mít formát zadaný pomocí/Z7,/zd, Zi nebo/ZI..|  
|**Generovat soubor databáze programu** ([/PDB: název](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|Do tohoto pole zadejte název souboru PDB. Pro formát informací o ladění je nutné vybrat možnost ZI nebo/ZI.|  
|**Odstranit privátní symboly** ([/PDBSTRIPPED: filename](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|Pokud nechcete zahrnout soukromé symboly do souboru PDB, zadejte do tohoto pole název souboru PDB. Tato možnost vytvoří druhý soubor programu databáze (PDB) při sestavování image programu pomocí kterékoli z možností kompilátoru nebo linkeru, které generují soubor PDB, jako je například/DEBUG,/Z7,/Zd. Nebo/ZI. Tento druhý soubor PDB vynechá symboly, které byste nechtěli dodávat svým zákazníkům. Další informace naleznete v tématu [/PDBSTRIPPED (proložení privátních symbolů)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Generovat soubor mapy** ([/map](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Instruuje linkeru, aby během propojování vygeneroval soubor mapy. Výchozí nastavení je ne. Další informace najdete v tématu [/map (Generate souboru mapování)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Název souboru mapy** ([/map:](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*název*)|Pokud zvolíte možnost generovat soubor mapy, můžete v tomto poli zadat soubor mapy. Další informace najdete v tématu [/map (Generate souboru mapování)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Exporty map** ([/MapInfo: EXPORTS](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Obsahuje exportované funkce v souboru mapy. Výchozí nastavení je ne. Další informace najdete v tématu [/MapInfo (zahrnutí informací v souboru mapování)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Laditelné sestavení** ([/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Určuje nastavení pro možnost linker/ASSEMBLYDEBUG. Možné hodnoty jsou následující:<br /><br /> -   **Neemitující se žádný laděný atribut**.<br />-   **Sledování za běhu a zakázání optimalizace (/ASSEMBLYDEBUG)**. Toto je výchozí nastavení.<br />-   **Nesledovat modul runtime a povolit optimalizace (/ASSEMBLYDEBUG: Disable)**<br />-   **\<inherit from parent or project defaults>**.<br />– Další informace najdete v tématu [/ASSEMBLYDEBUG (Add DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Tato nastavení můžete změnit ve složce vlastnosti konfigurace (kategorie ladění) programově pomocí rozhraní Microsoft. VisualStudio. VCProjectEngine. VCDebugSettings. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)   
 [Vytváření a Správa Visual C++ch projektů](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (přidat DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Společná makra pro příkazy a vlastnosti sestavení](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)
