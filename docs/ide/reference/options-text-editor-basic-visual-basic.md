---
title: Možnosti, Textový editor, základní (VB), upřesnit
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 562358ca90e223a07926aaa383ded41a5f7557cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431472"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Možnosti, Textový editor, základní (Visual Basic), upřesnit
Stránka **vlastností VB Specific** ve složce **Základní** ve složce **Textový editor** v dialogovém okně **Možnosti** **(Nástroje)** obsahuje následující vlastnosti:

## <a name="analysis"></a>Analýza

- Analýza živého kódu nebo obor analýzy pozadí

   Nakonfigurujte obor analýzy pozadí pro spravovaný kód. Další informace naleznete v [tématu Postup: Konfigurace oboru analýzy živého kódu pro spravovaný kód](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Používání směrnic

- Při řazení pomocí direktiv y nejprve umístěte direktivy "Systém"

   Když je tato volba vybraná, příkaz **Odebrat a seřadit usings** v nabídce po kliknutí pravým tlačítkem myši seřadí `using` direktivy a umístí obory názvů Systém na začátek seznamu.

- Samostatné pomocí skupin direktiv

   Když je tato volba vybraná, příkaz **Odebrat a seřadit usings** v nabídce po kliknutí pravým tlačítkem myši oddělí direktivy `using` vložením prázdného řádku mezi skupinami direktiv, které mají stejný kořenový obor názvů.

- Navrhnout použití pro typy v referenčních sestavách
- Navrhnout použití pro typy v balíčcích NuGet

   Pokud jsou vybrány tyto možnosti, [rychlá akce](../quick-actions.md) je k `using` dispozici k instalaci balíčku NuGet a přidat direktivu pro neodkazované typy.

   ![Rychlá akce pro instalaci balíčku NuGet v sadě Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Zvýraznění

 **Povolení zvýraznění odkazů a klíčových slov**

Textový editor může zvýraznit všechny výskyty symbolu nebo `If..Then` `While...End While`všech `Try...Catch...Finally`klíčových slov v klauzuli, například , nebo . Mezi zvýrazněnými odkazy nebo klíčovými slovy můžete přecházet stisknutím kláves **Ctrl** + **Shift** + **Down nebo** **Ctrl** + **Shift** + Shift**arrow**.

## <a name="outlining"></a>Sbalování

**Povolení režimu osnovy**

Když otevřete soubor v editoru kódu, můžete dokument zobrazit v režimu osnovy. Další informace naleznete [v tématu Osnova.](../../ide/outlining.md) Když je tato volba vybraná, funkce osnovy se aktivuje při otevření souboru.

**Zobrazit oddělovače čar procedury**

Textový editor označuje vizuální rozsah procedur. Čára je nakreslena ve zdrojových souborech *.vb* projektu v umístěních uvedených v následující tabulce:

|Umístění ve zdrojovém souboru .vb|Příklad umístění linky|
|---------------------------------|------------------------------|
|Po uzavření konstrukce deklarace bloku|- Na konci třídy, struktury, modulu, rozhraní nebo výčtu<br />- Po vlastnosti, funkce nebo sub<br />- Ne mezi get a set klauzule v nemovitosti|
|Po sadě jednořádkových konstrukcí|- Po příkazech importu před definicí typu v souboru třídy<br />- Po proměnných deklarovaných ve třídě, před všemi postupy|
|Po deklaracích jednoho řádku (deklarace neblokové úrovně)|- Následující příkazy importu dědí příkazy, deklarace proměnných, deklarace událostí, deklarace delegátů a deklarované příkazy dll.|

## <a name="block-structure-guides"></a>Vodítka blokové struktury

Když je tato volba vybraná, v editoru se zobrazí svislé čáry, které jsou zaokřovány do strukturovaných bloků kódu, což umožňuje snadno identifikovat jednotlivé bloky kódu. Například byste viděli čáru `Sub` mezi `EndSub` a `Sub` v příkazu.

## <a name="editor-help"></a>Nápověda k editoru

**Pretty Výpis (přeformátování) kódu** Textový editor přeformátuje váš kód podle potřeby. Pokud je vybrána tato možnost, editor kódu:

- Zarovnání kódu do správné polohy karty

- Přesuzovat klíčová slova, proměnné a objekty do správného případu

- Přidání chybějícího `Then` `If...Then` do příkazu

- Přidání závorek pro funkční volání

- Přidání chybějících koncových uvozovek do řetězců

- Přeformátovaný exponenciální zápis

- Přeformátovat data

**Automatické vkládání koncových konstrukcí**

Když píšete – například první řádek deklarace procedury `Sub Main`– a stiskněte `End Sub` **Enter**, textový editor přidá odpovídající řádek. Podobně pokud přidáte [for](/dotnet/visual-basic/language-reference/statements/for-next-statement) smyčky, textový editor přidá `Next` odpovídající příkaz. Když je vybrána tato možnost, editor kódu automaticky přidá koncovou konstrukci.

**Automatické vkládání členů Rozhraní a MustOverride**

Když potvrdíte `Implements` příkaz `Inherits` nebo příkaz pro třídu, textový editor vloží prototypy pro členy, které mají být implementovány nebo přepsány.

**Povolit návrhy oprav chyb**

Textový editor může navrhnout řešení běžných chyb a umožnit vám vybrat příslušnou opravu, která se pak použije na váš kód.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
