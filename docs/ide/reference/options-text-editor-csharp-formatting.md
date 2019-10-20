---
title: C#možnosti formátování editoru
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8947f6e2fee2b8615c750b770ac3b0dea85bb991
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666327"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Dialogové okno Možnosti: textový editor \> C# \> stylu kódu \> formátování

Pomocí stránky možnosti **formátování** a jejích podstránek ([**odsazení**](#indentation-page), **nové řádky**, **mezery**a **zalamování**) nastavte možnosti formátování kódu v editoru kódu.

Chcete-li získat přístup k této stránce Možnosti, v řádku nabídek vyberte možnost **nástroje**  > **Možnosti** . V dialogovém okně **Možnosti** vyberte možnost **textový editor**  > **C#**  > **stylu kódu**  > **formátování**.

> [!TIP]
> **Odsazení**, **nové řádky**, **mezery**a **zabalení** podstránky každý zobrazí okno náhledu v dolní části, které zobrazuje účinek jednotlivých možností. Chcete-li použít okno náhledu, vyberte možnost formátování. V okně náhledu se zobrazí příklad vybrané možnosti. Když změníte nastavení tak, že vyberete přepínač nebo zaškrtávací políčko, okno náhledu se aktualizuje a zobrazí efekt nového nastavení.

## <a name="formatting-general-page"></a>Stránka formátování (Obecné)

### <a name="general-settings"></a>Obecné nastavení

Tato nastavení mají vliv na to, *kdy* Editor kódu aplikuje možnosti formátování na kód.

|Popisek|Popis|
|-----------|-----------------|
|**Automaticky formátovat při psaní**|Při zrušení výběru jsou možnosti **Format zapnuté** a **formátový blok zapnuté** .|
|**Automaticky formátovat příkaz v;**|Pokud je tato možnost vybrána, formátuje příkazy při dokončení podle možností formátování vybraných pro Editor.|
|**Automaticky formátovat blok na}**|Je-li vybrána tato možnost, formátuje bloky kódu podle možností formátování vybraných pro Editor ihned po dokončení bloku kódu.|
|**Automaticky formátovat při návratu**|Když je tato možnost vybrána, formátuje text při stisknutí klávesy **ENTER** , aby odpovídaly možnostem formátování vybraným pro Editor.|
|**Automaticky formátovat při vložení**|Když se tato možnost vybere, zformátuje text, který se vloží do editoru, aby odpovídal možnostem formátování vybraným pro Editor.|

::: moniker range="vs-2019"

Pokud jste dřív použili nastavení stylu kódu pro C# soubory pomocí příkazu **formátovat dokument** v aplikaci Visual Studio 2017, tato funkce je teď k dispozici jako [**Vyčištění kódu**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Formátování nastavení dokumentu

Tato nastavení nakonfigurují příkaz **formátovat dokument** , aby pro soubor prováděl další vyčištění kódu. Další informace o tom, jak se tato nastavení používají, najdete v tématu [Format Document Command](../code-styles-and-code-cleanup.md#apply-code-styles).

|Popisek|Popis|Odpovídající pravidla možností > EditorConfig a nástrojů|
|-----------|-----------------|-----------------|-----------------|
|**Použít všechna C# pravidla formátování (odsazení, zalomení a mezery)**|Příkaz **Formát dokumentu** vždy opravuje problémy s formátováním. Toto nastavení nelze změnit.| [Základní možnosti EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Možnosti formátování .NET EditorConfig](../../ide/editorconfig-formatting-conventions.md)<br/><br/>**Nástroje**  > **Možnosti**  > **textový editor**  > **C#**  > **formátování** > [**odsazení** nebo **nové řádky** nebo **mezery** nebo **zabalení**]|
|**Při formátování provést vyčištění kódu**|Když se tato možnost vybere, použije opravy pro níže uvedená pravidla v příkazu **Edit. FormatDocument** .| Není k dispozici |
|**Odebrat nepotřebné direktivy using**|Pokud je tato možnost vybrána, při spuštění **Edit. FormatDocument** odebere nepotřebné direktivy `using`.| Není k dispozici |
|**Seřadit direktivy using**|Když se tato možnost vybere, seřadí `using` direktivy, když se aktivuje **Edit. FormatDocument** .| dotnet_sort_system_directives_first<br/><br/>**Nástroje**  > **Možnosti**  > **textový editor**  > **C#**  > **Pokročilé** 0**umístit direktivy System jako první při řazení direktiv using** |
|**Přidat/odebrat složené závorky pro jednořádkové Řídicí příkazy**|Je-li vybrána tato možnost, přidá nebo odstraní závorky z jednoduchých řídicích příkazů při aktivaci **Edit. FormatDocument** .| csharp_prefer_braces<br/><br/>**Nástroje**  > **Možnosti**  > **textový Editor**  > **C#**  > **styl kódu** 0**Předvolby bloku kódu** 2**preferovat složené závorky** |
|**Přidat Modifikátory dostupnosti**|Když se tato možnost vybere, při aktivaci **Edit. FormatDocument** přidá chybějící Modifikátory dostupnosti.| dotnet_style_require_accessibility_modifiers |
|**Seřadit Modifikátory dostupnosti**|Když se tato možnost vybere, seřadí při spuštění **Edit. FormatDocument** Modifikátory dostupnosti.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Použít předvolby textu výrazu nebo bloku**|Je-li vybrána tato možnost, převede členové Expression-těle na blokové tělo nebo naopak, když se aktivuje **Edit. FormatDocument** .| [Expression-těle – možnosti členů EditorConfig](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>**Nástroje**  > **Možnosti**  > **textový Editor**  > **C#**  > **stylu kódu** 0**Předvolby výrazů** 2**použití těla výrazu pro metody, konstruktory atd.** |
|**Použít předvolby implicitního/explicitního typu**|Pokud je tato možnost vybrána, převede `var` na explicitní typ, nebo naopak, když se aktivuje **Edit. FormatDocument** .| [Možnosti EditorConfig explicitního typu](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>**Nástroje**  > **Možnosti**  > **textový Editor**  > **C#**  > **styl kódu** 0**Předvolby ' var '** |
|**Použít předvolby vložených proměnných pro inline**|Je-li vybrána tato možnost, inlinees `out` proměnné, kde je to možné při spuštění **Edit. FormatDocument** .| csharp_style_inlined_variable_declaration<br/><br/>**Nástroje**  > **Možnosti**  > **textový Editor**  > **C#**  > **styl kódu** 0**Předvolby proměnných** 2**preferovat vloženou deklaraci proměnných** |
|**Použít předvolby pro typ jazyka nebo architektury**|Je-li vybrána tato možnost, převede typy jazyků na typy architektury nebo naopak, když je spuštěna **Edit. FormatDocument** .| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Nástroje**  > **Možnosti**  > **textový Editor**  > **C#**  > **styl kódu** 0**předdefinované předvolby typu** |
|**Použít předvolby inicializace objektu nebo kolekce**|Je-li vybrána tato možnost, používá Inicializátory objektů a kolekcí, pokud je to možné při spuštění **Edit. FormatDocument** .| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Nástroje**  > **Možnosti**  > **textový Editor**  > **C#**  > **styl kódu** 0**Předvolby výrazů** 2**preferovat inicializátor objektu** nebo **preferovat kolekci inicializátor** |
|**Použít předvolby pro kvalifikaci this.**|Když se tato možnost vybere, aplikuje `this.` předvolby při spuštění **Edit. FormatDocument** .| [Tento. možnosti EditorConfig kvalifikace](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>**Nástroje**  > **Možnosti**  > **textový Editor**  > **C#**  > **styl kódu** 0**Předvolby this.** |
|**Pokud je to možné, nastavit privátní pole jako jen pro čtení**|Když se tato možnost vybere, zpřístupní soukromá pole `readonly`, kde je to možné, když se spustí **Edit. FormatDocument** .| dotnet_style_readonly_field<br/><br/>**Nástroje**  > **Možnosti**  > **textový editor**  > **C#**  > m**stylu kódu** 0**Předvolby polí** 2**preferovat jen pro čtení** |
|**Odebrat nepotřebná přetypování**|Když se tato možnost vybere, odebere nepotřebná přetypování, pokud je to možné, když se spustí **Edit. FormatDocument** .| Není k dispozici |
|**Odebrat nepoužité proměnné**|Když se tato možnost vybere, odebere proměnné, které se nepoužívají při spuštění **Edit. FormatDocument** .| Není k dispozici |

![Nastavení vyčištění kódu pro C# v aplikaci Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Odsazení stránky

Možnosti odsazení na této stránce se použijí při automatickém formátování kódu. Jedním z příkladů při automatickém formátování kódu je při vložení kódu do souboru, když je vybraná možnost **automaticky formátovat při vložení** . (Možnost **automaticky formátovat při vložení** se nachází v části **formátování**  > **Obecné**.)

![C#Možnosti odsazení textového editoru v aplikaci Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> K dispozici jsou také možnosti odsazení na stránce možností  > **C#** **karty**  >  **textový editor** . Tyto možnosti určují, kde Editor kódu umístí kurzor po stisknutí klávesy **ENTER** na konci řádku.
>
> ![C#karty textový editor možnosti v aplikaci Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Viz také:

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)