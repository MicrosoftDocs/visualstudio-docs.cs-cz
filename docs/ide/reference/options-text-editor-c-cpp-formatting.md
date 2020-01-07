---
title: Možnosti, textový editor, C/C++, formátování
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
ms.openlocfilehash: d7a6029058ab0bc02a623df0e1733eb8548102d5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596252"
---
# <a name="options-text-editor-cc-formatting"></a>Možnosti, textový editor, C/C++, formátování

Pomocí těchto stránek vlastností můžete změnit výchozí chování editoru kódu při programování v jazyce C nebo C++.

![C++Formátování stránek vlastností](media/cpp-formatting.png)

Chcete-li získat přístup k této stránce, v dialogovém okně **Možnosti** rozbalte v levém podokně položku **textový editor**, rozbalte položku **C++C/** a klikněte na možnost **formátování**.

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

Ve výchozím nastavení používá Visual Studio clangformat. exe na pozadí při psaní formátování. Můžete také určit, že se má spustit pouze pro ručně vyvolané příkazy formátování **Formát dokumentu (CTRL + k, CTRL + D)** nebo **Výběr formátu (CTRL + k, CTRL + F)** .

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Odsazení, nové řádky, stránky zabalení mezer

Tyto stránky umožňují různá přizpůsobení formátování, ale pokud je ClangFormat povolená, ignorují se.

## <a name="see-also"></a>Viz také:

- [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)
