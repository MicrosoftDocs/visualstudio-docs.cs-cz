---
title: Možnosti, textový editor, JavaScript, projekt
description: Naučte se, jak používat stránku projektu v dialogovém okně Možnosti k určení možností projektu JavaScript a TypeScript v editoru kódu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b30aaec3087cece63e392cf7170ac85f6be0ad7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932329"
---
# <a name="options-text-editor-javascript-project"></a>Možnosti, textový editor, JavaScript, projekt

Pomocí stránky **projekt** v dialogovém okně **Možnosti** můžete určit možnosti projektu JavaScript a TypeScript v editoru kódu. Chcete-li získat přístup k této stránce, v řádku nabídek zvolte  >  **možnost** nástroje a potom rozbalte projekt **textový editor**  >  **JavaScript/TypeScript**  >  .

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

Tyto možnosti umožňují vybrat verzi ECMAScript pro soubory, které nejsou součástí projektu. Můžete zvolit mezi **ECMAScript 3**, **ECMAScript 5** nebo **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>JSX Emit pro soubory TSX, které nejsou součástí projektu

Tyto možnosti určují, jak editor zpracovává soubory TypeScript, které nejsou součástí projektu.

### <a name="uielement-list"></a>UIElement – seznam

|Možnost|Popis|
|------------|-----------------|
|**Reakce – architektura**|Pokud je vybrána tato možnost, Editor kódu vygeneruje příponu souboru *. js* .|
|**Chovají**|Pokud je vybrána tato možnost, Editor kódu udržuje JSX jako součást výstupu a generuje příponu souboru *. jsx* .|

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)