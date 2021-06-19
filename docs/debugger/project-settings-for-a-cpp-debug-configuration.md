---
title: Nastavení projektu pro konfiguraci ladění C++
description: Nakonfigurujte ladění C a C++ na stránkách vlastností. Tento článek popisuje nastavení a informuje vás o jejich kategorii.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 34dd9b82a642c9e9ec32dde383a8c2e02ac57aa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385185"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka C++
Nastavení projektu pro konfiguraci ladění C nebo C++ můžete změnit v dialogovém okně Stránky vlastností, jak je popsáno v tématu [Postupy:](../debugger/how-to-set-debug-and-release-configurations.md)Nastavení konfigurace ladění a vydání .  Následující tabulky ukazují, kde najít nastavení související s ladicím programem v dialogovém **okně Stránky** vlastností.

> [!NOTE]
> Nastavení projektu ladění v kategorii **Vlastnosti konfigurace/Ladění** se liší pro aplikace UPW a pro komponenty, které jsou napsané v jazyce C++. Viz [Spuštění ladicí relace (VB, C#, C++ a XAML).](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

 Každé nastavení vlastnosti ladění se automaticky zapisuje a ukládá do souboru pro jednotlivé uživatele (.vcxproj.user) pro vaše řešení, když řešení uložíte.

 Určete ladicí program, který se má použít v seznamu **Ladicí** program ke spuštění, jak je popsáno v následující tabulce. Vaše volba bude mít vliv na to, které vlastnosti jsou viditelné.

## <a name="configuration-properties-folder-debugging-category"></a>Složka Vlastnosti konfigurace (kategorie ladění)

| **Nastavení** | **Popis** |
| - | - |
| **Ladicí program ke spuštění** | Určuje ladicí program, který se má spustit, s následujícími volbami:<br /><br /> -   **Místní ladicí program Windows**<br />-   **Vzdálený ladicí program Systému Windows**<br />-   **Ladicí program webového prohlížeče**<br />-   **Ladicí program webové služby** |
| **Příkaz** (místní ladicí program systému Windows) | Určuje příkaz pro spuštění programu, který ladíte v místním počítači. |
| **Vzdálený příkaz** (vzdálený ladicí program systému Windows) | Cesta k souboru .exe na vzdáleném počítači. Zadejte cestu stejně, jako byste ji zadávat na vzdáleném počítači. |
| **Argumenty příkazů** (místní ladicí program systému Windows)<br /><br /> **Argumenty vzdáleného příkazu** (vzdálený ladicí program systému Windows) | – Určuje argumenty pro dříve zadaný příkaz.<br /><br /> V tomto poli můžete použít následující operátory přesměrování:<br /><br /> < `file`<br /> Přečte stdin ze souboru .<br /><br /> > `file`<br /> Zapíše stdout do souboru .<br /><br /> >> `file`<br /> Připojí stdout k souboru.<br /><br /> 2> `file`<br /> Zapíše stderr do souboru .<br /><br /> 2.>> `file`<br /> Připojí stderr k souboru.<br /><br /> 2> &1<br /> Odešle výstup stderr (2) do stejného umístění jako stdout (1).<br /><br /> 1> &2<br /> Odešle výstup stdout (1) do stejného umístění jako stderr (2).<br /><br /> Ve většině případů se tyto operátory vztahují pouze na konzolové aplikace. |
| **Pracovní adresář** | Určuje pracovní adresář laděného programu vzhledem k adresáři projektu, ve kterém se nachází soubor EXE. Pokud toto pole necháte prázdné, pracovní adresář bude adresář projektu. Pro vzdálené ladění je adresář projektu na vzdáleném serveru. |
| **Attach** (Local Windows Debugger and Remote Windows Debugger) | Určuje, jestli se má aplikace spustit nebo připojit. Výchozí nastavení je Ne. |
| **Název vzdáleného serveru** (vzdálený ladicí program systému Windows) | Určuje název počítače (jiného než vašeho), na kterém chcete ladit aplikaci.<br /><br /> Makro RemoteMachine Build je nastaveno na hodnotu této vlastnosti. Další informace najdete v tématu [Makra pro příkazy sestavení a vlastnosti](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **Připojení** (vzdálený ladicí program systému Windows) | Umožňuje přepínat mezi standardními typy připojení a typy připojení bez ověřování pro vzdálené ladění. Do pole Název vzdáleného serveru zadejte **název vzdáleného** počítače. Mezi typy připojení patří:<br /><br /> -   **Vzdálené s ověřováním systému Windows**<br />-   **Vzdálené bez ověřování**<br /><br /> **Poznámka:** Vzdálené ladění bez ověřování může způsobit zranitelnost vzdáleného počítače vůči narušení zabezpečení. Režim ověřování systému Windows je bezpečnější.<br /><br /> Další informace najdete v tématu [Nastavení vzdáleného ladění.](../debugger/remote-debugging.md) |
| **ADRESA URL PROTOKOLU HTTP** (ladicí program webové služby a ladicí program webového prohlížeče) | Určuje adresu URL, kde se nachází projekt, který ladíte. |
| **Typ ladicího programu** | Určuje typ ladicího programu, který se má použít: **Pouze** **nativní,** Pouze spravované, Pouze **GPU,** **Smíšené,** **Automaticky** (výchozí) nebo **Skript**.<br /><br /> -   **Native Only je** pouze pro nespravovaný kód jazyka C++.<br />-   **Managed Only je** pouze pro kód, který běží v modulu Clr (Common Language Runtime) (spravovaný kód).<br />-   **Mixed** vyvolá ladicí programy pro spravovaný i nespravovaný kód.<br />-   **Automaticky** určuje typ ladicího programu na základě informací o kompilátoru a souboru EXE.<br />-   **Skript** vyvolá ladicí program pro skripty.<br />-   **Gpu je** pouze C++ AMP kódu, který běží na zařízení GPU nebo na referenčním rasterizéru DirectX. Viz [Ladění kódu GPU.](../debugger/debugging-gpu-code.md) |
| **Prostředí** (místní ladicí program systému Windows a vzdálený ladicí program systému Windows) | Určuje proměnné prostředí pro program, který ladíte. Použijte standardní syntaxi proměnných prostředí (například `PATH="%SystemRoot%\..."` ). Tyto proměnné přepíší systémové prostředí nebo se sloučí se systémovým prostředím v závislosti na **nastavení Sloučit** prostředí. Když ve sloupci nastavení kliknete levým tlačítkem, zobrazí se zpráva Upravit. Výběrem tohoto odkazu můžete upravit proměnné prostředí. |
| **Prostředí sloučení** (místní ladicí program systému Windows) | Určuje, jestli se proměnné  zadané v poli Prostředí sloučí s prostředím definovaným operačním systémem. Výchozí nastavení je Ano. |
| **Ladění SQL** (veškerý ladicí program clusteru s ale MPI) | Umožňuje ladění procedur SQL z [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] vaší aplikace. Výchozí nastavení je Ne. |
| **Typ akcelerátoru** ladění (pouze ladění GPU) | Určuje zařízení GPU, které se má použít pro ladění. Instalace ovladačů zařízení pro kompatibilní zařízení GPU přidá další možnosti. Výchozí nastavení je **GPU – Emulátor softwaru.** |
| **Výchozí chování zarážek GPU** (pouze ladění GPU) | Určuje, jestli se má pro každé vlákno v simdu vyvolat událost zarážky. Výchozím nastavením je vyvolat událost zarážky pouze jednou pro každý zdroj. |
| **Amp Default Accelerator** | Určuje výchozí akcelerátor AMP při ladění kódu GPU. Pokud chcete zjistit, jestli je problém způsoben hardwarem nebo ovladačem, a ne vaším kódem, zvolte softwarový **akcelerátor ZAŘÍZENÍ.** |
| **Adresář nasazení** (vzdálený ladicí program systému Windows) | Určuje cestu ke vzdálenému počítači, kam se před spuštěním zkopíruje výstup projektu. Cesta může být sdílená síťová složka ve vzdáleném počítači nebo cesta ke složce ve vzdáleném počítači. Výchozí nastavení je prázdné, což znamená, že výstup projektu se nekopíruje do sdílené síťové složky. Pokud chcete povolit nasazování souborů, musíte také zaškrtovat políčko Nasadit v dialogovém Správce konfigurace počítače.  Další informace najdete v tématu [Postupy: Vytváření a úpravy konfigurací.](../ide/how-to-create-and-edit-configurations.md) |
| **Další soubory k nasazení** (vzdálený ladicí program systému Windows) | Pokud je nastavena vlastnost Adresář nasazení, jedná se o seznam dalších souborů oddělených středníky, které se mají zkopírovat do adresáře nasazení. Výchozí nastavení je prázdné, což znamená, že se do adresáře nasazení nekopírují žádné další soubory. Pokud chcete povolit nasazování souborů, musíte také zaškrtovat políčko Nasadit v dialogovém Správce konfigurace počítače.  Další informace najdete v tématu [Postupy: Vytváření a úpravy konfigurací.](../ide/how-to-create-and-edit-configurations.md) |
| **Nasazení Visual C++ modulu runtime ladění** (vzdálený ladicí program systému Windows) | Pokud je nastavena vlastnost Adresář nasazení, určuje, jestli se Visual C++ knihovny modulu runtime ladění pro aktuální platformu mají zkopírovat do sdílené síťové složky. Výchozí nastavení je Ano. |

## <a name="cc-folder-general-category"></a>Složka C/C++ (obecná kategorie)

|Nastavení|Popis|
|-------------|-----------------|
|**Formát informací o ladění** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Určuje typ ladicích informací, které se vytvoří pro projekt.<br /><br /> Výchozí možnost (/ZI) vytvoří programové databáze (PDB) ve formátu kompatibilním s režimem Upravit a pokračovat. Další informace najdete v tématu [/Z7, /Zd, /Zi, /ZI (formát informací o ladění).](/cpp/build/reference/z7-zi-zi-debug-information-format)|

## <a name="cc-folder-optimization-category"></a>Složka C/C++ (kategorie optimalizace)

|Nastavení|Popis|
|-------------|-----------------|
|**Optimalizace**|Určuje, jestli má kompilátor optimalizovat kód, který vytváří. Optimalizace změní kód, který se provede. Optimalizovaný kód už neodpovídá zdrojovému kódu, což ztěžuje ladění.<br /><br /> Výchozí možnost (**Zakázáno (/0d)**) potlačí optimalizaci. Můžete vyvíjet s potlačeně optimalizací a pak ji zapnout při vytváření produkční verze kódu.|

## <a name="linker-folder-debugging-category"></a>Složka linkeru (kategorie ladění)

|Nastavení|Popis|
|-------------|-----------------|
|**Generování ladicích informací** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Říká linkeru, aby zahrnoval informace o ladění, které budou mít formát určený parametrem [/Z7, /Zd, Zi nebo /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format).|
|**Generování databázového souboru programu** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Do tohoto pole zadejte název souboru programové databáze (PDB). Jako Formát informací o ladění musíte vybrat ZI nebo /Zi.|
|**Prokládaní privátních** symbolů ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|Pokud nechcete do souboru PDB zahrnout privátní symboly, zadejte do tohoto pole název souboru PDB. Tato možnost vytvoří při sestavování image programu druhý soubor PDB s libovolnou možností kompilátoru nebo linkeru, které generují soubor PDB, například /DEBUG, /Z7, /Zd. Nebo /Zi. Tento druhý soubor PDB vyrušuje symboly, které nechcete odeslat zákazníkům. Další informace najdete v tématu [/PDBSTRIPPED (pruh privátních symbolů).](/cpp/build/reference/pdbstripped-strip-private-symbols)|
|**Generování souboru mapy** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Sděluje linkeru, aby během propojování vygeneroval soubor mapy. Výchozí nastavení je Ne. Další informace najdete v tématu [/MAP (generování souboru mapy).](/cpp/build/reference/map-generate-mapfile)|
|**Název souboru mapy** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*name*)|Pokud zvolíte Generovat soubor mapy, můžete do tohoto pole zadat soubor mapy. Další informace najdete v tématu [/MAP (generování souboru mapy).](/cpp/build/reference/map-generate-mapfile)|
|**Export mapy** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Zahrnuje exportované funkce do souboru mapy. Výchozí nastavení je Ne. Další informace najdete v tématu [/MAPINFO (zahrnutí informací do souboru mapování).](/cpp/build/reference/mapinfo-include-information-in-mapfile)|
|**Laditelné sestavení** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Určuje nastavení pro možnost Linker /ASSEMBLYDEBUG. Možné hodnoty:<br /><br /> -   **Nevysílal se žádný laditelný atribut**.<br />-   **Sledování modulu runtime a zakázání optimalizací (/ASSEMBLYDEBUG)**. Toto je výchozí nastavení:<br />-   **Žádné sledování modulu runtime a povolení optimalizací (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<inherit from parent or project defaults>**.<br />– Další informace najdete v tématu [/ASSEMBLYDEBUG (přidání atributu DebuggableAttribute).](/cpp/build/reference/assemblydebug-add-debuggableattribute)|

 Tato nastavení ve složce Vlastnosti konfigurace (kategorie ladění) můžete změnit programově pomocí rozhraní Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Další nastavení projektu

Chcete-li ladit typy projektů, jako jsou statické knihovny a knihovny DLL, Visual Studio projekt musí být schopen najít správné soubory. Pokud je zdrojový kód k dispozici, můžete do stejného řešení přidat statické knihovny a knihovny DLL jako samostatné projekty, abyste usnadnili ladění. Informace o vytváření těchto typů projektů naleznete v tématu [Creating and using a Dynamic Link Library (DLL) and](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) Creating a using a static [library](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Když máte k dispozici zdrojový kód, můžete také vytvořit nový projekt Visual Studio tak, že zvolíte File New Project From Existing Code (Soubor nového  >    >  **projektu z existujícího kódu).**

Pokud chcete ladit knihovny DLL, které jsou pro váš projekt externí, podívejte se [na ladění projektů knihoven DLL.](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal) Pokud potřebujete ladit vlastní projekt knihovny DLL, ale nemáte přístup k projektu pro volající aplikaci, podívejte se na postup ladění [z projektu knihovny DLL.](../debugger/how-to-debug-from-a-dll-project.md)

## <a name="see-also"></a>Viz také
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [Vytváření a správa projektů C++](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (Přidat atribut DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Běžná makra pro příkazy a vlastnosti sestavení](/cpp/ide/common-macros-for-build-commands-and-properties)