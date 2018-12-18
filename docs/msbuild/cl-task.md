---
title: Cl – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c239dc78d152e9060d176ebe1d4abd3b981a57d
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220362"
---
# <a name="cl-task"></a>CL – úloha
Zabalí nástroj kompilátoru Visual C++ *cl.exe*. Kompilátor vytvoří spustitelný soubor (*.exe*) soubory, dynamická knihovna (*.dll*) soubory nebo modul s kódem (*.netmodule*) soubory. Další informace najdete v tématu [– možnosti kompilátoru](/cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parametry  
 Následující seznam popisuje parametry **CL** úloh. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
- **AdditionalIncludeDirectories**  
  
   Volitelný parametr, řetězec [].  
  
   Přidá adresář do seznamu adresáře, které se budou hledat vkládané soubory.  
  
   Další informace najdete v tématu [/I (Další adresáře souborů k zahrnutí)](/cpp/build/reference/i-additional-include-directories).  
  
- **AdditionalOptions**  
  
   Volitelný parametr řetězce.  
  
   Seznam možností příkazového řádku. Například "/\<možnost1 > /\<možnost2 > /\<možnost #>". Tento parametr použijte k určení možnosti příkazového řádku, které nejsou reprezentovány všechny ostatní parametry úlohy.  
  
   Další informace najdete v tématu [– možnosti kompilátoru](/cpp/build/reference/compiler-options).  
  
- **AdditionalUsingDirectories**

   Volitelný parametr, řetězec [].  
  
   Určuje adresář, který kompilátor bude vyhledávání pro přeložení referencí souboru předaných **#using** směrnice.  
  
   Další informace najdete v tématu [/AI (zadat adresáře metadat)](/cpp/build/reference/ai-specify-metadata-directories).  
  
- **AlwaysAppend**  
  
   Volitelný parametr řetězce.  
  
   Řetězec, který vždy získá, protože ho v příkazovém řádku. Výchozí hodnota je "**/c**".  
  
- **AssemblerListingLocation**  
  
   Vytvoří soubor výpisu, který obsahuje kód sestavení.  
  
   Další informace najdete v tématu **/Fa** možnost [/FA, /Fa (soubor seznamu)](/cpp/build/reference/fa-fa-listing-file).  
  
- **AssemblerOutput**  
  
   Volitelný parametr řetězce.  
  
   Vytvoří soubor výpisu, který obsahuje kód sestavení.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NoListing** - *\<žádné >*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** -   **/FAC**  
  
  - **AssemblyAndSourceCode** -   **/FAS**  
  
  - **Všechny** -   **/facs**  
  
    Další informace najdete v tématu **/FA**, **/FAC**, **/FAS**, a **/facs** možnosti [/FA, /Fa (soubor seznamu)](/cpp/build/reference/fa-fa-listing-file).  
  
- **BasicRuntimeChecks**  
  
   Volitelný parametr řetězce.  
  
   Povolí nebo zakáže funkci kontroly chyb za běhu ve spojení s [runtime_checks –](/cpp/preprocessor/runtime-checks) direktivy pragma.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** -                          *\<žádné >*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **za**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Další informace najdete v tématu [/RTC (Kontrola chyb za běhu)](/cpp/build/reference/rtc-run-time-error-checks).  
  
- **BrowseInformation**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, vytvoří soubor informací o procházení.  
  
   Další informace najdete v tématu **/FR** možnost [/FR, /Fr (vytvořit soubor .sbr)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
- **BrowseInformationFile**  
  
   Volitelný parametr řetězce.  
  
   Určuje název souboru pro informačního souboru procházení.  
  
   Další informace najdete v tématu **BrowseInformation** parametr v této tabulce a také viz [/FR, /Fr (vytvořit soubor .sbr)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
- **BufferSecurityCheck**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, rozpozná některá přetečení vyrovnávací paměti, která přepisují návratovou adresu běžná technika pro využívání kódu, která nevynucuje omezení velikosti vyrovnávací paměti.  
  
   Další informace najdete v tématu [/GS (Kontrola zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check).  
  
- **BuildingInIDE**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, označuje, že **MSBuild** vyvolá rozhraní IDE. V opačném případě **MSBuild** vyvolat na příkazovém řádku.  
  
- **CallingConvention**  
  
   Volitelný parametr řetězce.  
  
   Určuje konvenci volání, která určuje pořadí, ve které funkce jsou argumenty vloženy do zásobníku, zda funkce volajícího nebo volaná funkce odstraní argumenty ze zásobníku volání na konci volání, a konvence dekorování, který kompilátor používá k identifikaci jednotlivých funkcí.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Cdecl** - **/Gd**  
  
  - **FastCall** -                          **GR**  
  
  - **StdCall** -                          **/Gz**  
  
    Další informace najdete v tématu [/Gd, / GR, / gv, /Gz (konvence volání)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
- **CompileAs**  
  
   Volitelný parametr řetězce.  
  
   Určuje, jestli se má kompilovat vstupní soubor jako zdrojový soubor jazyka C nebo C++.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - *\<žádné >*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Další informace najdete v tématu [/Tc /Tp, /TC, /TP (typu zdrojového souboru zadejte)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
- **CompileAsManaged**  
  
   Volitelný parametr řetězce.  
  
   Umožňuje aplikací a komponent, pokud chcete používat funkce z common language runtime (CLR).  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **false** - *\<žádné >*  
  
  - **Hodnota TRUE** -   **/CLR**  
  
  - **Čistě** -   **/CLR: pure**  
  
  - **Bezpečné** -   **/CLR: safe**  
  
  - **OldSyntax** - **oldSyntax**  
  
    Další informace najdete v tématu [/CLR (kompilace Common language runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
- **CreateHotpatchableImage**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, instruuje kompilátor, aby připravit bitovou kopii pro *technologii hot patching*. Tento parametr se zajistí, že první instrukce pro každou funkci je o dva bajty, které jsou požadovány pro technologii hot patching.  
  
   Další informace najdete v tématu [/hotpatch (vytvořit bitovou kopii opravitelnou za provozu)](/cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
- **DebugInformationFormat**  
  
   Volitelný parametr řetězce.  
  
   Vybere typ ladicích informací vytvářených pro program a zda tyto informace se ukládají v objektu (*.obj*) soubory nebo v programu v jazyce databáze (PDB).  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Minuskové** -   **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Další informace najdete v tématu [/Z7, / zi, /ZI (formát ladicích informací)](/cpp/build/reference/z7-zi-zi-debug-information-format).  
  
- **DisableLanguageExtensions**  
  
   Volitelný logický parametr.  
  
   Pokud **true**, informuje kompilátor generuje chybu pro konstruktory jazyka, které nejsou kompatibilní s ANSI C a ANSI C++.  
  
   Další informace najdete v tématu **/Za** možnost [/Za, /Ze (zakázání jazykových rozšíření)](/cpp/build/reference/za-ze-disable-language-extensions).  
  
- **DisableSpecificWarnings**  
  
   Volitelný parametr, řetězec [].  
  
   Zakáže čísla upozornění, které jsou určené v seznam oddělený středníkem.  
  
   Další informace najdete v tématu `/wd` možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).  
  
- **EnableEnhancedInstructionSet**  
  
   Volitelný parametr řetězce.  
  
   Určuje architekturu pro generování kódu, který používá Streaming SIMD Extensions (SSE) a Streaming SIMD Extensions 2 (SSE2) pokyny.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
    Další informace najdete v tématu [/arch (x86)](/cpp/build/reference/arch-x86).  
  
- **EnableFiberSafeOptimizations**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, podporují bezpečnost vlákna pro data Alokovaná pomocí statického úložiště lokálního vlákna, to znamená, že data Alokovaná pomocí `__declspec(thread)`.  
  
   Další informace najdete v tématu [/GT (Podpora úložiště thread local zabezpečenými vlákénky)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
- **EnablePREfast**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, povolit analýzu kódu.  
  
   Další informace najdete v tématu [/ analyze (Analýza kódu)](/cpp/build/reference/analyze-code-analysis).  
  
- **ErrorReporting**  
  
   Volitelný parametr řetězce.  
  
   Umožňuje poskytnout informace o kompilátoru vnitřní chybě (ICE) přímo společnosti Microsoft. Ve výchozím nastavení v integrovaném vývojovém prostředí sestavení je **výzvy** a nastavení v sestavení příkazového řádku je **fronty**.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Žádný** -   **/errorreport: žádné**  
  
  - **Řádek** - **/errorReport:prompt**  
  
  - **Fronty** - **/errorReport:queue**  
  
  - **Odeslat** -   **/errorreport: Send**  
  
    Další informace najdete v tématu [/errorreport (sestava interními chybami kompilátoru)](/cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
- **ExceptionHandling**  
  
   Volitelný parametr řetězce.  
  
   Určuje model zpracování výjimek pro použití kompilátorem.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **false** - *\<žádné >*  
  
  - **Asynchronní** -   **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Další informace najdete v tématu [/EH (model zpracování výjimek)](/cpp/build/reference/eh-exception-handling-model).  
  
- **ExpandAttributedSource**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, vytvoří soubor výpisu, který se rozšířila atributy vloženými do zdrojového souboru.  
  
   Další informace najdete v tématu [/Fx (sloučení vložený kód)](/cpp/build/reference/fx-merge-injected-code).  
  
- **FavorSizeOrSpeed**  
  
   Volitelný parametr řetězce.  
  
   Určuje, jestli se má upřednostnit kód velikost nebo rychlost kódu.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Ani** - *\<žádné >*  
  
  - **Velikost** -   **/OS**  
  
  - **Rychlost** - **/Ot**  
  
    Další informace najdete v tématu [/OS, /Ot (upřednostnění malého kódu, upřednostnění rychlého kódu)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
- **FloatingPointExceptions**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, umožňuje spolehlivé výjimky s plovoucí desetinnou čárkou modelu. Výjimky, bude vyvolána okamžitě po aktivaci.  
  
   Další informace najdete v tématu /**fp: except** možnost [/fp (zadání chování plovoucí desetinné čárky)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
- **FloatingPointModel**  
  
   Volitelný parametr řetězce.  
  
   Nastaví plovoucí bodu modelu.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Přesné** -   **/FP: precise**  
  
  - **Striktní** -   **/FP: strict**  
  
  - **Rychlé** - **Fast**  
  
    Další informace najdete v tématu [/fp (zadání chování plovoucí desetinné čárky)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
- **ForceConformanceInForLoopScope**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, implementuje standardního chování jazyka C++ v [pro](/cpp/cpp/for-statement-cpp) smyček, které používají rozšíření společnosti Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).  
  
   Další informace najdete v tématu [/Zc: forscope (vynutit dodržování standardu pro obor cyklu for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).  
  
- **ForcedIncludeFiles**  
  
   Volitelné `String[]` parametru.  
  
   Způsobí, že preprocesor zpracovat jeden nebo více souborů zadanou hlavičku.  
  
   Další informace najdete v tématu [/FI (pojmenovat vynucený vložený soubor)](/cpp/build/reference/fi-name-forced-include-file).  
  
- **ForcedUsingFiles**  
  
   Volitelné **String []** parametru.  
  
   Způsobí, že preprocesor zpracovat jeden nebo více zadaných **#using** soubory.  
  
   Další informace najdete v tématu [/FU (názvem #using souboru)](/cpp/build/reference/fu-name-forced-hash-using-file).  
  
- **FunctionLevelLinking**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, umožňuje kompilátoru balíček individuálních funkcí ve formě zabalených funkcí (sekvence Comdat).  
  
   Další informace najdete v tématu [/Gy (povolení propojení úrovni funkcí)](/cpp/build/reference/gy-enable-function-level-linking).  
  
- **GenerateXMLDocumentationFiles**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že kompilátor ke zpracování dokumentační komentáře v souborech zdrojového kódu a k vytvoření *.xdc* soubor pro každý soubor zdrojového kódu, který se dokumentační komentáře.  
  
   Další informace najdete v tématu [/DOC (zpracování dokumentačních komentářů) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Viz také **XMLDocumentationFileName** parametr v této tabulce.  
  
- **IgnoreStandardIncludePath**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zabraňuje kompilátor hledal soubory k zahrnutí v adresářích zadaných v proměnné prostředí PATH či INCLUDE.  
  
   Další informace najdete v tématu [/X (ignorování standardních cest zahrnutí)](/cpp/build/reference/x-ignore-standard-include-paths).  
  
- **InlineFunctionExpansion**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje úroveň rozbalení vložených funkcí pro sestavení.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - *\<žádné >*  
  
  - **Zakázané** - **příkazu/ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** -   **/ob2**  
  
    Další informace najdete v tématu [/Ob (rozbalení vložené funkce)](/cpp/build/reference/ob-inline-function-expansion).  
  
- **Intrinsicfunctions –**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, nahradí určitou funkci volání s vnitřní nebo jinak speciální formuláře funkce, které vaší aplikaci pomůžou pracovat rychleji.  
  
   Další informace najdete v tématu [/Oi (Generovat vnitřní funkce)](/cpp/build/reference/oi-generate-intrinsic-functions).  
  
- **MinimalRebuild**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, povolí minimální opětovné sestavení, která určuje, zda zdrojové soubory C++ obsahující změněné C++ třídy definice (uložené v souborech hlaviček (.h)) musí zopakovat.  
  
   Další informace najdete v tématu [/Gm (povolení minimálního opětovného sestavení)](/cpp/build/reference/gm-enable-minimal-rebuild).  
  
- **MultiProcessorCompilation**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, kompilaci pomocí více procesorů. Tento parametr vytvoří proces pro každý efektivní procesor ve vašem počítači.  
  
   Další informace najdete v tématu [/MP (sestavení pomocí několika procesů)](/cpp/build/reference/mp-build-with-multiple-processes). Další informace naleznete **ProcessorNumber** parametr v této tabulce.  
  
- **ObjectFileName**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název souboru objektů (.obj) nebo adresáře se použije místo výchozího.  
  
   Další informace najdete v tématu [/Fo (název souboru objektů)](/cpp/build/reference/fo-object-file-name).  
  
- **ObjectFiles**  
  
   Volitelné **String []** parametru.  
  
   Seznam souborů objektů.  
  
- **OmitDefaultLibName**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, vynechá výchozí název knihovny run-time C z objektu (*.obj*) soubor. Ve výchozím nastavení, kompilátor vloží název tohoto knihovny do *.obj* souboru k řízení linkeru, aby je správná knihovna.  
  
   Další informace najdete v tématu [/Zl (vynechat výchozí název knihovny)](/cpp/build/reference/zl-omit-default-library-name).  
  
- **OmitFramePointers**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, potlačí vytváření ukazatelů rámců v zásobníku volání.  
  
   Další informace najdete v tématu [/Oy (vynechání ukazatele na rámec)](/cpp/build/reference/oy-frame-pointer-omission).  
  
- **OpenMPSupport**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že kompilátor zpracování OpenMP – klauzule a direktivy.  
  
   Další informace najdete v tématu [/OpenMP (Povolit OpenMP 2.0 podporu)](/cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
- **Optimalizace**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje různé kód optimalizací pro rychlost a velikosti.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Zakázané** - **/Od**  
  
  - **MinSpace** -   **/O1**  
  
  - **MaxSpeed** -   **/O2**  
  
  - **Úplné** - **/Ox**  
  
    Další informace najdete v tématu [/O možnosti (Optimalizace kódu)](/cpp/build/reference/o-options-optimize-code).  
  
- **PrecompiledHeader**  
  
   Volitelné **řetězec** parametru.  
  
   Vytvořit nebo použít předkompilovanou hlavičku (*.pch*) souboru během sestavování.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NotUsing** - *\<žádné >*  
  
  - **Vytvoření** - **/Yc**  
  
  - **Použití** - **/Yu**  
  
    Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](/cpp/build/reference/yc-create-precompiled-header-file) a [/Yu (Použít předkompilovaný hlavičkový soubor)](/cpp/build/reference/yu-use-precompiled-header-file). Další informace naleznete **PrecompiledHeaderFile** a **PrecompiledHeaderOutputFile** parametry v této tabulce.  
  
- **PrecompiledHeaderFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název souboru předkompilované hlavičky vytvořit nebo použít.  
  
   Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](/cpp/build/reference/yc-create-precompiled-header-file) a [/Yu (Použít předkompilovaný hlavičkový soubor)](/cpp/build/reference/yu-use-precompiled-header-file).  
  
- **PrecompiledHeaderOutputFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název cesty pro předkompilované hlavičky místo použití výchozí název cesty.  
  
   Další informace najdete v tématu [/FP (pojmenování souboru .pch)](/cpp/build/reference/fp-name-dot-pch-file).  
  
- **PreprocessKeepComments**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zachová komentáře při předzpracování.  
  
   Další informace najdete v tématu [/C (zachovat komentáře při předběžném zpracování)](/cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
- **PreprocessorDefinitions**  
  
   Volitelné `String[]` parametru.  
  
   Definuje symbol předzpracování pro zdrojový soubor.  
  
   Další informace najdete v tématu [/D (Definice preprocesoru)](/cpp/build/reference/d-preprocessor-definitions).  
  
- **PreprocessOutput**  
  
   Volitelné `ITaskItem[]` parametru.  
  
   Definuje pole objektů preprocesoru výstupní položky, které lze používat a, protože ho vygeneroval úlohy.  
  
- **PreprocessOutputPath**  
  
   Volitelné `String` parametru.  
  
   Určuje název výstupního souboru, do kterého **PreprocessToFile** parametr zapíše Předzpracovaný výstup.  
  
   Další informace najdete v tématu [/Fi (předběžné zpracování výstupu název souboru)](/cpp/build/reference/fi-preprocess-output-file-name).  
  
- **PreprocessSuppressLineNumbers**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`předzpracuje zdrojové soubory jazyka C a C++ a zkopíruje soubory předzpracovaná do standardního výstupního zařízení.  
  
   Další informace najdete v tématu [/EP (předzpracování do stdout bez direktiv #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
- **PreprocessToFile**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`předzpracuje zdrojové soubory jazyka C a C++ a zapíše Předzpracovaný výstup do souboru.  
  
   Další informace najdete v tématu [/P (předběžné zpracování souboru)](/cpp/build/reference/p-preprocess-to-a-file).  
  
- **ProcessorNumber**  
  
   Volitelné `Integer` parametru.  
  
   Určuje maximální počet procesorů pro použití v kompilaci s více procesory. Tento parametr použijte v kombinaci s **MultiProcessorCompilation** parametru.  
  
- **ProgramDataBaseFileName**  
  
   Volitelné `String` parametru.  
  
   Určuje název souboru pro soubor databáze (PDB) programu.  
  
   Další informace najdete v tématu [/Fd (název souboru databáze programu)](/cpp/build/reference/fd-program-database-file-name).  
  
- **RuntimeLibrary**  
  
   Volitelné `String` parametru.  
  
   Určuje, jestli je knihovna DLL vícevláknový modul a vybere prodejní nebo ladicí verze knihovny run-time.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Vícevláknové** -   **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** -   **/MDd**  
  
    Další informace najdete v tématu [/ / MD, / MT, /LD (použití knihovny run-time)](/cpp/build/reference/md-mt-ld-use-run-time-library).  
  
- **RuntimeTypeInfo**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, přidá kód pro kontrolu typů objektů jazyka C++ za běhu (informace typu za běhu).  
  
   Další informace najdete v tématu [/GR (povolit informace běhového typu)](/cpp/build/reference/gr-enable-run-time-type-information).  
  
- **ShowIncludes**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že kompilátor výstup seznam vložených souborů.  
  
   Další informace najdete v tématu [/showincludes (seznam vložených souborů)](/cpp/build/reference/showincludes-list-include-files).  
  
- **SmallerTypeCheck**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, pokud hodnota je přiřazená menší datový typ a vede ke ztrátě dat sestavy chyb za běhu.  
  
   Další informace najdete v tématu **/RTCc** možnost [/RTC (Kontrola chyb za běhu)](/cpp/build/reference/rtc-run-time-error-checks).  
  
- **Zdroje**  
  
   Vyžaduje `ITaskItem[]` parametru.  
  
   Určuje seznam zdrojových souborů, oddělené mezerami.  
  
- **StringPooling**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, umožňuje kompilátoru vytvořit jednu kopii shodného řetězce do bitové kopie programu.  
  
   Další informace najdete v tématu [/GF (eliminujete tak duplicitních řetězců)](/cpp/build/reference/gf-eliminate-duplicate-strings).  
  
- **StructMemberAlignment**  
  
   Volitelné `String` parametru.  
  
   Určuje zarovnání bajtů pro všechny členy ve struktuře.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    Další informace najdete v tématu [/Zp (zarovnání členů struktury)](/cpp/build/reference/zp-struct-member-alignment).  
  
- **SuppressStartupBanner**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.  
  
   Další informace najdete v tématu [/nologo (Potlačit úvodní nápis při spouštění) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
- **TrackerLogDirectory**  
  
   Volitelné `String` parametru.  
  
   Určuje zprostředkující adresář, kde jsou uloženy protokoly sledování pro tuto úlohu.  
  
   Další informace najdete v tématu **TLogReadFiles** a **TLogWriteFiles** parametry v této tabulce.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Volitelné **String []** parametru.  
  
   Zpracovává zadaný seznam upozornění kompilátoru jako chyby.  
  
   Další informace najdete v tématu **/we** `n` možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).  
  
- **TreatWarningAsError**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zpracovávat všechna upozornění kompilátoru jako chyby.  
  
   Další informace najdete v tématu **/WX** možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zpracovávat `wchar_t` typ jako nativního typu.  
  
   Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, nedefinovaných hodnot, které kompilátor definuje symboly specifické pro společnost Microsoft.  
  
   Další informace najdete v tématu **/u** možnost [/U, /u (nedefinované symboly)](/cpp/build/reference/u-u-undefine-symbols).  
  
- **UndefinePreprocessorDefinitions**  
  
   Volitelné `String[]` parametru.  
  
   Určuje seznam jednoho nebo více symboly preprocesoru definice.  
  
   Další informace najdete v tématu **/U** možnost [/U, /u (nedefinované symboly)](/cpp/build/reference/u-u-undefine-symbols).  
  
- **UseFullPaths**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zobrazí úplnou cestu souborů se zdrojovým kódem předány kompilátoru v diagnostice.  
  
   Další informace najdete v tématu [/FC (úplná cesta k souboru zdrojového kódu v diagnostice)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
- **UseUnicodeForAssemblerListing**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že výstupní soubor bude vytvořena ve formátu UTF-8.  
  
   Další informace najdete v tématu **/fau vytvořte** možnost [/FA, /Fa (soubor seznamu)](/cpp/build/reference/fa-fa-listing-file).  
  
- **WarningLevel**  
  
   Volitelné `String` parametru.  
  
   Určuje nejvyšší úroveň upozornění, že je generovaný kompilátorem.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** - **/W1**  
  
  - **Level2** - **/W2**  
  
  - **Level3** - **w3**  
  
  - **Level4** -   **/W4**  
  
  - **EnableAllWarnings** -   **/Wall**  
  
    Další informace najdete v tématu **/W**_n_ možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).  
  
- **WholeProgramOptimization**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, povolí optimalizaci celého programu.  
  
   Další informace najdete v tématu [/GL (celková optimalizace programu)](/cpp/build/reference/gl-whole-program-optimization).  
  
- **XMLDocumentationFileName**  
  
   Volitelné `String` parametru.  
  
   Určuje název vygenerovaných dokumentačních souborů XML. Tento parametr může být název souboru nebo adresáře.  
  
   Další informace najdete v tématu `name` argument v [/DOC (zpracování dokumentačních komentářů) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Viz také **GenerateXMLDocumentationFiles** parametr v této tabulce.  
  
- **MinimalRebuildFromTracking**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, provádí sledované přírůstkové sestavení; Pokud `false`, se provádí opětovné sestavení.  
  
- **TLogReadFiles**  
  
   Volitelné `ITaskItem[]` parametru.  
  
   Určuje pole, které představují *přečíst soubor protokoly sledování*.  
  
   Protokolu sledování souborů pro čtení (*.tlog*) obsahuje názvy vstupních souborů, které jsou přečteny úkolu a používá systém sestavení projektu pro podporu přírůstkové sestavení. Další informace najdete v tématu **TrackerLogDirectory** a **vlastnost TrackFileAccess** parametry v této tabulce.  
  
- **TLogWriteFiles**  
  
   Volitelné `ITaskItem[]` parametru.  
  
   Určuje pole, které představují *zapisovat do souboru protokoly sledování*.  
  
   Protokolu sledování souborů zápisu (*.tlog*) obsahuje názvy výstupní soubory, které jsou zapsány úlohou a používá systém sestavení projektu pro podporu přírůstkové sestavení. Další informace najdete v tématu **TrackerLogDirectory** a **vlastnost TrackFileAccess** parametry v této tabulce.  
  
- **TrackFileAccess**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, sleduje vzory přístupu k souboru.  
  
   Další informace najdete v tématu **TLogReadFiles** a **TLogWriteFiles** parametry v této tabulce.  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)