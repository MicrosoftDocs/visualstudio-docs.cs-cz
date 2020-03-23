---
title: Cl Úkol | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865333"
---
# <a name="cl-task"></a>CL – úloha

Zalomí kompilátorový nástroj Microsoft *C++cl.exe*. Kompilátor vytváří spustitelné soubory (*EXE*), soubory dynamické knihovny (*DLL*) nebo modul kódu (*.netmodule*). Další informace naleznete v [tématech Možnosti kompilátoru](/cpp/build/reference/compiler-options) a [Použití nástroje MSBuild z příkazového řádku](/cpp/build/msbuild-visual-cpp) a Použití sady nástrojů Microsoft [C++ z příkazového řádku](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametry

 Následující seznam popisuje parametry úlohy **CL.** Většina parametrů úlohy a několik sad parametrů odpovídají možnosti příkazového řádku.

- **Další includeředitelé adresáře**

   Volitelný parametr String[].

   Přidá adresář do seznamu adresářů, které jsou vyhledávány zahrnout soubory.

   Další informace naleznete [v tématu /I (Další zahrnutí adresářů)](/cpp/build/reference/i-additional-include-directories).

- **Další možnosti**

   Volitelný parametr String.

   Seznam možností příkazového řádku. Například "/\<option1\<> /\<option2> / option#>". Tento parametr slouží k určení možností příkazového řádku, které nejsou reprezentovány žádným jiným parametrem úkolu.

   Další informace naleznete v tématu [Možnosti kompilátoru](/cpp/build/reference/compiler-options).

- **Další použitíadresářů**

   Volitelný parametr String[].

   Určuje adresář, který bude kompilátor hledat, aby vyřešil odkazy na soubory předané direktivě **#using.**

   Další informace naleznete [v tématu /AI (Zadejte adresáře metadat).](/cpp/build/reference/ai-specify-metadata-directories)

- **AlwaysAppend**

   Volitelný parametr String.

   Řetězec, který se vždy dostane na příkazovém řádku. Jeho výchozí hodnota je "**/c**".

- **Umístění AssemblerListing**

   Vytvoří soubor výpisu, který obsahuje kód sestavení.

   Další informace naleznete v tématu **/Fa** možnost [/FA, /Fa (Výpis souboru)](/cpp/build/reference/fa-fa-listing-file).

- **Výstup assembleru**

   Volitelný parametr String.

   Vytvoří soubor výpisu, který obsahuje kód sestavení.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **NoListing žádný** - >*\<*

  - **AssemblyCode** - **/DM**

  - **AssemblyAndMachineCode** - **/FAc**

  - **AssemblyandSourceCode** - **/FAs**

  - **Všechny** - **/FAcs**

    Další informace naleznete v tématech **/FA**, **/FAc**, **/FA**, a **/FAcs** options in [/FA, /Fa (Listing file)](/cpp/build/reference/fa-fa-listing-file).

- **Základní kontroly běhu**

   Volitelný parametr String.

   Povolí a zakáže funkci kontroly chyb za běhu ve spojení s [runtime_checks](/cpp/preprocessor/runtime-checks) pragma.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** -                          *žádný>\<*

  - **StackFrameRuntimeCheck** - **/RTC**

  - **UninitializedLocalUsageCheck** - **/RTCu**

  - **EnableFastChecks** -                          **/RTC1**

    Další informace naleznete v tématu [/RTC (Run-time kontroly chyb)](/cpp/build/reference/rtc-run-time-error-checks).

- **ProcházetInformace**

   Volitelný logický parametr.

   Pokud `true`vytvoří soubor informací o procházení.

   Další informace naleznete v tématu **/FR** možnost v [/FR, /Fr (Vytvořit soubor SBR)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **Soubor BrowseInformationFile**

   Volitelný parametr String.

   Určuje název souboru informačního souboru procházení.

   Další informace naleznete v parametru **BrowseInformation** v této tabulce a také v [tématu /FR, /Fr (Create.sbr file).](/cpp/build/reference/fr-fr-create-dot-sbr-file)

- **Kontrola zabezpečení vyrovnávací paměti**

   Volitelný logický parametr.

   Pokud `true`zjistí některé přetečení vyrovnávací paměti, které přepíší zpáteční adresu, běžnou techniku pro zneužití kódu, který nevynucuje omezení velikosti vyrovnávací paměti.

   Další informace naleznete [v tématu /GS (Kontrola zabezpečení vyrovnávací paměti).](/cpp/build/reference/gs-buffer-security-check)

- **BuildinginiDE**

   Volitelný logický parametr.

   Pokud `true`, označuje, že **MSBuild** je vyvolána ide. V opačném případě je **msbuild** vyvolán na příkazovém řádku.

- **VoláníÚmluvy**

   Volitelný parametr String.

   Určuje konvence volání, která určuje pořadí, ve kterém jsou argumenty funkce posunuty do zásobníku, zda volající funkce nebo volaná funkce odebere argumenty ze zásobníku na konci volání a konvence zdobení názvů, které kompilátor používá k identifikaci jednotlivých funkcí.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Cdecl** - **/Gd**

  - **Rychlé volání** -                          **/Gr**

  - **Volání StdCall** -                          **/Gz**

    Další informace naleznete [v tématu /Gd, /Gr, /Gv, /Gz (Konvence volání)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **Kompilovat**

   Volitelný parametr String.

   Určuje, zda má být vstupní soubor kompilován jako zdrojový soubor jazyka C nebo C++.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** - *žádný>\<*

  - **Kompilovat** - **/TC**

  - **KompilaceAsCpp** - **/TP**

    Další informace naleznete v tématu [/Tc, /Tp, /TC, /TP (Zadejte typ zdrojového souboru).](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type)

- **CompileAsManaged**

   Volitelný parametr String.

   Umožňuje aplikacím a komponentám používat funkce z clr (COMMON Language runtime).

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **falešný** - *žádný>\<*

  - **true** - **/clr**

  - **Čistý** - **/clr:čistý**

  - **Bezpečné** - **/clr:bezpečné**

  - **oldSyntax** - **/clr:oldSyntax**

    Další informace naleznete v tématu [/clr (Kompilace za běhu běžného jazyka).](/cpp/build/reference/clr-common-language-runtime-compilation)

- **Vytvořit obrázek VytvořithotpatchableImage**

   Volitelný logický parametr.

   Pokud `true`, řekne kompilátoru připravit obraz pro *horké opravy*. Tento parametr zajišťuje, že první instrukce každé funkce je dva bajty, které jsou vyžadovány pro horké opravy.

   Další informace naleznete v tématu [/hotpatch (Create hotpatchable image).](/cpp/build/reference/hotpatch-create-hotpatchable-image)

- **DebugInformationFormat**

   Volitelný parametr String.

   Vybere typ informací o ladění vytvořených pro váš program a to, zda jsou tyto informace uloženy v souborech objektů (*OBJ*) nebo v databázi programů (PDB).

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Starý styl** - **/Z7**

  - **ProgramDatabáze** - **/Zi**

  - **EditAndContinue** - **/ZI**

    Další informace naleznete v tématu [/Z7, /Zi, /ZI (formát informací o ladění).](/cpp/build/reference/z7-zi-zi-debug-information-format)

- **Zakázat rozšíření jazyků**

   Volitelný logický parametr.

   Pokud **true**, říká kompilátoru vyzařovat chybu pro konstrukce jazyka, které nejsou kompatibilní s ANSI C nebo ANSI C ++.

   Další informace naleznete v tématu **/Za,** [/Ze (Zakázat rozšíření jazyka)](/cpp/build/reference/za-ze-disable-language-extensions).

- **Zakázatspecifickávarování**

   Volitelný parametr String[].

   Zakáže čísla upozornění, která jsou určena v seznamu odděleném středníkem.

   Další informace naleznete `/wd` v možnosti [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Volitelný parametr String.

   Určuje architekturu pro generování kódu, která používá streamovaná rozšíření SIMD (SSE) a streamovací rozšíření SIMD 2 (SSE2).

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **StreamingSIMDExtensions** - **/arch:SSE**

  - **StreamingSIMDExtensions2** - **/arch:SSE2**

    Další informace naleznete v tématu [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimalizace**

   Volitelný logický parametr.

   Pokud `true`podporují zabezpečení vláken pro data přidělená pomocí statického místního úložiště `__declspec(thread)`podprocesu, to znamená data přidělená pomocí .

   Další informace naleznete v tématu [/GT (Support fiber-safe thread-local storage)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **Povolit PREfast**

   Volitelný logický parametr.

   Pokud `true`povolte analýzu kódu.

   Další informace naleznete v tématu [/analyze (Analýza kódu).](/cpp/build/reference/analyze-code-analysis)

- **Hlášení chyb**

   Volitelný parametr String.

   Umožňuje poskytovat informace o interní chybě kompilátoru (ICE) přímo společnosti Microsoft. Ve výchozím nastavení je nastavení v sestaveních ide **Prompt** a nastavení v sestaveních příkazového řádku je **Fronta**.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Žádné** - **/errorReport:none**

  - **Výzva** - **/errorReport:výzva**

  - **Fronta** - **/errorReport:fronta**

  - **Odeslat** - **/errorReport:odeslat**

    Další informace naleznete v tématu [/errorReport (Report internal compiler errors).](/cpp/build/reference/errorreport-report-internal-compiler-errors)

- **Zpracování výjimek**

   Volitelný parametr String.

   Určuje model zpracování výjimek, který má kompilátor použít.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **falešný** - *žádný>\<*

  - **Asynchronní** - **/EHa**

  - **Synchronizace** - **/EHsc**

  - **SyncCThrow** - **/EHs**

    Další informace naleznete v tématu [/EH (Model zpracování výjimek)](/cpp/build/reference/eh-exception-handling-model).

- **Rozbalitatribut**

   Volitelný logický parametr.

   Pokud `true`vytvoří soubor výpisu, který má rozšířené atributy vložené do zdrojového souboru.

   Další informace naleznete v tématu [/Fx (Merge injected code)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Volitelný parametr String.

   Určuje, zda má být upřednostňována velikost kódu nebo rychlost kódu.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Ani** - *žádný>\<*

  - **Velikost** - **/Os**

  - **Rychlost** - **/Ot**

    Další informace naleznete [v tématu /Os, /Ot (Favor malý kód, favor rychlý kód)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **Výjimky s plovoucím bodem**

   Volitelný logický parametr.

   Pokud `true`, umožňuje spolehlivý model výjimky s plovoucí desetinnou desetinnou desetinnou tázkou. Výjimky budou vyvolány ihned po jejich aktivaci.

   Další informace naleznete v tématu /**fp:except** option in [/fp (Specify floating-point behavior)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **PlovoucíPointModel**

   Volitelný parametr String.

   Nastaví model s plovoucí desetinnou tázkou.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Přesné** - **/fp:přesné**

  - **Striktní** - **/fp:striktní**

  - **Rychlé** - **/fp:rychlé**

    Další informace naleznete v tématu [/fp (Zadejte chování s plovoucí desetinnou tázkem).](/cpp/build/reference/fp-specify-floating-point-behavior)

- **ForceConformanceInForLoopScope**

   Volitelný logický parametr.

   Pokud `true`implementuje standardní chování jazyka C++ v [pro](/cpp/cpp/for-statement-cpp) smyčky, které používají rozšíření Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Další informace naleznete v tématu [/Zc:forScope (Force conformance in for loop scope).](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope)

- **Vynucené includesoubory**

   Volitelný `String[]` parametr.

   Způsobí, že preprocesor zpracuje jeden nebo více zadaných souborů hlaviček.

   Další informace naleznete v tématu [/FI (Název vynucený soubor zahrnutí)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Volitelný **parametr String[].**

   Způsobí, že preprocesor zpracuje jeden nebo více určených **souborů #using.**

   Další informace naleznete v tématu [/FU (Název vynucený #using soubor)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunkceLevelLinking**

   Volitelný `Boolean` parametr.

   Pokud `true`umožňuje kompilátoru sbalit jednotlivé funkce ve formě balených funkcí (COMDAts).

   Další informace naleznete v tématu [/Gy (Povolit propojení na úrovni funkce).](/cpp/build/reference/gy-enable-function-level-linking)

- **GenerateXMLDocumentationFiles**

   Volitelný `Boolean` parametr.

   Pokud `true`způsobí, že kompilátor zpracuje komentáře dokumentace v souborech zdrojového kódu a vytvoří soubor *XDC* pro každý soubor zdrojového kódu, který má komentáře k dokumentaci.

   Další informace naleznete v tématu [/doc (Zpracování dokumentů komentáře) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Viz také parametr **XMLDocumentationFileName** v této tabulce.

- **Ignorovat cestu standardních zahrnutí**

   Volitelný `Boolean` parametr.

   Pokud `true`zabraňuje kompilátoru v hledání zahrnout soubory v adresářích určených v path a include proměnné prostředí.

   Další informace naleznete v tématu [/X (Ignorovat standardní zahrnout cesty)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Volitelný **parametr String.**

   Určuje úroveň rozšíření vřadné funkce pro sestavení.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** - *žádný>\<*

  - **Zakázáno** - **/Ob0**

  - **OnlyExplicitInline** - **/Ob1**

  - **AnySuitable** - **/Ob2**

    Další informace naleznete v tématu [/Ob (Rozšíření funkce inline).](/cpp/build/reference/ob-inline-function-expansion)

- **Vnitřní funkce**

   Volitelný `Boolean` parametr.

   Pokud `true`, nahradí některé volání funkce vnitřní nebo jinak zvláštní formy funkce, které pomáhají aplikace běžet rychleji.

   Další informace naleznete [v tématu /Oi (Generovat vnitřní funkce).](/cpp/build/reference/oi-generate-intrinsic-functions)

- **MinimalRebuild**

   Volitelný `Boolean` parametr.

   Pokud `true`, umožňuje minimální opětovné sestavení, které určuje, zda je nutné znovu zkompilovat zdrojové soubory jazyka C++, které obsahují změněné definice tříd jazyka C++ (uložené v souborech záhlaví (.h).

   Další informace naleznete v tématu [/Gm (Povolit minimální znovusestavit)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **Kompilace více procesorů**

   Volitelný `Boolean` parametr.

   Pokud `true`, použijte více procesorů ke kompilaci. Tento parametr vytvoří proces pro každý efektivní procesor v počítači.

   Další informace naleznete v tématu [/MP (Sestavení s více procesy).](/cpp/build/reference/mp-build-with-multiple-processes) Viz také parametr **ProcessorNumber** v této tabulce.

- **Název objektu ObjectFileName**

   Volitelný **parametr String.**

   Určuje název souboru nebo adresáře objektu (obj), který má být použit místo výchozího.

   Další informace naleznete v tématu [/Fo (Název souboru objektu).](/cpp/build/reference/fo-object-file-name)

- **Objektové soubory**

   Volitelný **parametr String[].**

   Seznam souborů objektů.

- **OmitDefaultLibName**

   Volitelný `Boolean` parametr.

   Pokud `true`vyneche výchozí název knihovny C run-time ze souboru objektu (*obj*). Ve výchozím nastavení kompilátor vloží název knihovny do souboru *OBJ,* aby nasměroval propojovací program do správné knihovny.

   Další informace naleznete v tématu [/Zl (Vynechání výchozího názvu knihovny).](/cpp/build/reference/zl-omit-default-library-name)

- **Vynechat ukazatele rámce**

   Volitelný `Boolean` parametr.

   Pokud `true`potlačí vytváření ukazatelů rámce v zásobníku volání.

   Další informace naleznete v tématu [/Oy (Vynechání ukazatele rámce)](/cpp/build/reference/oy-frame-pointer-omission).

- **Podpora OpenMPSupport**

   Volitelný `Boolean` parametr.

   Pokud `true`způsobí, že kompilátor zpracuje klauzule OpenMP a direktivy.

   Další informace naleznete v tématu [/openmp (Povolit podporu OpenMP 2.0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optimalizace**

   Volitelný **parametr String.**

   Určuje různé optimalizace kódu pro rychlost a velikost.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Zakázáno** - **/Od**

  - **MinSpace** - **/O1**

  - **Maximální rychlost** - **/O2**

  - **Plný** - **/Ox**

    Další informace naleznete v tématu [/O Options (Optimalizace kódu)](/cpp/build/reference/o-options-optimize-code).

- **Předkompilované záhlaví**

   Volitelný **parametr String.**

   Vytvořte nebo použijte předkompilovaný soubor záhlaví (*.pch)* během sestavení.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Nepoužívat žádný** - >*\<*

  - **Vytvořit** - **/Yc**

  - **Použít** - **/Yu**

    Další informace naleznete [v tématech /Yc (Vytvoření předkompilovaného souboru hlaviček)](/cpp/build/reference/yc-create-precompiled-header-file) a [/Yu (Použít předkompilovaný soubor záhlaví).](/cpp/build/reference/yu-use-precompiled-header-file) Viz také parametry **PrecompiledHeaderFile** a **PrecompiledHeaderOutputFile** v této tabulce.

- **Předkompilovaný soubor záhlaví**

   Volitelný **parametr String.**

   Určuje předkompilovaný název souboru záhlaví, který chcete vytvořit nebo použít.

   Další informace naleznete [v tématech /Yc (Vytvoření předkompilovaného souboru hlaviček)](/cpp/build/reference/yc-create-precompiled-header-file) a [/Yu (Použít předkompilovaný soubor záhlaví).](/cpp/build/reference/yu-use-precompiled-header-file)

- **Předkompilovanýsoubor Hlavička Výstupu**

   Volitelný **parametr String.**

   Určuje název cesty pro předkompilované záhlaví namísto použití výchozího názvu cesty.

   Další informace naleznete v tématu [/Fp (Název .pch file)](/cpp/build/reference/fp-name-dot-pch-file).

- **Předběžné zobrazení keepkomentáře**

   Volitelný `Boolean` parametr.

   Pokud `true`zachová komentáře během předběžného zpracování.

   Další informace naleznete [v tématu /C (Zachovat komentáře během předběžného zpracování)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **Definice preprocesoru**

   Volitelný `String[]` parametr.

   Definuje symbol předběžného zpracování zdrojového souboru.

   Další informace naleznete v tématu [/D (Definice preprocesoru).](/cpp/build/reference/d-preprocessor-definitions)

- **Předprocesvýstup**

   Volitelný `ITaskItem[]` parametr.

   Definuje pole výstupních položek preprocesoru, které mohou být spotřebovány a vydávány úkoly.

- **Předprocesoutputpath**

   Volitelný `String` parametr.

   Určuje název výstupního souboru, do kterého parametr **PreprocessToFile** zapisuje předem zpracovaný výstup.

   Další informace naleznete v tématu [/Fi (Název výstupního souboru před zpracováním).](/cpp/build/reference/fi-preprocess-output-file-name)

- **PreprocessSuppressLineNumbers**

   Volitelný `Boolean` parametr.

   If `true`, preprocesses C a C++ source files and copies the preprocessed files to the standard output device.

   Další informace naleznete [v tématu /EP (Preprocess to stdout bez #line direktivy).](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives)

- **Předprocestosoubor**

   Volitelný `Boolean` parametr.

   If `true`, preprocesses C a C++ source files and writes the preprocessed output to a file.

   Další informace naleznete v tématu [/P (Předběžná proces k souboru).](/cpp/build/reference/p-preprocess-to-a-file)

- **Číslo procesoru**

   Volitelný `Integer` parametr.

   Určuje maximální počet procesorů, které mají být používány v kompilaci s více procesory. Tento parametr použijte v kombinaci s parametrem **MultiProcessorCompilation.**

- **Název souboru ProgramDataBase**

   Volitelný `String` parametr.

   Určuje název souboru databáze programů (PDB).

   Další informace naleznete v tématu [/Fd (Název souboru databáze programu).](/cpp/build/reference/fd-program-database-file-name)

- **RuntimeLibrary**

   Volitelný `String` parametr.

   Označuje, zda je vícevláknový modul knihovnou DLL, a vybere maloobchodní nebo ladicí verze knihovny za běhu.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Vícevláknové** - **/MT**

  - **VícethreadedDebug** - **/MTd**

  - **Vícevláknová dll** - **/MD**

  - **VícethreadedDebugDLL** - **/MDd**

    Další informace naleznete v tématu [/MD, /MT, /LD (Použít knihovnu za běhu).](/cpp/build/reference/md-mt-ld-use-run-time-library)

- **Informace o typu runtimetype**

   Volitelný `Boolean` parametr.

   Pokud `true`, přidá kód pro kontrolu typů objektů Jazyka C++ za běhu (informace o typu za běhu).

   Další informace naleznete v tématu [/GR (Povolit informace o typu za běhu).](/cpp/build/reference/gr-enable-run-time-type-information)

- **Zobrazit zahrnuje**

   Volitelný `Boolean` parametr.

   Pokud `true`způsobí, že kompilátor výstup seznamu zahrnout soubory.

   Další informace naleznete v tématu [/showIncludes (Seznam zahrnutí souborů)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Volitelný `Boolean` parametr.

   Pokud `true`aplikace nahlásí chybu za běhu, pokud je hodnota přiřazena menšímu datovému typu a způsobí ztrátu dat.

   Další informace naleznete v tématu **/RTCc** možnost [/RTC (Run-time kontroly chyb)](/cpp/build/reference/rtc-run-time-error-checks).

- **Zdrojů**

   Požadovaný parametr `ITaskItem[]`.

   Určuje seznam zdrojových souborů oddělených mezerami.

- **Sdružování řetězců**

   Volitelný `Boolean` parametr.

   Pokud `true`umožňuje kompilátoru vytvořit jednu kopii identických řetězců v bitové kopii programu.

   Další informace naleznete v tématu [/GF (Odstranění duplicitních řetězců).](/cpp/build/reference/gf-eliminate-duplicate-strings)

- **StructMemberAlignment**

   Volitelný `String` parametr.

   Určuje zarovnání bajtů pro všechny členy ve struktuře.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Výchozí** - **/Zp1**

  - **1Bajt** - **/Zp1**

  - **2BajTy** - **/Zp2**

  - **4Bajty** - **/Zp4**

  - **8BajTů** - **/Zp8**

  - **16Bajtů** - **/Zp16**

    Další informace naleznete v tématu [/Zp (Struct member alignment).](/cpp/build/reference/zp-struct-member-alignment)

- **PotlačitStartupBanner**

   Volitelný `Boolean` parametr.

   Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.

   Další informace naleznete v tématu [/nologo (Potlačit spouštěcí banner) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   Volitelný `String` parametr.

   Určuje zprostředkující adresář, ve kterém jsou uloženy protokoly sledování pro tuto úlohu.

   Další informace naleznete v parametrech **TLogReadFiles** a **TLogWriteFiles** v této tabulce.

- **TreatSpecificWarningsAsErrors**

   Volitelný **parametr String[].**

   Považuje zadaný seznam upozornění kompilátoru za chyby.

   Další informace naleznete v možnosti **/we** `n` v [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Úroveň varování)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsChyba**

   Volitelný `Boolean` parametr.

   Pokud `true`, považovat všechna upozornění kompilátoru jako chyby.

   Další informace naleznete v tématu **/WX** option in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Volitelný `Boolean` parametr.

   Pokud `true`, `wchar_t` považovat typ jako nativní typ.

   Další informace naleznete v tématu [/Zc:wchar_t (wchar_t je nativní typ).](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type)

- **UndefineAllPreprocessorDefinitions UndefineAllPreprocessorDefinitions UndefineAllPreprocessorDefinitions Undefine**

   Volitelný `Boolean` parametr.

   Pokud `true`, undefines microsoft specifické symboly, které definuje kompilátor.

   Další informace naleznete v tématu **/u** možnost v [/U, /u (Nedefinovat symboly)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions Undefine**

   Volitelný `String[]` parametr.

   Určuje seznam jednoho nebo více symbolů preprocesoru, které mají být nedefinovány.

   Další informace naleznete v tématu **/U** option in [/U, /u (Undefine symbols)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Volitelný `Boolean` parametr.

   Pokud `true`aplikace , zobrazí úplnou cestu souborů zdrojového kódu předaných kompilátoru v diagnostice.

   Další informace naleznete v tématu [/FC (Úplná cesta souboru zdrojového kódu v diagnostice)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **PoužitíUnicodeForAssemblerListing**

   Volitelný `Boolean` parametr.

   Pokud `true`způsobí, že výstupní soubor, který má být vytvořen ve formátu UTF-8.

   Další informace naleznete v tématu **/FAu** option in [/FA, /Fa (Listing file)](/cpp/build/reference/fa-fa-listing-file).

- **Úroveň upozornění**

   Volitelný `String` parametr.

   Určuje nejvyšší úroveň upozornění, která má být generována kompilátorem.

   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

  - **Vypnoutvšechna varování** - **/W0**

  - **Úroveň1** - **/W1**

  - **Úroveň2** - **/W2**

  - **Úroveň3** - **/W3**

  - **Úroveň4** - **/W4**

  - **EnableAllWarnings** - **/Wall**

    Další informace naleznete v možnosti **/W**_n_ v [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Úroveň upozornění)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Volitelný `Boolean` parametr.

   Pokud `true`umožňuje optimalizaci celého programu.

   Další informace naleznete v tématu [/GL (Optimalizace celého programu).](/cpp/build/reference/gl-whole-program-optimization)

- **Název souboru XMLDocumentationFileName**

   Volitelný `String` parametr.

   Určuje název generovaných souborů dokumentace XML. Tento parametr může být název souboru nebo adresáře.

   Další informace naleznete `name` v argumentu [/doc (Zpracování dokumentů komentáře) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Viz také parametr **GenerateXMLDocumentationFiles** v této tabulce.

- **MinimalRebuildFromTracking**

   Volitelný `Boolean` parametr.

   Pokud `true`se provádí sledované přírůstkové sestavení; pokud `false`je provedeno opětovné sestavení.

- **Tlogready**

   Volitelný `ITaskItem[]` parametr.

   Určuje pole položek, které představují *protokoly sledování souborů pro čtení*.

   Protokol sledování souborů pro čtení (*Tlog*) obsahuje názvy vstupních souborů, které jsou čteny úlohou, a používá se systémem sestavení projektu k podpoře přírůstkových sestavení. Další informace naleznete v parametrech **TrackerLogDirectory** a **TrackFileAccess** v této tabulce.

- **Tlogwritefiles**

   Volitelný `ITaskItem[]` parametr.

   Určuje pole položek, které představují *protokoly sledování souborů zápisu*.

   Protokol sledování souborů zápisu (*.tlog*) obsahuje názvy výstupních souborů, které jsou zapsány úlohou, a používá se systémem sestavení projektu k podpoře přírůstkových sestavení. Další informace naleznete v parametrech **TrackerLogDirectory** a **TrackFileAccess** v této tabulce.

- **Přístup trackfileaccess**

   Volitelný `Boolean` parametr.

   Pokud `true`sleduje vzor přístupu k souborům.

   Další informace naleznete v parametrech **TLogReadFiles** a **TLogWriteFiles** v této tabulce.

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
