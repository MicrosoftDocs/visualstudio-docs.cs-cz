---
title: Propojení úkolů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cd79db9b5bfc2e68dea2ff711b2da6ce55c9bc0
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220118"
---
# <a name="link-task"></a>odkaz – úloha
Zabalí nástroj linker Visual C++ *link.exe*. Nástroj linker propojení objektových souborů Common Object File Format (COFF) a knihovny, které chcete vytvořit spustitelný soubor (*.exe*) soubor nebo dynamická knihovna (DLL). Další informace najdete v tématu [možnosti Linkeru](/cpp/build/reference/linker-options).  
  
## <a name="parameters"></a>Parametry  
 Následující text popisuje parametry **odkaz** úloh. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
-   **AdditionalDependencies**  
  
     Volitelné **String []** parametru.  
  
     Určuje seznam vstupních souborů přidejte do příkazu.  
  
     Další informace najdete v tématu [vstupní soubory LINK](/cpp/build/reference/link-input-files).  
  
-   **AdditionalLibraryDirectories**  
  
     Volitelné **String []** parametru.  
  
     Přepíše cestu ke knihovně prostředí. Zadejte název adresáře.  
  
     Další informace najdete v tématu [/Libpath (další proměnná Libpath)](/cpp/build/reference/libpath-additional-libpath).  
  
