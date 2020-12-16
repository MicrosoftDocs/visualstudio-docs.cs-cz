---
title: Klávesnice Office Word, nastavení, dialogové okno Možnosti
description: Seznamte se s tím, jak můžete aplikaci Microsoft Word přijmout příkazy klávesových zkratek, když se dokument soustředí na výběr dynamického schématu klávesnice.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf4cfbaf23ad9c1e545af25614722cd52c493df7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528439"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Systém Microsoft Office klávesnice Word, nastavení, dialogové okno Možnosti
  Systém Microsoft Office Word a Visual Studio oba zpracovávají klávesové zkratky. Stejná kombinace klávesových zkratek může být pro různé příkazy ve Wordu a v aplikaci Visual Studio. Když je Word otevřený v projektu na úrovni dokumentu v aplikaci Visual Studio, obdrží příkazy klávesových zkratek jenom jedna aplikace současně. Ve výchozím nastavení Visual Studio přijímá všechny příkazy klávesových zkratek, ale můžete je nechat přijmout, když se dokument soustředí na výběr **dynamického schématu klávesnice**.

 Pokud použijete klávesovou zkratku, která není přiřazena k příkazu v aplikaci, která aktuálně zpracovává klávesové zkratky, je klávesová zkratka předána do druhé aplikace.

 Vybraná možnost zůstane platná pro projekty aplikace Word, dokud ji nezměníte. Výběr nemá vliv na systém Microsoft Office excelové projekty; k provedení jakékoli změny v aplikaci Excel je nutné použít systém Microsoft Office možnosti klávesnice aplikace Excel.

## <a name="uielement-list"></a>UIElement – seznam
 **Schéma klávesnice sady Visual Studio** Visual Studio obdrží všechny příkazy klávesových zkratek i v případě, že se dokument aplikace Word zaměřuje. Pokud například stisknete klávesu Functions **F5** , zatímco má dokument fokus, Visual Studio začne ladit vaše řešení.

 **Dynamické schéma klávesnice** Visual Studio přijímá příkazy klávesových zkratek pouze v případě, že má fokus. Pokud je v dokumentu aplikace Word fokus, aplikace Word obdrží všechny příkazy klávesových zkratek. Pokud například stisknete klávesu Functions **F5** , zatímco má wordový dokument fokus, otevře se dialogové okno **Najít a nahradit** s vybraným polem **Přejít na** kartu. Pokud stisknete klávesu **F5** během fokusu sady Visual Studio, Visual Studio začne ladit vaše řešení.

## <a name="see-also"></a>Viz také
- [Systém Microsoft Office klávesnice aplikace Excel, nastavení systém Microsoft Office klávesnice, dialogové okno Možnosti](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
