---
title: Možnosti formátování editoru C#
description: Naučte se, jak pomocí stránky možnosti formátování a jejích podstránek nastavit možnosti formátování kódu v editoru kódu při programování v jazyce C#.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: eea4f9afd82dd87385e02ba9f149e91f336369a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944066"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Dialogové okno Možnosti: \> \> formátování stylu kódu C# editoru \> textu

Pomocí stránky možnosti **formátování** a jejích podstránek ([**odsazení**](#indentation-page), **nové řádky**, **mezery** a **zalamování**) nastavte možnosti formátování kódu v editoru kódu.

Chcete-li získat přístup k této stránce Možnosti,  >  v řádku nabídek **Vyberte možnost** nástroje. V dialogovém okně **Možnosti** vyberte možnost **textový editor**  >  **C#**  >  **formátování stylu kódu**  >  .

> [!TIP]
> **Odsazení**, **nové řádky**, **mezery** a **zabalení** podstránky každý zobrazí okno náhledu v dolní části, které zobrazuje účinek jednotlivých možností. Chcete-li použít okno náhledu, vyberte možnost formátování. V okně náhledu se zobrazí příklad vybrané možnosti. Když změníte nastavení tak, že vyberete přepínač nebo zaškrtávací políčko, okno náhledu se aktualizuje a zobrazí efekt nového nastavení.

## <a name="formatting-general-page"></a>Stránka formátování (Obecné)

### <a name="general-settings"></a>Obecná nastavení

Tato nastavení mají vliv na to, *kdy* Editor kódu aplikuje možnosti formátování na kód.

|Popisek|Description|
|-----------|-----------------|
|**Automaticky formátovat při psaní**|Při zrušení výběru jsou možnosti **Format zapnuté** a **formátový blok zapnuté** .|
|**Automaticky formátovat příkaz v;**|Pokud je tato možnost vybrána, formátuje příkazy při dokončení podle možností formátování vybraných pro Editor.|
|**Automaticky formátovat blok na}**|Je-li vybrána tato možnost, formátuje bloky kódu podle možností formátování vybraných pro Editor ihned po dokončení bloku kódu.|
|**Automaticky formátovat při návratu**|Když je tato možnost vybrána, formátuje text při stisknutí klávesy **ENTER** , aby odpovídaly možnostem formátování vybraným pro Editor.|
|**Automaticky formátovat při vložení**|Když se tato možnost vybere, zformátuje text, který se vloží do editoru, aby odpovídal možnostem formátování vybraným pro Editor.|

::: moniker range="vs-2019"

Pokud jste dříve použili nastavení stylu kódu pro soubory jazyka C# pomocí příkazu **formátovat dokument** v aplikaci Visual Studio 2017, je tato funkce nyní k dispozici jako [**Vyčištění kódu**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Formátování nastavení dokumentu

Tato nastavení nakonfigurují příkaz **formátovat dokument** , aby pro soubor prováděl další vyčištění kódu. Další informace o tom, jak se tato nastavení používají, najdete v tématu [Format Document Command](../code-styles-and-code-cleanup.md#apply-code-styles).

|Popisek|Description|Odpovídající pravidla možností > EditorConfig a nástrojů|
|-----------|-----------------|-----------------|-----------------|
|**Použít všechna pravidla formátování C# (odsazení, zalamování, rozestupy)**|Příkaz **Formát dokumentu** vždy opravuje problémy s formátováním. Toto nastavení nelze změnit.| [Základní možnosti EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Možnosti formátování .NET EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Formátování** > [**odsazení** nebo **nové řádky** nebo **mezery** nebo **zalomení**]|
|**Při formátování provést vyčištění kódu**|Když se tato možnost vybere, použije opravy pro níže uvedená pravidla v příkazu **Edit. FormatDocument** .| – |
|**Odebrat nepotřebné direktivy using**|Když se tato možnost vybere, odstraní nepotřebné `using` direktivy při spuštění **Edit. FormatDocument** .| – |
|**Seřadit direktivy using**|Při výběru této položky seřadí `using` direktivy, když se aktivuje **Edit. FormatDocument** .| dotnet_sort_system_directives_first<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Rozšířené možnosti**  >  **Při řazení direktiv using umístit nejdřív direktivy System** |
|**Přidat/odebrat složené závorky pro jednořádkové Řídicí příkazy**|Je-li vybrána tato možnost, přidá nebo odstraní závorky z jednoduchých řídicích příkazů při aktivaci **Edit. FormatDocument** .| csharp_prefer_braces<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **Předvolby**  >  bloku kódu **Preferovat složené závorky** |
|**Přidat Modifikátory dostupnosti**|Když se tato možnost vybere, při aktivaci **Edit. FormatDocument** přidá chybějící Modifikátory dostupnosti.| dotnet_style_require_accessibility_modifiers |
|**Seřadit Modifikátory dostupnosti**|Když se tato možnost vybere, seřadí při spuštění **Edit. FormatDocument** Modifikátory dostupnosti.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Použít předvolby textu výrazu nebo bloku**|Je-li vybrána tato možnost, převede členové Expression-těle na blokové tělo nebo naopak, když se aktivuje **Edit. FormatDocument** .| [Expression-těle – možnosti členů EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#expression-bodied-members)<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **Předvolby výrazů**  >  **Použijte tělo výrazu pro metody, konstruktory atd.** |
|**Použít předvolby implicitního/explicitního typu**|Když se vybere, převede se `var` na explicitní typ, nebo naopak, když se aktivuje **Edit. FormatDocument** .| [Možnosti EditorConfig explicitního typu](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types)<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **Předvolby ' var '** |
|**Použít předvolby vložených proměnných pro inline**|Je-li vybrána tato možnost, `out` zaznamená proměnné tam, kde je to možné při spuštění **Edit. FormatDocument** .| csharp_style_inlined_variable_declaration<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **Předvolby proměnných**  >  **Preferovat vloženou deklaraci proměnných** |
|**Použít předvolby pro typ jazyka nebo architektury**|Je-li vybrána tato možnost, převede typy jazyků na typy architektury nebo naopak, když je spuštěna **Edit. FormatDocument** .| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **předdefinované předvolby typu** |
|**Použít předvolby inicializace objektu nebo kolekce**|Je-li vybrána tato možnost, používá Inicializátory objektů a kolekcí, pokud je to možné při spuštění **Edit. FormatDocument** .| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **Předvolby výrazů**  >  **Preferovat inicializátor objektu** nebo **preferovat inicializátor kolekce** |
|**Použít předvolby pro kvalifikaci this.**|Když se tato možnost vybere, aplikuje se `this.` předvolby při aktivaci **Edit. FormatDocument** .| [Tento. možnosti EditorConfig kvalifikace](/dotnet/fundamentals/code-analysis/style-rules/language-rules#this-and-me)<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **Předvolby this.** |
|**Pokud je to možné, nastavit privátní pole jako jen pro čtení**|Když se tato možnost vybere, zpřístupní soukromá pole, pokud `readonly` je to možné, když se spustí **Edit. FormatDocument** .| dotnet_style_readonly_field<br/><br/>**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Styl kódu**  >  **Předvolby polí**  >  **Preferovat jen pro čtení** |
|**Odebrat nepotřebná přetypování**|Když se tato možnost vybere, odebere nepotřebná přetypování, pokud je to možné, když se spustí **Edit. FormatDocument** .| – |
|**Odebrat nepoužité proměnné**|Když se tato možnost vybere, odebere proměnné, které se nepoužívají při spuštění **Edit. FormatDocument** .| – |

![Nastavení vyčištění kódu pro C# v aplikaci Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Odsazení stránky

Možnosti odsazení na této stránce se použijí při automatickém formátování kódu. Jedním z příkladů při automatickém formátování kódu je při vložení kódu do souboru, když je vybraná možnost **automaticky formátovat při vložení** . (Možnost **automaticky formátovat při vložení** je v části **formátování**  >  **Obecné**.)

![Možnosti odsazení textového editoru v C# v aplikaci Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Na   >    >  stránce Možnosti na **kartě** C# editoru textu se nacházejí taky možnosti odsazení. Tyto možnosti určují, kde Editor kódu umístí kurzor po stisknutí klávesy **ENTER** na konci řádku.
>
> ![Možnosti karet textového editoru v jazyce C# v aplikaci Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
