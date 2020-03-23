---
title: Možnosti, Textový editor, JavaScript, Projekt
ms.date: 1/15/2019
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
ms.openlocfilehash: 190cbdb2a8096415985d83fc525b997572d252c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605932"
---
# <a name="options-text-editor-javascript-project"></a>Možnosti, Textový editor, JavaScript, Projekt

Pomocí stránky **Projekt** v dialogovém okně **Možnosti** určete volby projektu JavaScript u Jazyka TypeScript a TypeScript v Editoru kódu. Chcete-li získat přístup k této stránce, zvolte na řádku nabídek**možnosti** **nástrojů** > a potom **rozbalte aplikaci Text Editor** > **JavaScript/TypeScript** > **Project**.

## <a name="project-analysis-options"></a>Možnosti analýzy projektu

Tyto možnosti určují, jak editor analyzuje projekty, sestavy diagnostiky a navrhuje vylepšení. Vyberte nebo zrušte zaškrtnutí možnosti určit, jak editor zpracovává tyto situace.

### <a name="uielement-list"></a>Seznam Prvků UI

- **Analyzujte pouze projekty, které obsahují soubory otevřené v editoru**
- **Pouze diagnostika sestavy pro soubory otevřené v editoru**
- **Navrhnout možná zlepšení, která nejsou opravami**

## <a name="virtual-projects-in-solution-explorer"></a>Virtuální projekty v Průzkumníku řešení

Tyto možnosti umožňují zvolit, zda chcete zobrazit virtuální projekty při načtení nebo nenačtené řešení.

## <a name="compile-on-save"></a>Kompilace při uložení

Tyto volby určují, zda jsou automaticky kompilovány soubory typu TypeScript, které nejsou součástí projektu. Zaškrtněte políčko a pak zvolte typ generování kódu, který chcete použít.

### <a name="uielement-list"></a>Seznam Prvků UI

- **Použití generování kódu AMD pro moduly, které nejsou součástí projektu**
- **Použití generování kódu CommonJS pro moduly, které nejsou součástí projektu**
- **Generování kódu UMD pro moduly, které nejsou součástí projektu**
- **Generování systémového kódu pro moduly, které nejsou součástí projektu**
- **Použití generování kódu ES2015 pro moduly, které nejsou součástí projektu**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Verze ECMAScript pro soubory, které nejsou součástí projektu

Tyto volby umožňují vybrat verzi ECMAScript pro soubory, které nejsou součástí projektu. Můžete si vybrat mezi **ECMAScript 3**, **ECMAScript 5**nebo **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>JSX Emit pro soubory TSX, které nejsou součástí projektu

Tyto volby určují, jak editor zachází se soubory typu TypeScript, které nejsou součástí projektu.

### <a name="uielement-list"></a>Seznam Prvků UI

|Možnost|Popis|
|------------|-----------------|
|**Rozhraní React**|Pokud je tato volba vybraná, Editor kódu vyzařuje příponu *souboru JS.*|
|**Zachovat**|Je-li vybrána tato možnost, editor kódu zachová JSX jako součást výstupu a vyzařuje příponu *souboru JSX.*|

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)