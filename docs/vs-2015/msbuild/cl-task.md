---
title: Cl – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb9b6924f5d11e3d857308e3a1bcf1e1644f78bc
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220245"
---
# <a name="cl-task"></a>CL – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí nástroj kompilátoru Visual C++, cl.exe. Kompilátor vytvoří spustitelné soubory (.exe), dynamická knihovna (.dll) soubory nebo soubory kódu modulu (.netmodule). Další informace najdete v tématu [– možnosti kompilátoru](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **CL** úloh. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
- **AdditionalIncludeDirectories**  
  
   Volitelný parametr, řetězec [].  
  
   Přidá adresář do seznamu adresáře, které se budou hledat vkládané soubory.  
  
   Další informace najdete v tématu [/I (další vložené adresáře)](http://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   Volitelný parametr řetězce.  
  
   Seznam možností příkazového řádku. Například "/*možnost1* /*možnost2* /*možnost #*". Tento parametr použijte k určení možnosti příkazového řádku, které nejsou reprezentovány všechny ostatní parametry úlohy.  
  
   Další informace najdete v tématu [– možnosti kompilátoru](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories** parametr volitelný řetězec [].  
  
   Určuje adresář, který kompilátor bude vyhledávání pro přeložení referencí souboru předaných **#using** směrnice.  
  
   Další informace najdete v tématu [/AI (zadat adresáře metadat)](http://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   Volitelný parametr řetězce.  
  
   Řetězec, který vždy získá, protože ho v příkazovém řádku. Výchozí hodnota je "**/c**".  
  
- **AssemblerListingLocation**  
  
   Vytvoří soubor výpisu, který obsahuje kód sestavení.  
  
   Další informace najdete v tématu **/Fa** možnost [/FA, /Fa (soubor výpisu)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   Volitelný parametr řetězce.  
  
   Vytvoří soubor výpisu, který obsahuje kód sestavení.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NoListing** - *\<žádné >*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** -   **/FAC**  
  
  - **AssemblyAndSourceCode** -   **/FAS**  
  
  - **Všechny** -   **/facs**  
  
    Další informace najdete v tématu **/FA**, **/FAC**, **/FAS**, a **/facs** možnosti [/FA, /Fa (výpis soubor)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   Volitelný parametr řetězce.  
  
   Povolí nebo zakáže funkci kontroly chyb za běhu ve spojení s [runtime_checks –](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) direktivy pragma.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** -                          *\<žádné >*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **za**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Další informace najdete v tématu [/RTC (kontroly chyb za běhu)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, vytvoří soubor informací o procházení.  
  
   Další informace najdete v tématu **/FR** možnost [/FR, /Fr (vytvořit. Soubor SBR)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   Volitelný parametr řetězce.  
  
   Určuje název souboru pro informačního souboru procházení.  
  
   Další informace najdete v tématu **BrowseInformation** parametr v této tabulce a také viz [/FR, /Fr (vytvořit. Soubor SBR)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, rozpozná některá přetečení vyrovnávací paměti, která přepisují návratovou adresu běžná technika pro využívání kódu, která nevynucuje omezení velikosti vyrovnávací paměti.  
  
   Další informace najdete v tématu [/GS (Kontrola zabezpečení vyrovnávací paměti)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
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
  
    Další informace najdete v tématu [/Gd, / GR, / gv, /Gz (konvence volání)](http://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   Volitelný parametr řetězce.  
  
   Určuje, jestli se má kompilovat vstupní soubor jako zdrojový soubor jazyka C nebo C++.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - *\<žádné >*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Další informace najdete v tématu [/Tc /Tp, /TC, /TP (určení typu zdrojového souboru)](http://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   Volitelný parametr řetězce.  
  
   Umožňuje aplikací a komponent, pokud chcete používat funkce z common language runtime (CLR).  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **false** - *\<žádné >*  
  
  - **Hodnota TRUE** -   **/CLR**  
  
  - **Čistě** -   **/CLR: pure**  
  
  - **Bezpečné** -   **/CLR: safe**  
  
  - **OldSyntax** - **oldSyntax**  
  
    Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotpatchableImage**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, instruuje kompilátor, aby připravit bitovou kopii pro *technologii hot patching*. Tento parametr se zajistí, že první instrukce pro každou funkci je o dva bajty, které jsou požadovány pro technologii hot patching.  
  
   Další informace najdete v tématu [/hotpatch (vytvoření Image vyměnitelné za provozu)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   Volitelný parametr řetězce.  
  
   Vybere typ ladicích informací vytvářených pro program a zda tyto informace jsou uchovávány v souborech objektů (.obj) nebo v databázi programu (PDB).  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Minuskové** -   **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Další informace najdete v tématu [/Z7, / zi, /ZI (formát informací o ladění)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   Volitelný logický parametr.  
  
   Pokud **true**, informuje kompilátor generuje chybu pro konstruktory jazyka, které nejsou kompatibilní s ANSI C a ANSI C++.  
  
   Další informace najdete v tématu **/Za** možnost [/Za, /Ze (zakázat jazyková rozšíření)](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   Volitelný parametr, řetězec [].  
  
   Zakáže čísla upozornění, které jsou určené v seznam oddělený středníkem.  
  
   Další informace najdete v tématu `/wd` možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   Volitelný parametr řetězce.  
  
   Určuje architekturu pro generování kódu, který používá Streaming SIMD Extensions (SSE) a Streaming SIMD Extensions 2 (SSE2) pokyny.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
    Další informace najdete v tématu [/arch (x86)](http://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, podporují bezpečnost vlákna pro data Alokovaná pomocí statického úložiště lokálního vlákna, to znamená, že data Alokovaná pomocí `__declspec(thread)`.  
  
   Další informace najdete v tématu [/GT (Podpora úložiště Thread-Local zabezpečenými Vlákénky)](http://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, povolit analýzu kódu.  
  
   Další informace najdete v tématu [/ analyze (Analýza kódu)](http://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   Volitelný parametr řetězce.  
  
   Umožňuje poskytnout informace o kompilátoru vnitřní chybě (ICE) přímo společnosti Microsoft. Ve výchozím nastavení v integrovaném vývojovém prostředí sestavení je **výzvy** a nastavení v sestavení příkazového řádku je **fronty**.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Žádný** -   **/errorreport: žádné**  
  
  - **Řádek** - **/errorReport:prompt**  
  
  - **Fronty** - **/errorReport:queue**  
  
  - **Odeslat** -   **/errorreport: Send**  
  
    Další informace najdete v tématu [/errorreport (sestava interními chybami kompilátoru)](http://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   Volitelný parametr řetězce.  
  
   Určuje model zpracování výjimek pro použití kompilátorem.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **false** - *\<žádné >*  
  
  - **Asynchronní** -   **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Další informace najdete v tématu [/EH (Model zpracování výjimek)](http://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, vytvoří soubor výpisu, který se rozšířila atributy vloženými do zdrojového souboru.  
  
   Další informace najdete v tématu [/Fx (sloučení vloženého kódu)](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   Volitelný parametr řetězce.  
  
   Určuje, jestli se má upřednostnit kód velikost nebo rychlost kódu.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Ani** - *\<žádné >*  
  
  - **Velikost** -   **/OS**  
  
  - **Rychlost** - **/Ot**  
  
    Další informace najdete v tématu [/OS, /Ot (upřednostnění malého kódu, upřednostnění rychlého kódu)](http://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, umožňuje spolehlivé výjimky s plovoucí desetinnou čárkou modelu. Výjimky, bude vyvolána okamžitě po aktivaci.  
  
   Další informace najdete v tématu /**fp: except** možnost [/fp (určení chování plovoucí desetinné čárky)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   Volitelný parametr řetězce.  
  
   Nastaví plovoucí bodu modelu.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Přesné** -   **/FP: precise**  
  
  - **Striktní** -   **/FP: strict**  
  
  - **Rychlé** - **Fast**  
  
    Další informace najdete v tématu [/fp (určení chování plovoucí desetinné čárky)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   Volitelný logický parametr.  
  
   Pokud `true`, implementuje standardního chování jazyka C++ v [pro](http://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) smyček, které používají rozšíření společnosti Microsoft ([/Ze](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Další informace najdete v tématu [/Zc: forscope (vynutit dodržování standardu pro obor cyklu for)](http://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   Volitelné `String[]` parametru.  
  
   Způsobí, že preprocesor zpracovat jeden nebo více souborů zadanou hlavičku.  
  
   Další informace najdete v tématu [/FI (vynucené soubor zahrnutí názvu)](http://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   Volitelné **String []** parametru.  
  
   Způsobí, že preprocesor zpracovat jeden nebo více zadaných **#using** soubory.  
  
   Další informace najdete v tématu [/FU (vynuceným názvem #using souboru)](http://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, umožňuje kompilátoru balíček individuálních funkcí ve formě zabalených funkcí (sekvence Comdat).  
  
   Další informace najdete v tématu [/Gy (povolení funkce propojení na úrovni)](http://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že kompilátor zpracovat dokumentaci komentáře do souborů zdrojového kódu a pokud chcete vytvořit soubor .xdc pro každý zdroj souboru kódu, který se dokumentační komentáře.  
  
   Další informace najdete v tématu [/DOC (zpracování dokumentačních komentářů) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Viz také **XMLDocumentationFileName** parametr v této tabulce.  
  
- **IgnoreStandardIncludePath**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zabraňuje kompilátor hledal soubory k zahrnutí v adresářích zadaných v proměnné prostředí PATH či INCLUDE.  
  
   Další informace najdete v tématu [/X (Ignore Standard Include Paths)](http://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje úroveň rozbalení vložených funkcí pro sestavení.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - *\<žádné >*  
  
  - **Zakázané** - **příkazu/ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** -   **/ob2**  
  
    Další informace najdete v tématu [/Ob (rozbalení vložené funkce)](http://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **Intrinsicfunctions –**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, nahradí určitou funkci volání s vnitřní nebo jinak speciální formuláře funkce, které vaší aplikaci pomůžou pracovat rychleji.  
  
   Další informace najdete v tématu [/Oi (Generovat vnitřní funkce)](http://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, povolí minimální opětovné sestavení, která určuje, zda zdrojové soubory C++ obsahující změněné C++ třídy definice (uložené v souborech hlaviček (.h)) musí zopakovat.  
  
   Další informace najdete v tématu [/Gm (povolení minimálního opětovného sestavení)](http://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, kompilaci pomocí více procesorů. Tento parametr vytvoří proces pro každý efektivní procesor ve vašem počítači.  
  
   Další informace najdete v tématu [/MP (sestavení pomocí několika procesů)](http://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Další informace naleznete **ProcessorNumber** parametr v této tabulce.  
  
- **ObjectFileName**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název souboru objektů (.obj) nebo adresáře se použije místo výchozího.  
  
   Další informace najdete v tématu [/Fo (název souboru objektů)](http://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   Volitelné **String []** parametru.  
  
   Seznam souborů objektů.  
  
- **OmitDefaultLibName**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, vynechá výchozí název knihovny run-time C ze souboru objektů (.obj). Ve výchozím nastavení kompilátor vloží název tohoto knihovny do souboru .obj pro přesměrování linkeru, aby je správná knihovna.  
  
   Další informace najdete v tématu [/Zl (vynechat název výchozí knihovny)](http://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, potlačí vytváření ukazatelů rámců v zásobníku volání.  
  
   Další informace najdete v tématu [/Oy (vynechání ukazatele na rámec)](http://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že kompilátor zpracování OpenMP – klauzule a direktivy.  
  
   Další informace najdete v tématu [/OpenMP (povolit podporu OpenMP 2.0)](http://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **Optimalizace**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje různé kód optimalizací pro rychlost a velikosti.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Zakázané** - **/Od**  
  
  - **MinSpace** -   **/O1**  
  
  - **MaxSpeed** -   **/O2**  
  
  - **Úplné** - **/Ox**  
  
    Další informace najdete v tématu [/O možnosti (Optimalizace kódu)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   Volitelné **řetězec** parametru.  
  
   Vytvořit nebo použít soubor předkompilované hlavičky (pch) během sestavení.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NotUsing** - *\<žádné >*  
  
  - **Vytvoření** - **/Yc**  
  
  - **Použití** - **/Yu**  
  
    Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) a [/Yu (Použít předkompilovaný hlavičkový soubor)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Další informace naleznete **PrecompiledHeaderFile** a **PrecompiledHeaderOutputFile** parametry v této tabulce.  
  
- **PrecompiledHeaderFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název souboru předkompilované hlavičky vytvořit nebo použít.  
  
   Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) a [/Yu (Použít předkompilovaný hlavičkový soubor)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název cesty pro předkompilované hlavičky místo použití výchozí název cesty.  
  
   Další informace najdete v tématu [/Fp (název. Soubor pch)](http://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zachová komentáře při předzpracování.  
  
   Další informace najdete v tématu [/C (zachovat komentáře při předběžném zpracování)](http://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   Volitelné `String[]` parametru.  
  
   Definuje symbol předzpracování pro zdrojový soubor.  
  
   Další informace najdete v tématu [/D (Definice preprocesoru)](http://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   Volitelné `ITaskItem[]` parametru.  
  
   Definuje pole objektů preprocesoru výstupní položky, které lze používat a, protože ho vygeneroval úlohy.  
  
- **PreprocessOutputPath**  
  
   Volitelné `String` parametru.  
  
   Určuje název výstupního souboru, do kterého **PreprocessToFile** parametr zapíše Předzpracovaný výstup.  
  
   Další informace najdete v tématu [/Fi (předběžné zpracování název výstupního souboru)](http://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`předzpracuje zdrojové soubory jazyka C a C++ a zkopíruje soubory předzpracovaná do standardního výstupního zařízení.  
  
   Další informace najdete v tématu [/EP (předběžné zpracování do direktiv bez příkazů #line)](http://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`předzpracuje zdrojové soubory jazyka C a C++ a zapíše Předzpracovaný výstup do souboru.  
  
   Další informace najdete v tématu [/P (předběžné zpracování souboru)](http://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   Volitelné `Integer` parametru.  
  
   Určuje maximální počet procesorů pro použití v kompilaci s více procesory. Tento parametr použijte v kombinaci s **MultiProcessorCompilation** parametru.  
  
- **ProgramDataBaseFileName**  
  
   Volitelné `String` parametru.  
  
   Určuje název souboru pro soubor databáze (PDB) programu.  
  
   Další informace najdete v tématu [/Fd (název souboru databáze programu)](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   Volitelné `String` parametru.  
  
   Určuje, jestli je knihovna DLL vícevláknový modul a vybere prodejní nebo ladicí verze knihovny run-time.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Vícevláknové** -   **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** -   **/MDd**  
  
    Další informace najdete v tématu [/ / MD, / MT, /LD (použití knihovny Run-Time)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, přidá kód pro kontrolu typů objektů jazyka C++ za běhu (informace typu za běhu).  
  
   Další informace najdete v tématu [/GR (povolení běhové informace o typu)](http://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že kompilátor výstup seznam vložených souborů.  
  
   Další informace najdete v tématu [/showincludes (seznam vložených souborů)](http://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, pokud hodnota je přiřazená menší datový typ a vede ke ztrátě dat sestavy chyb za běhu.  
  
   Další informace najdete v tématu **/RTCc** možnost [/RTC (kontroly chyb za běhu)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **Zdroje**  
  
   Vyžaduje `ITaskItem[]` parametru.  
  
   Určuje seznam zdrojových souborů, oddělené mezerami.  
  
- **StringPooling**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, umožňuje kompilátoru vytvořit jednu kopii shodného řetězce do bitové kopie programu.  
  
   Další informace najdete v tématu [/GF (odstranění duplicitní řetězce)](http://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
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
  
    Další informace najdete v tématu [/Zp (zarovnání členů struktury)](http://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.  
  
   Další informace najdete v tématu [/nologo (Potlačení úvodního nápisu) (C/C++)](http://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   Volitelné `String` parametru.  
  
   Určuje zprostředkující adresář, kde jsou uloženy protokoly sledování pro tuto úlohu.  
  
   Další informace najdete v tématu **TLogReadFiles** a **TLogWriteFiles** parametry v této tabulce.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Volitelné **String []** parametru.  
  
   Zpracovává zadaný seznam upozornění kompilátoru jako chyby.  
  
   Další informace najdete v tématu **/we** `n` možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zpracovávat všechna upozornění kompilátoru jako chyby.  
  
   Další informace najdete v tématu **/WX** možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zpracovávat `wchar_t` typ jako nativního typu.  
  
   Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](http://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, nedefinovaných hodnot, které kompilátor definuje symboly specifické pro společnost Microsoft.  
  
   Další informace najdete v tématu **/u** možnost [/U, /u (nedefinované symboly)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   Volitelné `String[]` parametru.  
  
   Určuje seznam jednoho nebo více symboly preprocesoru definice.  
  
   Další informace najdete v tématu **/U** možnost [/U, /u (nedefinované symboly)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zobrazí úplnou cestu souborů se zdrojovým kódem předány kompilátoru v diagnostice.  
  
   Další informace najdete v tématu [/FC (úplná cesta ze souboru zdrojového kódu v diagnostice)](http://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, způsobí, že výstupní soubor bude vytvořena ve formátu UTF-8.  
  
   Další informace najdete v tématu **/fau vytvořte** možnost [/FA, /Fa (soubor výpisu)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
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
  
    Další informace najdete v tématu **/W**_n_ možnost [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, povolí optimalizaci celého programu.  
  
   Další informace najdete v tématu [/GL (optimalizace celého programu)](http://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   Volitelné `String` parametru.  
  
   Určuje název vygenerovaných dokumentačních souborů XML. Tento parametr může být název souboru nebo adresáře.  
  
   Další informace najdete v tématu `name` argument v [/DOC (zpracování dokumentačních komentářů) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Viz také **GenerateXMLDocumentationFiles** parametr v této tabulce.  
  
- **MinimalRebuildFromTracking**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, provádí sledované přírůstkové sestavení; Pokud `false`, se provádí opětovné sestavení.  
  
- **TLogReadFiles**  
  
   Volitelné `ITaskItem[]` parametru.  
  
   Určuje pole, které představují *přečíst soubor protokoly sledování*.  
  
   Protokolu sledování souborů pro čtení (.tlog) obsahuje názvy vstupních souborů, které jsou přečteny úkolu a používá systém sestavení projektu pro podporu přírůstkové sestavení. Další informace najdete v tématu **TrackerLogDirectory** a **vlastnost TrackFileAccess** parametry v této tabulce.  
  
- **TLogWriteFiles**  
  
   Volitelné `ITaskItem[]` parametru.  
  
   Určuje pole, které představují *zapisovat do souboru protokoly sledování*.  
  
   Protokolu sledování souborů zápisu (.tlog) obsahuje názvy výstupní soubory, které jsou zapsány úlohou a používá systém sestavení projektu pro podporu přírůstkové sestavení. Další informace najdete v tématu **TrackerLogDirectory** a **vlastnost TrackFileAccess** parametry v této tabulce.  
  
- **TrackFileAccess**  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, sleduje vzory přístupu k souboru.  
  
   Další informace najdete v tématu **TLogReadFiles** a **TLogWriteFiles** parametry v této tabulce.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



