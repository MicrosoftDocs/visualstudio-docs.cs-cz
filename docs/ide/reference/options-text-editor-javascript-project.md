---
title: Možnosti, textový editor, JavaScript, projekt
ms.date: 06/19/2020
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6e4f5ff4e1081bbbe6aced4465afb40318048a5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285358"
---
# <a name="options-text-editor-javascript-project"></a>Možnosti, textový editor, JavaScript, projekt

Pomocí stránky **projekt** v dialogovém okně **Možnosti** můžete určit možnosti projektu JavaScript a TypeScript v editoru kódu. Chcete-li získat přístup k této stránce, v řádku **Tools**nabídek zvolte  >  **možnost**nástroje a potom rozbalte projekt **textový editor**  >  **JavaScript/TypeScript**  >  **Project**.

## <a name="project-analysis-options"></a>Možnosti analýzy projektu

Tyto možnosti určují, jak editor analyzuje projekty, sestavuje diagnostiku a navrhuje vylepšení. Zaškrtněte nebo zrušte zaškrtnutí možností pro určení způsobu, jakým Editor zpracovává tyto situace.

### <a name="uielement-list"></a>UIElement – seznam

- **Analyzovat pouze projekty, které obsahují soubory otevřené v editoru**
- **Pouze diagnostiku sestav pro soubory otevřené v editoru**
- **Navrhnout možná vylepšení, která nejsou opravena**

## <a name="virtual-projects-in-solution-explorer"></a>Virtuální projekty v Průzkumník řešení

Tyto možnosti umožňují zvolit, zda se mají zobrazit virtuální projekty, když je řešení načteno nebo není načteno.

## <a name="compile-on-save"></a>Kompilovat při uložení

Tyto možnosti určují, zda jsou soubory TypeScript, které nejsou součástí projektu, automaticky kompilovány. Visual Studio kompiluje pomocí nejnovější verze TypeScript nainstalované v adresáři *C:\Program Files (x86) \Microsoft SDKs\TypeScript*.

Zaškrtněte políčko a pak zvolte typ generování kódu, který chcete použít.

### <a name="uielement-list"></a>UIElement – seznam

- **Pro moduly, které nejsou součástí projektu, použijte generování kódu AMD**
- **Použít generování kódu CommonJS u modulů, které nejsou součástí projektu**
- **Použít generování kódu UMD u modulů, které nejsou součástí projektu**
- **Použít generování systémového kódu pro moduly, které nejsou součástí projektu**
- **Použít generování kódu ES2015 u modulů, které nejsou součástí projektu**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Verze ECMAScript pro soubory, které nejsou součástí projektu

Tyto možnosti umožňují vybrat verzi ECMAScript pro soubory, které nejsou součástí projektu. Můžete zvolit mezi **ECMAScript 3**, **ECMAScript 5**nebo **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>JSX Emit pro soubory TSX, které nejsou součástí projektu

Tyto možnosti určují, jak editor zpracovává soubory TypeScript, které nejsou součástí projektu.

### <a name="uielement-list"></a>UIElement – seznam

|Možnost|Popis|
|------------|-----------------|
|**Reakce – architektura**|Pokud je vybrána tato možnost, Editor kódu vygeneruje příponu souboru *. js* .|
|**Chovají**|Pokud je vybrána tato možnost, Editor kódu udržuje JSX jako součást výstupu a generuje příponu souboru *. jsx* .|

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)