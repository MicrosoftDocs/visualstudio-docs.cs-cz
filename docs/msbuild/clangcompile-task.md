---
title: Úkol ClangCompile | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: c1526fbd3c2c0822781f0e011999ddcb9c679170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275462"
---
# <a name="clangcompile-task"></a>Úkol ClangCompile

Zabalí kompilátorový nástroj Microsoft C++c, clang.exe.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **ClangCompile.**

|Parametr|Popis|
|---------------|-----------------|
|**Další includeředitelé adresáře**|Volitelný **parametr string[].**<br/><br/>Určuje jeden nebo více adresářů, které chcete přidat do cesty zahrnutí; oddělte středníky, pokud je více než jeden.<br/><br/>Použijte `-I[path]`.|
|**Další možnosti**|Volitelný parametr **řetězce.**|
|**Kontrola zabezpečení vyrovnávací paměti**|Volitelný parametr **řetězce.**<br/><br/>Kontrola zabezpečení pomáhá zjistit přetečení vyrovnávací paměti zásobníku, což je běžný pokus o útok na zabezpečení programu. <br/><br/>Použijte `fstack-protector`.|
|**BuildingInIde**|Volitelný **parametr bool.**|
|**CLanguageStandard**|Volitelný parametr **řetězce.**<br/><br/>Určuje standard jazyka C.<br/><br/>Použijte `std=[value]` s hodnotou **c89**, **c99**, **c11**, **gnu99**nebo **gnu11**.|
|**ClangVersion**|Volitelný parametr **řetězce.**|
|**Kompilovat**|Volitelný parametr **řetězce.**<br/><br/>Vyberte možnost jazyka kompilace pro soubory C a CPP. Výchozí nastavení bude rozpoznáno na základě rozšíření .c nebo .cpp.<br/><br/>Použití `-x c` `-x c++`, .|
|**CppLanguageStandard**|Volitelný parametr **řetězce.**<br/><br/>Určuje jazykový standard jazyka C++.<br/><br/>Použijte `std=[value]` s hodnotou **c++98**, **c++11**, **c++1y**, **gnu++98**, **gnu++11**nebo **gnu++1y**.|
|**DataLevelLinking**|Volitelný **parametr bool.**<br/><br/>Umožňuje optimalizace propojovacího programu k odebrání nevyužitých dat vyzařováním jednotlivých datových položek v samostatné části.|
|**DebugInformationFormat**|Volitelný parametr **řetězce.**<br/><br/>Určuje typ informací o ladění generovaných kompilátorem.<br/><br/>**Žádné**, nevytváří žádné informace o ladění, takže `g0`kompilace může být rychlejší (použití ).<br/>**FullDebug**, generovat informace o `g2 -gdwarf-2`ladění DWARF2 (použít).<br/>**Číslo řádku**, vygenerujte pouze informace o čísle řádku (použití). `gline-tables-only`|
|**EnableNeonCodegen**|Volitelný **parametr bool.**<br/><br/>Umožňuje generování kódu pro hardware s plovoucí desetinnou čárou NEON. To platí pouze pro architekturu ramen.|
|**Zpracování výjimek**|Volitelný parametr **řetězce.**<br/><br/>Určuje model zpracování výjimek, který má kompilátor použít.<br/><br/>**Zakázáno**, zakázat `fno-exceptions`zpracování výjimek (použití).<br/>**Povoleno**, povolit `fexceptions`zpracování výjimek (použití ).<br/>**UnwindTables**, generuje všechna potřebná statická data, ale `funwind-tables`nemá vliv na generovaný kód (použití).|
|**FloatABI**|Volitelný parametr **řetězce.**<br/><br/>Možnost výběru pro výběr ABI s plovoucí desetinnou tísní.<br/><br/>**soft**, způsobí, že kompilátor generovat výstup obsahující `mfloat-abi=soft`volání knihovny pro operace s plovoucí desetinnou desetinnou tálicí (použití).<br/>**softfp**, umožňuje generování kódu pomocí hardwaru s plovoucí desetinnou čárkou `mfloat-abi=softfp`pokyny, ale stále používá soft-float konvence volání (použití).<br/>**tvrdý**, umožňuje generování pokynů s plovoucí desetinnou tálicí a používá konvence volání specifické pro FPU (použití). `mfloat-abi=hard`|
|**Vynucené includesoubory**|Volitelný **parametr string[].**<br/><br/>Jeden nebo více vynucených zahrnutí souborů.<br/><br/>Použijte `-include [name]`.|
|**FunkceLevelLinking**|Volitelný **parametr bool.**<br/><br/>Umožňuje kompilátoru sbalit jednotlivé funkce ve formě balených funkcí (COMDAts). Vyžadováno pro úpravy a pokračovat v práci.<br/><br/>Použijte `ffunction-sections`.|
|**GccToolChain**|Volitelný parametr **řetězce.**<br/><br/>Cesta ke složce Gcc Tool Chain.|
|**Režim GNU**|Volitelný **parametr bool.**<br/><br/>|
|**MSKompatibilita**|Volitelný **parametr bool.**<br/><br/>Povolte úplnou kompatibilitu s microsoftem C++.|
|**Verze mskompatibility**|Volitelný parametr **řetězce.**<br/><br/>Hodnota oddělená tečkami představující číslo verze kompilátoru Microsoft, které má být vykazováno v _MSC_VER (0 = nedefinujte ji (výchozí)).|
|**Rozšíření MSExtensions**|Volitelný **parametr bool.**<br/><br/>Přijmout některé nestandardní konstrukce podporované kompilátorem Společnosti Microsoft.|
|**MSCompilerVersion**|Volitelný parametr **řetězce.**<br/><br/>Číslo verze kompilátoru Microsoft sestavy v _MSC_VER (0 = nedefinujte ji (výchozí)).|
|**Zpráva o chybě msv**|Volitelný **parametr bool.**<br/><br/>Oznamte chyby, které může Visual Studio použít k analýzě informací o souborech a řádcích.|
|**Název objektu ObjectFileName**|Volitelný parametr **řetězce.**<br/><br/>Určuje název, který má přepsat název výchozího souboru objektu. může být název souboru nebo adresáře.<br/><br/>Použijte `/Fo[name]`.|
|**Vynechat ukazatele rámce**|Volitelný **parametr bool.**<br/><br/>Zakazuje vytváření ukazatelů na rámce v zásobníku volání.|
|**Optimalizace**|Volitelný parametr **řetězce.**<br/><br/>Určuje úroveň optimalizace pro aplikaci.<br/><br/>**Vlastní**, vlastní optimalizace.<br/>**Zakázáno**, zakázat optimalizaci (použití `O0`).<br/>**MinSize**, optimalizovat pro `Os`velikost (použití ).<br/>**MaxSpeed**, optimalizovat pro `O2`rychlost (použití).<br/>**Úplné,** drahé optimalizace `O3`(použití).|
|**PositionIndependentCode**|Volitelný **parametr bool.**<br/><br/>Generovat kód nezávislé ho umístění (PIC) pro použití ve sdílené knihovně.|
|**Předkompilované záhlaví**|Volitelný parametr **řetězce.**<br/><br/>Umožňuje vytvoření nebo použití předkompilované hlavičky během sestavení.|
|**Předkompilovaný soubor záhlaví**|Volitelný parametr **řetězce.**<br/><br/>Určuje název souboru záhlaví, který má být používán pro předkompilovaný soubor záhlaví. Tento soubor bude také přidán do **vynucených zahrnutí souborů** během sestavení.|
|**Předkompilovaný adresář HlavičkavýstupuFileDirectory**|Volitelný parametr **řetězce.**<br/><br/>Určuje adresář generované předkompilované hlavičky. Tento adresář bude také přidán do **další zahrnout adresáře** během sestavení.|
|**Předkompilované kompilovanékompiluje**|Volitelný parametr **řetězce.**<br/><br/>Vyberte možnost jazyka kompilace pro předkompilovaný soubor záhlaví.<br/><br/>Použití `-x c-header` `-x c++-header`, .|
|**Definice preprocesoru**|Volitelný **parametr string[].**<br/><br/>Definuje symboly předběžného zpracování pro zdrojový soubor.<br/><br/>Použijte `-D`.|
|**RuntimeLibrary**|Volitelný parametr **řetězce.**<br/><br/>Zadejte runtime knihovnu pro propojení.<br/><br/>Použijte `MSVC /MT` `/MTd`přepínače , , `/MD`. `/MDd`<br/><br/>**MultiThreaded**, způsobí, že aplikace používat vícevláknové, statické verze knihovny run-time.<br/>**MultiThreadedDebug**, definuje _DEBUG a _MT. Tento parametr navíc způsobí, že kompilátor umístí knihovnu s názvem LIBCMTD.lib do souboru .obj, aby linker použil k překladu externích symbolů soubor LIBCMTD.lib.<br/>**MultiThreadedDLL**, způsobí, že aplikace používat vícevláknové a DLL specifické verze knihovny run-time. Definuje _MT a _DLL a způsobí, že kompilátor umístí název knihovny MSVCRT.lib do souboru OBJ.<br/>**MultiThreadedDebugDLL**, definuje _DEBUG, _MT a _DLL a způsobí, že aplikace použít ladicí verzi knihovny specifické pro více vláken a knihovny DLL. Navíc způsobí, že kompilátor umístí knihovnu s názvem MSVCRTD.lib do souboru .obj.|
|**Informace o typu runtimetype**|Volitelný **parametr bool.**<br/><br/>Přidá kód pro kontrolu typů objektů jazyka C++ za běhu (informace o typu runtime).<br/><br/>Použití `frtti` `fno-rtti`, .|
|**Zobrazit zahrnuje**|Volitelný **parametr bool.**<br/><br/>Generuje seznam zahrnutí souborů s výstupem kompilátoru.<br/><br/>Použijte `-H`.|
|**Zdrojů**|Povinný parametr **ITaskItem[].**|
|**StrictAliasing**|Volitelný **parametr bool.**<br/><br/>Předpokládejme nejpřísnější pravidla aliasingu. Objekt jednoho typu se nikdy nepředpokládá, že by se nastejném místě jako objekt jiného typu.|
|**Sysroot (Sysroot)**|Volitelný parametr **řetězce.**<br/><br/>Cesta ke složce ke kořenovému adresáři pro záhlaví a knihovny.|
|**Cílová archa**|Volitelný parametr **řetězce.**<br/><br/>Cílová architektura.|
|**Režim palce**|Volitelný parametr **řetězce.**<br/><br/>Generovat kód, který se spustí pro thumb mikroarchitekturu. To platí pouze pro architekturu ramen.<br/><br/>**Palec**, generovat palec `mthumb`kód (použití).<br/>**ARM**, generovat kód `marm`ramene (použití).<br/>**Zakázáno**, možnost není použitelná pro vybranou platformu.|
|**TrackerLogDirectory**|Volitelný parametr **řetězce.**<br/><br/>Adresář protokolu sledování.|
|**TreatWarningAsChyba**|Volitelný **parametr bool.**<br/><br/>Považuje všechna upozornění kompilátoru za chyby.<br/><br/>Pro nový projekt může být nejlepší `/WX` použít ve všech kompilacích; vyřešení všech varování zajistí co nejméně chyb kódu, které se dá těžko najít.|
|**UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions Undefine**|Volitelný **parametr string[].**<br/><br/>Určuje jeden nebo více nedefinuje jeden nebo více předprocesorových nedefinuje.<br/><br/>Použijte `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions UndefineAllPreprocessorDefinitions UndefineAllPreprocessorDefinitions Undefine**|Volitelný **parametr bool.**<br/><br/>Zrušit definici všech dříve definovaných hodnot preprocesoru.<br/><br/>Použijte `-undef`.|
|**UseMultiToolTask**|Volitelný **parametr bool.**<br/><br/>Kompilace s více procesory.|
|**UseShortEnums**|Volitelný **parametr bool.**<br/><br/>Typ výčtu používá pouze tolik bajtů vyžadované vstupní sadou možných hodnot.|
|**Podrobné**|Volitelný **parametr bool.**<br/><br/>Zobrazit příkazy ke spuštění a použití podrobného výstupu.|
|**Úroveň upozornění**|Volitelný parametr **řetězce.**<br/><br/>Vyberte, jak přísný má být kompilátor o chybách kódu. Další příznaky by měly být `/w`přidány `/Weverything`přímo do **další možnosti** (se , ).<br/><br/>**TurnOffAllWarnings**, zakáže všechna `w`upozornění kompilátoru (použití ).<br/>**EnableAllWarnings**, umožňuje všechna upozornění, včetně `Wall`těch, které jsou ve výchozím nastavení zakázány (použití ).|

## <a name="see-also"></a>Viz také

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)