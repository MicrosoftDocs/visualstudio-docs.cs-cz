---
title: Možnosti formátování editoru C#
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1176232eb3354a9b425e9432eb83037367ee7706
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303076"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Dialogové okno Možnosti: \> Formátování \> stylu kódu editoru \> C#

Pomocí stránky **Možnosti formátování** a jejích podstránek ([**Odsazení**](#indentation-page), **Nové řádky**, Mezery a **Obtékání**) nastavte možnosti formátování kódu v editoru kódu kódu. **Spacing**

Chcete-li získat přístup k této stránce možností, zvolte**Možnosti** **nástrojů** > z řádku nabídek. V dialogovém okně **Možnosti** zvolte Formátování > stylu kódu **textového editoru** > **C#** > **Code Style****.**

> [!TIP]
> Podstránky **Odsazení**, **Nové čáry**, Mezery a **Obtékání** zobrazují v dolní části okno náhledu, které zobrazuje efekt jednotlivých možností. **Spacing** Chcete-li použít okno náhledu, vyberte možnost formátování. Okno náhledu ukazuje příklad vybrané možnosti. Když změníte nastavení zaškrtnutím přepínacího tlačítka nebo zaškrtávacího políčka, okno náhledu se aktualizuje, aby se zobrazil účinek nového nastavení.

## <a name="formatting-general-page"></a>Stránka Formátování (Obecné)

### <a name="general-settings"></a>Obecná nastavení

Tato nastavení *ovlivňují, když* editor kódu použije možnosti formátování kódu.

|Popisek|Popis|
|-----------|-----------------|
|**Automatické formátování při psaní**|Pokud není vybrána možnosti **, příkaz formátu na ;** a blok formátu na **}** možnosti jsou zakázány.|
|**Automaticky formátovat příkaz na ;**|Je-li tato možnost vybrána, naformátuje příkazy při dokončení podle možností formátování vybraných pro editor.|
|**Automaticky formátovat blok na }**|Pokud je tato možnost vybrána, formátuje bloky kódu podle možností formátování vybraných pro editor, jakmile dokončíte blok kódu.|
|**Automaticky formátovat při návratu**|Když je tato volba vybraná, zformátuje text při stisknutí **Enter,** aby se vešly volby formátování vybrané pro editor.|
|**Automatické formátování při vložení**|Je-li tato možnost vybrána, naformátuje text vložený do editoru tak, aby odpovídal možnostem formátování vybraným pro editor.|

::: moniker range="vs-2019"

Pokud jste dříve použili nastavení stylu kódu pro soubory C# pomocí příkazu **Formát dokumentu** v sadě Visual Studio 2017, je tato funkce nyní k dispozici jako [**vyčištění kódu**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Formátování nastavení dokumentu

