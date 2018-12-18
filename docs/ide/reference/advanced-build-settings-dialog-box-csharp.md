---
title: Dialogové okno Upřesnit nastavení sestavení (C#)
ms.date: 06/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cf4fd5b48dc3bfcfbfe1809eebe656a5b8f2079d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928279"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Dialogové okno Upřesnit nastavení sestavení (C#)

Použití **pokročilé nastavení sestavení** dialogovému oknu **Návrháře projektu** k určení rozšířenou vlastností konfigurace sestavení projektu. Toto dialogové okno se vztahuje na [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] pouze pro projekty.

## <a name="general"></a>Obecné

Tyto možnosti umožňují nastavit obecné upřesňující nastavení.

**Verze jazyka**

Určuje verzi modulu jazyka. Sada funkcí se liší v jednotlivých verzích, proto tato možnost umožňuje vynutit na kompilátoru povolit pouze podmnožinu implementovaných funkcí nebo povolte jenom funkce, kompatibilní s současných standardů. Toto nastavení obsahuje následující možnosti:

- **default**

   Cílí na aktuální verzi.

- **ISO-1** a **ISO-2**

   Standardní funkce ISO-1 a ISO-2, zaměřuje v uvedeném pořadí.

- **C#[číslo verze]**

   Cílí na konkrétní verzi C#. Další informace najdete v tématu [/langversion (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).

**Vnitřní kompilátor zpráv o chybách**

Určuje, zda chcete zprávy o chybách kompilátoru společnosti Microsoft. Pokud nastavit **řádku** (výchozí), zobrazí se výzva Pokud dojde k chybě vnitřní kompilátor, získáte možnost elektronicky odešle zprávu o chybách společnosti Microsoft. Pokud hodnotu **odeslat**, zprávu o chybách se automaticky odešlou. Pokud hodnotu **fronty**, zprávy o chybách se zařadí do fronty. Pokud nastavena na **žádný**, ohlásí chybu pouze v kompilátoru textový výstup. Další informace najdete v tématu [/errorreport (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Kontrolovat aritmetické přetečení a podtečení**

Určuje, zda celočíselný aritmetické příkaz, který není v oboru [zaškrtnutí](/dotnet/csharp/language-reference/keywords/checked) nebo [Nekontrolovaná](/dotnet/csharp/language-reference/keywords/unchecked) klíčová slova a způsobí, že výsledkem je hodnota mimo rozsah datového typu za běhu došlo k výjimce. Další informace najdete v tématu [/ checked (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Neodkazovat na mscorlib.dll**

Určuje, zda mscorlib.dll se naimportují do programu, definování celý <xref:System> oboru názvů. Toto políčko zaškrtněte, pokud chcete definovat nebo si vytvořte svoje vlastní <xref:System> obor názvů a objekty. Další informace najdete v tématu [/nostdlib (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Výstup

Tyto možnosti umožňují zadat možnosti pokročilé výstupu.

**Informace o ladění**

Určuje typ ladicích informací generovaných kompilátorem. Informace o tom, jak konfigurovat výkon ladění aplikace najdete v tématu [usnadnění bitové kopie k ladění](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Toto nastavení obsahuje následující možnosti:

- **None**

   Určuje, že se nevygeneruje žádná informace o ladění.

- **Úplné**

   Umožňuje připojení ladicího programu ke spuštěnému programu.

- **pdbonly**

   Umožňuje zdrojového kódu, ladění, když program se spustí v ladicím programu, ale zobrazí jenom assembler když spuštěný program je připojen k ladicímu programu.

-  **Přenosná**

   Vytvoří. Soubor PDB, soubor se symboly bez specifický pro platformu, přenosná, která poskytuje další nástroje, zejména ladicí programy, informace o tom, co je v hlavní spustitelný soubor a jak byl vytvořen. Zobrazit [souboru PDB typu Portable](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) Další informace.

- **Vložený**

   Vloží informace o symbolech přenosný do sestavení. Žádné externí. Soubor PDB je vytvořen.

Další informace najdete v tématu [/Debug (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Zarovnání souboru**

Určuje velikost oddíly výstupního souboru. Platné hodnoty jsou **512**, **1024**, **2048**, **4096**, a **8192**. Tyto hodnoty se měří v bajtech. Každý oddíl se zarovnáno na hranici, která je násobkem tuto hodnotu by to ovlivnilo velikost výstupního souboru. Další informace najdete v tématu [/filealign (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Základní adresa knihovny**

Určuje upřednostňovaná základní adresa, ve kterém se má načíst knihovnu DLL. Výchozí základní adresa pro knihovnu DLL se nastavuje [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] společného jazykového modulu runtime. Další informace najdete v tématu [/BaseAddress (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Stránka Sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)