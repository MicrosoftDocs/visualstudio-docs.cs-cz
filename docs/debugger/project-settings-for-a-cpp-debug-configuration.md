---
title: Nastavení projektu pro konfiguraci ladění jazyka C++
ms.custom: seodec18
ms.date: 11/26/2018
ms.topic: reference
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
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: bca39b97f6363d8b8fefcfd691b69baf85c32170
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450372"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka C++
Můžete změnit nastavení projektu pro konfiguraci jazyka C nebo C++ ladění v dialogovém okně **stránky vlastností** , jak je popsáno v tématu [Postupy: nastavení ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky popisují, kde najít nastavení související s ladicí program v **stránky vlastností** dialogové okno.

> [!NOTE]
> Nastavení ladění projektu v **konfigurační vlastnosti/ladění** kategorie se liší pro aplikace pro UPW a pro součásti, které jsou napsané v jazyce C++. Zobrazit [spustíte relaci ladění (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Nastavení jednotlivých vlastností ladění automaticky zapíše a uloží do souboru "za user" (. vcxproj.user) pro vaše řešení při uložení vašeho řešení.

 Určete, který ladicí program používat v **ladicí program ke spuštění** pole se seznamem, jak je popsáno v následující tabulce. Vaše volba bude mít vliv na vlastnosti, které jsou viditelné.

## <a name="configuration-properties-folder-debugging-category"></a>Složka s vlastnostmi konfigurace (kategorie ladění)

| **Nastavení** | **Popis** |
| - | - |
| **Ladicí program ke spuštění** | Určuje ladicí program ke spuštění, s následujícími možnostmi:<br /><br /> -   **Ladicí program místní Windows**<br />-   **Windows vzdáleného ladicího programu**<br />-   **Ladicí program webového prohlížeče**<br />-   **Ladicí program webové služby** |
| **Příkaz** (ladicí program místní Windows) | Určuje příkaz pro spuštění programu, který právě ladíte v místním počítači. |
| **Vzdálený příkaz** (Windows vzdálený ladicí program) | Cesta k .exe ve vzdáleném počítači. Zadejte cestu stejně, jako byste ji zadávali ve vzdáleném počítači. |
| **Argumenty příkazového** (ladicí program místní Windows)<br /><br /> **Argumenty vzdáleného příkazu** (Windows vzdálený ladicí program) | -Určuje argumenty pro příkaz zadaný dříve.<br /><br /> V tomto poli můžete použít následující operátory přesměrování:<br /><br /> < `file`<br /> Čte stdin ze souboru.<br /><br /> > `file`<br /> Zapíše hodnotu stdout do souboru.<br /><br /> >> `file`<br /> Připojí stdout do souboru.<br /><br /> 2> `file`<br /> Zapíše hodnotu stderr do souboru.<br /><br /> 2>> `file`<br /> Připojí stderr do souboru.<br /><br /> 2> &1<br /> Odešle výstup stderr (2) do stejného umístění jako stdout (1).<br /><br /> 1> &2<br /> Odešle stdout (1) výstup do stejného umístění jako stderr (2).<br /><br /> Ve většině případů jsou tyto operátory použitelné pouze pro konzolové aplikace. |
| **Pracovní adresář** | Určuje pracovní adresář laděného programu, relativně vzhledem k adresáři projektu, kde je umístěn váš soubor EXE. Pokud toto pole ponecháte prázdné, pracovní adresář je adresář projektu. Pro vzdálené ladění projektu adresář je na vzdáleném serveru. |
| **Připojit** (ladicí program místní Windows a Windows vzdálený ladicí program) | Určuje, zda chcete spustit nebo připojit k aplikaci. Výchozí nastavení je Ne. |
| **Název vzdáleného severu** (Windows vzdálený ladicí program) | Určuje název počítače (kromě vašeho), na kterém chcete ladit aplikace.<br /><br /> Makro sestavení RemoteMachine je nastavena na hodnotu této vlastnosti; Další informace najdete v tématu [sestavení makra pro příkazy a vlastnosti](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **Připojení** (Windows vzdálený ladicí program) | Umožňuje přepínat mezi typy standard a bez ověřování připojení pro vzdálené ladění. Zadejte název vzdáleného počítače v **název vzdáleného serveru** pole. Typy připojení patří:<br /><br /> -   **Vzdálený s ověřováním Windows**<br />-   **Vzdálený bez ověřování**<br /><br /> **Poznámka:** vzdálené ladění bez ověřování může zanechat vzdálený počítač zranitelné vůči narušení zabezpečení. Režim ověřování Windows je bezpečnější.<br /><br /> Další informace najdete v tématu [vzdálené ladění nastavení](../debugger/remote-debugging.md). |
| **Adresa URL operace HTTP** (Web ladicí program služby a ladicí program webového prohlížeče) | Určuje adresu URL, kde je umístěn projekt, který ladíte. |
| **Typ ladicího programu** | Určuje typ ladicího programu, který se má použít: **pouze nativní**, **pouze spravované**, **pouze GPU**, **smíšený**, **automaticky**(výchozí), nebo **skript**.<br /><br /> -   **Pouze nativní** je pro nespravovaný kód jazyka C++.<br />-   **Režim pouze spravovaný** je pro kód, který běží v rámci common language runtime (spravovaný kód).<br />-   **Smíšené** vyvolá ladicí programy pro spravovaný i nespravovaný kód.<br />-   **Automatické** Určuje typ ladicího programu na základě kompilátoru a informací souboru EXE.<br />-   **Skript** vyvolá ladicí program skriptů.<br />-   **Pouze GPU** je pro kód C++ AMP, který běží na GPU zařízení nebo v rasterizéru referenčního rozhraní DirectX. Zobrazit [kódu ladění GPU](../debugger/debugging-gpu-code.md). |
| **Prostředí** (ladicí program místní Windows a Windows vzdálený ladicí program) | Určuje proměnné prostředí pro program, který ladíte. Použijte syntaxi proměnných standardního prostředí (například `PATH="%SystemRoot%\..."`). Tyto proměnné přepisují prostředí systému nebo jsou sloučeny s prostředím systému v závislosti na tom **sloučit prostředí** nastavení. Když levým tlačítkem myši ve sloupci nastavení "Upravit..." se zobrazí. Vyberte tento odkaz upravíte proměnné prostředí. |
| **Sloučit prostředí** (ladicí program místní Windows) | Určuje, zda proměnné, které jsou určené v **prostředí** pole se sloučí s prostředím, který je definován v operačním systému. Výchozí nastavení je Ano. |
| **Ladění SQL** (všechny kromě ladicího programu clusteru MPI) | Umožňuje ladění procedur SQL z vašich [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikace. Výchozí nastavení je Ne. |
| **Typ akcelerátoru ladění** (pouze ladění GPU) | Určuje zařízení GPU používané pro ladění. Instalace ovladačů pro kompatibilní zařízení GPU přidá další možnosti. Ve výchozím nastavení **GPU - softwarový emulátor**. |
| **Výchozí chování zarážky GPU** (pouze ladění GPU) | Určuje, zda by měla být zvýšena událost zarážky pro každý podproces v křivce SIMD. Ve výchozím nastavení je pro vyvolání události zarážky pouze jednou na každý svazek. |
| **Výchozí akcelerátor amp** | Určuje výchozí akcelerátor AMP při ladění kódu GPU. Zvolte **softwarový akcelerátor WARP** pro zjištění, zda problém způsoben hardwarem nebo ovladačem namísto kódu. |
| **Adresář nasazení** (Windows vzdálený ladicí program) | Určuje cestu ve vzdáleném počítači, kde bude výstup projektu zkopírovaný před spuštěním. Cesta může být síťová sdílená položka vzdáleného počítače, nebo může být cesta ke složce ve vzdáleném počítači. Ve výchozím nastavení je prázdný, což znamená, že výstup projektu není zkopírován do sdílené síťové složky. Pokud chcete povolit nasazení souborů, musíte také vybrat **nasadit** zaškrtávací políčko v dialogovém okně nástroje Configuration Manager. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md). |
| **Další soubory k nasazení** (Windows vzdálený ladicí program) | Pokud je nastavena vlastnost adresáře nasazení, toto je seznam oddělený středníkem další soubory ke zkopírování do adresáře nasazení. Ve výchozím nastavení je prázdný, což znamená, že žádné další soubory nejsou zkopírovány do adresáře nasazení. Pokud chcete povolit nasazení souborů, musíte také vybrat **nasadit** zaškrtávací políčko v dialogovém okně nástroje Configuration Manager. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md). |
| **Nasadit běhové knihovny pro ladění jazyka Visual C++** (Windows vzdálený ladicí program) | Pokud je nastavena vlastnost adresáře nasazení, určuje, zda mají být běhové knihovny ladicího programu Visual C++ pro aktuální platformu zkopírovány do sdílené síťové složce. Ve výchozím nastavení je Ano. |

## <a name="cc-folder-general-category"></a>Složka C/C++ (obecná kategorie)

|Nastavení|Popis|
|-------------|-----------------|
|**Formát ladicích informací** ([/Z7, / Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Určuje typ ladicích informací vytvářených pro projekt.<br /><br /> Výchozí možnost (/ZI) vytvoří databázi programu (PDB) ve formátu kompatibilním upravit a pokračovat. Další informace najdete v tématu [/Z7, / Zd, / zi, /ZI (formát ladicích informací)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>Složka C/C++ (optimalizační kategorie)

|Nastavení|Popis|
|-------------|-----------------|
|**Optimalizace**|Určuje, zda by měl kompilátor optimalizovat kód, který vytvoří. Optimalizace změní kód, který se spouští. Optimalizovaný kód již neodpovídá zdrojovému kódu, takže ladění obtížnější.<br /><br /> Výchozí možnost (**zakázáno (/ 0d)** ) potlačí optimalizaci. Můžete vyvíjet s potlačenou optimalizací a potom zapnout, když vytváříte výrobní verzi kódu.|

## <a name="linker-folder-debugging-category"></a>Složka linkeru (kategorie ladění)

|Nastavení|Popis|
|-------------|-----------------|
|**Generovat ladicí informace** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Přikáže linkeru, aby zahrnul informace o ladění, který bude mít formát určený pomocí [/Z7, / Zd, Zi nebo /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format).|
|**Generovat soubor databáze programu** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Zadejte název souboru databáze (PDB) programu v tomto poli. Je nutné vybrat ZI nebo /Zi pro formát informací o ladění.|
|**Odstranit privátní symboly** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|Pokud nechcete zahrnout privátní symboly do souboru PDB, zadejte název souboru PDB do tohoto pole. Tato volba vytvoří druhý soubor PDB při vytváření bitové kopie programu s žádným z kompilátoru nebo linkeru, které vytvářejí soubor PDB, např. / Debug, / Z7, / zd. Nebo/zi. Tento druhý soubor PDB vynechává symboly, které není vhodné k odeslání vašich zákazníků. Další informace najdete v tématu [/PDBSTRIPPED (odstranění privátních symbolů)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Generovat soubor mapy** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Přikáže linkeru, aby generoval soubor mapy během propojení. Výchozí nastavení je Ne. Další informace najdete v tématu [parametr/map (generování souboru mapování)](/cpp/build/reference/map-generate-mapfile).|
|**Název souboru mapy** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*název*)|Pokud vyberete možnost Generovat soubor mapy, můžete zadat soubor mapy v tomto poli. Další informace najdete v tématu [parametr/map (generování souboru mapování)](/cpp/build/reference/map-generate-mapfile).|
|**Mapovat exporty** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Obsahuje exportované funkce v souboru mapy. Výchozí nastavení je Ne. Další informace najdete v tématu [parametr/MapInfo (zahrnout informace do souboru mapování)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Laditelné sestavení** ([/assemblydebug](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Určuje nastavení pro Linker/assemblydebug – možnost. Možné hodnoty jsou:<br /><br /> -   **Nevysílat žádný laditelný atribut**.<br />-   **Modul runtime sledování a zakázat optimalizace (/ ASSEMBLYDEBUG)** . Toto je výchozí nastavení<br />-   **Žádný modul runtime sledování a povolit optimizations(/ASSEMBLYDEBUG:DISABLE)** .<br />-    **\<Zdědit z nadřazené nebo projektu výchozích nastavení >** .<br />-Další informace najdete v tématu [/assemblydebug (přidání atributu DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Můžete změnit tato nastavení ve složce vlastnosti konfigurace (kategorie ladění) programově pomocí rozhraní Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Další informace najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Další nastavení projektu

Chcete-li ladit typy projektů, jako je například statických knihoven a knihovny DLL, musí být schopen najít správné soubory projektu sady Visual Studio. Pokud zdrojový kód je k dispozici, můžete přidat statických knihoven a knihovny DLL jako samostatné projekty do stejného řešení, k usnadnění ladění. Informace o vytvoření těchto typů projektu naleznete v tématu [vytváření a použití knihovny pro dynamické propojení (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) a [vytváření použití statické knihovny](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Se zdrojovým kódem k dispozici, můžete také vytvořit nový projekt sady Visual Studio výběrem **souboru** > **nový** > **projekt z existujícího kódu**.

Ladění knihoven DLL, které jsou externí vzhledem k projektu, naleznete v tématu [projektů knihovny DLL ladění](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Pokud budete muset svůj projekt knihovny DLL, ladění, ale není mají přístup k projektu pro volající aplikace naleznete v tématu [ladění z projektu knihovny DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Viz také:
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [Vytváření a Správa C++ projektů](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (přidání atributu DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Běžná makra pro příkazy a vlastnosti sestavení](/cpp/ide/common-macros-for-build-commands-and-properties)