Tato nastavení nakonfigurují příkaz **Formát dokumentu** pro provádění dalšího vyčištění kódu v souboru. Další informace o použití těchto nastavení naleznete v [příkazu Formát dokumentu](../code-styles-and-code-cleanup.md#apply-code-styles).

|Popisek|Popis|Odpovídající pravidla EditorConfig a Tools > Options|
|-----------|-----------------|-----------------|-----------------|
|**Použít všechna pravidla formátování Jazyka C# (odsazení, obtékání, mezery)**|Příkaz **Formát dokumentu** vždy řeší problémy s formátováním. Toto nastavení nelze změnit.| [Základní editorConfig možnosti](../../ide/create-portable-custom-editor-options.md)<br/>[Možnosti formátování editoru .NETConfig](../../ide/editorconfig-formatting-conventions.md)<br/><br/>**Možnosti** >  > nástroje**Textový editor** > **C#** > **Formátování** > [**Odsazení** nebo **Nové řádky** nebo **Mezery** nebo **obtékání**]**Options**|
|**Provést vyčištění kódu sčítání během formátování**|Pokud je tato možnost vybrána, použije opravy pro níže uvedená pravidla v příkazu **Edit.FormatDocument.**| Není dostupné. |
|**Odebrání zbytečných použití**|Když je tato `using` volba vybraná, odebere nepotřebné direktivy při aktivaci **funkce Edit.FormatDocument.**| Není dostupné. |
|**Řazení pomocí**|Když je `using` tato volba vybraná, seřadí direktivy při aktivaci **souboru Edit.FormatDocument.**| dotnet_sort_system_directives_first<br/><br/>**Možnosti** >  > nástrojů**Textový editor** > **C#** > **Rozšířené** > **místo 'Systém' direktivy jako první při řazení pomocí** **Options** |
|**Přidání nebo odebrání složených závorek pro jednořádkové příkazy ovládacího prvku**|Když je tato volba vybraná, přidá nebo odebere závorky z jednořádkových příkazů ovládacího prvku při **aktivaci příkazu Edit.FormatDocument.**| csharp_prefer_braces<br/><br/>**Možnosti** >  > nástrojů**Textový editor** > **C#** > **Kód styl** > **kód blok předvolby** > **Preferovat závorky** **Options** |
|**Přidání modifikátorů usnadnění přístupu**|Když je tato volba vybraná, přidá chybějící modifikátory usnadnění přístupu **při aktivaci funkce Edit.FormatDocument.**| dotnet_style_require_accessibility_modifiers |
|**Řazení modifikátorů usnadnění přístupu**|Když je tato volba vybraná, seřadí modifikátory usnadnění přístupu **při aktivaci funkce Edit.FormatDocument.**| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Použití předvoleb textu výrazu/bloku**|Když je tato volba vybraná, převede členy s výrazem na blokovat těla nebo naopak, když je **edit.FormatDocument** spuštěn.| [Výraz-tělesně člen EditorConfig možnosti](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>**Možnosti** >  > nástrojů**Textový editor** > **C#** > **Předvolby** > **výrazu stylu** > kódu**Použijte text výrazu pro metody, konstruktory atd.** **Options** |
|**Použití předvoleb implicitního/explicitního typu**|Když je tato `var` volba vybraná, převede se na explicitní typ nebo naopak, když je spuštěn **edit.FormatDocument.**| [Možnosti explicitního typu EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>**Tools** > **Možnosti** > **Code Style** > **Text Editor** > **C#****'var' preferences** nástrojů Textový editor C# Styl kódu 'var' předvolby >  |
|**Použít předvolby inline 'out' proměnných**|Když je tato `out` volba vybraná, vřádky, kde je to možné **při aktivaci Edit.FormatDocument.**| csharp_style_inlined_variable_declaration<br/><br/>**Možnosti** >  > nástrojů**Textový editor** > **C#** > **Předvolby proměnných** > **stylu** > kódu**Preferují vloženou deklaraci proměnných** **Options** |
|**Použití předvoleb typu jazyka/architektury**|Když je tato volba vybraná, převádí typy jazyků na typy architektury nebo naopak, když je spuštěn **edit.FormatDocument.**| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Možnosti** > **Options** >  >  > **Code Style****Text Editor****C#****predefined type preferences** nástrojů Textový editor C# Předdefinované předvolby stylu kódu >  |
|**Použít předvolby inicializace objektu/kolekce**|Když je tato volba vybraná, používá inicializátory objektů a kolekcí tam, kde je to možné, když je spuštěn **edit.FormatDocument.**| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Možnosti** > **Options** > **Expression preferences** > **Text Editor** > **C#** > **Code Style****Prefer object initializer** nástroje Text Editor C# Výraz stylu kódu Preference objekt inicializátor nebo **Preferovat inicializátor kolekce**  >  |
|**Použít "toto".**|Když je tato `this.` volba vybraná, použije předvolby při **aktivaci funkce Edit.FormatDocument.**| [Tento. možnosti kvalifikace EditorConfig](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>**Tools** > **Možnosti** > **Code Style** > **Text Editor** > **C#** nástroje Textový editor C# Styl kódu **'to.' předvolby**  >  |
|**Pokud je to možné, poměšete na to, aby soukromá pole byla čitelná**|Když je tato `readonly` volba vybraná, vytvoří privátní pole tam, kde je to možné **při aktivaci funkce Edit.FormatDocument.**| dotnet_style_readonly_field<br/><br/>**Tools** > **Možnosti** > **Code Style** > **Text Editor** > **C#** > **Prefer readonly** **Field preferences**nástrojů Text Editor C# Kód Styl Pole předvolby Preferovat jen pro čtení >  |
|**Odstranění zbytečných náhozů**|Je-li tato možnost vybrána, odebere nepotřebná přetypování, pokud je to možné **při aktivaci funkce Edit.FormatDocument.**| Není dostupné. |
|**Odebrání nepoužívaných proměnných**|Když je tato volba vybraná, odebere proměnné, které nejsou použity při **aktivaci funkce Edit.FormatDocument.**| Není dostupné. |

![Nastavení vyčištění kódu pro C# v sadě Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Stránka Odsazení

Možnosti odsazení na této stránce platí, když je kód formátován automaticky. Jedním z příkladů, kdy je kód automaticky formátován, je vložení kódu do souboru, zatímco je vybrána volba **Automaticky formátovat při vložení.** (Možnost **Automaticky formátovat při vložení** je v části**Obecné** **formátování** > .)

![Možnosti odsazení textového editoru jazyka C# v sadě Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Existují také možnosti odsazení na stránce možností**karty** **C#** >  **textového editoru.** >  Tyto možnosti určují pouze místo, kam editor kódu umístí kurzor, když stisknete **enter** na konci řádku.
>
> ![Možnosti karet textového editoru jazyka C# v sadě Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Viz také

- [Dialogové okno Obecné, Prostředí, Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
