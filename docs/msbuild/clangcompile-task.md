---
title: Úloha ClangCompile | Microsoft Docs
description: Popisuje účel a parametry úlohy ClangCompile MSBuild, která balí nástroj kompilátoru jazyka C++, clang.exe.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 63b278f322e66e6622064288d322709c51df336d
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796820"
---
# <a name="clangcompile-task"></a>ClangCompile – úloha

Zabalí nástroj kompilátoru Microsoft C++, clang.exe.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **ClangCompile** .

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parametr volitelného **řetězce []** .<br/><br/>Určuje jeden nebo více adresářů, které mají být přidány do cesty include; oddělte je středníkem, pokud je více než jedna.<br/><br/>Použijte `-I[path]`.|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.|
|**BufferSecurityCheck**|Volitelný **řetězcový** parametr.<br/><br/>Kontrola zabezpečení pomáhá detekovat přetečení vyrovnávací paměti zásobníku, což je běžný pokus o útok na zabezpečení programu. <br/><br/>Použijte `fstack-protector`.|
|**BuildingInIde**|Volitelný parametr **bool** .|
|**CLanguageStandard**|Volitelný **řetězcový** parametr.<br/><br/>Určuje standard jazyka C.<br/><br/>Použijte `std=[value]` s hodnotou **c89** , **C99** , **C11** , **gnu99** nebo **gnu11** .|
|**ClangVersion**|Volitelný **řetězcový** parametr.|
|**CompileAs**|Volitelný **řetězcový** parametr.<br/><br/>Umožňuje vybrat možnost jazyka kompilace pro soubory. c a. cpp. Výchozí hodnota se detekuje na základě rozsahu. c nebo. cpp.<br/><br/>Použijte `-x c` , `-x c++` .|
|**CppLanguageStandard**|Volitelný **řetězcový** parametr.<br/><br/>Určuje standard jazyka C++.<br/><br/>Použijte `std=[value]` s hodnotou **c++ 98** , **c++ 11** , **c + + 1Y** , **GNU + + 98** , **GNU + + 11** nebo **GNU + + 1Y** .|
|**DataLevelLinking**|Volitelný parametr **bool** .<br/><br/>Umožňuje optimalizaci linkeru odebrat nepoužívaná data vygenerováním jednotlivých datových položek v samostatné části.|
|**DebugInformationFormat**|Volitelný **řetězcový** parametr.<br/><br/>Určuje typ ladicích informací generovaných kompilátorem.<br/><br/>**Žádné** , nevytváří žádné ladicí informace, takže kompilace může být rychlejší (použijte `g0` ).<br/>**FullDebug** vygenerujte informace o ladění DWARF2 (použít `g2 -gdwarf-2` ).<br/>**Číslo řádku** , generuje jenom informace o číslech řádků (použijte `gline-tables-only` ).|
|**EnableNeonCodegen**|Volitelný parametr **bool** .<br/><br/>Povoluje generování kódu pro hardware s plovoucí desetinnou čárkou NEON. To platí jenom pro architekturu ARM.|
|**ExceptionHandling**|Volitelný **řetězcový** parametr.<br/><br/>Určuje model zpracování výjimek, který má kompilátor použít.<br/><br/>**Zakázáno** , zakázat zpracování výjimek (použít `fno-exceptions` ).<br/>**Povoleno** , povolit zpracování výjimek (použít `fexceptions` ).<br/>**UnwindTables** vygeneruje všechna potřebná statická data, ale neovlivňuje generovaný kód (Use `funwind-tables` ).|
|**FloatABI**|Volitelný **řetězcový** parametr.<br/><br/>Možnost výběru pro výběr plovoucí desetinné čárky.<br/><br/>**Soft** , způsobí, že kompilátor generuje výstup obsahující volání knihovny pro operace s plovoucí desetinnou čárkou (použít `mfloat-abi=soft` ).<br/>**softfp** umožňuje generování kódu pomocí hardwarových instrukcí s plovoucí desetinnou čárkou, ale stále používá konvence volání Soft-float (použít `mfloat-abi=softfp` ).<br/>**pevné** , umožňuje generování instrukcí s plovoucí desetinnou čárkou a používá konvence volání specifické pro FPU (použít `mfloat-abi=hard` ).|
|**ForcedIncludeFiles**|Parametr volitelného **řetězce []** .<br/><br/>Jeden nebo více souborů s vynuceným zahrnutím.<br/><br/>Použijte `-include [name]`.|
|**FunctionLevelLinking**|Volitelný parametr **bool** .<br/><br/>Umožňuje kompilátoru zabalit jednotlivé funkce ve formě zabalených funkcí (sekvence COMDAT). Vyžaduje se pro úpravy a pokračování v práci.<br/><br/>Použijte `ffunction-sections`.|
|**GccToolChain**|Volitelný **řetězcový** parametr.<br/><br/>Cesta ke složce pro řetězec nástroje RSZ|
|**GNUMode**|Volitelný parametr **bool** .<br/><br/>|
|**MSCompatibility**|Volitelný parametr **bool** .<br/><br/>Povolí plnou kompatibilitu Microsoft C++.|
|**MSCompatibilityVersion**|Volitelný **řetězcový** parametr.<br/><br/>Hodnota oddělená tečkou představující číslo verze kompilátoru Microsoftu, které se má ohlásit v _MSC_VER (0 = nedefinovat (výchozí)).|
|**MSExtensions**|Volitelný parametr **bool** .<br/><br/>Přijmout některé nestandardní konstrukce podporované kompilátorem Microsoftu.|
|**MSCompilerVersion**|Volitelný **řetězcový** parametr.<br/><br/>Číslo verze kompilátoru Microsoftu, které se má ohlásit v _MSC_VER (0 = nedefinovat (výchozí)).|
|**MSVCErrorReport**|Volitelný parametr **bool** .<br/><br/>Oznamovat chyby, které může Visual Studio použít k analýze informací o souboru a řádku.|
|**ObjectFileName**|Volitelný **řetězcový** parametr.<br/><br/>Určuje název, kterým se má přepsat výchozí název souboru objektu. může být název souboru nebo adresáře.<br/><br/>Použijte `/Fo[name]`.|
|**OmitFramePointers**|Volitelný parametr **bool** .<br/><br/>Zakazuje vytváření ukazatelů na rámce v zásobníku volání.|
|**Optimalizace**|Volitelný **řetězcový** parametr.<br/><br/>Určuje úroveň optimalizace pro aplikaci.<br/><br/>**Vlastní** a vlastní optimalizace.<br/>**Zakázáno** , zakázat optimalizaci (použít `O0` ).<br/>**MinSize** , optimalizovat pro velikost (použít `Os` ).<br/>**MaxSpeed** , optimalizujte pro rychlost (použití `O2` ).<br/>**Plně** náročná optimalizace (použití `O3` ).|
|**PositionIndependentCode**|Volitelný parametr **bool** .<br/><br/>Generuje nezávislý kód pozice (PIC) pro použití ve sdílené knihovně.|
|**PrecompiledHeader**|Volitelný **řetězcový** parametr.<br/><br/>Povolí vytvoření nebo použití předkompilované hlavičky během sestavení.|
|**PrecompiledHeaderFile**|Volitelný **řetězcový** parametr.<br/><br/>Určuje název hlavičkového souboru, který se má použít pro soubor předkompilované hlavičky. Tento soubor bude také přidán do **vynucených souborů k zahrnutí** během sestavení.|
|**PrecompiledHeaderOutputFileDirectory**|Volitelný **řetězcový** parametr.<br/><br/>Určuje adresář pro generovanou předkompilovanou hlavičku. Tento adresář se přidá také k **dalším adresářům include** během sestavování.|
|**PrecompiledHeaderCompileAs**|Volitelný **řetězcový** parametr.<br/><br/>Umožňuje vybrat možnost jazyka kompilace pro soubor předkompilované hlavičky.<br/><br/>Použijte `-x c-header` , `-x c++-header` .|
|**PreprocessorDefinitions**|Parametr volitelného **řetězce []** .<br/><br/>Definuje symboly předzpracování pro zdrojový soubor.<br/><br/>Použijte `-D`.|
|**RuntimeLibrary**|Volitelný **řetězcový** parametr.<br/><br/>Zadejte běhovou knihovnu pro propojování.<br/><br/>Použijte `MSVC /MT` `/MTd` přepínače,, `/MD` , `/MDd` .<br/><br/>**Multithreading** , způsobí, že aplikace použije vícevláknovou a statickou verzi knihovny run-time.<br/>**MultiThreadedDebug** definuje _DEBUG a _MT. Tento parametr navíc způsobí, že kompilátor umístí knihovnu s názvem LIBCMTD.lib do souboru .obj, aby linker použil k překladu externích symbolů soubor LIBCMTD.lib.<br/>**MultiThreadedDLL** způsobí, že aplikace bude používat knihovnu run-time specifickou pro vícevláknovou a DLL. Definuje _MT a _DLL a způsobí, že kompilátor umístí do souboru. obj název knihovny MSVCRT. lib.<br/>**MultiThreadedDebugDLL** , definuje _DEBUG, _MT a _DLL a způsobí, že vaše aplikace bude používat běhovou verzi knihovny run-time, která je specifická pro knihovnu DLL. Navíc způsobí, že kompilátor umístí knihovnu s názvem MSVCRTD.lib do souboru .obj.|
|**RuntimeTypeInfo**|Volitelný parametr **bool** .<br/><br/>Přidá kód pro kontrolu typů objektů jazyka C++ za běhu (informace o typu modulu runtime).<br/><br/>Použijte `frtti` , `fno-rtti` .|
|**ShowIncludes –**|Volitelný parametr **bool** .<br/><br/>Generuje seznam souborů k zahrnutí s výstupem kompilátoru.<br/><br/>Použijte `-H`.|
|**Prostředky**|Povinný parametr **ITaskItem []** .|
|**StrictAliasing**|Volitelný parametr **bool** .<br/><br/>Předpokládají nejpřísnější pravidla aliasování. U objektu jednoho typu se nikdy nepředpokládá, že se nachází na stejné adrese jako objekt jiného typu.|
|**Kořenová složka systému**|Volitelný **řetězcový** parametr.<br/><br/>Cesta ke složce kořenového adresáře pro hlavičky a knihovny.|
|**TargetArch**|Volitelný **řetězcový** parametr.<br/><br/>Cílová architektura|
|**ThumbMode**|Volitelný **řetězcový** parametr.<br/><br/>Vygeneruje kód, který se spustí pro mikroarchitekturu pro palec. To platí jenom pro architekturu ARM.<br/><br/>**Palec** , generovat kód miniatury (použít `mthumb` ).<br/>**ARM** , vygenerujte kód ARM (použít `marm` ).<br/>Možnost **disabled** se pro zvolenou platformu nedá použít.|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br/><br/>Adresář protokolu sledovacího modulu|
|**TreatWarningAsError**|Volitelný parametr **bool** .<br/><br/>Zpracovává všechna upozornění kompilátoru jako chyby.<br/><br/>Pro nový projekt může být nejvhodnější použít `/WX` ve všech kompilacích; řešení všech upozornění zajistí nejmenší možné nedostatky v obtížném hledání kódu.|
|**UndefinePreprocessorDefinitions**|Parametr volitelného **řetězce []** .<br/><br/>Určuje jeden nebo více zrušení definujících preprocesoru.<br/><br/>Použijte `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Volitelný parametr **bool** .<br/><br/>Zruší definici všech dříve definovaných hodnot preprocesoru.<br/><br/>Použijte `-undef`.|
|**UseMultiToolTask**|Volitelný parametr **bool** .<br/><br/>Kompilace s více procesory.|
|**UseShortEnums**|Volitelný parametr **bool** .<br/><br/>Typ výčtu používá pouze tolik bajtů, kolik vyžaduje vstupní sada možných hodnot.|
|**Podrobné**|Volitelný parametr **bool** .<br/><br/>Zobrazit příkazy ke spuštění a použití podrobného výstupu.|
|**WarningLevel**|Volitelný **řetězcový** parametr.<br/><br/>Vyberte, jak striktní má kompilátor obsahovat chyby kódu. Další příznaky by se měly přidat přímo k **dalším možnostem** (se `/w` , `/Weverything` ).<br/><br/>**TurnOffAllWarnings** zakáže všechna upozornění kompilátoru (použít `w` ).<br/>**Povolit všechna upozornění** povolí všechna upozornění, včetně těch, která jsou ve výchozím nastavení zakázaná (použít `Wall` ).|

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
