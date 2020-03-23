---
title: Úkol propojení | Dokumenty společnosti Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01105e3fd4c86d57077df7804e66592e32ebae07
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865346"
---
# <a name="link-task"></a>odkaz – úloha

Zalomí nástroj propojovací program Microsoft C++, *link.exe*. Nástroj linker propojuje soubory objektů AC (COFF) a vytváří spustitelný soubor *(EXE)* nebo knihovnu dll (Dynamic-link). Další informace naleznete v [tématech Možnosti propojovacího programu](/cpp/build/reference/linker-options) a [Použití nástroje MSBuild z příkazového řádku](/cpp/build/msbuild-visual-cpp) a Použití sady nástrojů Microsoft [C++ z příkazového řádku](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametry

 Následující text popisuje parametry úkolu **Propojení.** Většina parametrů úlohy a několik sad parametrů odpovídají možnosti příkazového řádku.

- **Další závislosti**

  Volitelný **parametr String[].**

  Určuje seznam vstupních souborů, které chcete přidat do příkazu.

  Další informace naleznete v tématu [LINK input files](/cpp/build/reference/link-input-files).

- **Další adresáře knihovny**

  Volitelný **parametr String[].**

  Přepíše cestu knihovny prostředí. Zadejte název adresáře.

  Další informace naleznete v tématu [/LIBPATH (Additional Libpath)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  Volitelný **parametr String[].**

  Určuje atributy, které budou `dependency` umístěny do části souboru manifestu.

  Další informace naleznete v tématu [/MANIFESTDEPENDENCY (Zadat závislosti manifestu)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Viz také [konfigurační soubory aplikace Publisher](/windows/desktop/SbsCs/publisher-configuration-files).

- **Další možnosti**

  Volitelný **parametr String.**

  Seznam možností propojovacího zařízení, jak je určeno na příkazovém řádku. Například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností propojovacího objektu, které nejsou reprezentovány žádným jiným parametrem **úlohy propojení.**

  Další informace naleznete v tématu [Možnosti linkeru](/cpp/build/reference/linker-options).

- **Přidat názvy modulůkk**

  Volitelný **parametr String[].**

  Přidá odkaz na modul do sestavy.

  Další informace naleznete v tématu [/ASSEMBLYMODULE (Add a MSIL modul do sestavení)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **Povolit izolaci**

  Volitelný **logický** parametr.

  Pokud `true`, způsobí, že operační systém provést vyhledávání manifestu a zatížení. Pokud `false`, označuje, že knihovny DLL jsou načteny, jako kdyby nebyl žádný manifest.

  Další informace naleznete [v tématu /ALLOWISOLATION (Vyhledávání manifestu).](/cpp/build/reference/allowisolation-manifest-lookup)

- **Ladění sestavení**

  Volitelný **logický** parametr.

  Pokud `true`, vydává **Laditatribut** atribut spolu s ladění min. sledování informací a zakáže optimalizace JIT. Pokud `false`aplikace vydává atribut **Laditatribut,** ale zakáže sledování ladicích informací a povolí optimalizaci JIT.

  Další informace naleznete v tématu [/ASSEMBLYDEBUG (Add DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  Volitelný **parametr String[].**

  Vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru. soubor prostředků není umístěn do výstupního souboru. Zadejte název prostředku.

  Další informace naleznete v tématu [/ASSEMBLYLINKRESOURCE (Link to .NET Framework resource)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Implicitní **logický** parametr.

  Umožňuje hlubší sledování souborů pro zachycení přírůstkového chování propojení. Vždy vrátí hodnotu `true`.

- **Základní adresa**

  Volitelný **parametr String.**

  Nastaví základní adresu pro program nebo dll, které jsou sestaveny. Zadejte `{address[,size] | @filename,key}`.

  Další informace naleznete v tématu [/BASE (Základní adresa)](/cpp/build/reference/base-base-address).

- **BuildinginiDE**

  Volitelný **logický** parametr.

  Pokud true, označuje, že MSBuild je vyvolána z ide. V opačném případě označuje, že MSBuild je vyvolána z příkazového řádku.

  Tento parametr nemá žádnou ekvivalentní možnost propojovacího objektu.

- **Typ clrimage**

  Volitelný **parametr String.**

  Nastaví typ obrázku CLR (COMMON Language runtime).

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti propojovacího propojení.

  - **Výchozí** - *žádný>\<*

  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**

  Další informace naleznete v tématu [/CLRIMAGETYPE (Zadejte typ obrázku CLR)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **ClRSupportLastError**

  Volitelný **parametr String.**

  Zachová poslední kód chyby funkcí volaných prostřednictvím mechanismu P/Invoke.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti propojovacího propojení.

  - **Povolena** - **chyba /CLRSupportLastError**

  - **Zakázáno** - **/CLRSupportLastError:NO**

  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**

  Další informace naleznete v tématu [/CLRSUPPORTLASTERROR (Zachovat poslední kód chyby pro volání PInvoke).](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls)

- **Atribut CLRThread**

  Volitelný **parametr String.**

  Explicitně určuje atribut zřetězení pro vstupní bod programu CLR.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti propojovacího propojení.

  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**

  - **Atribut MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**

  - **Atribut STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**

  Další informace naleznete v tématu [/CLRTHREADATTRIBUTE (Set CLR thread attribute)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  Volitelný **logický** parametr.

  Určuje, zda bude propojovací program používat **suppressUnmanagedCodeSecurityAttribute** pro volání P/Invoke generované propojovacím programem ze spravovaného kódu do nativních knihoven DLL.

  Další informace naleznete v tématu [/CLRUNMANAGEDCODECHECK (Add SuppressSuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **VytvořitObrázHotPatchableImage**

  Volitelný **parametr String.**

  Připraví obraz pro horké záplatování.

  Zadejte jednu z následujících hodnot, která odpovídá možnosti propojovacího propojení.

  - **Povoleno** - **/FUNCTIONPADMIN**

  - **X86Image** - **/FUNCTIONPADMIN:5**

  - **X64Image** - **/FUNCTIONPADMIN:6**

  - **ItaniumImage** - **/FUNCTIONPADMIN:16**

  Další informace naleznete v tématu [/FUNCTIONPADMIN (Create hotpatchable image).](/cpp/build/reference/functionpadmin-create-hotpatchable-image)

- **DataExecutionPrevention**

  Volitelný **logický** parametr.

  Pokud `true`aplikace označuje, že spustitelný soubor byl testován jako kompatibilní s funkcí Zabránění spuštění dat systému Windows.

  Další informace naleznete v tématu [/NXCOMPAT (Kompatibilní s zabráněním spuštění dat)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDL**

  Volitelný **parametr String[].**

  Tento parametr způsobí *zpožděné načítání* knihoven DLL. Zadejte název dll zpoždění zatížení.

  Další informace naleznete v tématu [/DELAYLOAD (Delay load import)](/cpp/build/reference/delayload-delay-load-import).

- **Delaysign**

  Volitelný **logický** parametr.

  Pokud `true`, částečně podepíše sestavení. Výchozí hodnota je `false`.

  Další informace naleznete v tématu [/DELAYSIGN (Částečně podepsat sestavení)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Ovladač**

  Volitelný **parametr String.**

  Zadejte tento parametr pro vytvoření ovladače režimu jádra systému Windows NT.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti propojovacího propojení.

  - **NotNastavit žádný** - >*\<*

  - **Ovladač** - **/Řidič**

  - **UpOnly** - **/DRIVER:UPONLY**

  - **WDM** - **/DRIVER:WDM**

  Další informace naleznete v tématu [/DRIVER (Windows NT kernel mode driver)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **Soubor EmbedManagedResourceFile**

  Volitelný **parametr String[].**

  Vloží soubor prostředků do sestavení. Zadejte požadovaný název souboru prostředků. Volitelně zadejte logický název, který se používá k načtení prostředku, a možnost **PRIVATE,** která v manifestu sestavení označuje, že soubor prostředků je soukromý.

  Další informace naleznete v tématu [/ASSEMBLYRESOURCE (Vložit spravovaný prostředek)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **Povolit skládání COMDAT**

  Volitelný **logický** parametr.

  Pokud `true`, umožňuje identické COMDAT skládání.

  Další informace naleznete `ICF[= iterations]` v argumentu [/OPT (Optimalizace)](/cpp/build/reference/opt-optimizations).

- **EnableuAC**

  Volitelný **logický** parametr.

  Pokud `true`aplikace určuje, že informace o řízení uživatelských účtů (UAC) jsou vloženy do manifestu programu.

  Další informace naleznete [v tématu /MANIFESTUAC (Embeds UAC informace v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  Volitelný **parametr String.**

  Určuje funkci vstupního bodu jako počáteční adresu souboru *EXE* nebo dll. Jako hodnotu parametru zadejte název funkce.

  Další informace naleznete v tématu [/ENTRY (symbol vstupního bodu).](/cpp/build/reference/entry-entry-point-symbol)

- **Adresa FixedBaseAddress**

  Volitelný **logický** parametr.

  Pokud `true`, vytvoří program nebo dll, který lze načíst pouze na jeho preferované základní adresu.

  Další informace naleznete v tématu [/FIXED (Pevná základní adresa)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  Volitelný **parametr String.**

  Sděluje propojovacímu systému vytvoření platného souboru *EXE* nebo knihovny DLL, i když je symbol odkazován, ale není definován, nebo je definován.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Povoleno** - **/FORCE**

  - **MultiplyDefinedSymbolOnly** - **/FORCE:NÁSOBEK**

  - **UndefinedSymbolOnly** - **/FORCE:NEVYŘEŠENO**

  Další informace naleznete v tématu [/FORCE (Force file output).](/cpp/build/reference/force-force-file-output)

- **ForceSymbolReferences**

  Volitelný **parametr String[].**

  Tento parametr říká propojovacímu objektu, aby do tabulky symbolů přidal zadaný symbol.

  Další informace naleznete v tématu [/INCLUDE (Force symbol reference)](/cpp/build/reference/include-force-symbol-references).

- **Příkaz funkce**

  Volitelný **parametr String.**

  Tento parametr optimalizuje program umístěním zadaných zabalených funkcí (COMDAts) do obrazu v předem určeném pořadí.

  Další informace naleznete v tématu [/ORDER (Dát funkce v pořadí)](/cpp/build/reference/order-put-functions-in-order).

- **GenerateDebugInformation**

  Volitelný **logický** parametr.

  Pokud `true`aplikace vytvoří informace o ladění pro soubor *EXE* nebo dll.

  Další informace naleznete v tématu [/DEBUG (Generate debug info)](/cpp/build/reference/debug-generate-debug-info).

- **Generovat manifest**

  Volitelný **logický** parametr.

  Pokud `true`vytvoří soubor manifestu vedle sebe.

  Další informace naleznete v tématu [/MANIFEST (Vytvoření manifestu sestavení vedle sebe).](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest)

- **Soubor GenerateMapFile**

  Volitelný **logický** parametr.

  Pokud `true`vytvoří *soubor mapy*. Přípona názvu souboru mapy je *.map*.

  Další informace naleznete v tématu [/MAP (Generate mapfile)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  Volitelný **parametr String.**

  Určuje množství fyzické paměti na haldě, kterou chcete přidělit najednou.

  Další informace naleznete `commit` v argumentu [/HEAP (Set haldy velikost)](/cpp/build/reference/heap-set-heap-size). Také naleznete **HeapReserveSize** parametr.

- **HeapReserveSize**

  Volitelný **parametr String.**

  Určuje celkové přidělení haldy ve virtuální paměti.

  Další informace naleznete `reserve` v argumentu [/HEAP (Set haldy velikost)](/cpp/build/reference/heap-set-heap-size). Viz také parametr **HeapCommitSize** v této tabulce.

- **Ignorovatvšechny výchozí knihovny**

  Volitelný **logický** parametr.

  Pokud `true`aplikace napojovací systém sděluje propojovacímu systému odebrání jedné nebo více výchozích knihoven ze seznamu knihoven, které hledá při řešení externích odkazů.

  Další informace naleznete v tématu [/NODEFAULTLIB (Ignorovat knihovny).](/cpp/build/reference/nodefaultlib-ignore-libraries)

- **IgnorovatEmbeddedIDL**

  Volitelný **logický** parametr.

  Pokud `true`aplikace , určuje, že žádné atributy IDL ve zdrojovém kódu by neměly být zpracovány do souboru *.idl.*

  Další informace naleznete v tématu [/IGNOREIDL (Nezpracovávat atributy do MIDL).](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl)

- **IgnoreImportLibrary**

  Volitelný **logický** parametr.

  Pokud `true`aplikace určuje, že knihovna importu vygenerovaná touto konfigurací by neměla být importována do závislých projektů.

  Tento parametr neodpovídá možnosti propojovacího objektu.

- **IgnoreSpecificDefaultKnihovny**

  Volitelný **parametr String[].**

  Určuje jeden nebo více názvů výchozích knihoven, které chcete ignorovat. Oddělte více knihoven pomocí středníků.

  Další informace naleznete v tématu [/NODEFAULTLIB (Ignorovat knihovny).](/cpp/build/reference/nodefaultlib-ignore-libraries)

- **ImageHasSafeExceptionHandlers**

  Volitelný **logický** parametr.

  Pokud `true`propojovací aplikace vytvoří bitovou kopii pouze v případě, že může také vytvořit tabulku s obslužnými rutinami bezpečných výjimek bitové kopie.

  Další informace naleznete v tématu [/SAFESEH (Image has safe exception handlers)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **Importovat knihovnu**

  Uživatelem určený název knihovny importu, který nahrazuje výchozí název knihovny.

  Další informace naleznete v tématu [/IMPLIB (Knihovna importu názvů).](/cpp/build/reference/implib-name-import-library)

- **Keycontainer**

  Volitelný **parametr String.**

  Kontejner, který obsahuje klíč pro podepsané sestavení.

  Další informace naleznete v tématu [/KEYCONTAINER (Zadejte kontejner klíčů k podepsání sestavení).](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) Viz také **keyfile** parametr v této tabulce.

- **Keyfile**

  Volitelný **parametr String.**

  Určuje soubor, který obsahuje klíč pro podepsané sestavení.

  Další informace naleznete v tématu [/KEYFILE (Zadejte klíč nebo dvojici klíčů k podepsání sestavení).](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) Viz také **KeyContainer** parametr.

- **LargeAddressAware**

  Volitelný **logický** parametr.

  Pokud `true`aplikace dokáže zpracovat adresy větší než 2 gigabajty.

  Další informace naleznete v tématu [/LARGEADDRESSAWARE (Zpracování velkých adres).](/cpp/build/reference/largeaddressaware-handle-large-addresses)

- **LinkDLL**

  Volitelný **logický** parametr.

  Pokud `true`vytvoří dll jako hlavní výstupní soubor.

  Další informace naleznete [v tématu /DLL (Build a DLL)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  Volitelný **parametr String.**

  Umožňuje poskytovat informace o interní chybě kompilátoru (ICE) přímo společnosti Microsoft.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NoErrorReport** - **/ERRORREPORT:NONE**

  - **PromptImmediately** - **/ERRORREPORT:VÝZVA**

  - **QueueForNextLogin** - **/ERRORREPORT:FRONTA**

  - **SendErrorReport** - **/ERRORREPORT:ODESLAT**

  Další informace naleznete v tématu [/ERRORREPORT (Nahlásit interní chyby propojovacího systému).](/cpp/build/reference/errorreport-report-internal-linker-errors)

- **LinkIncremental**

  Volitelný **logický** parametr.

  Pokud `true`, umožňuje přírůstkové propojení.

  Další informace naleznete v tématu [/INCREMENTAL (Link incrementally).](/cpp/build/reference/incremental-link-incrementally)

- **Závislostí knihovny propojení**

  Volitelný **logický** parametr.

  Pokud `true`aplikace určuje, že výstupy knihovny ze závislostí projektu jsou automaticky propojeny.

  Tento parametr neodpovídá možnosti propojovacího objektu.

- **Stav odkazu**

  Volitelný **logický** parametr.

  Pokud `true`, určuje, že propojovací program je zobrazit indikátor průběhu, který ukazuje, jaké procento propojení je dokončeno.

  Další informace naleznete `STATUS` v argumentu [/LTCG (Generování kódu v době propojení).](/cpp/build/reference/ltcg-link-time-code-generation)

- **Generování kódu LinkTime**

  Volitelný **parametr String.**

  Určuje možnosti optimalizace s asistencí profilu.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** - *žádný>\<*

  - **UseLinkTimeCodeGeneration** - **/LTCG**

  - **PGInstrument** - **/LTCG:PGInstrument**

  - **PGOptimization** - **/LTCG:PGOptimize**

  - **PgUpdate**

    \-**/LTCG:PGUpdate**

  Další informace naleznete v tématu [/LTCG (Generování kódu v době propojení).](/cpp/build/reference/ltcg-link-time-code-generation)

- **Soubor manifestu**

  Volitelný **parametr String.**

  Změní výchozí název souboru manifestu na zadaný název souboru.

  Další informace naleznete v tématu [/MANIFESTFILE (Název manifestu souboru)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapVývoz**

  Volitelný **logický** parametr.

  Pokud `true`aplikace napomene, aby do souboru mapy zahrnul exportované funkce.

  Další informace naleznete `EXPORTS` v argumentu [/MAPINFO (Zahrnout informace do souboru mapy).](/cpp/build/reference/mapinfo-include-information-in-mapfile)

- **Název mapového souboru**

  Volitelný **parametr String.**

  Změní výchozí název mapového souboru na zadaný název souboru.

- **MergediDLBaseNázevsouboru**

  Volitelný **parametr String.**

  Určuje název souboru a příponu názvu souboru *IDL.*

  Další informace naleznete v tématu [/IDLOUT (Název výstupních souborů MIDL).](/cpp/build/reference/idlout-name-midl-output-files)

- **Sloučit oddíly**

  Volitelný **parametr String.**

  Kombinuje oddíly v obraze. Zadejte `from-section=to-section`.

  Další informace naleznete v tématu [/MERGE (Kombinovat oddíly)](/cpp/build/reference/merge-combine-sections).

- **Soubor MidlCommandFile**

  Volitelný **parametr String.**

  Zadejte název souboru, který obsahuje volby příkazového řádku MIDL.

  Další informace naleznete v tématu [/MIDL (Zadejte volby příkazového řádku MIDL).](/cpp/build/reference/midl-specify-midl-command-line-options)

- **Minimální požadovaná verze**

  Volitelný **parametr String.**

  Určuje minimální požadovanou verzi subsystému. Argumenty jsou desetinná čísla v rozsahu 0 až 65535.

- **ModuleDefinitionFile**

  Volitelný **parametr String.**

  Určuje název [definičního souboru modulu](/cpp/build/reference/module-definition-dot-def-files).

  Další informace naleznete v tématu [/DEF (Specify module-definition file).](/cpp/build/reference/def-specify-module-definition-file)

- **Název souboru MSDOSStubFileName**

  Volitelný **parametr String.**

  Připojí zadaný program se zakázaným inzerováním ms-DOS k programu Win32.

  Další informace naleznete v tématu [/STUB (název souboru se zakázaným inzerováním systému MS-DOS).](/cpp/build/reference/stub-ms-dos-stub-file-name)

- **NoEntryPoint**

  Volitelný **logický** parametr.

  Pokud `true`určuje dll pouze pro prostředky.

  Další informace naleznete v tématu [/NOENTRY (Žádný vstupní bod)](/cpp/build/reference/noentry-no-entry-point).

- **Objektové soubory**

  Implicitní **parametr String[].**

  Určuje soubory objektů, které jsou propojeny.

- **OptimizeReferences**

  Volitelný **logický** parametr.

  Pokud `true`, eliminuje funkce a/nebo data, která nejsou nikdy odkazována.

  Další informace naleznete `REF` v argumentu [/OPT (Optimalizace)](/cpp/build/reference/opt-optimizations).

- **Výstupní soubor**

  Volitelný **parametr String.**

  Přepíše výchozí název a umístění programu, který propojovací program vytvoří.

  Další informace naleznete v tématu [/OUT (Název výstupního souboru).](/cpp/build/reference/out-output-file-name)

- **PerUserRedirection**

  Volitelný **logický** parametr.

  Pokud `true` je povolena funkce Registrovat výstup, vynutí, **aby** HKEY_CLASSES_ROOT zápisy registru byly přesměrovány na **HKEY_CURRENT_USER**.

- **Předprocesvýstup**

  Volitelný `ITaskItem[]` parametr.

  Definuje pole výstupních položek preprocesoru, které mohou být spotřebovány a vydávány úkoly.

- **PreventDllBinding**

  Volitelný **logický** parametr.

  Pokud `true`, označuje *Bind.exe,* že propojený obrázek by neměl být vázán.

  Další informace naleznete v tématu [/ALLOWBIND (Prevent DLL binding).](/cpp/build/reference/allowbind-prevent-dll-binding)

- **Profil**

  Volitelný **logický** parametr.

  Pokud `true`vytvoří výstupní soubor, který lze použít s profilerem **Nástroje výkonu.**

  Další informace naleznete v tématu [/PROFILE (Performance Tools profiler)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabáze**

  Volitelný **parametr String.**

  Určuje název souboru *PGD,* který bude použit k uložení informací o spuštěném programu.

  Další informace naleznete v tématu [/PGD (Zadat databázi pro optimalizace s asistencí profilu)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  Volitelný **parametr String.**

  Určuje název databáze programu (PDB), který vytvoří propojovací program.

  Další informace naleznete v tématu [/PDB (Use program database)](/cpp/build/reference/pdb-use-program-database).

- **Randomizovanázákladní adresa**

  Volitelný **logický** parametr.

  Pokud `true`aplikace vygeneruje spustitelný obrázek, který lze náhodně přepojit v době načítání pomocí funkce *aslr (randomization) rozložení adresního prostoru* (ASLR).

  Další informace naleznete v tématu [/DYNAMICBASE (Použití randomizace rozložení adresního prostoru).](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization)

- **RegisterOutput**

  Volitelný **logický** parametr.

  Pokud `true`, registruje primární výstup tohoto sestavení.

- **SectionAlignment**

  Volitelný **čtyřčíselné** číslo.

  Určuje zarovnání jednotlivých oddílů v rámci lineárního adresního prostoru programu. Hodnota parametru je počet bajtů jednotky a je mocninu dvou.

  Další informace naleznete v tématu [/ALIGN (zarovnání řezu).](/cpp/build/reference/align-section-alignment)

- **SetChecksum**

  Volitelný **logický** parametr.

  Pokud `true`nastaví kontrolní součet v záhlaví souboru *EXE.*

  Další informace naleznete v tématu [/RELEASE (Set the checksum).](/cpp/build/reference/release-set-the-checksum)

- **Zobrazit průběh**

  Volitelný **parametr String.**

  Určuje podrobnost sestav průběhu pro operaci propojení.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NotNastavit žádný** - >*\<*

  - **LinkVerbose** - **/VERBOSE**

  - **LinkVerboseLib** - **/VERBOSE:Lib**

  - **LinkVerboseICF** - **/VERBOSE:ICF**

  - **LinkVerboseREF** - **/VERBOSE:ODKAZ**

  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR** - **/VERBOSE:CLR**

  Další informace naleznete v tématu [/VERBOSE (Tisk zpráv průběhu)](/cpp/build/reference/verbose-print-progress-messages).

- **Zdrojů**

  Požadovaný parametr `ITaskItem[]`.

  Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a vydávány úkoly.

- **Zadat atributy oddílu**

  Volitelný **parametr String.**

  Určuje atributy oddílu. Tím se přepíší atributy, které byly nastaveny při kompilaci souboru *OBJ* pro oddíl.

  Další informace naleznete v tématu [/SECTION (Zadejte atributy oddílu).](/cpp/build/reference/section-specify-section-attributes)

- **StackCommitSize**

  Volitelný **parametr String.**

  Určuje velikost fyzické paměti v každém přidělení při přidělení další paměti.

  Další informace naleznete `commit` v argumentu [/STACK (Stack allocations)](/cpp/build/reference/stack-stack-allocations).

- **StackReserveSize**

  Volitelný **parametr String.**

  Určuje celkovou velikost přidělení zásobníku ve virtuální paměti.

  Další informace naleznete `reserve` v argumentu [/STACK (Stack allocations)](/cpp/build/reference/stack-stack-allocations).

- **Stripsoukromé symboly**

  Volitelný **parametr String.**

  Vytvoří soubor druhé programové databáze (PDB), který vynese symboly, které nechcete distribuovat zákazníkům. Zadejte název druhého souboru PDB.

  Další informace naleznete v tématu [/PDBSTRIPPED (Strip soukromé symboly).](/cpp/build/reference/pdbstripped-strip-private-symbols)

- **Subsystému**

  Volitelný **parametr String.**

  Určuje prostředí pro spustitelný soubor.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NotNastavit žádný** - >*\<*

  - **Konzola** - **/SUBSYSTÉM:KONZOLA**

  - **Windows** - **/SUBSYSTÉM:WINDOWS**

  - **Nativní** - **/SUBSYSTEM:NATIVNÍ**

  - **Aplikace EFI** - **/SUBSYSTÉM:EFI_APPLICATION**

  - **Ovladač spouštěcí služby EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM** - **/SUBSYSTÉM:EFI_ROM**

  - **EFI Runtime** - **/SUBSYSTÉM:EFI_RUNTIME_DRIVER**

  - **WindowsCE** - **/SUBSYSTÉM:WINDOWSCE**

  - **POSIX** - **/SUBSYSTÉM:POSIX**

  Další informace naleznete v tématu [/SUBSYSTEM (Specify subsystem)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL LL**

  Volitelný **logický** parametr.

  Pokud `true`aplikace navazující zařízení sděluje, aby do konečné bitové kopie nezahrnul tabulku adres importu (IAT) s hotelnou vazbou.

  Další informace naleznete `NOBIND` v argumentu [/DELAY (Nastavení importu zpoždění načítání)](/cpp/build/reference/delay-delay-load-import-settings).

- **SupportUnloadOfDelayLoadedDLL**

  Volitelný **logický** parametr.

  Pokud `true`, sděluje pomocné funkce zpoždění zatížení pro podporu explicitního uvolnění dll.

  Další informace naleznete `UNLOAD` v argumentu [/DELAY (Nastavení importu zpoždění načítání)](/cpp/build/reference/delay-delay-load-import-settings).

- **PotlačitStartupBanner**

  Volitelný **logický** parametr.

  Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.

  Další informace naleznete v tématu [/NOLOGO (Suppress startup banner) (linker)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  Volitelný **logický** parametr.

  Pokud `true`aplikace nařídí operačnímu systému, aby nejprve zkopíroval výstup linkeru do odkládacího souboru a potom obraz spusťte.

  Další informace naleznete `CD` v argumentu [/SWAPRUN (Load linker výstup pro odkládací soubor)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Viz také **Parametr SwapRunFromNET.**

- **SwapRunFromNET**

  Volitelný **logický** parametr.

  Pokud `true`aplikace nařídí operačnímu systému, aby nejprve zkopíroval výstup linkeru do odkládacího souboru a potom obraz spusťte.

  Další informace naleznete `NET` v argumentu [/SWAPRUN (Load linker výstup pro odkládací soubor)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Viz také **Parametr SwapRunFromCD** v této tabulce.

- **TargetMachine**

  Volitelný **parametr String.**

  Určuje cílovou platformu pro program nebo dll.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NotNastavit žádný** - >*\<*

  - **MachineARM** - **/ STROJ: ARM**

  - **MachineEBC** - **/STROJ:EBC**

  - **MachineIA64** - **/STROJ:IA64**

  - **MachineMIPS** - **/STROJ:MIPS**

  - **MachineMIPS16** - **/STROJ:MIPS16**

  - **MachineMIPSFPU** - **/STROJ:MIPSFPU**

  - **MachineMIPSFPU16** - **/STROJ:MIPSFPU16**

  - **StrojSH4** - **/STROJ:SH4**

  - **MachineTHUMB** - **/ STROJ: PALEC**

  - **StrojX64** - **/STROJ:X64**

  - **StrojX86** - **/STROJ:X86**

  Další informace naleznete v tématu [/MACHINE (Zadat cílovou platformu).](/cpp/build/reference/machine-specify-target-platform)

- **TerminalServerAware**

  Volitelný **logický** parametr.

  Pokud `true`nastaví příznak v poli IMAGE_OPTIONAL_HEADER DllCharacteristics ve volitelné masce obrázku programu. Je-li tento příznak nastaven, terminálový server neprovede určité změny v aplikaci.

  Další informace naleznete v tématu [/TSAWARE (Create Terminal Server aware application)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  Volitelný **parametr String.**

  Určuje adresář protokolu sledování.

- **Chyby Upozornění na linker**

  Volitelný **logický** parametr.

  Pokud `true`, způsobí, že žádný výstupní soubor, který má být generován, pokud propojovací systém generuje upozornění.

  Další informace naleznete v tématu [/WX (Považovat upozornění linkeru za chyby).](/cpp/build/reference/wx-treat-linker-warnings-as-errors)

- **TurnoffAssemblyGeneration**

  Volitelný **logický** parametr.

  Pokud `true`vytvoří obraz pro aktuální výstupní soubor bez sestavení rozhraní .NET Framework.

  Další informace naleznete v tématu [/NOASSEMBLY (Create a MSIL module)](/cpp/build/reference/noassembly-create-a-msil-module).

- **Soubor TypeLibraryFile**

  Volitelný **parametr String.**

  Určuje název souboru a příponu názvu souboru *TLB.* Zadejte název souboru nebo cestu a název souboru.

  Další informace naleznete v tématu [/TLBOUT (Název souboru TLB).](/cpp/build/reference/tlbout-name-dot-tlb-file)

- **ID resourceiknihovny typeLibrary**

  Volitelný **čtyřčíselné** číslo.

  Určuje uživatelsky zadanou hodnotu pro knihovnu typů vytvořenou linkerem. Zadejte hodnotu od 1 do 65535.

  Další informace naleznete v tématu [/TLBID (Zadejte ID prostředku pro TypeLib)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **Úroveň uacpopravy**

  Volitelný **parametr String.**

  Určuje požadovanou úroveň spuštění aplikace při spuštění pod pomocí řízení uživatelských účtů.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Asinvoker** - `level='asInvoker'`

  - **NejvyššíK dispozici** - `level='highestAvailable'`

  - **Vyžadovatsprávce** - `level='requireAdministrator'`

  Další informace naleznete `level` v argumentu [/MANIFESTUAC (Embeds UAC informace v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **Přístup UACUIAccess**

  Volitelný **logický** parametr.

  Pokud `true`aplikace obchází úrovně ochrany uživatelského rozhraní a předává vstup do oken s vyšším oprávněním na ploše; v `false`opačném případě .

  Další informace naleznete `uiAccess` v argumentu [/MANIFESTUAC (Embeds UAC informace v manifestu)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UseLibraryDependencyInputs**

  Volitelný **logický** parametr.

  Pokud `true`se vstupy knihovníkového nástroje používají, nikoli samotný soubor knihovny, když jsou propojeny výstupy knihovny závislostí projektu.

- **Verze**

  Volitelný **parametr String.**

  Do záhlaví souboru *EXE* nebo *DLL* vložte číslo verze. Zadejte`major[.minor]`" ". A `major` `minor` argumenty jsou desetinná čísla od 0 do 65535.

  Další informace naleznete v tématu [/VERSION (Version information)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