-   **AdditionalManifestDependencies**  
  
     Volitelné **String []** parametru.  
  
     Určuje atributy, které budou umístěny do `dependency` části souboru manifestu.  
  
     Další informace najdete v tématu [/MANIFESTDEPENDENCY (určení závislostí manifestu)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Viz také [konfiguračních souborů vydavatele](https://docs.microsoft.com/windows/desktop/SbsCs/publisher-configuration-files).  
  
-   **AdditionalOptions**  
  
     Volitelné **řetězec** parametru.  
  
     Seznam možností linkeru uvedená na příkazovém řádku. Třeba /\<možnost1 > /\<možnost2 > /\<možnost #>. Tento parametr použijte k určení možnosti linkeru, které nejsou reprezentovány jakýkoli jiný **odkaz** parametr úlohy.  
  
     Další informace najdete v tématu [možnosti Linkeru](/cpp/build/reference/linker-options).  
  
-   **AddModuleNamesToAssembly**  
  
     Volitelné **String []** parametru.  
  
     Přidá odkaz modulu na sestavení.  
  
     Další informace najdete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).  
  
-   **AllowIsolation**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, způsobí, že operační systém do manifestu vyhledávání a načte. Pokud `false`, označuje, zda jsou načteny knihovny DLL, jako kdyby byl žádný manifest.  
  
     Další informace najdete v tématu [/ALLOWISOLATION (vyhledání manifestu)](/cpp/build/reference/allowisolation-manifest-lookup).  
  
-   **AssemblyDebug**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, generuje **DebuggableAttribute** atribut spolu s ladicí informace o sledování a zakazuje optimalizace JIT. Pokud `false`, generuje **DebuggableAttribute** atribut ale zakáže sledování informací o ladění a povolí optimalizace JIT.  
  
     Další informace najdete v tématu [/assemblydebug (přidání atributu DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).  
  
-   **AssemblyLinkResource**  
  
     Volitelné **String []** parametru.  
  
     Vytvoří odkaz na prostředek rozhraní .NET Framework do výstupního souboru; soubor prostředků není umístěn do výstupního souboru. Zadejte název prostředku.  
  
     Další informace najdete v tématu [/ASSEMBLYLINKRESOURCE (odkaz na prostředek rozhraní .NET Framework)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).  
  
-   **AttributeFileTracking**  
  
     Implicitní **logická** parametru.  
  
     Povolí podrobnější souborů sledování k zachycení odkazu přírůstkové od chování. Vždy vrátí `true`.  
  
-   **Vlastnost BaseAddress**  
  
     Volitelné **řetězec** parametru.  
  
     Nastaví základní adresu pro program nebo knihovnu DLL při sestavování. Zadejte `{address[,size] | @filename,key}`.  
  
     Další informace najdete v tématu [propojovacího (základní adresa)](/cpp/build/reference/base-base-address).  
  
-   **BuildingInIDE**  
  
     Volitelné **logická** parametru.  
  
     Hodnota true určuje to, že nástroj MSBuild je vyvolána z rozhraní IDE. V opačném případě označuje, zda nástroj MSBuild je vyvolána z příkazového řádku.  
  
     Tento parametr nemá žádný ekvivalent linkeru.  
  
-   **CLRImageType**  
  
     Volitelné **řetězec** parametru.  
  
     Nastaví typ bitovou kopii common language runtime (CLR).  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
    -   **Výchozí** - *\<žádné >*  
  
    -   **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
    -   **ForcePureILImage** -   **/CLRIMAGETYPE: PURE**  
  
    -   **ForceSafeILImage** - **Safe**  
  
    Další informace najdete v tématu [/CLRIMAGETYPE (zadání typu bitové kopie modulu CLR)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).  
  
-   **CLRSupportLastError**  
  
     Volitelné **řetězec** parametru.  
  
     Zachová poslední kód chyby funkcí volaných mechanismem P/Invoke.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
    -   **Povolené** - **/CLRSupportLastError**  
  
    -   **Zakázané** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Další informace najdete v tématu [/CLRSUPPORTLASTERROR (zachování kódu poslední chyby pro volání PInvoke)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).  
  
-   **CLRThreadAttribute**  
  
     Volitelné **řetězec** parametru.  
  
     Explicitně určuje atribut dělení na vlákna pro vstupní bod programu CLR.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE: žádné**  
  
    -   **MTAThreadingAttribute** - **: MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Další informace najdete v tématu [/CLRTHREADATTRIBUTE (atribut vlákna modulu CLR nastavit)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).  
  
-   **CLRUnmanagedCodeCheck**  
  
     Volitelné **logická** parametru.  
  
     Určuje, zda linker použije **SuppressUnmanagedCodeSecurityAttribute** linkerem generovaná volání nespravovaného volání ze spravovaného kódu do nativních knihoven DLL.  
  
    Další informace najdete v tématu [/CLRUNMANAGEDCODECHECK (přidat atribut SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).  
  
-   **CreateHotPatchableImage**  
  
     Volitelné **řetězec** parametru.  
  
     Připravuje obrázek na horké záplatování.  
  
     Zadejte jednu z následujících hodnot, které odpovídá možností propojovacího programu.  
  
    -   **Povolené** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Další informace najdete v tématu [/FUNCTIONPADMIN (vytvořit bitovou kopii opravitelnou za provozu)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).  
  
-   **DataExecutionPrevention**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, označuje, že spustitelný soubor byl testován jako kompatibilní s funkcí Zabránění spuštění dat Windows.  
  
     Další informace najdete v tématu [/NXCOMPAT (kompatibilní s předcházením spuštění dat)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).  
  
-   **DelayLoadDLLs**  
  
     Volitelné **String []** parametru.  
  
     Způsobí, že tento parametr *s odloženým načtením* knihoven DLL. Zadejte název knihovny DLL pro odložené načtení.  
  
     Další informace najdete v tématu [/delayload (import odloženého načtení)](/cpp/build/reference/delayload-delay-load-import).  
  
-   **DelaySign**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, částečně podepíše sestavení. Výchozí hodnota je `false`.  
  
     Další informace najdete v tématu [/delaysign (částečně podepsání sestavení)](/cpp/build/reference/delaysign-partially-sign-an-assembly).  
  
-   **Ovladač**  
  
     Volitelné **řetězec** parametru.  
  
     Zadejte tento parametr k vytvoření ovladač režimu jádra Windows NT.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Ovladač** - **Driver/Driver**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** - **/DRIVER:WDM**  
  
    Další informace najdete v tématu [Driver/Driver (ovladač režimu jádra Windows NT)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).  
  
-   **EmbedManagedResourceFile**  
  
     Volitelné **String []** parametru.  
  
     Vloží soubor prostředků v sestavení. Zadejte název souboru požadovaný prostředek. Volitelně zadejte logický název, který slouží k načtení prostředku, a **PRIVÁTNÍ** možnost, která označuje v manifestu sestavení, že soubor prostředků je privátní.  
  
     Další informace najdete v tématu [narozdíl od (vložení spravovaného prostředku)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).  
  
-   **EnableCOMDATFolding**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, povoluje skládání identických sekvencí COMDAT.  
  
     Další informace najdete v tématu `ICF[= iterations]` argument [/OPT (optimalizace)](/cpp/build/reference/opt-optimizations).  
  
-   **EnableUAC**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, určuje, že informace o řízení uživatelských účtů (UAC) je vloženy do manifestu.  
  
     Další informace najdete v tématu [/MANIFESTUAC (vložené informace UAC v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **EntryPointSymbol**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje funkci vstupního bodu jako počáteční adresu *.exe* soubor nebo knihovny DLL. Zadejte název funkce jako hodnotu parametru.  
  
     Další informace najdete v tématu [/Entry (symbol vstupního bodu)](/cpp/build/reference/entry-entry-point-symbol).  
  
-   **FixedBaseAddress**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vytvoří program nebo knihovnu DLL, který lze načíst pouze na jeho upřednostňované základní adrese.  
  
     Další informace najdete v tématu [/fixed (pevná základní adresa)](/cpp/build/reference/fixed-fixed-base-address).  
  
-   **ForceFileOutput**  
  
     Volitelné **řetězec** parametru.  
  
     Říká linkeru, aby vytvořil platný *.exe* soubor nebo knihovny DLL i v případě, ale ne odkazovaný symbol definovaný, nebo je definovaná víckrát.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    -   **Povolené** -   **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
    -   **UndefinedSymbolOnly** -   **/FORCE: NEROZPOZNANÝ**  
  
    Další informace najdete v tématu [/Force (vynucení výstupu souboru)](/cpp/build/reference/force-force-file-output).  
  
-   **ForceSymbolReferences**  
  
     Volitelné **String []** parametru.  
  
     Tento parametr přikazuje linkeru, aby přidal zadaný symbol do tabulky symbolů.  
  
     Další informace najdete v tématu [parametr/include (vynucení odkazů na symboly)](/cpp/build/reference/include-force-symbol-references).  
  
-   **FunctionOrder**  
  
     Volitelné **řetězec** parametru.  
  
     Tento parametr optimalizuje program tak, že zadaný zabalených funkcí (sekvence Comdat) do bitové kopie v předurčeném pořadí.  
  
     Další informace najdete v tématu [/Order (Put funkcí v pořadí)](/cpp/build/reference/order-put-functions-in-order).  
  
-   **GenerateDebugInformation**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vytvoří ladicí informace pro *.exe* soubor nebo knihovny DLL.  
  
     Další informace najdete v tématu [/Debug (Generovat ladicí informace)](/cpp/build/reference/debug-generate-debug-info).  
  
-   **GenerateManifest**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vytvoří soubor manifestu vedle sebe.  
  
     Další informace najdete v tématu [volbu/manifest (vytvoření manifestu sestavení vedle sebe)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).  
  
-   **GenerateMapFile**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vytvoří *souboru s mapováním*. Přípona názvu souboru souboru s mapováním je *.map*.  
  
     Další informace najdete v tématu [parametr/map (generování souboru mapování)](/cpp/build/reference/map-generate-mapfile).  
  
-   **HeapCommitSize**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje množství fyzické paměti v haldě přidělit najednou.  
  
     Další informace najdete v tématu `commit` argument v [/HEAP (nastavení velikosti haldy)](/cpp/build/reference/heap-set-heap-size). Další informace naleznete **HeapReserveSize** parametru.  
  
-   **HeapReserveSize**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje celkový počet haldy ve virtuální paměti.  
  
     Další informace najdete v tématu `reserve` argument v [/HEAP (nastavení velikosti haldy)](/cpp/build/reference/heap-set-heap-size). Další informace naleznete **HeapCommitSize** parametr v této tabulce.  
  
-   **IgnoreAllDefaultLibraries**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, říká linkeru, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven prohledává při překladu externích odkazů.  
  
     Další informace najdete v tématu [: / NODEFAULTLIB (ignorování knihoven)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **IgnoreEmbeddedIDL**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, určuje, že atributy IDL ve zdrojovém kódu nemají být zpracovány do *.idl* souboru.  
  
     Další informace najdete v tématu [/IGNOREIDL (Nezpracovávat atributy do MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).  
  
-   **IgnoreImportLibrary**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, určuje, že knihovna importů generovaná touto konfigurací by neměla být importována do závislých projektů.  
  
     Tento parametr neodpovídá možností propojovacího programu.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     Volitelné **String []** parametru.  
  
     Určuje jeden nebo více názvů výchozích knihoven k ignorování. Více knihoven oddělte středníkem.  
  
     Další informace najdete v tématu [: / NODEFAULTLIB (ignorování knihoven)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, linker vytvoří bitovou kopii pouze v případě, že můžete také vytvořit tabulku na obrázku bezpečných obslužných rutin výjimek.  
  
     Další informace najdete v tématu [/SAFESEH (bitová kopie má bezpečné obslužné rutiny výjimek)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).  
  
-   **ImportLibrary**  
  
     Název knihovny importu zadané uživatelem, který nahrazuje výchozí název knihovny.  
  
     Další informace najdete v tématu [/IMPLIB (pojmenování knihovny importu)](/cpp/build/reference/implib-name-import-library).  
  
-   **KeyContainer**  
  
     Volitelné **řetězec** parametru.  
  
     Kontejner, který obsahuje klíč pro podepsané sestavení.  
  
     Další informace najdete v tématu [/keycontainer (určení kontejneru klíčů pro podpis sestavení)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Další informace naleznete **KeyFile** parametr v této tabulce.  
  
-   **KeyFile**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje soubor, který obsahuje klíč pro podepsané sestavení.  
  
     Další informace najdete v tématu [/keyfile (zadat klíč nebo dvojici klíčů k podepsání sestavení)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Další informace naleznete **KeyContainer** parametru.  
  
-   **LargeAddressAware**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, že aplikace dokáže zpracovat adresy větší než 2 GB.  
  
     Další informace najdete v tématu [/LARGEADDRESSAWARE (zpracování velkých adres)](/cpp/build/reference/largeaddressaware-handle-large-addresses).  
  
-   **LinkDLL**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, sestavení a knihovny DLL jako hlavní výstupního souboru.  
  
     Další informace najdete v tématu [/DLL (sestavení knihovny DLL)](/cpp/build/reference/dll-build-a-dll).  
  
-   **LinkErrorReporting**  
  
     Volitelné **řetězec** parametru.  
  
     Umožňuje poskytnout informace o kompilátoru vnitřní chybě (ICE) přímo společnosti Microsoft.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    -   **NoErrorReport** -   **/errorreport: žádné**  
  
    -   **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** -   **/errorreport: Send**  
  
    Další informace najdete v tématu [/errorreport (sestava interními chybami linkeru)](/cpp/build/reference/errorreport-report-internal-linker-errors).  
  
-   **LinkIncremental**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, umožňuje přírůstkové propojení.  
  
     Další informace najdete v tématu [/INCREMENTAL (inkrementální odkaz)](/cpp/build/reference/incremental-link-incrementally).  
  
-   **LinkLibraryDependencies**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, určuje, že knihovny vytvořené jako výstupy závislostí projektu automaticky připojeny.  
  
     Tento parametr neodpovídá možností propojovacího programu.  
  
-   **LinkStatus**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, určuje, zda linker zobrazit ukazatel průběhu, který ukazuje, jaké je procento odkazu je dokončena.  
  
     Další informace najdete v tématu `STATUS` argument [parametru/LTCG (generování kódu při propojování odkaz)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **LinkTimeCodeGeneration**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje možnosti pro optimalizace na základě profilu.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    -   **Výchozí** - *\<žádné >*  
  
    -   **UseLinkTimeCodeGeneration** - **/LTCG**  
  
    -   **PGInstrument** - **/LTCG:PGInstrument**  
  
    -   **PGOptimization** - **/LTCG:PGOptimize**  
  
    -   **PGUpdate**  
  
         \- **/LTCG:PGUpdate**  
  
    Další informace najdete v tématu [parametru/LTCG (generování kódu při propojování odkaz)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **ManifestFile**  
  
     Volitelné **řetězec** parametru.  
  
     Mění název výchozího souboru manifestu pro zadaný název souboru.  
  
     Další informace najdete v tématu [manifestfile (pojmenování souboru manifestu)](/cpp/build/reference/manifestfile-name-manifest-file).  
  
-   **MapExports**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, přikazuje linkeru začlenit exportované funkce v souboru mapy.  
  
     Další informace najdete v tématu `EXPORTS` argument [parametr/MapInfo (zahrnout informace do souboru mapování)](/cpp/build/reference/mapinfo-include-information-in-mapfile).  
  
-   **MapFileName**  
  
     Volitelné **řetězec** parametru.  
  
     Výchozí název souboru mapy se změní na zadaný název souboru.  
  
-   **MergedIDLBaseFileName**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název souboru a přípony názvu souboru *.idl* souboru.  
  
     Další informace najdete v tématu [/IDLOUT (MIDL název výstupních souborů)](/cpp/build/reference/idlout-name-midl-output-files).  
  
-   **MergeSections**  
  
     Volitelné **řetězec** parametru.  
  
     Kombinuje oddíly v obraze. Zadejte `from-section=to-section`.  
  
     Další informace najdete v tématu [/Merge (sloučení oddílů)](/cpp/build/reference/merge-combine-sections).  
  
-   **MidlCommandFile**  
  
     Volitelné **řetězec** parametru.  
  
     Zadejte název souboru, který obsahuje parametry příkazového řádku MIDL.  
  
     Další informace najdete v tématu [/MIDL (Možnosti příkazového řádku zadejte MIDL)](/cpp/build/reference/midl-specify-midl-command-line-options).  
  
-   **MinimumRequiredVersion**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje minimální požadovanou verzi subsystému. Argumenty jsou desetinná čísla v rozsahu 0 až 65535.  
  
-   **ModuleDefinitionFile**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název [soubor definice modulu](/cpp/build/reference/module-definition-dot-def-files).  
  
     Další informace najdete v tématu [def (zadání souboru definice modulu)](/cpp/build/reference/def-specify-module-definition-file).  
  
-   **MSDOSStubFileName**  
  
     Volitelné **řetězec** parametru.  
  
     Připojí zadaný zástupný program MS-DOS k programu Win32.  
  
     Další informace najdete v tématu [/stub (název souboru zástupného kódu MS-DOS zástupné procedury)](/cpp/build/reference/stub-ms-dos-stub-file-name).  
  
-   **NoEntryPoint**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, určuje knihovnu DLL pouze prostředků.  
  
     Další informace najdete v tématu [NOENTRY (bez vstupního bodu)](/cpp/build/reference/noentry-no-entry-point).  
  
-   **ObjectFiles**  
  
     Implicitní **String []** parametru.  
  
     Určuje soubory objektů, které jsou propojeny.  
  
-   **OptimizeReferences**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, eliminuje funkce nebo data, která nejsou nikdy odkazována.  
  
     Další informace najdete v tématu `REF` argument v [/OPT (optimalizace)](/cpp/build/reference/opt-optimizations).  
  
-   **Výstupní soubor**  
  
     Volitelné **řetězec** parametru.  
  
     Přepíše výchozí název a umístění programu, který vytvoří linker.  
  
     Další informace najdete v tématu [/OUT (název výstupního souboru)](/cpp/build/reference/out-output-file-name).  
  
-   **PerUserRedirection**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true` a je povolen výstup registru, vynutí registru zapisuje do **HKEY_CLASSES_ROOT** přesměrovat na **HKEY_CURRENT_USER**.  
  
-   **PreprocessOutput**  
  
     Volitelné `ITaskItem[]` parametru.  
  
     Definuje pole objektů preprocesoru výstupní položky, které lze používat a, protože ho vygeneroval úlohy.  
  
-   **PreventDllBinding**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, označuje *Bind.exe* , který by neměl být vázaný propojený obrázek.  
  
     Další informace najdete v tématu [/ALLOWBIND (zabránit vazbě knihoven DLL)](/cpp/build/reference/allowbind-prevent-dll-binding).  
  
-   **Profil**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vytvoří výstupní soubor, který lze použít s **nástroje pro měření výkonu** profileru.  
  
     Další informace najdete v tématu [/Profile (profiler nástrojů výkonu)](/cpp/build/reference/profile-performance-tools-profiler).  
  
-   **ProfileGuidedDatabase**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název *.pgd* soubor, který se použije k ukládání informací o spuštění programu  
  
     Další informace najdete v tématu [/PGD (určení databáze pro optimalizace na základě profilu)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).  
  
-   **ProgramDatabaseFile**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název databáze programu (PDB), který vytvoří linker.  
  
     Další informace najdete v tématu [/pdb (použití databáze programu)](/cpp/build/reference/pdb-use-program-database).  
  
-   **RandomizedBaseAddress**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, generuje spustitelnou bitovou kopii, která lze náhodně změnit základ v okamžiku načtení pomocí *náhodného generování rozložení prostoru adres* (technologie ASLR) funkce systému Windows.  
  
     Další informace najdete v tématu [možnost/DynamicBase (použití adres náhodného generování rozložení prostoru)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).  
  
-   **RegisterOutput**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, zaregistruje primární výstup tohoto sestavení.  
  
-   **SectionAlignment**  
  
     Volitelné **celé číslo** parametru.  
  
     Určuje zarovnání jednotlivých oddílů uvnitř lineárního adresního prostoru programu. Hodnota tohoto parametru je jednotka počet bajtů a je mocninou čísla 2.  
  
     Další informace najdete v tématu [/align (zarovnání oddílů)](/cpp/build/reference/align-section-alignment).  
  
-   **Setchecksum –**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, nastaví kontrolní součet v hlavičce *.exe* souboru.  
  
     Další informace najdete v tématu [/Release (nastavení kontrolního součtu)](/cpp/build/reference/release-set-the-checksum).  
  
-   **ShowProgress**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje úroveň podrobností sestav průběhu pro operace propojení.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    -   **NotSet** - *\<none>*  
  
    -   **LinkVerbose** - **/VERBOSE**  
  
    -   **LinkVerboseLib** - **/VERBOSE:Lib**  
  
    -   **LinkVerboseICF** - **/VERBOSE:ICF**  
  
    -   **LinkVerboseREF** - **/VERBOSE:REF**  
  
    -   **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
    -   **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Další informace najdete v tématu [verbose (Tisk zprávy o průběhu)](/cpp/build/reference/verbose-print-progress-messages).  
  
-   **Zdroje**  
  
     Vyžaduje `ITaskItem[]` parametru.  
  
     Definuje pole objektů položky nástroje MSBuild zdrojových souborů, které lze používat a, protože ho vygeneroval úlohy.  
  
-   **SpecifySectionAttributes**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje atributy oddílu. Tím se přepíše atributy, které byly nastaveny při *.obj* soubor pro kompilaci části.  
  
     Další informace najdete v tématu [/Section (určit atributy oddílu)](/cpp/build/reference/section-specify-section-attributes).  
  
-   **StackCommitSize**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje množství fyzické paměti v každém přidělení při další paměť je přidělena.  
  
     Další informace najdete v tématu `commit` argument [/Stack (přidělení zásobníku)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StackReserveSize**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje, celkovou velikost zásobníku přidělenou ve virtuální paměti.  
  
     Další informace najdete v tématu `reserve` argument [/Stack (přidělení zásobníku)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StripPrivateSymbols**  
  
     Volitelné **řetězec** parametru.  
  
     Vytvoří druhý soubor databáze (PDB) programu, která vynechává symboly, které nechcete k distribuci zákazníkům. Zadejte název druhý soubor PDB.  
  
     Další informace najdete v tématu [/PDBSTRIPPED (odstranění privátních symbolů)](/cpp/build/reference/pdbstripped-strip-private-symbols).  
  
-   **Subsystém**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje prostředí pro spustitelný soubor.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Konzola** -   **/Subsystem: Console**  
  
    -   **Windows** -   **/Subsystem: Windows**  
  
    -   **Nativní** - **souboru**  
  
    -   **Aplikace EFI** - **/SUBSYSTEM:EFI_APPLICATION**  
  
    -   **Ovladač spouštěcí služby EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
    -   **PAMĚŤ ROM EFI** - **/SUBSYSTEM:EFI_ROM**  
  
    -   **Modul Runtime EFI** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
    -   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
    -   **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Další informace najdete v tématu [/Subsystem (určení subsystému)](/cpp/build/reference/subsystem-specify-subsystem).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, přikazuje linkeru, které nechcete zahrnout do finální bitové kopie s možností vazby tabulky importu adres (IAT).  
  
     Další informace najdete v tématu `NOBIND` argument [/delay (nastavení importu odloženého načtení)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, říká odloženě zaváděné pomocnou funkci, aby podporovala explicitní uvolnění knihovny DLL.  
  
     Další informace najdete v tématu `UNLOAD` argument [/delay (nastavení importu odloženého načtení)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SuppressStartupBanner**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.  
  
     Další informace najdete v tématu [/nologo (Potlačit úvodní nápis při spouštění) (linker)](/cpp/build/reference/nologo-suppress-startup-banner-linker).  
  
-   **SwapRunFromCD**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, informuje operační systém nejprve zkopírovat linkeru výstupu do odkládacího souboru, a potom spusťte bitovou kopii z něj.  
  
     Další informace najdete v tématu `CD` argument [swaprun (Načtení výstupu linkeru do odkládacího souboru)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Další informace naleznete **SwapRunFromNET** parametru.  
  
-   **SwapRunFromNET**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, informuje operační systém nejprve zkopírovat linkeru výstupu do odkládacího souboru, a potom spusťte bitovou kopii z něj.  
  
     Další informace najdete v tématu `NET` argument [swaprun (Načtení výstupu linkeru do odkládacího souboru)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Další informace naleznete **SwapRunFromCD** parametr v této tabulce.  
  
-   **TargetMachine**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje cílovou platformu pro program nebo knihovnu DLL.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    -   **NotSet** - *\<none>*  
  
    -   **MachineARM** - **/MACHINE:ARM**  
  
    -   **MachineEBC** - **/MACHINE:EBC**  
  
    -   **MachineIA64** - **/MACHINE:IA64**  
  
    -   **MachineMIPS** - **/MACHINE:MIPS**  
  
    -   **MachineMIPS16** - **/MACHINE:MIPS16**  
  
    -   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
    -   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
    -   **MachineSH4** - **/MACHINE:SH4**  
  
    -   **MachineTHUMB** - **/MACHINE:THUMB**  
  
    -   **MachineX64** - **/MACHINE:X 64**  
  
    -   **MachineX86** - **/MACHINE:X 86**  
  
    Další informace najdete v tématu [/Machine (zadání cílové platformy)](/cpp/build/reference/machine-specify-target-platform).  
  
-   **TerminalServerAware**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, nastaví příznak v poli IMAGE_OPTIONAL_HEADER dllcharacteristics v nepovinné hlavičce bitové kopie programu. Pokud je tento příznak nastaven, neprovede Terminálový Server určité změny aplikace.  
  
     Další informace najdete v tématu [parametr/TSAWARE (vytvoření Terminálový Server aplikace s)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).  
  
-   **TrackerLogDirectory**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje adresář protokolu sledovacího modulu.  
  
-   **TreatLinkerWarningAsErrors**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, způsobí, že žádný výstupní soubor, který chcete vygenerovat, pokud linker vydá upozornění.  
  
     Další informace najdete v tématu [/WX (zpracovávat upozornění linkeru jako chyb)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).  
  
-   **TurnOffAssemblyGeneration**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vytvoří bitovou kopii pro aktuální výstupní soubor bez sestavení rozhraní .NET Framework.  
  
     Další informace najdete v tématu [parametr/noassembly (vytvoření modulu MSIL)](/cpp/build/reference/noassembly-create-a-msil-module).  
  
-   **TypeLibraryFile**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název souboru a přípony názvu souboru *.tlb* souboru. Zadejte název souboru nebo název a cesta k souboru.  
  
     Další informace najdete v tématu [/TLBOUT (pojmenování souboru .tlb)](/cpp/build/reference/tlbout-name-dot-tlb-file).  
  
-   **TypeLibraryResourceID**  
  
     Volitelné **celé číslo** parametru.  
  
     Určuje hodnotu zadané uživatelem pro knihovnu typů vytvoří linker. Zadejte hodnotu od 1 do 65535.  
  
     Další informace najdete v tématu [/TLBID (určení ID prostředku pro knihovnu typů)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).  
  
-   **UACExecutionLevel**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje požadovanou úroveň spuštění aplikace při spuštění v části s řízením uživatelských účtů.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    -   **AsInvoker** - `level='asInvoker'`  
  
    -   **HighestAvailable** - `level='highestAvailable'`  
  
    -   **RequireAdministrator** - `level='requireAdministrator'`  
  
    Další informace najdete v tématu `level` argument [/MANIFESTUAC (vložené informace UAC v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UACUIAccess**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, aplikace obchází úrovně ochrany uživatelského rozhraní a vstup na vyšší oprávnění windows na ploše; v opačném případě jednotky `false`.  
  
     Další informace najdete v tématu `uiAccess` argument [/MANIFESTUAC (vložené informace UAC v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UseLibraryDependencyInputs**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, jsou použity vstupy nástroje librarian spíše než soubor knihovny sám při knihovny výstupy závislostí projektu se připojují.  
  
-   **Verze**  
  
     Volitelné **řetězec** parametru.  
  
     Vložil číslo verze v záhlaví *.exe* nebo *.dll* souboru. Zadejte "`major[.minor]`". `major` a `minor` argumenty jsou desetinná čísla od 0 do 65535.  
  
     Další informace najdete v tématu [/Version (informace o verzi)](/cpp/build/reference/version-version-information).  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
