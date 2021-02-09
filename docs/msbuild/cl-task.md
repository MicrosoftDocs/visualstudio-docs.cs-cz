---
title: CL – úloha | Microsoft Docs
description: Popisuje účel a parametry úlohy MSBuild CL, která zabalí nástroj kompilátoru Microsoft C++ cl.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542d84f4c0279c1f76fa1ea29a244e78c53b394d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878432"
---
# <a name="cl-task"></a>CL – úloha

Zabalí nástroj kompilátoru Microsoft C++, *cl.exe*. Kompilátor vytváří spustitelné soubory (*. exe*), soubory dynamické knihovny (*. dll*) nebo soubory modulu kódu (*. netmodule*). Další informace naleznete v tématu [Možnosti kompilátoru](/cpp/build/reference/compiler-options) a [použití nástroje MSBuild z příkazového řádku](/cpp/build/msbuild-visual-cpp) a [použití sady nástrojů Microsoft C++ z příkazového řádku](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametry

 Následující seznam popisuje parametry úlohy **CL** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.

- **AdditionalIncludeDirectories**

   Parametr volitelného řetězce [].

   Přidá adresář do seznamu adresářů, ve kterých jsou vyhledávány soubory k zahrnutí.

   Další informace najdete v tématu [/i (další adresáře k zahrnutí)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   Volitelný řetězcový parametr.

   Seznam možností příkazového řádku Například "/ \<option1>  / \<option2>  / \<option#> ". Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy.

   Další informace naleznete v tématu [Možnosti kompilátoru](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Parametr volitelného řetězce [].

   Určuje adresář, který kompilátor bude hledat k překladu odkazů na soubory předaných do direktivy **#using** .

   Další informace najdete v tématu [/AI (určení adresářů metadat)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Volitelný řetězcový parametr.

   Řetězec, který je vždy generován na příkazovém řádku. Výchozí hodnota je "**/c**".

- **AssemblerListingLocation**

   Vytvoří soubor výpisu, který obsahuje kód sestavení.

   Další informace naleznete v možnosti **/Fa** v [/FA,/FA (soubor výpisu)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Volitelný řetězcový parametr.

   Vytvoří soubor výpisu, který obsahuje kód sestavení.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Seznam není** - *\<none>*

  - **AssemblyCode**  -  **/FA**

  - **AssemblyAndMachineCode**  -  **/FAc**

  - **AssemblyAndSourceCode**  -  **/FAS**

  - **Vše**  -  **/FAcs**

    Další informace najdete v tématu možnosti **/Fa**, **/FAc**, **/FAS** a **/FAcs** v [/FA,/FA (soubor výpisu)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Volitelný řetězcový parametr.

   Povolí nebo zakáže funkci kontroly chyb za běhu ve spojení s direktivou pragma [runtime_checks](/cpp/preprocessor/runtime-checks) .

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTCs**

  - **UninitializedLocalUsageCheck**  -  **/RTCu**

  - **EnableFastChecks**  -                           **/RTC1**

    Další informace naleznete v tématu [/RTC (kontrola chyb za běhu)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Volitelný logický parametr.

   Pokud `true` se vytvoří soubor s informacemi o procházení.

   Další informace naleznete v možnosti **/fr** v [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Volitelný řetězcový parametr.

   Určuje název souboru s informacemi o procházení.

   Další informace naleznete v parametru **BrowseInformation** v této tabulce a také v tématu [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   Volitelný logický parametr.

   Pokud `true` aplikace zjistí některé přetečení vyrovnávací paměti, které přepíší zpáteční adresu, jedná se o běžnou techniku pro zneužití kódu, který nevynutil omezení velikosti vyrovnávací paměti.

   Další informace najdete v tématu [/GS (kontrolní zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   Volitelný logický parametr.

   Pokud `true` , označuje, že nástroj **MSBuild** je vyvolán rozhraním IDE. V opačném případě je nástroj **MSBuild** vyvolán na příkazovém řádku.

- **CallingConvention**

   Volitelný řetězcový parametr.

   Určuje konvenci volání, která určuje pořadí, ve kterém jsou argumenty funkce vloženy do zásobníku, zda volající funkce nebo volaná funkce odebere argumenty ze zásobníku na konci volání a konvenci názvu-upravení, kterou kompilátor používá k identifikaci jednotlivých funkcí.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **CDECL**  -  **/GD**

  - **FastCall**  -                           **/Gr**

  - **STDCALL**  -                           **/GZ**

    Další informace naleznete v tématu [/GD,/GR,/GV,/GZ (konvence volání)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Volitelný řetězcový parametr.

   Určuje, zda má být vstupní soubor kompilován jako zdrojový soubor jazyka C nebo C++.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** - *\<none>*

  - **CompileAsC**  -  **/TC**

  - **CompileAsCpp**  -  **/TP**

    Další informace naleznete v tématu [/TC,/TP,/TC,/TP (určení typu zdrojového souboru)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Volitelný řetězcový parametr.

   Umožňuje aplikacím a komponentám používat funkce z modulu CLR (Common Language Runtime).

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **chybné** - *\<none>*

  - **hodnota true**  -  **/CLR**

  - **Čistý**  -  **/clr: Pure**

  - **Bezpečná**  -  **/clr: Safe**

  - **OldSyntax**  -  **/clr: oldSyntax**

    Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Volitelný logický parametr.

   Pokud `true` aplikace, instruuje kompilátor, aby připravil obrázek pro *Hot patching*. Tento parametr zajišťuje, že první instrukce každé funkce jsou dvě bajty, které jsou požadovány pro Hot patching.

   Další informace najdete v tématu [/hotpatch (Create opravitelnou za provozu image)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Volitelný řetězcový parametr.

   Vybere typ ladicích informací vytvořených pro program a zda jsou tyto informace uloženy v souborech objektů (*. obj*) nebo v databázi programu (PDB).

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **OldStyle**  -  **/Z7**

  - **ProgramDatabase**  -  **/Zi**

  - **EditAndContinue**  -  **/Zi**

    Další informace naleznete v tématu [/Z7,/Zi,/Zi (formát ladicích informací)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Volitelný logický parametr.

   Pokud je **true**, instruuje kompilátor, aby vygeneroval chybu pro jazykové konstrukce, které nejsou kompatibilní se standardem ANSI C nebo ANSI C++.

   Další informace najdete v možnosti **/za** v [/za,/ze (zakázání jazykových rozšíření)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Parametr volitelného řetězce [].

   Zakáže čísla upozornění, která jsou uvedena v seznamu středníkem oddělených.

   Další informace najdete `/wd` v tématu možnost v příkazech [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Volitelný řetězcový parametr.

   Určuje architekturu pro generování kódu, která používá instrukce Streaming SIMD Extensions (SSE) a Streaming SIMD Extensions 2 (SSE2).

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **StreamingSIMDExtensions**  -  **/arch: SSE**

  - **StreamingSIMDExtensions2**  -  **/arch: SSE2**

    Další informace najdete v tématu [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Volitelný logický parametr.

   Pokud `true` podporuje bezpečnost vlákna pro data přidělená pomocí statického úložiště místního vlákna, to znamená data přidělená pomocí `__declspec(thread)` .

   Další informace najdete v tématu [/gt (podpora místního úložiště s vlákny pro vlákno)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Volitelný logický parametr.

   Pokud chcete `true` Povolit analýzu kódu.

   Další informace naleznete v tématu [/analyze (analýza kódu)](/cpp/build/reference/analyze-code-analysis).

- **ErrorReporting**

   Volitelný řetězcový parametr.

   Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo společnosti Microsoft. Ve výchozím nastavení je nastavení v rozhraní IDE **vyzváné** a nastavení v sestavení příkazového řádku je **Queue**.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Žádné**  -  **/errorreport: none**

  - **Zobrazit výzvu**  -  **/errorreport: prompt**

  - **Fronta**  -  **/errorreport: Queue**

  - **Odeslat**  -  **/errorreport: Send**

    Další informace najdete v tématu [/errorreport (hlášení chyb interních kompilátorů)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Volitelný řetězcový parametr.

   Určuje model zpracování výjimek, který má kompilátor použít.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **chybné** - *\<none>*

  - **Asynchronní**  -  operace **/EHa**

  - **Synchronizovat**  -  **/EHsc**

  - **SyncCThrow**  -  **/EHS**

    Další informace naleznete v tématu [/EH (model zpracování výjimek)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Volitelný logický parametr.

   Pokud `true` , vytvoří soubor výpisu s rozbalenými atributy vloženými do zdrojového souboru.

   Další informace najdete v tématu [/FX (sloučení vloženého kódu)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Volitelný řetězcový parametr.

   Určuje, zda má být upřednostněna velikost kódu nebo rychlost kódu.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Ani** - *\<none>*

  - **Velikost**  -  **/OS**

  - **Rychlost**  -  **/Ot**

    Další informace najdete v tématu [/OS,/ot (upřednostnění malého kódu, upřednostnění rychlého kódu)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Volitelný logický parametr.

   `true`V případě, umožňuje spolehlivý model výjimek s plovoucí desetinnou čárkou. Výjimky budou vyvolány okamžitě po aktivaci.

   Další informace naleznete v tématu/**FP: except** – možnost v [/FP (určení chování s plovoucí](/cpp/build/reference/fp-specify-floating-point-behavior)desetinnou čárkou).

- **FloatingPointModel**

   Volitelný řetězcový parametr.

   Nastaví model plovoucí desetinné čárky.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Přesná**  -  **/FP: přesný**

  - **Striktní**  -  **/FP: Strict**

  - **Rychlé**  -  **/FP: Fast**

    Další informace najdete v tématu [/FP (určení chování s plovoucí](/cpp/build/reference/fp-specify-floating-point-behavior)desetinnou čárkou).

- **ForceConformanceInForLoopScope**

   Volitelný logický parametr.

   Pokud `true` , implementuje standardní chování C++ v [pro](/cpp/cpp/for-statement-cpp) smyčky, které používají rozšíření Microsoft Extensions ([/ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Další informace najdete v tématu [/Zc: forScope (vynucení shody v oboru for Loop)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Volitelný `String[]` parametr.

   Způsobí, že preprocesor zpracuje jeden nebo více zadaných souborů hlaviček.

   Další informace najdete v tématu [/Fi (soubor s vynuceným zahrnutím názvu)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Parametr volitelného **řetězce []** .

   Způsobí, že preprocesor zpracuje jeden nebo více zadaných **#using** souborů.

   Další informace najdete v tématu [/Fu (název vynuceného #using souboru)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Volitelný `Boolean` parametr.

   Pokud `true` , umožňuje kompilátoru zabalit jednotlivé funkce ve formě zabalených funkcí (sekvence COMDAT).

   Další informace najdete v tématu [/Gy (povolení propojení na úrovni funkcí)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Volitelný `Boolean` parametr.

   Pokud `true` Nástroj způsobí, že kompilátor zpracuje dokumentační komentáře v souborech zdrojového kódu a vytvoří soubor *. xdc* pro každý soubor zdrojového kódu, který obsahuje dokumentační komentáře.

   Další informace naleznete v tématu [/doc (zpracování dokumentačních komentářů) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). V této tabulce se také zobrazí parametr **XMLDocumentationFileName** .

- **IgnoreStandardIncludePath**

   Volitelný `Boolean` parametr.

   Pokud `true` , zabrání kompilátoru v hledání souborů include v adresářích zadaných v cestě a proměnných prostředí include.

   Další informace naleznete v části [/x (ignorování standardních cest zahrnutí)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Volitelný **řetězcový** parametr.

   Určuje úroveň rozšíření vložené funkce pro sestavení.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** - *\<none>*

  - **Zakázáno**  -  **/Ob0**

  - **OnlyExplicitInline**  -  **/OB1**

  - **AnySuitable**  -  **/Ob2**

    Další informace naleznete v tématu [/ob (rozšíření vložené funkce)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Volitelný `Boolean` parametr.

   Pokud `true` , nahradí některá volání funkce vnitřními nebo jinak speciálními formami funkce, které pomůžou aplikaci rychleji běžet.

   Další informace najdete v tématu [/Oi (generování vnitřních funkcí)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Volitelný `Boolean` parametr.

   Pokud `true` , umožňuje minimální opětovné sestavení, které určuje, zda je nutné znovu zkompilovat zdrojové soubory jazyka c++, které obsahují změněné definice tříd c++ (uložené v hlavičkových souborech (. h)).

   Další informace najdete v tématu [/GM (povolení minimálního opětovného sestavení)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   Volitelný `Boolean` parametr.

   Pokud `true` chcete kompilovat více procesorů, použijte. Tento parametr vytvoří proces pro každý efektivní procesor v počítači.

   Další informace naleznete v tématu [/MP (sestavení s více procesy)](/cpp/build/reference/mp-build-with-multiple-processes). Viz také parametr **ProcessorNumber** v této tabulce.

- **ObjectFileName**

   Volitelný **řetězcový** parametr.

   Určuje název souboru objektu (. obj) nebo adresář, který má být použit místo výchozí.

   Další informace naleznete v tématu [/FO (název souboru objektu)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Parametr volitelného **řetězce []** .

   Seznam souborů objektů.

- **OmitDefaultLibName**

   Volitelný `Boolean` parametr.

   Pokud `true` , vynechá výchozí název běhové knihovny jazyka C ze souboru objektu (*. obj*). Ve výchozím nastavení kompilátor umístí do souboru *. obj* název knihovny a nasměruje linker do správné knihovny.

   Další informace najdete v tématu [/zl (vynechání názvu výchozí knihovny)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Volitelný `Boolean` parametr.

   Pokud `true` , potlačí vytváření ukazatelů rámců v zásobníku volání.

   Další informace naleznete v tématu [/Oy (vynechání ukazatele na rámec)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Volitelný `Boolean` parametr.

   Pokud `true` Nástroj způsobí, že kompilátor zpracuje klauzule a direktivy OpenMP.

   Další informace najdete v tématu [/OpenMP (povolení podpory openmp 2,0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optimalizace**

   Volitelný **řetězcový** parametr.

   Určuje různé optimalizace kódu pro rychlost a velikost.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Zakázáno**  -  **/Od**

  - **MinSpace**  -  **/O1**

  - **MaxSpeed**  -  **/O2**

  - **Úplný**  -  **/Ox**

    Další informace najdete v tématu [Možnosti/o (optimalizace kódu)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Volitelný **řetězcový** parametr.

   Během sestavování vytvořte nebo použijte soubor předkompilované hlavičky (*. pch*).

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NotUsing** - *\<none>*

  - **Vytvořit**  -  **/YC**

  - **Použití**  -  **/Yu**

    Další informace naleznete v tématu [/Yc (Create a Compiled hlavičkový soubor)](/cpp/build/reference/yc-create-precompiled-header-file) a [/Yu (použít předkompilovaný hlavičkový soubor)](/cpp/build/reference/yu-use-precompiled-header-file). Podívejte se také na parametry **PrecompiledHeaderFile** a **PrecompiledHeaderOutputFile** v této tabulce.

- **PrecompiledHeaderFile**

   Volitelný **řetězcový** parametr.

   Určuje název souboru předkompilované hlavičky, který se má vytvořit nebo použít.

   Další informace naleznete v tématu [/Yc (Create a Compiled hlavičkový soubor)](/cpp/build/reference/yc-create-precompiled-header-file) a [/Yu (použít předkompilovaný hlavičkový soubor)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   Volitelný **řetězcový** parametr.

   Určuje název cesty pro předkompilovanou hlavičku namísto použití výchozího názvu cesty.

   Další informace naleznete v tématu [/FP (pojmenování souboru. pch)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   Volitelný `Boolean` parametr.

   Pokud `true` aplikace zachová komentáře během předběžného zpracování.

   Další informace najdete v tématu [/c (zachování komentářů během předběžného zpracování)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Volitelný `String[]` parametr.

   Definuje symbol předzpracování pro zdrojový soubor.

   Další informace naleznete v tématu [/d (Definice preprocesoru)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Volitelný `ITaskItem[]` parametr.

   Definuje pole výstupních položek preprocesoru, které mohou být spotřebovány a generovány úlohami.

- **PreprocessOutputPath**

   Volitelný `String` parametr.

   Určuje název výstupního souboru, do kterého parametr **PreprocessToFile** zapisuje předzpracovaný výstup.

   Další informace naleznete v tématu [/Fi (předběžné zpracování názvu výstupního souboru)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Volitelný `Boolean` parametr.

   Pokud `true` , předzpracovává zdrojové soubory C a C++ a kopíruje soubory předzpracovaného na standardní výstupní zařízení.

   Další informace naleznete v tématu [/EP (předzpracování do stdout bez #line direktiv)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Volitelný `Boolean` parametr.

   Pokud `true` , předzpracovává zdrojové soubory C a C++ a zapisuje předzpracovaný výstup do souboru.

   Další informace naleznete v tématu [/p (předběžné zpracování souboru)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Volitelný `Integer` parametr.

   Určuje maximální počet procesorů, které se mají použít při kompilaci ve více procesorech. Tento parametr použijte v kombinaci s parametrem **MultiProcessorCompilation** .

- **ProgramDataBaseFileName**

   Volitelný `String` parametr.

   Určuje název souboru pro soubor databáze programu (PDB).

   Další informace najdete v tématu [/FD (název souboru databáze programu)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Volitelný `String` parametr.

   Označuje, zda je vícevláknový modul knihovnou DLL, a vybere prodejní nebo ladicí verze knihovny run-time.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Vícevláknové**  -  **/Mt**

  - **MultiThreadedDebug**  -  **/MTD**

  - **MultiThreadedDLL**  -  **/MD**

  - **MultiThreadedDebugDLL**  -  **/MDD**

    Další informace naleznete v tématu [/MD,/MT,/LD (použití běhové knihovny)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Volitelný `Boolean` parametr.

   Pokud `true` , přidá kód pro kontrolu typů objektů jazyka C++ za běhu (informace o typu za běhu).

   Další informace najdete v tématu [/gr (povolení informací o běhovém typu)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes –**

   Volitelný `Boolean` parametr.

   Pokud `true` dojde k tomu, vyvolá kompilátor výstup seznamu souborů k zahrnutí.

   Další informace najdete v tématu [/showIncludes (seznam vložených souborů)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Volitelný `Boolean` parametr.

   `true`V případě, že hlásí chybu za běhu, pokud je přiřazena hodnota k menšímu datovému typu a způsobuje ztrátu dat.

   Další informace naleznete v možnosti **/RTCc** v [/RTC (kontrola chyb za běhu)](/cpp/build/reference/rtc-run-time-error-checks).

- **zdroje**

   Požadovaný parametr `ITaskItem[]`.

   Určuje seznam zdrojových souborů oddělených mezerami.

- **StringPooling**

   Volitelný `Boolean` parametr.

   Pokud `true` , umožňuje kompilátoru vytvořit jednu kopii stejných řetězců v imagi programu.

   Další informace najdete v tématu [/GF (odstranění duplicitních řetězců)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Volitelný `String` parametr.

   Určuje zarovnání bajtů pro všechny členy ve struktuře.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí nastavení**  -  **/Zp1**

  - **1Byte**  -  **/Zp1**

  - **2Bytes**  -  **/Zp2**

  - **4Bytes**  -  **/Zp4**

  - **8bytes**  -  **/ZP8**

  - **16Bytes**  -  **/Zp16**

    Další informace naleznete v tématu [/zp (zarovnání členů struktury)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Volitelný `Boolean` parametr.

   Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.

   Další informace naleznete v tématu [/nologo (potlačení úvodního nápisu při spouštění) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   Volitelný `String` parametr.

   Určuje zprostředkující adresář, ve kterém jsou uložené protokoly sledování pro tento úkol.

   Další informace najdete v tématu parametry **TLogReadFiles** a **TLogWriteFiles** v této tabulce.

- **TreatSpecificWarningsAsErrors**

   Parametr volitelného **řetězce []** .

   Zachází s zadaným seznamem upozornění kompilátoru jako s chybami.

   Další informace najdete v tématu možnost **/We** `n` v [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Volitelný `Boolean` parametr.

   Pokud `true` , považovat všechna upozornění kompilátoru za chyby.

   Další informace najdete v tématu **/WX** Option v [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Volitelný `Boolean` parametr.

   Pokud `true` je typ považován za `wchar_t` nativní typ.

   Další informace naleznete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Volitelný `Boolean` parametr.

   Pokud `true` , zruší definici symbolů specifických pro společnost Microsoft, které definuje kompilátor.

   Další informace naleznete v možnosti **/u** v části [/u,/u (nedefinované symboly)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Volitelný `String[]` parametr.

   Určuje seznam jednoho nebo více symbolů preprocesoru, které mají být nedefinovány.

   Další informace naleznete v části **/u** Option v [/u,/u (nedefinované symboly)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Volitelný `Boolean` parametr.

   Pokud `true` , zobrazí úplnou cestu souborů se zdrojovým kódem předaných kompilátoru v diagnostice.

   Další informace naleznete v tématu [/FC (úplná cesta k souboru zdrojového kódu v diagnostice)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Volitelný `Boolean` parametr.

   Pokud `true` Nástroj způsobí, že se výstupní soubor vytvoří ve formátu UTF-8.

   Další informace naleznete v možnosti **/FAU** v [/FA,/FA (soubor výpisu)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Volitelný `String` parametr.

   Určuje nejvyšší úroveň upozornění, které má kompilátor generovat.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **TurnOffAllWarnings**  -  **/W0**

  - **Level1**  -  **/W1**

  - **Level2**  -  **/W2**

  - **Level3**  -  **/W3**

  - **Level4**  -  **/W4**

  - **Povolit všechna upozornění**  -  **/Wall**

    Další informace naleznete v části **/w**_n_ v příkazu [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Volitelný `Boolean` parametr.

   Pokud `true` , povolí optimalizaci celého programu.

   Další informace naleznete v tématu [/GL (celá optimalizace programu)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Volitelný `String` parametr.

   Určuje název generovaných souborů dokumentace XML. Tento parametr může být název souboru nebo adresáře.

   Další informace naleznete `name` v argumentu v [/doc (Process dokumentačních komentářů) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). V této tabulce se také zobrazí parametr **GenerateXMLDocumentationFiles** .

- **MinimalRebuildFromTracking**

   Volitelný `Boolean` parametr.

   Je-li `true` provedeno sledované přírůstkové sestavení, je-li `false` provedeno opětovné sestavení.

- **TLogReadFiles**

   Volitelný `ITaskItem[]` parametr.

   Určuje pole položek, které reprezentují *protokoly sledování čtecího souboru*.

   Protokol sledování souboru Readme (*. tlog*) obsahuje názvy vstupních souborů, které jsou čteny úlohou a které používá systém sestavení projektu pro podporu přírůstkových sestavení. Další informace najdete v tématu parametry **TrackerLogDirectory** a **TrackFileAccess** v této tabulce.

- **TLogWriteFiles**

   Volitelný `ITaskItem[]` parametr.

   Určuje pole položek, které reprezentují *protokoly sledování souborů*.

   Protokol sledování zápisu souboru (*. tlog*) obsahuje názvy výstupních souborů, které jsou zapsány úlohou a které používá systém sestavení projektu pro podporu přírůstkových sestavení. Další informace najdete v tématu parametry **TrackerLogDirectory** a **TrackFileAccess** v této tabulce.

- **TrackFileAccess**

   Volitelný `Boolean` parametr.

   Pokud `true` aplikace sleduje vzory přístupu k souborům.

   Další informace najdete v tématu parametry **TLogReadFiles** a **TLogWriteFiles** v této tabulce.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
