---
title: Vlastnosti projektu Clang (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 7c64ccedaeb8c13e353daaba0aeec0a388885bdf
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950659"
---
# <a name="clang-project-properties-android-c"></a>Vlastnosti projektu Clang (Android C++)

Vlastnost | Popis | Vlastnit
--- | ---| ---
Další adresáře k zahrnutí | Určuje jeden nebo více adresářů, které mají být přidány do cesty include; oddělte je středníkem, pokud je více než jedna. (-I [cesta]).
Formát ladicích informací | Určuje typ ladicích informací generovaných kompilátorem. | **None** – nevytváří žádné ladicí informace, takže kompilace může být rychlejší.<br>**Úplné ladicí informace (DWARF2)** – vygeneruje informace o ladění DWARF2.<br>**Informace o číslech řádků** – vygeneruje jenom informace o číslech řádků.<br>
Název souboru objektu | Určuje název, kterým se má přepsat výchozí název souboru objektu. může být název souboru nebo adresáře. (/FO [název]).
Úroveň upozornění | Vyberte, jak striktní má kompilátor obsahovat chyby kódu.  Další příznaky by se měly přidat přímo k dalším možnostem. (/w,/Weverything). | Vypnout **všechna upozornění** – zakáže všechna upozornění kompilátoru.<br>**Povolit všechna upozornění** – povolí všechna upozornění, včetně těch, která jsou ve výchozím nastavení zakázaná.<br>
Zpracovávat upozornění jako chyby | Zpracovává všechna upozornění kompilátoru jako chyby. Pro nový projekt může být nejvhodnější používat/WX ve všech kompilacích; řešení všech upozornění zajistí nejmenší možné nedostatky v obtížném hledání kódu.
Zapnout režim podrobného výpisu | Zobrazit příkazy ke spuštění a použití podrobného výstupu.
Optimalizace | Určuje úroveň optimalizace pro aplikaci. | **Vlastní** optimalizace.<br>**Zakázáno** – zakázat optimalizaci.<br>**Minimalizovat velikost** – optimalizovat pro velikost<br>**Maximalizujte rychlost** – Optimalizujte rychlost.<br>**Úplná optimalizace** – nákladné optimalizace<br>
Striktní aliasy | Předpokládají nejpřísnější pravidla aliasování.  U objektu jednoho typu se nikdy nepředpokládá, že se nachází na stejné adrese jako objekt jiného typu.
Vynechat ukazatel na rámec | Zakazuje vytváření ukazatelů na rámce v zásobníku volání.
Povolit C++ výjimky | Určuje model zpracování výjimek, který má kompilátor použít. | **Bez** zákazu zpracování výjimek.<br>**Ano** – povolí zpracování výjimek.<br>**Unwind tabulky** – vygeneruje všechna potřebná statická data, ale neovlivní generovaný kód.<br>
Povolit propojování na úrovni funkcí | Umožňuje kompilátoru zabalit jednotlivé funkce ve formě zabalených funkcí (sekvence COMDAT). Vyžaduje se pro úpravy a pokračování v práci.     (ffunction – oddíly).
Povolit propojování na úrovni dat | Umožňuje optimalizaci linkeru odebrat nepoužívaná data vygenerováním jednotlivých datových položek v samostatné části.
Povolit Advanced SIMD (Neon) | Povoluje generování kódu pro hardware s plovoucí desetinnou čárkou NEON. To platí jenom pro architekturu ARM.
ABI s plovoucí desetinnou čárkou | Možnost výběru pro výběr plovoucí desetinné čárky. | **Soft** – Soft způsobí, že kompilátor generuje výstup obsahující volání knihovny pro operace s plovoucí desetinnou čárkou.<br>**SoftFP** -' SoftFP ' umožňuje generování kódu pomocí hardwarových instrukcí s plovoucí desetinnou čárkou, ale stále používá konvence volání Soft-float.<br>**Hard** – umožňuje generování instrukcí s plovoucí desetinnou čárkou a používá konvence volání specifické pro FPU.<br>
Kontrolu zabezpečení | Kontrola zabezpečení pomáhá detekovat přetečení vyrovnávací paměti zásobníku, což je běžný pokus o útok na zabezpečení programu. (fstack-Protector). | **Zakázat kontrolu zabezpečení** – zakázat kontrolu zabezpečení.<br>**Povolit kontrolu zabezpečení** – povolit kontrolu zabezpečení. (fstack-Protector)<br>
Pozice nezávislého kódu | Generuje nezávislý kód pozice (PIC) pro použití ve sdílené knihovně.
Použití krátkých výčtů | Typ výčtu používá pouze tolik bajtů, kolik vyžaduje vstupní sada možných hodnot.
Povolit informace běhového typu | Přidá kód pro kontrolu C++ typů objektů v době běhu (informace o typu modulu runtime).     (frtti, fno-rtti)
Standard jazyka C | Určuje standard jazyka C. | **Výchozí**<br>Standard jazyka **c89** -c89.<br>Standard jazyka **C99** -C99.<br>Standard jazyka **C11** -C11.<br>**C99 (DIALEKT GNU)** – Standard jazyka C99 (dialekt GNU)<br>**C11 (DIALEKT GNU)** – Standard jazyka C11 (dialekt GNU)<br>
C++Standardní jazyk | Určuje standardní C++ jazyk. | **Výchozí**<br>**C++ 03** – Standard jazyka c++ 03.<br>**C++** 11 – Standard jazyka c++ 11.<br>**C++** 14 – Standard jazyka c++ 14.<br>**C++ 03 (DIALEKT GNU)** – Standard jazyka c++ 03 (dialekt GNU)<br>**C++ 11 (DIALEKT GNU)** – Standard jazyka c++ 11 (dialekt GNU)<br>**C++ 14 (DIALEKT GNU)** – Standard jazyka c++ 14 (dialekt GNU)<br>
Definice preprocesoru | Definuje symboly předzpracování pro zdrojový soubor. (-D)
Zrušit Definice preprocesoru | Určuje jeden nebo více zrušení definujících preprocesoru.  (-U [makro])
Zrušit definici všech definic preprocesoru | Zruší definici všech dříve definovaných hodnot preprocesoru.  (-undef)
Zobrazit zahrnutí | Generuje seznam souborů k zahrnutí s výstupem kompilátoru.  (-H)
Předkompilovaná hlavička | Vytvořit/použít předkompilovanou hlavičku: umožňuje vytvoření nebo použití předkompilované hlavičky během sestavení. | **Use** – použijte předkompilovanou hlavičku.<br>**Bez použití předkompilovaných hlaviček** – nepoužívá se Předkompilovaná hlavička.<br>
Soubor předkompilované hlavičky | Určuje název hlavičkového souboru, který se má použít pro soubor předkompilované hlavičky. Tento soubor se během sestavení přidá taky do souborů Vynucené zahrnutí.
Adresář výstupního souboru předkompilované hlavičky | Určuje adresář pro generovanou předkompilovanou hlavičku. Tento adresář se během sestavení přidá taky k dalším adresářům include.
Kompilovat předkompilovanou hlavičku jako | Umožňuje vybrat možnost jazyka kompilace pro soubor předkompilované hlavičky (-x c-Header,-x c++-Header). | **Kompilovat jako kód jazyka c** – kompilovat jako kód jazyka c.<br>**Kompilovat jako C++**  kód – kompilovat jako C++ kód.<br>
Kompilovat jako | Umožňuje vybrat možnost jazyka kompilace pro soubory. c a. cpp.  Klíčové slovo Default se detekuje na základě rozsahu. c nebo. cpp. (-x c, -x c++) | **Výchozí** – výchozí.<br>**Kompilovat jako kód jazyka c** – kompilovat jako kód jazyka c.<br>**Kompilovat jako C++**  kód – kompilovat jako C++ kód.<br>
Vynucené vložené soubory | jeden nebo více souborů s vynuceným zahrnutím.     (-Include [název])
Kompilace s využitím více procesorů | Kompilace s více procesory.
Další možnosti | Další možnosti
