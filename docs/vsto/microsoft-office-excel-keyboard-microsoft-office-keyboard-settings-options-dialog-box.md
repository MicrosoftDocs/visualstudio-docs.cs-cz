---
title: Klávesnice Office Excel, nastavení klávesnice, dialogové okno Možnosti
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836040"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Systém Microsoft Office klávesnice aplikace Excel, nastavení systém Microsoft Office klávesnice, dialogové okno Možnosti
  Systém Microsoft Office Excel a Visual Studio oba zpracovávají i klávesové zkratky. Stejná kombinace klávesových zkratek může být pro různé příkazy v Excelu a v aplikaci Visual Studio. Když je Excel otevřený v projektu na úrovni dokumentu v aplikaci Visual Studio, obdrží příkazy klávesových zkratek jenom jedna aplikace v jednom okamžiku. Ve výchozím nastavení Visual Studio přijímá všechny příkazy klávesových zkratek, ale můžete je nechat zobrazit v aplikaci Excel, pokud se dokument zaměřuje na výběr **dynamického schématu klávesnice**.

 Pokud použijete klávesovou zkratku, která není přiřazena k příkazu v aplikaci, která aktuálně zpracovává klávesové zkratky, je klávesová zkratka předána do druhé aplikace.

 Vybraná možnost zůstane platná pro projekty aplikace Excel, dokud ji nezměníte. Výběr nemá vliv na systém Microsoft Office wordové projekty; k provedení jakékoli změny aplikace Word je potřeba použít systém Microsoft Office možnosti klávesnice Wordu.

## <a name="uielement-list"></a>UIElement – seznam
 **Schéma klávesnice sady Visual Studio** Visual Studio obdrží všechny příkazy klávesových zkratek, i když má aplikace Excel fokus. Pokud například stisknete klávesu Functions **F5** , zatímco má aplikace Excel fokus, začne aplikace Visual Studio ladit vaše řešení.

 **Dynamické schéma klávesnice** Visual Studio přijímá příkazy klávesových zkratek pouze v případě, že má fokus. Pokud má aplikace Excel fokus, aplikace Excel obdrží všechny příkazy klávesových zkratek. Pokud například stisknete klávesu Functions **F5** , zatímco má aplikace Excel fokus, otevře se v aplikaci Excel dialogové okno **Přejít na** . Pokud stisknete klávesu **F5** během fokusu sady Visual Studio, Visual Studio začne ladit vaše řešení.

## <a name="see-also"></a>Viz také
- [Systém Microsoft Office klávesnice Word systém Microsoft Office nastavení klávesnice, dialogové okno Možnosti](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
