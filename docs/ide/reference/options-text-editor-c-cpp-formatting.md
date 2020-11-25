---
title: Možnosti, textový editor, C/C++, formátování
description: Naučte se, jak pomocí stránky možnosti formátování a jejích podstránek nastavit možnosti formátování kódu v editoru kódu při programování v jazyce C a C++.
ms.custom: SEO-VS-2020
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 264485fd8f20ee31046035dba7b208795d0d91b0
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041084"
---
# <a name="options-text-editor-cc-formatting"></a>Možnosti, textový editor, C/C++, formátování

Pomocí těchto stránek vlastností můžete změnit výchozí chování editoru kódu při programování v jazyce C nebo C++.

![Stránky vlastností formátování C++](media/cpp-formatting.png)

Chcete-li získat přístup k této stránce, v dialogovém okně **Možnosti** rozbalte v levém podokně položku **textový editor**, rozbalte položku **C/C++** a klikněte na možnost **formátování**.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Stránka Obecné

Tato stránka obsahuje možnosti formátování příkazů a bloků při jejich psaní.

::: moniker range="vs-2017"

**Visual Studio 2017 verze 15,7 a novější**:

::: moniker-end

Stránka také obsahuje možnosti pro konfiguraci podpory pro [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) verze 5,0. ClangFormat je nástroj, který usnadňuje formátování a formátování kódu na základě sady pravidel, která se dají nakonfigurovat ve formátu. Clang nebo ve formátu souboru _clang.

### <a name="configuring-clangformat-options"></a>Konfigurace možností ClangFormat

::: moniker range="vs-2017"

**Visual Studio 2017 verze 15,7 a novější**:

::: moniker-end

Podpora ClangFormat je ve výchozím nastavení povolená. Můžete zvolit, které z těchto běžných konvencí formátování se mají použít pro všechny vaše projekty: LLVM, Google, chrom, Mozilla nebo WebKit. Můžete také vytvořit vlastní definici formátu. Clang-Format nebo soubor _clang-Format. Pokud je takový soubor přítomen ve složce projektu, Visual Studio použije ho k formátování všech souborů zdrojového kódu v této složce a jejích podsložkách.

Ve výchozím nastavení se Visual Studio spouští clangformat.exe na pozadí při psaní aplikuje formátování. Můžete také určit, že se má spustit pouze pro ručně vyvolané příkazy formátování **Formát dokumentu (CTRL + k, CTRL + D)** nebo **Výběr formátu (CTRL + k, CTRL + F)**.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Odsazení, nové řádky, stránky zabalení mezer

Tyto stránky umožňují různá přizpůsobení formátování, ale pokud je ClangFormat povolená, ignorují se.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Pomocí technologie IntelliSense](../../ide/using-intellisense.md)
