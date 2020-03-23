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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f25f9d96cd8de8dcb140c79c7dfb3a7a5981986c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595849"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Dialogové okno Upřesnit nastavení sestavení (C#)

Dialogové okno **Upřesnit nastavení sestavení** **návrháře projektu** slouží k určení rozšířených vlastností konfigurace sestavení projektu. Toto dialogové okno platí pouze pro projekty jazyka C#.

## <a name="general"></a>Obecné

Následující možnosti umožňují nastavit obecné upřesňující nastavení.

**Jazyková verze**

::: moniker range=">=vs-2019"

Odkazy na [/langversion (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option), který poskytuje informace o tom, jak je vybrána výchozí jazyková verze na základě cílového rozhraní projektu.

::: moniker-end

::: moniker range="vs-2017"

Určuje verzi jazyka, který se má použít. Sada funkcí se v každé verzi liší, takže tuto možnost lze použít k vynucení kompilátoru tak, aby povolil pouze podmnožinu implementovaných funkcí, nebo aby povoloval pouze ty funkce kompatibilní s existujícím standardem.

Výchozí hodnota je C# 7.0.

::: moniker-end

**Interní zasílání zpráv o chybách kompilátoru**

Určuje, zda má být nahlásit chyby kompilátoru společnosti Microsoft. Pokud je nastavena **výzva** (výchozí), zobrazí se výzva, pokud dojde k chybě interníkompilátor, což vám dává možnost odeslat zprávu o chybě elektronicky společnosti Microsoft. Pokud je nastaveno na **odeslání**, bude automaticky odeslána zpráva o chybě. Pokud je nastavena na **frontu**, budou zprávy o chybách zařazeny do fronty. Pokud je nastavena na **žádnou**, chyba bude hlášena pouze v textovém výstupu kompilátoru. Další informace naleznete v tématu [/errorreport (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Kontrola aritmetického přetečení/podtečení**

Určuje, zda celočíselný aritmetický příkaz, který není v oboru [kontrolovaných](/dotnet/csharp/language-reference/keywords/checked) nebo [nekontrolovaných](/dotnet/csharp/language-reference/keywords/unchecked) klíčových slov a výsledkem je hodnota mimo rozsah datového typu, způsobí výjimku za běhu. Další informace naleznete v tématu [/checked (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Neodkazovat na soubor mscorlib.dll**

Určuje, zda bude do programu importován soubor mscorlib.dll, který bude definován celý <xref:System> obor názvů. Toto políčko zaškrtněte, pokud <xref:System> chcete definovat nebo vytvořit vlastní obor názvů a objekty. Další informace naleznete v tématu [/nostdlib (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Výstup

Následující možnosti umožňují zadat rozšířené možnosti výstupu.

**Informace o ladění**

Určuje typ informací o ladění generovaných kompilátorem. Informace o konfiguraci výkonu ladění aplikace naleznete v tématu [Usnadnění ladění bitové kopie](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Toto nastavení má následující možnosti:

- **žádný**

   Určuje, že nebudou generovány žádné informace o ladění.

- **Plné**

   Umožňuje připojení ladicího programu ke spuštěnému programu.

- **pdbonly**

   Umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazí assembler pouze v případě, že je spuštěný program připojen k ladicímu programu.

- **Přenosné**

   Vytváří . PDB soubor, neplatformní, přenosný symbol soubor, který poskytuje další nástroje, zejména ladicí program, informace o tom, co je v hlavním spustitelném souboru a jak byl vyroben. Další informace naleznete [v tématu Portable PDB.](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md)

- **Vložené**

   Vloží do sestavy informace o přenosném symbolu. Žádné externí . PDB soubor je vytvořen.

Další informace naleznete v tématu [/debug (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Zarovnání souborů**

Určuje velikost oddílů ve výstupním souboru. Platné hodnoty jsou **512**, **1024**, **2048**, **4096**a **8192**. Tyto hodnoty se měří v bajtech. Každý oddíl bude zarovnán na hranici, která je násobkem této hodnoty, což ovlivní velikost výstupního souboru. Další informace naleznete v tématu [/filealign (C# Compiler Options).](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)

**Základní adresa knihovny**

Určuje upřednostňovanou základní adresu, na kterou má být načíst dll. Výchozí základní adresa pro dll je nastavena za běhu mll .NET Framework common language. Další informace naleznete v tématu [/baseaddress (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
