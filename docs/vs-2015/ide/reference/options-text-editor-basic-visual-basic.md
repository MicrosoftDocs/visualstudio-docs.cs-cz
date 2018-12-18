---
title: Možnosti, textový Editor, Basic (Visual Basic) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb8856f250810988b73058562402c8d1fe8c644f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902474"
---
# <a name="options-text-editor-basic-visual-basic"></a>Možnosti, textový editor, Basic (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**VB konkrétní** stránce vlastností **základní** složky **textový Editor** složky **možnosti** (**nástroje** nabídky) dialogové okno obsahuje následující vlastnosti:  
  
 **Automatické vkládání koncových konstruktorů**  
 Po zadání – například první řádek deklaraci procedury `Sub Main—`a stiskněte klávesu ENTER, textový editor přidá odpovídající `End Sub` řádku. Podobně pokud chcete přidat [pro](http://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9) smyčky, textový editor přidá odpovídající `Next` příkazu. Pokud je vybraná tato možnost, editor kódu automaticky přidá koncová konstrukce.  
  
 **Přehlednou výpis (přeformátování) kódu**  
 Textový editor přeformátuje kódu podle potřeby. Pokud je vybraná tato možnost, bude se editor kódu:  
  
- Zarovnat kód do umístění správné tabulátoru  
  
- Recase klíčová slova, proměnných a objektů na správnou velikost.  
  
- Přidat chybějící `Then` do `If...Then` – příkaz  
  
- Přidat závorky k volání funkce  
  
- Přidat chybí koncové uvozovky na řetězce  
  
- U vydavatelských exponenciální zápis  
  
- U vydavatelských kalendářních dat  
  
  **Povolení režimu sbalení**  
  Při otevření souboru v editoru kódu se zobrazí dokument v režimu sbalování. Zobrazit [Osnova](../../ide/outlining.md) Další informace. Pokud je vybraná tato možnost, funkci sbalování se aktivuje při otevření souboru.  
  
  **Automatické vložení členů rozhraní a MustOverride**  
  Pokud jste se zavázali `Implements` příkaz nebo `Inherits` příkaz pro třídu, textový editor vloží prototypy pro členy, které musí být implementován nebo jeho přepsána, v uvedeném pořadí.  
  
  **Zobrazit oddělovače řádků procedury**  
  Textový editor označuje visual oboru postupy. Řádek je vykreslena ve zdrojových souborech .vb vašeho projektu v umístěních uvedených v následující tabulce:  
  
|Umístění ve zdrojovém souboru .vb|Příklad umístění řádku|  
|---------------------------------|------------------------------|  
|Po uzavření bloku deklarace konstruktoru|– Na konci třída, struktura, modul, rozhraní nebo výčet<br />-After vlastnost, funkce nebo procedury sub<br />-Není mezi get a set klauzule ve vlastnosti|  
|Po sadu konstrukce jeden řádek|-After příkazy pro import, před definici typu v souboru třídy<br />-After proměnné deklarované ve třídě, před všechny postupy|  
|Po jeden řádek deklarací (deklarace mimo blok úrovně)|-Následující příkazy pro import, dědí příkazy deklarace proměnných, deklarace události, delegát deklarace a příkazy deklarovat knihovny DLL|  
  
 **Povolit návrhy oprav**  
 Do textového editoru můžete navrhnout řešení pro běžné chyby a umožní vám vybrat příslušnou opravu se následně použije na váš kód.  
  
 **Povolit zvýrazňování odkazů a klíčových slov**  
 Do textového editoru můžete zvýraznit všechny výskyty symbolu nebo všechna klíčová slova v klauzuli například `If..Then`, `While...End While`, nebo `Try...Catch...Finally`. Mezi zvýrazněných odkazů nebo klíčová slova můžete přejít stisknutím kombinace kláves CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="see-also"></a>Viz také  
 [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)   
 [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)



