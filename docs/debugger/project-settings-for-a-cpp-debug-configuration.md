---
title: Nastavení projektu pro konfiguraci ladění jazyka C++
description: Konfigurace ladění v jazyce C a C++ na stránkách vlastností. Tento článek popisuje nastavení a oznamuje vám jejich kategorii.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 6130b49beecb3411c275fc5d2005b7aabee262fd
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975287"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka C++
Můžete změnit nastavení projektu pro konfiguraci ladění jazyka C nebo C++ v dialogovém okně **stránky vlastností** , jak je popsáno v tématu [Postupy: nastavení ladění a konfigurací vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky ukazují, kde najít nastavení související s ladicím programem v dialogovém okně **stránky vlastností** .

> [!NOTE]
> Nastavení ladění projektu v kategorii **Vlastnosti konfigurace/ladění** se liší pro aplikace pro UWP a pro součásti, které jsou napsané v jazyce C++. Viz [Spustit ladicí relaci (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Každé nastavení vlastnosti ladění je automaticky zapisováno a uloženo do souboru pro jednotlivé uživatele (. vcxproj. User) pro vaše řešení při uložení řešení.

 Určete, který ladicí program se má použít v poli se seznamem **pro spuštění ladicího programu** , jak je popsáno v následující tabulce. Vaše volba bude mít vliv na to, které vlastnosti jsou viditelné.

## <a name="configuration-properties-folder-debugging-category"></a>Složka vlastností konfigurace (kategorie ladění)

| **Nastavení** | **Popis** |
| - | - |
| **Spuštění ladicího programu** | Určuje ladicí program, který se má spustit, s následujícími možnostmi:<br /><br /> -   **Místní ladicí program systému Windows**<br />-   **Vzdálený ladicí program systému Windows**<br />-   **Ladicí program webového prohlížeče**<br />-   **Ladicí program webové služby** |
| – **Příkaz** (místní ladicí program systému Windows) | Určuje příkaz pro spuštění programu, který ladíte v místním počítači. |
| **Vzdálený příkaz** (vzdálený ladicí program systému Windows) | Cesta k souboru. exe na vzdáleném počítači. Zadejte cestu stejně, jako byste ji zadali na vzdáleném počítači. |
| **Argumenty příkazu** (místní ladicí program systému Windows)<br /><br /> **Argumenty vzdáleného příkazu** (vzdálený ladicí program systému Windows) | – Určuje argumenty pro příkaz, který jste zadali dříve.<br /><br /> V tomto poli můžete použít následující operátory přesměrování:<br /><br /> < `file`<br /> Čte stdin ze souboru.<br /><br /> > `file`<br /> Zapíše stdout do souboru.<br /><br /> >> `file`<br /> Připojí stdout do souboru.<br /><br /> 2> `file`<br /> Zapíše stderr do souboru.<br /><br /> 2>> `file`<br /> Připojí stderr do souboru.<br /><br /> 2> &1<br /> Odešle výstup stderr (2) do stejného umístění jako stdout (1).<br /><br /> 1> &2<br /> Odešle výstup stdout (1) do stejného umístění jako stderr (2).<br /><br /> Ve většině případů se tyto operátory vztahují pouze na konzolové aplikace. |
| **Pracovní adresář** | Určuje pracovní adresář laděného programu, který je relativní vzhledem k adresáři projektu, ve kterém je umístěn váš soubor EXE. Necháte-li toto pole prázdné, bude pracovním adresářem adresář projektu. Pro vzdálené ladění je adresář projektu na vzdáleném serveru. |
| **Připojit** (místní ladicí program systému Windows a vzdálený ladicí program systému Windows) | Určuje, jestli se má aplikace spustit nebo připojit. Výchozí nastavení je ne. |
| **Název vzdáleného serveru** (vzdálený ladicí program systému Windows) | Určuje název počítače (jiný než váš), na kterém chcete aplikaci ladit.<br /><br /> Makro sestavení RemoteMachine je nastaveno na hodnotu této vlastnosti; Další informace naleznete v tématu [makra pro příkazy a vlastnosti sestavení](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **Připojení** (vzdálený ladicí program systému Windows) | Umožňuje přepínat mezi typy připojení Standard a No-Authentication pro vzdálené ladění. Do pole **název vzdáleného serveru** zadejte název vzdáleného počítače. Typy připojení zahrnují následující:<br /><br /> -   **Vzdálený s ověřováním systému Windows**<br />-   **Vzdálené bez ověřování**<br /><br /> **Poznámka:** Vzdálené ladění bez ověřování může způsobit ohrožení vzdáleného počítače vůči narušení zabezpečení. Režim ověřování systému Windows je bezpečnější.<br /><br /> Další informace najdete v tématu [Nastavení vzdáleného ladění](../debugger/remote-debugging.md). |
| **Http URL** (ladicí program webové služby a ladicí program webového prohlížeče) | Určuje adresu URL, kde se nachází projekt, který ladíte. |
| **Typ ladicího programu** | Určuje typ ladicího programu, který se má použít: **jenom nativní**, **jenom spravované**, **jenom GPU**, **smíšený**, **automaticky** (výchozí) nebo **skript**.<br /><br /> -   **Pouze nativní** je pro nespravovaný kód jazyka C++.<br />-   **Pouze spravované** je pro kód, který běží v modulu CLR (Common Language Runtime) (spravovaný kód).<br />-   **Smíšené** vyvolá ladicí programy pro spravovaný i nespravovaný kód.<br />-   **Automaticky** určuje typ ladicího programu na základě informací o kompilátoru a exe.<br />-   **Skript** vyvolá ladicí program pro skripty.<br />-   **Pouze GPU** je určena pro C++ amp kód, který běží na zařízení GPU nebo v rastrovém odkazu rozhraní DirectX. Viz [ladění kódu GPU](../debugger/debugging-gpu-code.md). |
| **Prostředí** (místní ladicí program systému Windows a vzdálený ladicí program systému Windows) | Určuje proměnné prostředí pro program, který ladíte. Použijte syntaxi proměnné prostředí Standard (například `PATH="%SystemRoot%\..."` ). Tyto proměnné přepíšou prostředí systému nebo jsou sloučeny se systémovým prostředím v závislosti na nastavení **prostředí sloučení** . Když kliknete levým na sloupec nastavení, zobrazí se zpráva "Edit...". Vyberte tento odkaz pro úpravu proměnných prostředí. |
| **Sloučit prostředí** (místní ladicí program systému Windows) | Určuje, zda proměnné, které jsou zadány v poli **prostředí** , budou sloučeny s prostředím, které je definováno operačním systémem. Výchozí nastavení je Ano. |
| **Ladění SQL** (všechny kromě ladicího programu clusteru MPI) | Povolí ladění procedur SQL z vaší [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikace. Výchozí nastavení je ne. |
| **Typ akcelerátoru ladění** (pouze ladění GPU) | Určuje zařízení GPU, které se má použít pro ladění. Při instalaci ovladačů zařízení pro kompatibilní zařízení GPU budou přidány další možnosti. Výchozím nastavením je **GPU-software emulátor**. |
| **Výchozí chování zarážky GPU** (jenom ladění GPU) | Určuje, zda má být pro každé vlákno v SIMD křivce vyvolána událost zarážky. Výchozím nastavením je vyvolat událost zarážky pouze jednou pro pokřivení. |
| **Výchozí akcelerátor amp** | Určuje výchozí akcelerátor AMP při ladění kódu GPU. Chcete-li zjistit, zda je problém způsoben hardwarem nebo ovladačem namísto kódu, vyberte možnost **pokřivit softwarový akcelerátor** . |
| **Adresář nasazení** (vzdálený ladicí program systému Windows) | Určuje cestu na vzdáleném počítači, kde bude zkopírován výstup projektu před spuštěním. Cestou může být síťová sdílená složka na vzdáleném počítači nebo může se jednat o cestu ke složce na vzdáleném počítači. Výchozí nastavení je prázdné, což znamená, že výstup projektu není zkopírován do sdílené síťové složky. Chcete-li povolit nasazení souborů, je nutné také zaškrtnout políčko **nasadit** v dialogovém okně Configuration Manager. Další informace najdete v tématu [Postup: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md). |
| **Další soubory k nasazení** (vzdálený ladicí program systému Windows) | Pokud je nastavena vlastnost adresáře nasazení, jedná se o seznam dalších souborů, které budou zkopírovány do adresáře nasazení. Výchozí nastavení je prázdné, což znamená, že do adresáře nasazení nejsou zkopírovány žádné další soubory. Chcete-li povolit nasazení souborů, je nutné také zaškrtnout políčko **nasadit** v dialogovém okně Configuration Manager. Další informace najdete v tématu [Postup: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md). |
| **Nasazení ladicích knihoven modulu Runtime Visual C++** (vzdálený ladicí program systému Windows) | Pokud je nastavena vlastnost adresáře nasazení, určuje, zda má být Visual C++ běhové knihovny pro ladění pro aktuální platformu zkopírovány do sdílené síťové složky. Výchozí nastavení je Ano. |

## <a name="cc-folder-general-category"></a>Složka C/C++ (obecná kategorie)

|Nastavení|Popis|
|-------------|-----------------|
|**Formát ladicích informací** ([/Z7,/zd, Zi,/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format))|Určuje typ ladicích informací, které mají být vytvořeny pro projekt.<br /><br /> Výchozí možnost (/ZI) vytvoří databázi programu (PDB) ve formátu kompatibilním s úpravou a pokračováním. Další informace naleznete v tématu [/Z7,/zd,/Zi,/Zi (formát ladicích informací)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>Složka C/C++ (kategorie optimalizace)

|Nastavení|Popis|
|-------------|-----------------|
|**Optimalizace**|Určuje, zda má kompilátor optimalizovat kód, který vytváří. Optimalizace změní kód, který je spuštěn. Optimalizovaný kód již neodpovídá zdrojovému kódu, který usnadňuje ladění.<br /><br /> Výchozí možnost (**disabled (/0d)**) potlačí optimalizaci. Můžete vyvíjet s potlačením optimalizace a pak je zapnout při vytváření produkční verze kódu.|

## <a name="linker-folder-debugging-category"></a>Složka Linkeru (kategorie ladění)

|Nastavení|Popis|
|-------------|-----------------|
|**Generovat ladicí informace** ([/Debug](/cpp/build/reference/debug-generate-debug-info))|Instruuje linkeru, aby zahrnoval informace o ladění, které budou mít formát určený parametrem [/Z7,/zd, Zi nebo/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format).|
|**Generovat soubor databáze programu** ([/PDB: název](/cpp/build/reference/pdb-use-program-database))|Do tohoto pole zadejte název souboru programu databáze (PDB). Pro formát informací o ladění je nutné vybrat možnost ZI nebo/ZI.|
|**Odstranit privátní symboly** ([/PDBSTRIPPED: filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|Pokud nechcete zahrnout soukromé symboly do souboru PDB, zadejte do tohoto pole název souboru PDB. Tato možnost vytvoří druhý soubor PDB při sestavování image programu pomocí kterékoli z možností kompilátoru nebo linkeru, které generují soubor PDB, jako je například/DEBUG,/Z7,/Zd. Nebo/ZI. Tento druhý soubor PDB vynechá symboly, které byste nechtěli dodávat svým zákazníkům. Další informace naleznete v tématu [/PDBSTRIPPED (proložení privátních symbolů)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Generovat soubor mapy** ([/map](/cpp/build/reference/map-generate-mapfile))|Instruuje linkeru, aby během propojování vygeneroval soubor mapy. Výchozí nastavení je ne. Další informace najdete v tématu [/map (Generate souboru mapování)](/cpp/build/reference/map-generate-mapfile).|
|**Název souboru mapy** ([/map:](/cpp/build/reference/map-generate-mapfile)*název*)|Pokud zvolíte možnost generovat soubor mapy, můžete v tomto poli zadat soubor mapy. Další informace najdete v tématu [/map (Generate souboru mapování)](/cpp/build/reference/map-generate-mapfile).|
|**Exporty map** ([/MapInfo: EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Obsahuje exportované funkce v souboru mapy. Výchozí nastavení je ne. Další informace najdete v tématu [/MapInfo (zahrnutí informací v souboru mapování)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Laditelné sestavení** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Určuje nastavení pro možnost linker/ASSEMBLYDEBUG. Možné hodnoty:<br /><br /> -   **Neemitující se žádný laděný atribut**.<br />-   **Sledování za běhu a zakázání optimalizace (/ASSEMBLYDEBUG)**. Toto je výchozí nastavení.<br />-   **Nesledovat modul runtime a povolit optimalizace (/ASSEMBLYDEBUG: Disable)**<br />-   **\<inherit from parent or project defaults>**.<br />– Další informace najdete v tématu [/ASSEMBLYDEBUG (Add DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Tato nastavení můžete změnit ve složce vlastnosti konfigurace (kategorie ladění) programově pomocí rozhraní Microsoft. VisualStudio. VCProjectEngine. VCDebugSettings. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Další nastavení projektu

Chcete-li ladit typy projektů, jako jsou statické knihovny a knihovny DLL, váš projekt aplikace Visual Studio musí být schopný najít správné soubory. Když je zdrojový kód k dispozici, můžete přidat statické knihovny a knihovny DLL jako samostatné projekty do stejného řešení, aby bylo ladění snazší. Informace o vytváření těchto typů projektů naleznete v tématu [Vytvoření a použití dynamické knihovny (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) a [vytvoření pomocí statické knihovny](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Pokud je k dispozici zdrojový kód, můžete také vytvořit nový projekt sady Visual Studio tak, že  >    >  **v existujícím kódu** kliknete na soubor nový projekt.

Chcete-li ladit knihovny DLL, které jsou pro váš projekt externí, přečtěte si téma [ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Pokud potřebujete ladit vlastní projekt knihovny DLL, ale nemáte přístup k projektu volající aplikace, přečtěte si téma [jak ladit z projektu knihovny DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Viz také
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [Vytváření a správa projektů v jazyce C++](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (Přidat atribut DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Běžná makra pro příkazy a vlastnosti sestavení](/cpp/ide/common-macros-for-build-commands-and-properties)