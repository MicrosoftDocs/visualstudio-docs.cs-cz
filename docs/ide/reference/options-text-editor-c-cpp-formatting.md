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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596252"
---
# <a name="options-text-editor-cc-formatting"></a>Možnosti, textový editor, C/C++, formátování

Pomocí těchto stránek vlastností můžete změnit výchozí chování editoru kódu při programování v jazyce C nebo C++.

![C++ Formátování stránek vlastností](media/cpp-formatting.png)

Chcete-li získat přístup **Options** k této stránce, rozbalte v levém podokně v levém podokně **textový editor**, rozbalte **c/c++** a klepněte na **položku Formátování**.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace naleznete [v tématu Přizpůsobení prostředí IDE sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Obecná stránka

Tato stránka obsahuje možnosti pro formátování příkazů a bloků při jejich psaní.

::: moniker range="vs-2017"

**Visual Studio 2017 verze 15.7 a novější**:

::: moniker-end

Stránka má také možnosti pro konfiguraci podpory pro [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) verze 5.0. ClangFormat je nástroj, který usnadňuje styl a formátování kódu na základě sady pravidel, která lze nakonfigurovat v souboru formátu .clang nebo _clang formátu.

### <a name="configuring-clangformat-options"></a>Konfigurace voleb ClangFormat

::: moniker range="vs-2017"

**Visual Studio 2017 verze 15.7 a novější**:

::: moniker-end

Podpora ClangFormat je ve výchozím nastavení povolena. Můžete si vybrat, které z těchto běžných konvencí formátování se použijí na všechny vaše projekty: LLVM, Google, Chromium, Mozilla nebo WebKit. Můžete také vytvořit vlastní definici formátu .clang-format nebo _clang-format souboru. Pokud je takový soubor přítomen ve složce projektu, sada Visual Studio jej používá k formátování všech souborů zdrojového kódu v této složce a jejích podsložkách.

Ve výchozím nastavení visual studio spustí clangformat.exe na pozadí použije formátování při psaní. Můžete také určit, chcete-li jej spustit pouze pro ručně vyvolané příkazy formátování **Formát dokumentu (Ctrl+K, Ctrl+D)** nebo **Výběr formátu (Ctrl + K, Ctrl + F).**

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Odsazení, Nové řádky, Obtékání mezer

Tyto stránky umožňují různá vlastní nastavení formátování, ale jsou ignorovány, pokud je povolen formát ClangFormat.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)
