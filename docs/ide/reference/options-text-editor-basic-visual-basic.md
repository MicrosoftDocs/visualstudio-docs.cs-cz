---
title: Možnosti, textový editor, Basic (VB), Upřesnit
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a07645597846bd85f3152da866a253b079bc3963
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666345"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Možnosti, textový editor, Basic (Visual Basic), Upřesnit
Stránka **vlastností specifická pro VB** se nachází ve složce **základní** ve složce **textový editor** v dialogovém okně **Možnosti** (nabídka**nástroje** ), která obsahuje následující vlastnosti:

## <a name="analysis"></a>Analýza

- Povolení úplné analýzy řešení

   Povolí analýzu kódu pro všechny soubory v řešení, nikoli pouze otevřené soubory kódu. Další informace najdete v tématu [Úplná analýza řešení](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Direktivy using

- Při řazení direktiv using umístit nejdřív direktivy System

   Pokud je tato možnost vybrána, příkazy **Remove a Sort using** v nabídce po kliknutí pravým tlačítkem myši seřadí direktivy `using` a umístí do horní části seznamu obory názvů System.

- Samostatné použití skupin direktiv

   Pokud je tato možnost vybrána, příkaz **Odebrat a seřadit pomocí** v nabídce po kliknutí pravým tlačítkem myši oddělí `using` direktivy vložením prázdného řádku mezi skupiny směrnic, které mají stejný kořenový obor názvů.

- Navrhnout použití typů v referenčních sestaveních
- Navrhnout použití typů v balíčcích NuGet

   Pokud jsou tyto možnosti vybrány, je k dispozici [rychlá akce](../quick-actions.md) pro instalaci balíčku NuGet a přidání direktivy `using` pro neodkazované typy.

   ![Rychlá akce pro instalaci balíčku NuGet v aplikaci Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Zvýrazňovač

 **Povolit zvýraznění odkazů a klíčových slov**

Textový editor může zvýraznit všechny výskyty symbolu nebo všechna klíčová slova v klauzuli, jako je například `If..Then`, `While...End While` nebo `Try...Catch...Finally`. Můžete přecházet mezi zvýrazněnými odkazy nebo klíčovými slovy stisknutím **kombinace kláves ctrl**  + **SHIFT**  + **šipka dolů** nebo **kombinací kláves CTRL**  + **SHIFT**  + **šipka nahoru**.

## <a name="outlining"></a>Sbalování

**Povolit režim sbalení**

Když otevřete soubor v editoru kódu, můžete zobrazit dokument v režimu sbalení. Další informace najdete v tématu [popisujícím sbalení](../../ide/outlining.md) . Když je vybraná tato možnost, funkce sbalení se aktivuje při otevření souboru.

**Zobrazit oddělovače řádků procedury**

Textový editor označuje vizuální rozsah procedur. Řádek se vykreslí ve zdrojových souborech *. vb* projektu v umístěních uvedených v následující tabulce:

|Umístění ve zdrojovém souboru. vb|Příklad umístění řádku|
|---------------------------------|------------------------------|
|Po ukončení konstrukce deklarace bloku|– Na konci třídy, struktury, modulu, rozhraní nebo výčtu<br />– Za vlastností, funkcí nebo sub<br />– Není mezi klauzulemi Get a set ve vlastnosti.|
|Po sadě jednoduchých konstrukcí|-Po příkazech importu před definicí typu v souboru třídy<br />– Po proměnných deklarovaných ve třídě, před všemi postupy|
|Po deklaracích s jedním řádkem (deklarace na úrovni bez blokování)|– Následující příkazy pro import dědí příkazy, deklarace proměnných, deklarace událostí, deklarace delegátů a příkazy DLL Declare.|

## <a name="block-structure-guides"></a>Vodítka struktury bloku

Je-li vybrána tato možnost, zobrazí se v editoru svislé čáry, které se zařadí do strukturovaných bloků kódu, což vám umožní snadno identifikovat jednotlivé bloky kódu. Například by se zobrazila čára mezi `Sub` a `EndSub` v příkazu `Sub`.

## <a name="editor-help"></a>Pomocník s editorem

**Poměrně se seznamem (přeformátování) kódu** Textový editor přeformátuje kód podle potřeby. Pokud je vybrána tato možnost, Editor kódu bude:

- Zarovnejte kód se správnou polohou tabulátoru.

- Případná klíčová slova, proměnné a objekty se správným případem

- Přidání chybějícího `Then` do příkazu `If...Then`

- Přidání závorek do volání funkce

- Přidat chybějící koncové uvozovky do řetězců

- Přeformátovat exponenciální zápis

- Přeformátovat data

**Automatické vložení koncových konstrukcí**

Při psaní – například první řádek deklarace procedury, `Sub Main` – a stiskněte klávesu **ENTER**, textový editor přidá vyhovující řádek `End Sub`. Podobně pokud přidáte smyčku [for](/dotnet/visual-basic/language-reference/statements/for-next-statement) , textový editor přidá příkaz, který odpovídá `Next`. Pokud je vybrána tato možnost, Editor kódu automaticky přidá koncovou konstrukci.

**Automatické vložení členů rozhraní a MustOverride**

Při potvrzení příkazu `Implements` nebo příkazu `Inherits` pro třídu vloží textový editor prototypy pro členy, kteří mají být implementováni nebo potlačeni v uvedeném pořadí.

**Povolit návrhy oprav chyb**

Textový editor může navrhovat řešení běžných chyb a umožňuje vybrat příslušnou opravu, která se pak použije na váš kód.

## <a name="see-also"></a>Viz také:

- [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
