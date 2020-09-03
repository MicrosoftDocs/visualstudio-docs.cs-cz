---
title: Možnosti, textový editor, Basic (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1edb7ceae1ba187b01b92d64ca33d41d83364e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662376"
---
# <a name="options-text-editor-basic-visual-basic"></a>Možnosti, textový editor, Basic (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stránka **vlastností specifická pro VB** v dialogovém okně **základní** složky **textového editoru** v nabídce **Možnosti** (**nástroje** ) obsahuje následující vlastnosti:

 **Automatické vložení koncových konstrukcí** Když zadáte například první řádek deklarace procedury `Sub Main—` a stisknete klávesu ENTER, textový editor přidá shodný `End Sub` řádek. Podobně pokud přidáte smyčku [for](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9) , textový editor přidá shodný `Next` příkaz. Pokud je vybrána tato možnost, Editor kódu automaticky přidá koncovou konstrukci.

 **Poměrně se seznamem (přeformátování) kódu** Textový editor přeformátuje kód podle potřeby. Pokud je vybrána tato možnost, Editor kódu bude:

- Zarovnejte kód se správnou polohou tabulátoru.

- Případná klíčová slova, proměnné a objekty se správným případem

- Přidat chybějící `Then` `If...Then` příkaz do příkazu

- Přidání závorek do volání funkce

- Přidat chybějící koncové uvozovky do řetězců

- Přeformátovat exponenciální zápis

- Přeformátovat data

  **Povolit režim sbalení** Když otevřete soubor v editoru kódu, můžete zobrazit dokument v režimu sbalení. Další informace najdete v tématu [popisujícím sbalení](../../ide/outlining.md) . Když je vybraná tato možnost, funkce sbalení se aktivuje při otevření souboru.

  **Automatické vložení členů rozhraní a MustOverride** Při potvrzení `Implements` příkazu nebo `Inherits` příkazu pro třídu vloží textový editor prototypy pro členy, kteří mají být implementováni nebo přepsáni v uvedeném pořadí.

  **Zobrazit oddělovače řádků procedury** Textový editor označuje vizuální rozsah procedur. Řádek se vykreslí ve zdrojových souborech. vb projektu v umístěních uvedených v následující tabulce:

|Umístění ve zdrojovém souboru. vb|Příklad umístění řádku|
|---------------------------------|------------------------------|
|Po ukončení konstrukce deklarace bloku|– Na konci třídy, struktury, modulu, rozhraní nebo výčtu<br />– Za vlastností, funkcí nebo sub<br />– Není mezi klauzulemi Get a set ve vlastnosti.|
|Po sadě jednoduchých konstrukcí|-Po příkazech importu před definicí typu v souboru třídy<br />– Po proměnných deklarovaných ve třídě, před všemi postupy|
|Po deklaracích s jedním řádkem (deklarace na úrovni bez blokování)|– Následující příkazy pro import dědí příkazy, deklarace proměnných, deklarace událostí, deklarace delegátů a příkazy DLL Declare.|

 **Povolit návrhy oprav chyb** Textový editor může navrhovat řešení běžných chyb a umožňuje vybrat příslušnou opravu, která se pak použije na váš kód.

 **Povolit zvýraznění odkazů a klíčových slov** Textový editor může zvýraznit všechny výskyty symbolu nebo všechna klíčová slova v klauzuli, jako například `If..Then` , `While...End While` nebo `Try...Catch...Finally` . Stisknutím kombinace kláves CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru můžete procházet mezi zvýrazněnými odkazy nebo klíčovými slovy.

## <a name="see-also"></a>Viz také
 [Obecné, prostředí, možnosti dialogového okna](../../ide/reference/general-environment-options-dialog-box.md) možnosti [, textový editor, všechny jazyky, karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
