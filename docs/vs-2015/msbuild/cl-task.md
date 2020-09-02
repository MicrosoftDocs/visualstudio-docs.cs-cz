---
title: CL – úloha | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8307bc2c9efcbbab531754cd2d49fa18b04cc48a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698641"
---
# <a name="cl-task"></a>CL – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí nástroj Visual C++ kompilátoru cl.exe. Kompilátor vytváří spustitelné soubory (. exe), soubory dynamické knihovny (. dll) nebo soubory modulu kódu (. netmodule). Další informace naleznete v tématu [Možnosti kompilátoru](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **CL** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.  
  
- **AdditionalIncludeDirectories**  
  
   Parametr volitelného řetězce [].  
  
   Přidá adresář do seznamu adresářů, ve kterých jsou vyhledávány soubory k zahrnutí.  
  
   Další informace najdete v tématu [/i (další adresáře k zahrnutí)](https://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   Volitelný řetězcový parametr.  
  
   Seznam možností příkazového řádku Například "/*možnost1*  / *možnost2*  / *Option #*". Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy.  
  
   Další informace naleznete v tématu [Možnosti kompilátoru](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories** Parametr volitelného řetězce [].  
  
   Určuje adresář, který kompilátor bude hledat k překladu odkazů na soubory předaných do direktivy **#using** .  
  
   Další informace najdete v tématu [/AI (určení adresářů metadat)](https://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   Volitelný řetězcový parametr.  
  
   Řetězec, který je vždy generován na příkazovém řádku. Výchozí hodnota je "**/c**".  
  
- **AssemblerListingLocation**  
  
   Vytvoří soubor výpisu, který obsahuje kód sestavení.  
  
   Další informace naleznete v možnosti **/Fa** v [/FA,/FA (soubor výpisu)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   Volitelný řetězcový parametr.  
  
   Vytvoří soubor výpisu, který obsahuje kód sestavení.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Seznam není** - *\<none>*  
  
  - **AssemblyCode**  -  **/FA**  
  
  - **AssemblyAndMachineCode**  -  **/FAc**  
  
  - **AssemblyAndSourceCode**  -  **/FAS**  
  
  - **Vše**  -  **/FAcs**  
  
    Další informace najdete v tématu možnosti **/Fa**, **/FAc**, **/FAS**a **/FAcs** v [/FA,/FA (soubor výpisu)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   Volitelný řetězcový parametr.  
  
   Povolí nebo zakáže funkci kontroly chyb za běhu ve spojení s direktivou pragma [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) .  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** -                          *\<none>*  
  
  - **StackFrameRuntimeCheck**  -  **/RTCs**  
  
  - **UninitializedLocalUsageCheck**  -  **/RTCu**  
  
  - **EnableFastChecks**  -                           **/RTC1**  
  
    Další informace naleznete v tématu [/RTC (kontrola chyb za běhu)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   Volitelný logický parametr.  
  
   Pokud `true` se vytvoří soubor s informacemi o procházení.  
  
   Další informace naleznete v možnosti **/fr** v [/fr,/fr (Create. Soubor SBR)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   Volitelný řetězcový parametr.  
  
   Určuje název souboru s informacemi o procházení.  
  
   Další informace najdete v parametru **BrowseInformation** v této tabulce a také v tématu [/fr,/fr (Create. Soubor SBR)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   Volitelný logický parametr.  
  
   Pokud `true` aplikace zjistí některé přetečení vyrovnávací paměti, které přepíší zpáteční adresu, jedná se o běžnou techniku pro zneužití kódu, který nevynutil omezení velikosti vyrovnávací paměti.  
  
   Další informace najdete v tématu [/GS (kontrolní zabezpečení vyrovnávací paměti)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
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
  
    Další informace naleznete v tématu [/GD,/GR,/GV,/GZ (konvence volání)](https://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   Volitelný řetězcový parametr.  
  
   Určuje, zda má být vstupní soubor kompilován jako zdrojový soubor jazyka C nebo C++.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - *\<none>*  
  
  - **CompileAsC**  -  **/TC**  
  
  - **CompileAsCpp**  -  **/TP**  
  
    Další informace naleznete v tématu [/TC,/TP,/TC,/TP (určení typu zdrojového souboru)](https://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   Volitelný řetězcový parametr.  
  
   Umožňuje aplikacím a komponentám používat funkce z modulu CLR (Common Language Runtime).  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **chybné** - *\<none>*  
  
  - **hodnota true**  -  **/CLR**  
  
  - **Čistý**  -  **/clr: Pure**  
  
  - **Bezpečná**  -  **/clr: Safe**  
  
  - **OldSyntax**  -  **/clr: oldSyntax**  
  
    Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotpatchableImage**  
  
   Volitelný logický parametr.  
  
   Pokud `true` aplikace, instruuje kompilátor, aby připravil obrázek pro *Hot patching*. Tento parametr zajišťuje, že první instrukce každé funkce jsou dvě bajty, které jsou požadovány pro Hot patching.  
  
   Další informace najdete v tématu [/hotpatch (Create opravitelnou za provozu image)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   Volitelný řetězcový parametr.  
  
   Vybere typ ladicích informací vytvořených pro program a zda jsou tyto informace uloženy v souborech objektů (. obj) nebo v databázi programu (PDB).  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **OldStyle**  -  **/Z7**  
  
  - **ProgramDatabase**  -  **/Zi**  
  
  - **EditAndContinue**  -  **/Zi**  
  
    Další informace naleznete v tématu [/Z7,/Zi,/Zi (formát ladicích informací)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   Volitelný logický parametr.  
  
   Pokud je **true**, instruuje kompilátor, aby vygeneroval chybu pro jazykové konstrukce, které nejsou kompatibilní se standardem ANSI C nebo ANSI C++.  
  
   Další informace najdete v možnosti **/za** v [/za,/ze (zakázání jazykových rozšíření)](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   Parametr volitelného řetězce [].  
  
   Zakáže čísla upozornění, která jsou uvedena v seznamu středníkem oddělených.  
  
   Další informace najdete `/wd` v tématu možnost v příkazech [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   Volitelný řetězcový parametr.  
  
   Určuje architekturu pro generování kódu, která používá instrukce Streaming SIMD Extensions (SSE) a Streaming SIMD Extensions 2 (SSE2).  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **StreamingSIMDExtensions**  -  **/arch: SSE**  
  
  - **StreamingSIMDExtensions2**  -  **/arch: SSE2**  
  
    Další informace najdete v tématu [/arch (x86)](https://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   Volitelný logický parametr.  
  
   Pokud `true` podporuje bezpečnost vlákna pro data přidělená pomocí statického úložiště místního vlákna, to znamená data přidělená pomocí `__declspec(thread)` .  
  
   Další informace najdete v tématu [/gt (podpora místního úložiště s vlákny pro vlákno)](https://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   Volitelný logický parametr.  
  
   Pokud chcete `true` Povolit analýzu kódu.  
  
   Další informace naleznete v tématu [/analyze (analýza kódu)](https://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   Volitelný řetězcový parametr.  
  
   Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo společnosti Microsoft. Ve výchozím nastavení je nastavení v rozhraní IDE **vyzváné** a nastavení v sestavení příkazového řádku je **Queue**.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Žádné**  -  **/errorreport: none**  
  
  - **Zobrazit výzvu**  -  **/errorreport: prompt**  
  
  - **Fronta**  -  **/errorreport: Queue**  
  
  - **Odeslat**  -  **/errorreport: Send**  
  
    Další informace najdete v tématu [/errorreport (hlášení chyb interních kompilátorů)](https://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   Volitelný řetězcový parametr.  
  
   Určuje model zpracování výjimek, který má kompilátor použít.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **chybné** - *\<none>*  
  
  - **Asynchronní**  -  operace **/EHa**  
  
  - **Synchronizovat**  -  **/EHsc**  
  
  - **SyncCThrow**  -  **/EHS**  
  
    Další informace naleznete v tématu [/EH (model zpracování výjimek)](https://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   Volitelný logický parametr.  
  
   Pokud `true` , vytvoří soubor výpisu s rozbalenými atributy vloženými do zdrojového souboru.  
  
   Další informace najdete v tématu [/FX (sloučení vloženého kódu)](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   Volitelný řetězcový parametr.  
  
   Určuje, zda má být upřednostněna velikost kódu nebo rychlost kódu.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Ani** - *\<none>*  
  
  - **Velikost**  -  **/OS**  
  
  - **Rychlost**  -  **/Ot**  
  
    Další informace najdete v tématu [/OS,/ot (upřednostnění malého kódu, upřednostnění rychlého kódu)](https://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   Volitelný logický parametr.  
  
   `true`V případě, umožňuje spolehlivý model výjimek s plovoucí desetinnou čárkou. Výjimky budou vyvolány okamžitě po aktivaci.  
  
   Další informace naleznete v tématu/**FP: except** – možnost v [/FP (určení chování s plovoucí](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e)desetinnou čárkou).  
  
- **FloatingPointModel**  
  
   Volitelný řetězcový parametr.  
  
   Nastaví model plovoucí desetinné čárky.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Přesná**  -  **/FP: přesný**  
  
  - **Striktní**  -  **/FP: Strict**  
  
  - **Rychlé**  -  **/FP: Fast**  
  
    Další informace najdete v tématu [/FP (určení chování s plovoucí](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e)desetinnou čárkou).  
  
- **ForceConformanceInForLoopScope**  
  
   Volitelný logický parametr.  
  
   Pokud `true` , implementuje standardní chování C++ v [pro](https://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) smyčky, které používají rozšíření Microsoft Extensions ([/ze](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Další informace najdete v tématu [/Zc: forScope (vynucení shody v oboru for Loop)](https://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   Volitelný `String[]` parametr.  
  
   Způsobí, že preprocesor zpracuje jeden nebo více zadaných souborů hlaviček.  
  
   Další informace najdete v tématu [/Fi (soubor s vynuceným zahrnutím názvu)](https://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   Parametr volitelného **řetězce []** .  
  
   Způsobí, že preprocesor zpracuje jeden nebo více zadaných **#using** souborů.  
  
   Další informace najdete v tématu [/Fu (název vynuceného #using souboru)](https://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , umožňuje kompilátoru zabalit jednotlivé funkce ve formě zabalených funkcí (sekvence COMDAT).  
  
   Další informace najdete v tématu [/Gy (povolení propojení na úrovni funkcí)](https://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` Nástroj způsobí, že kompilátor zpracuje dokumentační komentáře v souborech zdrojového kódu a vytvoří soubor. xdc pro každý soubor zdrojového kódu, který obsahuje dokumentační komentáře.  
  
   Další informace naleznete v tématu [/doc (zpracování dokumentačních komentářů) (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). V této tabulce se také zobrazí parametr **XMLDocumentationFileName** .  
  
- **IgnoreStandardIncludePath**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , zabrání kompilátoru v hledání souborů include v adresářích zadaných v cestě a proměnných prostředí include.  
  
   Další informace naleznete v části [/x (ignorování standardních cest zahrnutí)](https://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje úroveň rozšíření vložené funkce pro sestavení.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - *\<none>*  
  
  - **Zakázáno**  -  **/Ob0**  
  
  - **OnlyExplicitInline**  -  **/OB1**  
  
  - **AnySuitable**  -  **/Ob2**  
  
    Další informace naleznete v tématu [/ob (rozšíření vložené funkce)](https://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , nahradí některá volání funkce vnitřními nebo jinak speciálními formami funkce, které pomůžou aplikaci rychleji běžet.  
  
   Další informace najdete v tématu [/Oi (generování vnitřních funkcí)](https://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , umožňuje minimální opětovné sestavení, které určuje, zda je nutné znovu zkompilovat zdrojové soubory jazyka c++, které obsahují změněné definice tříd c++ (uložené v hlavičkových souborech (. h)).  
  
   Další informace najdete v tématu [/GM (povolení minimálního opětovného sestavení)](https://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` chcete kompilovat více procesorů, použijte. Tento parametr vytvoří proces pro každý efektivní procesor v počítači.  
  
   Další informace naleznete v tématu [/MP (sestavení s více procesy)](https://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Viz také parametr **ProcessorNumber** v této tabulce.  
  
- **ObjectFileName**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název souboru objektu (. obj) nebo adresář, který má být použit místo výchozí.  
  
   Další informace naleznete v tématu [/FO (název souboru objektu)](https://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   Parametr volitelného **řetězce []** .  
  
   Seznam souborů objektů.  
  
- **OmitDefaultLibName**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , vynechá výchozí název běhové knihovny jazyka C ze souboru objektu (. obj). Ve výchozím nastavení kompilátor umístí do souboru. obj název knihovny a nasměruje linker do správné knihovny.  
  
   Další informace najdete v tématu [/zl (vynechání názvu výchozí knihovny)](https://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , potlačí vytváření ukazatelů rámců v zásobníku volání.  
  
   Další informace naleznete v tématu [/Oy (vynechání ukazatele na rámec)](https://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` Nástroj způsobí, že kompilátor zpracuje klauzule a direktivy OpenMP.  
  
   Další informace najdete v tématu [/OpenMP (povolení podpory openmp 2,0)](https://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **Optimalizace**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje různé optimalizace kódu pro rychlost a velikost.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Zakázáno**  -  **/Od**  
  
  - **MinSpace**  -  **/O1**  
  
  - **MaxSpeed**  -  **/O2**  
  
  - **Úplný**  -  **/Ox**  
  
    Další informace najdete v tématu [Možnosti/o (optimalizace kódu)](https://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   Volitelný **řetězcový** parametr.  
  
   Během sestavování vytvořte nebo použijte soubor předkompilované hlavičky (. pch).  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **NotUsing** - *\<none>*  
  
  - **Vytvořit**  -  **/YC**  
  
  - **Použití**  -  **/Yu**  
  
    Další informace naleznete v tématu [/Yc (Create a Compiled hlavičkový soubor)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) a [/Yu (použít předkompilovaný hlavičkový soubor)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Podívejte se také na parametry **PrecompiledHeaderFile** a **PrecompiledHeaderOutputFile** v této tabulce.  
  
- **PrecompiledHeaderFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název souboru předkompilované hlavičky, který se má vytvořit nebo použít.  
  
   Další informace naleznete v tématu [/Yc (Create a Compiled hlavičkový soubor)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) a [/Yu (použít předkompilovaný hlavičkový soubor)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název cesty pro předkompilovanou hlavičku namísto použití výchozího názvu cesty.  
  
   Další informace najdete v tématu [/FP (název. Soubor PCH)](https://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` aplikace zachová komentáře během předběžného zpracování.  
  
   Další informace najdete v tématu [/c (zachování komentářů během předběžného zpracování)](https://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   Volitelný `String[]` parametr.  
  
   Definuje symbol předzpracování pro zdrojový soubor.  
  
   Další informace naleznete v tématu [/d (Definice preprocesoru)](https://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   Volitelný `ITaskItem[]` parametr.  
  
   Definuje pole výstupních položek preprocesoru, které mohou být spotřebovány a generovány úlohami.  
  
- **PreprocessOutputPath**  
  
   Volitelný `String` parametr.  
  
   Určuje název výstupního souboru, do kterého parametr **PreprocessToFile** zapisuje předzpracovaný výstup.  
  
   Další informace naleznete v tématu [/Fi (předběžné zpracování názvu výstupního souboru)](https://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , předzpracovává zdrojové soubory C a C++ a kopíruje soubory předzpracovaného na standardní výstupní zařízení.  
  
   Další informace naleznete v tématu [/EP (předzpracování do stdout bez #line direktiv)](https://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , předzpracovává zdrojové soubory C a C++ a zapisuje předzpracovaný výstup do souboru.  
  
   Další informace naleznete v tématu [/p (předběžné zpracování souboru)](https://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   Volitelný `Integer` parametr.  
  
   Určuje maximální počet procesorů, které se mají použít při kompilaci ve více procesorech. Tento parametr použijte v kombinaci s parametrem **MultiProcessorCompilation** .  
  
- **ProgramDataBaseFileName**  
  
   Volitelný `String` parametr.  
  
   Určuje název souboru pro soubor databáze programu (PDB).  
  
   Další informace najdete v tématu [/FD (název souboru databáze programu)](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   Volitelný `String` parametr.  
  
   Označuje, zda je vícevláknový modul knihovnou DLL, a vybere prodejní nebo ladicí verze knihovny run-time.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Vícevláknové**  -  **/Mt**  
  
  - **MultiThreadedDebug**  -  **/MTD**  
  
  - **MultiThreadedDLL**  -  **/MD**  
  
  - **MultiThreadedDebugDLL**  -  **/MDD**  
  
    Další informace naleznete v tématu [/MD,/MT,/LD (použití běhové knihovny)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , přidá kód pro kontrolu typů objektů jazyka C++ za běhu (informace o typu za běhu).  
  
   Další informace najdete v tématu [/gr (povolení informací o běhovém typu)](https://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes –**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` dojde k tomu, vyvolá kompilátor výstup seznamu souborů k zahrnutí.  
  
   Další informace najdete v tématu [/showIncludes (seznam vložených souborů)](https://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   Volitelný `Boolean` parametr.  
  
   `true`V případě, že hlásí chybu za běhu, pokud je přiřazena hodnota k menšímu datovému typu a způsobuje ztrátu dat.  
  
   Další informace naleznete v možnosti **/RTCc** v [/RTC (kontrola chyb za běhu)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **zdroje**  
  
   Požadovaný parametr `ITaskItem[]`.  
  
   Určuje seznam zdrojových souborů oddělených mezerami.  
  
- **StringPooling**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , umožňuje kompilátoru vytvořit jednu kopii stejných řetězců v imagi programu.  
  
   Další informace najdete v tématu [/GF (odstranění duplicitních řetězců)](https://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
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
  
    Další informace naleznete v tématu [/zp (zarovnání členů struktury)](https://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.  
  
   Další informace naleznete v tématu [/nologo (potlačení úvodního nápisu při spouštění) (C/C++)](https://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   Volitelný `String` parametr.  
  
   Určuje zprostředkující adresář, ve kterém jsou uložené protokoly sledování pro tento úkol.  
  
   Další informace najdete v tématu parametry **TLogReadFiles** a **TLogWriteFiles** v této tabulce.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Parametr volitelného **řetězce []** .  
  
   Zachází s zadaným seznamem upozornění kompilátoru jako s chybami.  
  
   Další informace najdete v tématu možnost **/We** `n` v [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , považovat všechna upozornění kompilátoru za chyby.  
  
   Další informace najdete v tématu **/WX** Option v [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` je typ považován za `wchar_t` nativní typ.  
  
   Další informace naleznete v tématu [/Zc: wchar_t (Wchar_t je nativní typ)](https://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , zruší definici symbolů specifických pro společnost Microsoft, které definuje kompilátor.  
  
   Další informace naleznete v možnosti **/u** v části [/u,/u (nedefinované symboly)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   Volitelný `String[]` parametr.  
  
   Určuje seznam jednoho nebo více symbolů preprocesoru, které mají být nedefinovány.  
  
   Další informace naleznete v části **/u** Option v [/u,/u (nedefinované symboly)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , zobrazí úplnou cestu souborů se zdrojovým kódem předaných kompilátoru v diagnostice.  
  
   Další informace naleznete v tématu [/FC (úplná cesta k souboru zdrojového kódu v diagnostice)](https://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` Nástroj způsobí, že se výstupní soubor vytvoří ve formátu UTF-8.  
  
   Další informace naleznete v možnosti **/FAU** v [/FA,/FA (soubor výpisu)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
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
  
    Další informace naleznete v části **/w**_n_ v příkazu [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` , povolí optimalizaci celého programu.  
  
   Další informace naleznete v tématu [/GL (celá optimalizace programu)](https://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   Volitelný `String` parametr.  
  
   Určuje název generovaných souborů dokumentace XML. Tento parametr může být název souboru nebo adresáře.  
  
   Další informace naleznete `name` v argumentu v [/doc (Process dokumentačních komentářů) (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). V této tabulce se také zobrazí parametr **GenerateXMLDocumentationFiles** .  
  
- **MinimalRebuildFromTracking**  
  
   Volitelný `Boolean` parametr.  
  
   Je-li `true` provedeno sledované přírůstkové sestavení, je-li `false` provedeno opětovné sestavení.  
  
- **TLogReadFiles**  
  
   Volitelný `ITaskItem[]` parametr.  
  
   Určuje pole položek, které reprezentují *protokoly sledování čtecího souboru*.  
  
   Protokol sledování souboru Readme (. tlog) obsahuje názvy vstupních souborů, které jsou čteny úlohou a které používá systém sestavení projektu pro podporu přírůstkových sestavení. Další informace najdete v tématu parametry **TrackerLogDirectory** a **TrackFileAccess** v této tabulce.  
  
- **TLogWriteFiles**  
  
   Volitelný `ITaskItem[]` parametr.  
  
   Určuje pole položek, které reprezentují *protokoly sledování souborů*.  
  
   Protokol sledování zápisu souboru (. tlog) obsahuje názvy výstupních souborů, které jsou zapsány úlohou a které používá systém sestavení projektu pro podporu přírůstkových sestavení. Další informace najdete v tématu parametry **TrackerLogDirectory** a **TrackFileAccess** v této tabulce.  
  
- **TrackFileAccess**  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` aplikace sleduje vzory přístupu k souborům.  
  
   Další informace najdete v tématu parametry **TLogReadFiles** a **TLogWriteFiles** v této tabulce.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
