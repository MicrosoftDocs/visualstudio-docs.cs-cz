---
title: Clang vlastnosti projektu (Android C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: douge
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
ms.openlocfilehash: efceeb201a7f1afcbf7cc2c6d46619301284d823
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232114"
---
# <a name="clang-project-properties-android-c"></a>Vlastnosti projektu clang (Android C++)

Vlastnost | Popis | Možnosti
--- | ---| ---
Další adresáře souborů k zahrnutí | Určuje jeden nebo více adresářů, které chcete přidat do cesty zahrnutí; oddělte středníkem, pokud více než jeden. (-I[cesta]).
Formát ladicích informací | Určuje typ ladicích informací generovaných kompilátorem. | **Žádný** -nevytváří žádné ladicí informace, takže kompilace může být rychlejší.<br>**Úplné informace o ladění (DWARF2)** -ladicí informace DWARF2 generovat.<br>**Informace o číslech řádků** – jenom informace o generování číslo řádku.<br>
Název souboru objektů | Určuje název, který má přepsat výchozí název souboru objektů; může být název souboru nebo adresáře. (/ /FO[název]).
Úroveň upozornění | Vyberte, jak přísně má kompilátor, aby se informace o kódu chyby.  Další příznaky se přidávají přímo do další možnosti. (/ w, / weverything). | **Vypnout všechna upozornění** – zakáže všechna upozornění kompilátoru.<br>**EnableAllWarnings** – povoluje všechna upozornění včetně těch, které ve výchozím nastavení zakázané.<br>
Zpracovávat upozornění jako chyby | Zpracuje všechna upozornění kompilátoru jako chyby. Pro nový projekt může být nejlepší použít při všech kompilacích; parametr /WX vyřešením všech upozornění zajistíte, že nejmenším počtem vad kódu možné obtížné najít.
Povolíte režim s komentářem | Zobrazit příkazy ke spuštění a používají podrobný výstup.
Optimalizace | Určuje úroveň optimalizace pro aplikaci. | **Vlastní** – vlastní optimalizace.<br>**Zakázané** – zakáže optimalizaci.<br>**Minimální velikost** -optimalizovat pro velikost.<br>**Maximalizovat rychlost** -optimalizovat rychlost.<br>**Plná optimalizace** – nákladné optimalizace.<br>
Striktní aliasy | Předpokládejme nejpřísnější pravidla pro aliasy.  Objekt jednoho typu se nikdy být předpokládat, že na stejné adrese jako objekt jiného typu.
Vypustit ukazatel na rámec | Zakazuje vytváření ukazatelů na rámce v zásobníku volání.
Povolit výjimky jazyka C++ | Určuje model zpracování výjimek pro použití kompilátorem. | **Ne** – zakáže zpracování výjimek.<br>**Ano** -povolit zpracování výjimek.<br>**Tabulky unwind** – generuje všechna potřebná statická data, ale nemá vliv na kód vygenerovaný.<br>
Povolit propojování na úrovni funkcí | Umožňuje kompilátoru vytvořit balíček individuálních funkcí ve formě zabalených funkcí (sekvence Comdat). Vyžaduje se pro úpravy a pokračovat v práci.     (ffunction-sections).
Povolit propojování na úrovni dat | Umožňuje, aby optimalizace linkeru odebraly nepoužívaná data generováním jednotlivých datových položek v samostatných oddílech.
Povolit rozšíření Advanced SIMD (neon) | Umožňuje generování kódu pro bod hardware s plovoucí desetinnou čárkou NEON. To platí jenom pro architekturu arm.
ABI s plovoucí desetinnou čárkou | Výběr možností výběru z ABI s plovoucí desetinnou. | **Obnovitelné** – "Soft způsobí, že kompilátor bude generovat výstup obsahující volání knihoven pro operace s plovoucí desetinnou čárkou.<br>**SoftFP** – 'SoftFP' umožňuje generování kódu pomocí hardwarových instrukcí s plovoucí desetinnou čárkou, ale stále používá konvence volání využitím.<br>**Pevný** – generování alows "Pevného" s plovoucí desetinnou čárkou instrukcí specifických pro FPU konvence volání.<br>
Kontrola zabezpečení | Kontrola zabezpečení pomáhá odhalit vyrovnávací paměti na zásobníku typu over-pass-the útoku na zabezpečení programu. (fstack-protector). | **Zakáže kontrolu zabezpečení** – zakáže kontrolu zabezpečení.<br>**Povolit kontrolu zabezpečení** -povolit kontrolu zabezpečení. (fstack-protector)<br>
Pozičně nezávislý kód | Generovat pozice nezávislý kód (PIC) pro použití ve sdílené knihovně.
Používat krátké výčty | Typ výčtu bude používat jenom tolik bajtů vyžaduje vstupní sada možných hodnot.
Povolit informace běhového typu | Přidává kód pro kontrolu typů objektů jazyka C++ za běhu (informace typu za běhu).     (frtti, fno-rtti)
Standard jazyka C | Určuje standard jazyka C. | **Default**<br>**C89** – Standard jazyka C89.<br>**C99** – Standard jazyka C99.<br>**C11** – Standard jazyka C11.<br>**C99 (dialekt GNU)** – Standard jazyka C99 (dialekt GNU).<br>**C11 (dialekt GNU)** – Standard jazyka C11 (dialekt GNU).<br>
Standard jazyka C++ | Určuje standard jazyka C++. | **Default**<br>**C ++ 03** – Standard C ++ 03 jazyka.<br>**C ++ 11** – Standard C ++ 11 jazyka.<br>**C ++ 14** – Standard C ++ 14 jazyka.<br>**C ++ 03 (dialekt GNU)** – C ++ 03 (dialekt GNU) Standard jazyka.<br>**C ++ 11 (dialekt GNU)** – C ++ 11 (dialekt GNU) Standard jazyka.<br>**C ++ 14 (dialekt GNU)** – C ++ 14 (dialekt GNU) Standard jazyka.<br>
Definice preprocesoru | Definuje symboly předzpracování pro zdrojový soubor. (-D)
Zrušit Definice preprocesoru | Určuje že jeden nebo více nedefinovaných hodnot preprocesoru.  (-U [makro])
Zrušit všechny definice preprocesoru | Zruší definici všech dříve definovaných hodnot preprocesoru.  (-undef)
Zobrazit soubory k zahrnutí | Generuje seznam vložených souborů s výstupem kompilátoru.  (-H).
Předkompilované hlavičky | Vytvořit/použít předkompilovanou hlavičku: umožňuje nebo použít předkompilovanou hlavičku během sestavení. | **Použití** -použít předkompilovanou hlavičku.<br>**Bez použití předkompilovaných hlaviček** – bez použití předkompilovaných hlaviček.<br>
Soubor předkompilované hlavičky | Určuje název hlavičkového souboru pro soubor předkompilované hlavičky. Tento soubor se také přidají do 'vynucené vložených souborů během sestavování
Adresář výstupního souboru předkompilované hlavičky | Určuje adresář pro vygenerované předkompilované hlavičky. Tento adresář se také přidají do 'Další adresáře k zahrnutí' během sestavení
Kompilovat předkompilovanou hlavičku jako | Vyberte možnost jazyka kompilace pro soubor předkompilované hlavičky (- x c-header, - x c ++ - záhlaví). | **Kompilovat jako kód jazyka C** -kompilovat jako kód jazyka C.<br>**Kompilovat jako kód jazyka C++** -kompilovat jako kód jazyka C++.<br>
Kompilovat jako | Vyberte možnost jazyka kompilace pro soubory .c a .cpp.  "Výchozí" rozpozná na základě přípony .c nebo .cpp rozšíření. (-x c, - x c ++) | **Výchozí** – výchozí.<br>**Kompilovat jako kód jazyka C** -kompilovat jako kód jazyka C.<br>**Kompilovat jako kód jazyka C++** -kompilovat jako kód jazyka C++.<br>
Nuceně zahrnuté soubory | jeden nebo více vynucených k zahrnutí souborů.     (-include [název])
Kompilace s využitím více procesorů | Kompilace s využitím více procesorů.
Další možnosti | Další možnosti.
