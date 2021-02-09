---
title: Klávesnice aplikace Office Excel, nastavení, dialogové okno Možnosti
description: Seznamte se s tím, jak můžete aplikaci Microsoft Excel přijmout příkazy klávesových zkratek, když se dokument soustředí na výběr dynamického schématu klávesnice.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 914b86e6e2b27d18e2089d44ce97810f82294c5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880343"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Systém Microsoft Office klávesnicí aplikace Excel, nastavení, dialogové okno Možnosti
  Systém Microsoft Office Excel a Visual Studio oba zpracovávají i klávesové zkratky. Stejná kombinace klávesových zkratek může být pro různé příkazy v Excelu a v aplikaci Visual Studio. Když je Excel otevřený v projektu na úrovni dokumentu v aplikaci Visual Studio, obdrží příkazy klávesových zkratek jenom jedna aplikace v jednom okamžiku. Ve výchozím nastavení Visual Studio přijímá všechny příkazy klávesových zkratek, ale můžete je nechat zobrazit v aplikaci Excel, pokud se dokument zaměřuje na výběr **dynamického schématu klávesnice**.

 Pokud použijete klávesovou zkratku, která není přiřazena k příkazu v aplikaci, která aktuálně zpracovává klávesové zkratky, je klávesová zkratka předána do druhé aplikace.

 Vybraná možnost zůstane platná pro projekty aplikace Excel, dokud ji nezměníte. Výběr nemá vliv na systém Microsoft Office wordové projekty; k provedení jakékoli změny aplikace Word je potřeba použít systém Microsoft Office možnosti klávesnice Wordu.

## <a name="uielement-list"></a>UIElement – seznam
 **Schéma klávesnice sady Visual Studio** Visual Studio obdrží všechny příkazy klávesových zkratek, i když má aplikace Excel fokus. Pokud například stisknete klávesu Functions **F5** , zatímco má aplikace Excel fokus, začne aplikace Visual Studio ladit vaše řešení.

 **Dynamické schéma klávesnice** Visual Studio přijímá příkazy klávesových zkratek pouze v případě, že má fokus. Pokud má aplikace Excel fokus, aplikace Excel obdrží všechny příkazy klávesových zkratek. Pokud například stisknete klávesu Functions **F5** , zatímco má aplikace Excel fokus, otevře se v aplikaci Excel dialogové okno **Přejít na** . Pokud stisknete klávesu **F5** během fokusu sady Visual Studio, Visual Studio začne ladit vaše řešení.

## <a name="see-also"></a>Viz také
- [Systém Microsoft Office klávesnice Word systém Microsoft Office nastavení klávesnice, dialogové okno Možnosti](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
