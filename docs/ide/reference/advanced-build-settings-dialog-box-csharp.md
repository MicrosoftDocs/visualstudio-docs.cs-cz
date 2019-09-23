---
title: Dialogové okno Upřesnit nastavení sestavení (C#)
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c4a1c902047b76ef3b29814d10cfc112ab9c7274
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186785"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Dialogové okno Upřesnit nastavení sestavení (C#)

Dialogové okno **Upřesnit nastavení sestavení** **Návrháře projektu** slouží k určení rozšířených vlastností konfigurace sestavení projektu. Toto dialogové okno se vztahuje C# pouze na projekty.

## <a name="general"></a>Obecné

Následující možnosti umožňují nastavit obecná Pokročilá nastavení.

**Verze jazyka**

::: moniker range=">=vs-2019"

Odkazuje na [/langversion (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option), které poskytují informace o výběru výchozí jazykové verze v závislosti na cílové verzi rozhraní projektu.

::: moniker-end

::: moniker range="vs-2017"

Určuje verzi jazyka, který se má použít. Sada funkcí se v každé verzi liší, takže tuto možnost lze použít k vynucení, aby kompilátor povoloval pouze podmnožinu implementovaných funkcí, nebo aby povoloval pouze ty funkce, které jsou kompatibilní se stávajícím standardem.

Výchozí hodnota je C# 7,0.

::: moniker-end

**Zasílání zpráv o vnitřních chybách kompilátoru**

Určuje, jestli se mají hlásit chyby kompilátoru Microsoftu. Pokud se nastaví **výzva** (výchozí nastavení), zobrazí se výzva, pokud dojde k vnitřní chybě kompilátoru, takže budete moct poslat zprávu o chybě elektronicky společnosti Microsoft. Pokud je nastavená na **Odeslat**, pošle se automaticky zpráva o chybě. Pokud je nastaveno na **Queue**, zprávy o chybách budou zařazeny do fronty. Pokud je nastavena na **hodnotu None**, bude chyba zaznamenána pouze v textovém výstupu kompilátoru. Další informace naleznete v tématu [/errorreport (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Kontrolovat aritmetické přetečení a podtečení**

Určuje, zda je celočíselný aritmetický příkaz, který není v rozsahu [kontrolovány](/dotnet/csharp/language-reference/keywords/checked) zkontrolovaných [nezaškrtnuto](/dotnet/csharp/language-reference/keywords/unchecked) nebo nekontrolovaných klíčových slov a který má za následek, že hodnota mimo rozsah datového typu způsobí výjimku za běhu. Další informace naleznete v tématu [/checked (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Neodkazovat na mscorlib. dll**

Určuje, zda bude do programu importována knihovna mscorlib. dll a definuje celý <xref:System> obor názvů. Zaškrtněte toto políčko, pokud chcete definovat nebo vytvořit vlastní <xref:System> obor názvů a objekty. Další informace naleznete v tématu [/nostdlib (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Výstup

Následující možnosti umožňují zadat upřesňující možnosti výstupu.

**Informace o ladění**

Určuje typ ladicích informací generovaných kompilátorem. Informace o tom, jak nakonfigurovat výkon ladění aplikace, najdete v tématu [Vytvoření obrázku pro snadnější ladění](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Toto nastavení má následující možnosti:

- **nTato**

   Určuje, že se nevygenerují žádné informace o ladění.

- **kompletní**

   Umožňuje připojit k běžícímu programu ladicí program.

- **pdbonly**

   Umožňuje ladění zdrojového kódu, když je program spuštěn v ladicím programu, ale zobrazí pouze Assembler, pokud je spuštěný program připojen k ladicímu programu.

- **přenosné**

   Vytvoří. Soubor PDB, přenosový soubor, který není specifický pro platformu, který poskytuje další nástroje, zejména ladicí programy, informace o tom, co je v hlavním spustitelném souboru a jak bylo vytvořeno. Další informace najdete v části [přenosná PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) .

- **vložené**

   Vloží do sestavení přenositelné informace o symbolech. Žádná externí. Vytvoří se soubor PDB.

Další informace naleznete v tématu [/Debug (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Zarovnání souboru**

Určuje velikost oddílů ve výstupním souboru. Platné hodnoty jsou **512**, **1024**, **2048**, **4096**a **8192**. Tyto hodnoty se měří v bajtech. Každý oddíl bude zarovnán na hranici, která je násobkem této hodnoty, což ovlivní velikost výstupního souboru. Další informace naleznete v tématu [/filealign (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Základní adresa knihovny**

Určuje upřednostňovanou základní adresu, na které se má načíst knihovna DLL. Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework modul CLR (Common Language Runtime). Další informace naleznete v tématu [/BaseAddress (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
