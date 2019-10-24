---
title: Propojit úkol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), Link task
- Link task (MSBuild (C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2241daa50a35a9714fd66b10966298279bc37fe
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747293"
---
# <a name="link-task"></a>odkaz – úloha
Zabalí nástroj Microsoft C++ linker, *Link. exe*. Nástroj Linker propojuje soubory objektů a knihoven Common Object File Format (COFF) a vytvoří spustitelný soubor ( *. exe*) nebo dynamickou knihovnu (DLL). Další informace naleznete v tématu [Možnosti linkeru](/cpp/build/reference/linker-options).

## <a name="parameters"></a>Parametry
 Následující popis popisuje parametry úkolu **propojení** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.

- **AdditionalDependencies**

  Parametr volitelného **řetězce []** .

  Určuje seznam vstupních souborů, které mají být přidány do příkazu.

  Další informace najdete v tématu [připojení vstupních souborů](/cpp/build/reference/link-input-files).

- **AdditionalLibraryDirectories**

  Parametr volitelného **řetězce []** .

  Přepíše cestu ke knihovně prostředí. Zadejte název adresáře.

  Další informace najdete v tématu [/LIBPATH (Další Libpath)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  Parametr volitelného **řetězce []** .

  Určuje atributy, které budou umístěny v sekci `dependency` souboru manifestu.

  Další informace najdete v tématu [/MANIFESTDEPENDENCY (určení závislostí manifestu)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Viz také [konfigurační soubory vydavatele](https://docs.microsoft.com/windows/desktop/SbsCs/publisher-configuration-files).

- **AdditionalOptions**

  Volitelný **řetězcový** parametr.

  Seznam možností linkeru, jak je uvedeno na příkazovém řádku. Například/\<option1 >/\<option2 >/\<option # >. Pomocí tohoto parametru lze zadat možnosti linkeru, které nejsou reprezentovány žádným jiným parametrem **Propojovací úlohy.**

  Další informace naleznete v tématu [Možnosti linkeru](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  Parametr volitelného **řetězce []** .

  Přidá do sestavení odkaz na modul.

  Další informace naleznete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **AllowIsolation**

  Volitelný **logický** parametr.

  Pokud `true`, způsobí, že operační systém provede vyhledání a načtení manifestu. Pokud `false`, označuje, že knihovny DLL jsou načteny, jako kdyby nebyl žádný manifest.

  Další informace naleznete v tématu [/ALLOWISOLATION (Lookup Manifesting)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug**

  Volitelný **logický** parametr.

  Pokud `true`, vygeneruje atribut **DebuggableAttribute** společně s trasováním informací o ladění a ZAKÁŽE optimalizace JIT. Pokud `false`, vygeneruje atribut **DebuggableAttribute** , ale zakáže sledování ladicích informací a POVOLÍ optimalizace JIT.

  Další informace najdete v tématu [/ASSEMBLYDEBUG (Add DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  Parametr volitelného **řetězce []** .

  Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru; zdrojový soubor není umístěný do výstupního souboru. Zadejte název prostředku.

  Další informace najdete v tématu [/ASSEMBLYLINKRESOURCE (odkaz na prostředek .NET Framework)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Implicitní parametr **Boolean**

  Umožňuje hlubší sledování souborů pro funkci přírůstkového propojení při zachytávání. Vždycky vrátí `true`.

- **BaseAddress**

  Volitelný **řetězcový** parametr.

  Nastaví základní adresu pro sestavení programu nebo knihovny DLL. Zadejte `{address[,size] | @filename,key}`.

  Další informace najdete v tématu [/Base (základní adresa)](/cpp/build/reference/base-base-address).

- **BuildingInIDE**

  Volitelný **logický** parametr.

  Pokud je nastaveno na true, označuje, že nástroj MSBuild je vyvolán z rozhraní IDE. V opačném případě označuje, že nástroj MSBuild je vyvolán z příkazového řádku.

  Tento parametr nemá ekvivalentní možnost linkeru.

- **CLRImageType**

  Volitelný **řetězcový** parametr.

  Nastaví typ image modulu CLR (Common Language Runtime).

  Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.

  - **Výchozí**  -  *\<none >*

  - **ForceIJWImage**  -  **/CLRIMAGETYPE: IJW**

  - **ForcePureILImage**  -  **/CLRIMAGETYPE: Pure**

  - **ForceSafeILImage**  -  **/CLRIMAGETYPE: Safe**

  Další informace najdete v tématu [/CLRIMAGETYPE (určení typu image CLR)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSupportLastError**

  Volitelný **řetězcový** parametr.

  Zachová poslední chybový kód funkcí volaných prostřednictvím mechanismu volání nespravovaného kódu.

  Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.

  - **Povoleno**  -  **/CLRSupportLastError**

  - **Disabled**  -  **/CLRSupportLastError: No**

  - **SystemDlls**  -  **/CLRSupportLastError: SYSTEMDLL**

  Další informace naleznete v tématu [/CLRSUPPORTLASTERROR (zachování kódu poslední chyby pro volání PInvoke)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).

- **CLRThreadAttribute**

  Volitelný **řetězcový** parametr.

  Explicitně určuje atribut vlákna pro vstupní bod programu CLR.

  Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.

  - **DefaultThreadingAttribute**  -  **/CLRTHREADATTRIBUTE: žádné**

  - **MTAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE: MTA**

  - **STAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE: sta**

  Další informace najdete v tématu [/CLRTHREADATTRIBUTE (nastavení atributu vlákna modulu CLR)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  Volitelný **logický** parametr.

  Určuje, zda linker bude použít **SuppressUnmanagedCodeSecurityAttribute** na volání volání volání nespravovaného kódu do nativních knihoven DLL.

  Další informace najdete v tématu [/CLRUNMANAGEDCODECHECK (přidání SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  Volitelný **řetězcový** parametr.

  Připraví obrázek pro Hot patching.

  Zadejte jednu z následujících hodnot, která odpovídá možnosti linkeru.

  - **Povoleno**  -  **/functionpadmin**

  - **X86Image**  -  **/functionpadmin: 5**

  - **X64Image**  -  **/functionpadmin: 6**

  - **ItaniumImage**  -  **/functionpadmin: 16**

  Další informace najdete v tématu [/functionpadmin (Create opravitelnou za provozu image)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  Volitelný **logický** parametr.

  Pokud `true`, označuje, že spustitelný soubor byl testován tak, aby byl kompatibilní s funkcí Zabránění spuštění dat systému Windows.

  Další informace najdete v tématu [/NXCOMPAT (kompatibilní se zabráněním spuštění dat)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLLs**

  Parametr volitelného **řetězce []** .

  Tento parametr způsobí *opožděné načtení* knihoven DLL. Zadejte název knihovny DLL pro odložené načtení.

  Další informace najdete v tématu [/DELAYLOAD (import zpožděného načtení)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  Volitelný **logický** parametr.

  Pokud `true`, částečně podepíše sestavení. Ve výchozím nastavení je hodnota `false`.

  Další informace naleznete v tématu [/delaysign (částečné podepsání sestavení)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Faktorů**

  Volitelný **řetězcový** parametr.

  Zadáním tohoto parametru sestavíte ovladač režimu jádra systému Windows NT.

  Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.

  - **NotSet**  -  *\<none >*

  - **/Driver** **ovladače**  - 

  - **Pouze**  -  **/Driver: pouze** pro

  - **Wdm**  -  **/Driver: WDM**

  Další informace najdete v tématu [/Driver (ovladač režimu jádra Windows NT)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  Parametr volitelného **řetězce []** .

  Vloží soubor prostředků do sestavení. Zadejte požadovaný název souboru prostředků. Volitelně můžete zadat logický název, který se používá k načtení prostředku, a možnost **Private** , která označuje manifest sestavení, že soubor prostředků je privátní.

  Další informace najdete v tématu [/ASSEMBLYRESOURCE (vložení spravovaného prostředku)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **EnableCOMDATFolding**

  Volitelný **logický** parametr.

  Pokud `true`, povolí identické skládání COMDAT.

  Další informace najdete v argumentu `ICF[= iterations]` [/opt (optimalizace)](/cpp/build/reference/opt-optimizations).

- **EnableUAC**

  Volitelný **logický** parametr.

  Pokud `true`, určuje, že informace nástroje řízení uživatelských účtů (UAC) budou vloženy do manifestu programu.

  Další informace naleznete v tématu [/MANIFESTUAC (vložení informací o nástroji Řízení uživatelských účtů v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  Volitelný **řetězcový** parametr.

  Určuje funkci vstupního bodu jako počáteční adresu souboru *. exe* nebo knihovny DLL. Jako hodnotu parametru zadejte název funkce.

  Další informace naleznete v tématu [/entry (symbol vstupního bodu)](/cpp/build/reference/entry-entry-point-symbol).

- **FixedBaseAddress**

  Volitelný **logický** parametr.

  Pokud `true`, vytvoří program nebo knihovnu DLL, které se dají načíst jenom na upřednostňovanou základní adresu.

  Další informace najdete v tématu [/fixed (pevná základní adresa)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  Volitelný **řetězcový** parametr.

  Instruuje linker, aby vytvořil platný soubor *. exe* nebo knihovnu DLL i v případě, že se na symbol odkazuje, ale není definován, nebo je definován násobek.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Povoleno**  -  **/Force**

  - **MultiplyDefinedSymbolOnly**  -  **/Force: více**

  - **UndefinedSymbolOnly**  -  **/Force: nevyřešené**

  Další informace najdete v tématu [/Force (vynucení výstupu souboru)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences**

  Parametr volitelného **řetězce []** .

  Tento parametr oznamuje linkeru, aby přidal zadaný symbol do tabulky symbolů.

  Další informace naleznete v tématu [/include (vynucení odkazů na symboly)](/cpp/build/reference/include-force-symbol-references).

- **FunctionOrder**

  Volitelný **řetězcový** parametr.

  Tento parametr optimalizuje program tím, že do bitové kopie umístí zadané zabalené funkce (sekvence COMDAT) do obrazu v předdefinovaném pořadí.

  Další informace najdete v tématu [/Order (vložení funkcí v pořadí)](/cpp/build/reference/order-put-functions-in-order).

- **GenerateDebugInformation**

  Volitelný **logický** parametr.

  Pokud `true`, vytvoří informace o ladění pro soubor *. exe* nebo knihovnu DLL.

  Další informace najdete v tématu [/Debug (generování informací o ladění)](/cpp/build/reference/debug-generate-debug-info).

- **GenerateManifest**

  Volitelný **logický** parametr.

  Pokud `true`, vytvoří soubor souběžného manifestu.

  Další informace naleznete v tématu [/manifest (Vytvoření manifestu souběžného sestavení)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  Volitelný **logický** parametr.

  Pokud `true`, vytvoří *soubor mapy*. Přípona názvu souboru souboru mapy je *. map*.

  Další informace najdete v tématu [/map (Generate souboru mapování)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  Volitelný **řetězcový** parametr.

  Určuje velikost fyzické paměti v haldě, která se má přidělit v čase.

  Další informace najdete v argumentu `commit` v [/Heap (nastavení velikosti haldy)](/cpp/build/reference/heap-set-heap-size). Další informace najdete také v parametru **HeapReserveSize** .

- **HeapReserveSize**

  Volitelný **řetězcový** parametr.

  Určuje celkové přidělení haldy ve virtuální paměti.

  Další informace najdete v argumentu `reserve` v [/Heap (nastavení velikosti haldy)](/cpp/build/reference/heap-set-heap-size). Viz také parametr **HeapCommitSize** v této tabulce.

- **IgnoreAllDefaultLibraries**

  Volitelný **logický** parametr.

  Pokud `true`, přikáže linkeru, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven, které vyhledává, když přeloží externí odkazy.

  Další informace najdete v tématu [/NODEFAULTLIB (ignorování knihoven)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  Volitelný **logický** parametr.

  Pokud `true`, určuje, že žádné atributy IDL ve zdrojovém kódu by neměly být zpracovány do souboru *. idl* .

  Další informace naleznete v tématu [/IGNOREIDL (Nezpracovávat atributy do MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  Volitelný **logický** parametr.

  Pokud `true`, určuje, že knihovna importu vygenerovaná touto konfigurací by neměla být importována do závislých projektů.

  Tento parametr neodpovídá Možnosti linkeru.

- **IgnoreSpecificDefaultLibraries**

  Parametr volitelného **řetězce []** .

  Určuje jeden nebo více názvů výchozích knihoven, které se mají ignorovat. Více knihoven oddělte středníkem.

  Další informace najdete v tématu [/NODEFAULTLIB (ignorování knihoven)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  Volitelný **logický** parametr.

  Pokud `true`, linker vytvoří obrázek pouze v případě, že může také vytvořit tabulku bezpečných obslužných rutin výjimek pro image.

  Další informace naleznete v tématu [/SAFESEH (Image má bezpečné obslužné rutiny výjimek)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Uživatelem zadaný název knihovny importu, který nahradí výchozí název knihovny.

  Další informace najdete v tématu [/IMPLIB (pojmenování knihovny importu)](/cpp/build/reference/implib-name-import-library).

- **KeyContainer**

  Volitelný **řetězcový** parametr.

  Kontejner, který obsahuje klíč pro podepsané sestavení.

  Další informace naleznete v tématu [/keycontainer (určení kontejneru klíčů pro podepsání sestavení)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Podívejte se také na parametr **keyfile** v této tabulce.

- **KeyFile**

  Volitelný **řetězcový** parametr.

  Určuje soubor, který obsahuje klíč pro podepsané sestavení.

  Další informace naleznete v tématu [/keyfile (určení klíče nebo páru klíčů pro podepsání sestavení)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Podívejte se také na parametr **obsahuje** .

- **LargeAddressAware**

  Volitelný **logický** parametr.

  Pokud `true`, aplikace může zpracovávat adresy větší než 2 gigabajty.

  Další informace najdete v tématu [/LARGEADDRESSAWARE (zpracování velkých adres)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  Volitelný **logický** parametr.

  Pokud `true`, aplikace vytvoří knihovnu DLL jako hlavní výstupní soubor.

  Další informace naleznete v tématu [/DLL (sestavení knihovny DLL)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  Volitelný **řetězcový** parametr.

  Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo společnosti Microsoft.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NoErrorReport**  -  **/errorreport: none**

  - **Vyzvat okamžitě**  -  **/errorreport: prompt**

  - **QueueForNextLogin**  -  **/errorreport: Queue**

  - **SendErrorReport**  -  **/errorreport: Send**

  Další informace najdete v tématu [/errorreport (hlášení chyb interního linkeru)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **LinkIncremental**

  Volitelný **logický** parametr.

  Pokud `true`, umožňuje přírůstkové propojení.

  Další informace najdete v tématu [/incremental (propojování přírůstkově)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  Volitelný **logický** parametr.

  Pokud `true`, určuje, že výstupy knihoven ze závislostí projektu jsou automaticky propojeny v.

  Tento parametr neodpovídá Možnosti linkeru.

- **LinkStatus**

  Volitelný **logický** parametr.

  Pokud `true`, určuje, že linker má zobrazit indikátor průběhu, který ukazuje, jaké procento odkazu je dokončeno.

  Další informace naleznete v argumentu `STATUS` [/LTCG (generování kódu při propojování)](/cpp/build/reference/ltcg-link-time-code-generation).

- **LinkTimeCodeGeneration**

  Volitelný **řetězcový** parametr.

  Určuje možnosti optimalizace na základě profilu.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí**  -  *\<none >*

  - **UseLinkTimeCodeGeneration**  -  **/LTCG**

  - **PGInstrument**  -  **/LTCG: PGInstrument**

  - **PGOptimization**  -  **/LTCG: PGOptimize**

  - **PGUpdate**

    \- **/LTCG: PGUpdate**

  Další informace naleznete v tématu [/LTCG (generování kódu při propojování)](/cpp/build/reference/ltcg-link-time-code-generation).

- **ManifestFile**

  Volitelný **řetězcový** parametr.

  Změní výchozí název souboru manifestu na zadaný název souboru.

  Další informace naleznete v tématu [/MANIFESTFILE (název souboru manifestu)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapExports**

  Volitelný **logický** parametr.

  Pokud `true`, instruuje linker, aby zahrnoval exportované funkce v souboru mapy.

  Další informace najdete v argumentu `EXPORTS` [/MapInfo (zahrnutí informací v souboru mapování)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **MapFileName**

  Volitelný **řetězcový** parametr.

  Změní výchozí název souboru mapy na zadaný název souboru.

- **MergedIDLBaseFileName**

  Volitelný **řetězcový** parametr.

  Určuje název souboru a příponu názvu souboru *. idl* .

  Další informace naleznete v tématu [/IDLOUT (pojmenování výstupních souborů MIDL)](/cpp/build/reference/idlout-name-midl-output-files).

- **MergeSections**

  Volitelný **řetězcový** parametr.

  Kombinuje oddíly v obrázku. Zadejte `from-section=to-section`.

  Další informace naleznete v tématu [/merge (kombinování oddílů)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile**

  Volitelný **řetězcový** parametr.

  Zadejte název souboru, který obsahuje možnosti příkazového řádku MIDL.

  Další informace naleznete v tématu [/MIDL (určení možností příkazového řádku MIDL)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **Určovat minimumRequiredVersion**

  Volitelný **řetězcový** parametr.

  Určuje minimální požadovanou verzi subsystému. Argumenty jsou desítková čísla v rozsahu 0 až 65535.

- **ModuleDefinitionFile**

  Volitelný **řetězcový** parametr.

  Určuje název [souboru definice modulu](/cpp/build/reference/module-definition-dot-def-files).

  Další informace najdete v tématu [/def (určení souboru definice modulu)](/cpp/build/reference/def-specify-module-definition-file).

- **MSDOSStubFileName**

  Volitelný **řetězcový** parametr.

  Připojí zadaný program pro zástupné procedury systému MS-DOS k programu Win32.

  Další informace najdete v tématu [/stub (název souboru zástupného kódu MS-DOS)](/cpp/build/reference/stub-ms-dos-stub-file-name).

- **Parametr-EntryPoint**

  Volitelný **logický** parametr.

  Pokud `true`, určuje knihovnu DLL pouze pro prostředky.

  Další informace najdete v tématu [/NOENTRY (bez vstupního bodu)](/cpp/build/reference/noentry-no-entry-point).

- **ObjectFiles**

  Parametr implicitního **řetězce []** .

  Určuje soubory objektů, které jsou propojeny.

- **OptimizeReferences**

  Volitelný **logický** parametr.

  Pokud `true`, eliminuje funkce nebo data, která nejsou nikdy odkazována.

  Další informace najdete v argumentu `REF` v [/opt (optimalizace)](/cpp/build/reference/opt-optimizations).

- **OutputFile**

  Volitelný **řetězcový** parametr.

  Přepíše výchozí název a umístění programu, který vytvoří linker.

  Další informace naleznete v tématu [/out (název výstupního souboru)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  Volitelný **logický** parametr.

  Pokud je povolený výstup `true` a registru, vynutí přesměrování zápisu registru **HKEY_CLASSES_ROOT** do **klíče HKEY_CURRENT_USER**.

- **PreprocessOutput**

  Volitelný parametr `ITaskItem[]`.

  Definuje pole výstupních položek preprocesoru, které mohou být spotřebovány a generovány úlohami.

- **PreventDllBinding**

  Volitelný **logický** parametr.

  Pokud `true`, označuje, že se má *svázat. exe* , že by se neměla svázat propojený obrázek.

  Další informace naleznete v tématu [/ALLOWBIND (zabránění vazbě knihoven DLL)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profilu**

  Volitelný **logický** parametr.

  Pokud `true`, vytvoří výstupní soubor, který se dá použít s profilerem **Performance Tools** .

  Další informace najdete v tématu [/Profile (Performance Tools profiler)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

  Volitelný **řetězcový** parametr.

  Určuje název souboru *. pgd* , který se použije k uložení informací o spuštěném programu.

  Další informace najdete v tématu [/PGD (určení databáze pro optimalizace na základě profilu)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  Volitelný **řetězcový** parametr.

  Určuje název pro databázi programu (PDB), kterou linker vytvoří.

  Další informace najdete v tématu [/PDB (použití databáze programu)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  Volitelný **logický** parametr.

  Pokud `true`, nástroj vygeneruje spustitelnou bitovou kopii, která se dá náhodně využít při načítání, pomocí funkce ASLR ( *Address Space Layout layout* ) systému Windows.

  Další informace najdete v tématu [/DYNAMICBASE (použití náhodnosti rozložení adresního prostoru)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RegisterOutput**

  Volitelný **logický** parametr.

  Pokud `true`, zaregistruje primární výstup tohoto sestavení.

- **Zarovnání oddílu**

  Volitelný **celočíselný** parametr

  Určuje zarovnání jednotlivých oddílů v rámci lineárního adresního prostoru programu. Hodnota parametru je jednotkový počet bajtů a je mocninou dvou.

  Další informace najdete v tématu [/align (zarovnání oddílů)](/cpp/build/reference/align-section-alignment).

- **SetChecksum –**

  Volitelný **logický** parametr.

  Pokud `true`, nastaví kontrolní součet v hlavičce souboru *. exe* .

  Další informace naleznete v tématu [/release (Nastavení kontrolního součtu)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  Volitelný **řetězcový** parametr.

  Určuje podrobnosti o sestavách průběhu operace propojení.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NotSet**  -  *\<none >*

  - **LinkVerbose**  -  **/verbose**

  - **LinkVerboseLib**  -  **/verbose: lib**

  - **LinkVerboseICF**  -  **/verbose: ICF**

  - **LinkVerboseREF**  -  **/verbose: ref**

  - **LinkVerboseSAFESEH**  -  **/verbose: SAFESEH**

  - **LinkVerboseCLR**  -  **/verbose: CLR**

  Další informace najdete v tématu [/verbose (Tisk zpráv o průběhu)](/cpp/build/reference/verbose-print-progress-messages).

- **Prostředky**

  Vyžaduje se `ITaskItem[]` parametr.

  Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.

- **SpecifySectionAttributes**

  Volitelný **řetězcový** parametr.

  Určuje atributy oddílu. Tím dojde k přepsání atributů, které byly nastaveny při kompilaci souboru *. obj* pro oddíl.

  Další informace najdete v tématu [/section (určení atributů oddílu)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize**

  Volitelný **řetězcový** parametr.

  Určuje velikost fyzické paměti v každém přidělení, pokud je přidělena další paměť.

  Další informace naleznete v argumentu `commit` [/Stack (přidělení zásobníku)](/cpp/build/reference/stack-stack-allocations).

- **StackReserveSize**

  Volitelný **řetězcový** parametr.

  Určuje celkovou velikost alokačního zásobníku ve virtuální paměti.

  Další informace naleznete v argumentu `reserve` [/Stack (přidělení zásobníku)](/cpp/build/reference/stack-stack-allocations).

- **StripPrivateSymbols**

  Volitelný **řetězcový** parametr.

  Vytvoří druhý soubor programové databáze (PDB), který vynechá symboly, které nechcete distribuovat vašim zákazníkům. Zadejte název druhého souboru PDB.

  Další informace naleznete v tématu [/PDBSTRIPPED (proložení privátních symbolů)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Provozuschopn**

  Volitelný **řetězcový** parametr.

  Určuje prostředí pro spustitelný soubor.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NotSet**  -  *\<none >*

  - **Konzola**  -  **/SUBSYSTEM: konzola**

  - **Windows**  -  **/SUBSYSTEM: Windows**

  - **Nativní**  -  **/SUBSYSTEM: Native**

  - **Aplikace rozhraní EFI**  -  **/SUBSYSTEM: EFI_APPLICATION**

  - **Ovladač spouštěcí služby EFI**  -  **/SUBSYSTEM: EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM**  -  **/SUBSYSTEM: EFI_ROM**

  - **Běhové prostředí EFI**  -  **/SUBSYSTEM: EFI_RUNTIME_DRIVER**

  - **WindowsCE**  -  **/SUBSYSTEM: WindowsCE**

  - **Posix**  -  **/SUBSYSTEM: POSIX**

  Další informace najdete v tématu [/Subsystem (určení subsystému)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  Volitelný **logický** parametr.

  Pokud `true`, sdělí linkeru, aby do finální image nezahrnula tabulku importních adres (IAT) s možností vazby.

  Další informace najdete v argumentu `NOBIND` [/Delay (nastavení importu zpožděného načtení)](/cpp/build/reference/delay-delay-load-import-settings).

- **SupportUnloadOfDelayLoadedDLL**

  Volitelný **logický** parametr.

  Pokud `true`, sdělí pomocnou funkci opožděného načtení, aby podporovala explicitní uvolnění knihovny DLL.

  Další informace najdete v argumentu `UNLOAD` [/Delay (nastavení importu zpožděného načtení)](/cpp/build/reference/delay-delay-load-import-settings).

- **SuppressStartupBanner**

  Volitelný **logický** parametr.

  Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.

  Další informace naleznete v tématu [/nologo (potlačení úvodního nápisu při spouštění) (Linker)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  Volitelný **logický** parametr.

  Pokud `true`, sdělí operačnímu systému, aby nejprve zkopíroval výstup linkeru do odkládacího souboru, a pak z něj spusťte bitovou kopii.

  Další informace naleznete v argumentu `CD` [/SWAPRUN (načtení výstupu linkeru do odkládacího souboru)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Další informace najdete také v parametru **SwapRunFromNET** .

- **SwapRunFromNET**

  Volitelný **logický** parametr.

  Pokud `true`, sdělí operačnímu systému, aby nejprve zkopíroval výstup linkeru do odkládacího souboru, a pak z něj spusťte bitovou kopii.

  Další informace naleznete v argumentu `NET` [/SWAPRUN (načtení výstupu linkeru do odkládacího souboru)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Viz také parametr **SwapRunFromCD** v této tabulce.

- **TargetMachine**

  Volitelný **řetězcový** parametr.

  Určuje cílovou platformu pro program nebo knihovnu DLL.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NotSet**  -  *\<none >*

  - **MachineARM**  -  **/Machine: ARM**

  - **MachineEBC**  -  **/Machine: EBC**

  - **MachineIA64**  -  **/Machine: ia64**

  - **MachineMIPS**  -  **/Machine: MIPS**

  - **MachineMIPS16**  -  **/Machine: MIPS16**

  - **MachineMIPSFPU**  -  **/Machine: MIPSFPU**

  - **MachineMIPSFPU16**  -  **/Machine: MIPSFPU16**

  - **MachineSH4**  -  **/Machine: sh4**

  - **MachineTHUMB**  -  **/Machine: palec**

  - **MachineX64**  -  **/Machine: x64**

  - **MachineX86**  -  **/Machine: x86**

  Další informace najdete v tématu [/Machine (určení cílové platformy)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  Volitelný **logický** parametr.

  Pokud `true`, nastaví příznak v poli IMAGE_OPTIONAL_HEADER DllCharacteristics v volitelné hlavičce obrázku programu. Pokud je tento příznak nastaven, terminálový server neprovede určité změny aplikace.

  Další informace najdete v tématu [/TSAWARE (vytvoření aplikace pracující s terminálovým serverem)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  Volitelný **řetězcový** parametr.

  Určuje adresář protokolu sledování.

- **TreatLinkerWarningAsErrors**

  Volitelný **logický** parametr.

  Pokud `true`, negeneruje žádný výstupní soubor, pokud linker vygeneruje upozornění.

  Další informace naleznete v tématu [/WX (zpracovávání upozornění linkeru jako chyby)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  Volitelný **logický** parametr.

  Pokud `true`, vytvoří obrázek pro aktuální výstupní soubor bez sestavení .NET Framework.

  Další informace naleznete v tématu [/NOASSEMBLY (Vytvoření modulu MSIL)](/cpp/build/reference/noassembly-create-a-msil-module).

- **SouborKnihovnyTypů**

  Volitelný **řetězcový** parametr.

  Určuje název souboru a příponu názvu souboru *. tlb* . Zadejte název souboru nebo cestu a název souboru.

  Další informace najdete v tématu [/TLBOUT (pojmenování souboru. tlb)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  Volitelný **celočíselný** parametr

  Určuje uživatelem zadanou hodnotu pro knihovnu typů vytvořenou linkerem. Zadejte hodnotu od 1 do 65535.

  Další informace najdete v tématu [/TLBID (určení ID prostředku pro knihovnu TypeLib)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  Volitelný **řetězcový** parametr.

  Určuje požadovanou úroveň spuštění aplikace v případě, že je spuštěna pomocí nástroje řízení uživatelských účtů.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Podle volajícího**  -  `level='asInvoker'`

  - **Nejvyšší dostupná**  -  `level='highestAvailable'`

  - **Vyžadovat správce**  -  `level='requireAdministrator'`

  Další informace naleznete v argumentu `level` [/MANIFESTUAC (vložení informací o nástroji Řízení uživatelských účtů v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UACUIAccess**

  Volitelný **logický** parametr.

  Pokud `true`, aplikace obchází úrovně ochrany uživatelského rozhraní a vstup jednotek do oken s vyšším oprávněním na ploše. v opačném případě `false`.

  Další informace naleznete v argumentu `uiAccess` [/MANIFESTUAC (vložení informací o nástroji Řízení uživatelských účtů v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UseLibraryDependencyInputs**

  Volitelný **logický** parametr.

  Pokud je `true`, místo samotného souboru knihovny se použijí vstupy pro nástroj Librarian, když jsou v knihovně výstupy na závislosti projektu.

- **Verze**

  Volitelný **řetězcový** parametr.

  Vložte číslo verze do hlavičky souboru *. exe* nebo *. dll* . Zadejte "`major[.minor]`". Argumenty `major` a `minor` jsou desítková čísla od 0 do 65535.

  Další informace najdete v tématu [/Version (informace o verzi)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
