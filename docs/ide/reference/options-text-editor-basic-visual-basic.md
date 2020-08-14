---
title: Možnosti, textový editor, Basic (VB), Upřesnit
ms.date: 08/12/2020
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
author: akhera99
ms.author: midumont
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 778cd1f9c126b176cafad8b33a147d284bea1b67
ms.sourcegitcommit: 2946d802aec1418e87bfa779d81834eeb7be5c9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2020
ms.locfileid: "88214642"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Možnosti, textový editor, Basic (Visual Basic), Upřesnit
Stránka **vlastností specifická pro VB** se nachází ve složce **základní** ve složce **textový editor** v dialogovém okně **Možnosti** (nabídka**nástroje** ), která obsahuje následující vlastnosti:

## <a name="analysis"></a>Analýza

- Živá analýza kódu nebo obor analýzy na pozadí

   Nakonfigurujte obor analýzy na pozadí pro spravovaný kód. Další informace naleznete v tématu [How to: Configure Live Code Analysis Scope for Managed Code](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Direktivy using

- Při řazení direktiv using umístit nejdřív direktivy System

   Pokud je tato možnost vybrána, příkazy **Remove a Sort using** v nabídce po kliknutí pravým tlačítkem myši seřadí `using` direktivy a umístí do horní části seznamu obory názvů System.

- Samostatné použití skupin direktiv

   Pokud je tato možnost vybrána, příkaz **Odebrat a seřadit pomocí** v nabídce po kliknutí pravým tlačítkem myši oddělí `using` direktivy vložením prázdného řádku mezi skupiny směrnic, které mají stejný kořenový obor názvů.

- Navrhnout použití typů v referenčních sestaveních
- Navrhnout použití typů v balíčcích NuGet

   Pokud jsou tyto možnosti vybrány, je k dispozici [rychlá akce](../quick-actions.md) pro instalaci balíčku NuGet a přidání `using` direktivy pro neodkazované typy.

   ![Rychlá akce pro instalaci balíčku NuGet v aplikaci Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Zvýraznění

 **Povolit zvýraznění odkazů a klíčových slov**

Textový editor může zvýraznit všechny výskyty symbolu nebo všechna klíčová slova v klauzuli, jako například `If..Then` , `While...End While` nebo `Try...Catch...Finally` . Můžete přecházet mezi zvýrazněnými odkazy nebo klíčovými slovy stisknutím **kombinace kláves CTRL**  +  **+**  +  **šipka dolů** nebo **kombinací kláves CTRL**  +  **+**  +  **šipka nahoru**.

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

Je-li vybrána tato možnost, zobrazí se v editoru svislé čáry, které se zařadí do strukturovaných bloků kódu, což vám umožní snadno identifikovat jednotlivé bloky kódu. Například by se zobrazil řádek mezi `Sub` a `EndSub` v `Sub` příkazu.

## <a name="editor-help"></a>Pomocník s editorem

::: moniker range=">=vs-2019"
**Parametry názvu vloženého parametru**    
Je-li vybrána tato možnost, vloží parametry názvu parametru pro literály, přetypováníný literál a instance objektů před každý argument ve volání funkce.  

![Parametry názvu vloženého parametru pro Visual Basic](media/inline-parameter-name-hints-visualbasic.png)
::: moniker-end

**Poměrně se seznamem (přeformátování) kódu** Textový editor přeformátuje kód podle potřeby. Pokud je vybrána tato možnost, Editor kódu bude:

- Zarovnejte kód se správnou polohou tabulátoru.

- Případná klíčová slova, proměnné a objekty se správným případem

- Přidat chybějící `Then` `If...Then` příkaz do příkazu

- Přidání závorek do volání funkce

- Přidat chybějící koncové uvozovky do řetězců

- Přeformátovat exponenciální zápis

- Přeformátovat data

**Automatické vložení koncových konstrukcí**

Když zadáte, například první řádek deklarace procedury, `Sub Main` a stisknete klávesu **ENTER**, textový editor přidá shodný `End Sub` řádek. Podobně pokud přidáte smyčku [for](/dotnet/visual-basic/language-reference/statements/for-next-statement) , textový editor přidá shodný `Next` příkaz. Pokud je vybrána tato možnost, Editor kódu automaticky přidá koncovou konstrukci.

**Automatické vložení členů rozhraní a MustOverride**

Při potvrzení `Implements` příkazu nebo `Inherits` příkazu pro třídu vloží textový editor prototypy pro členy, kteří mají být implementováni nebo přepsáni v uvedeném pořadí.

**Povolit návrhy oprav chyb**

Textový editor může navrhovat řešení běžných chyb a umožňuje vybrat příslušnou opravu, která se pak použije na váš kód.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
