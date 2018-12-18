---
title: Možnosti, textový editor, C/C++, formátování
ms.date: 04/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ee7fab1564b39b29ae288e96c7aa77e0da21e88c
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235138"
---
# <a name="options-text-editor-cc-formatting"></a>Možnosti, textový editor, C/C++, formátování

Chcete-li změnit výchozí chování editoru kódu, pokud jsou programování v C nebo C++ použijte tyto stránky vlastností.

[Formátování C++ stránky vlastností](media/cpp-formatting.png)

 Pro přístup k této stránce v **možnosti** dialogové okno, v levém podokně rozbalte **textového editoru**, rozbalte položku **C/C++** a potom klikněte na **formátování** .

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení prostředí Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Obecná stránka

Tato stránka obsahuje možnosti pro formátování příkazů a blocích při psaní.

**Visual Studio 2017 verze 15.7 a novější**: stránka také obsahuje možnosti pro konfiguraci podpory pro [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) verze 5.0. ClangFormat je nástroj, který usnadňuje styl a formátování kódu na základě sady pravidel, které lze konfigurovat v souboru formátu .clang nebo _clang formátu.

### <a name="configuring-clangformat-options"></a>Konfigurace možností ClangFormat

V aplikaci Visual Studio 2017 verze 15.7 a novější je ve výchozím nastavení zapnutá podpora ClangFormat. Můžete zvolit, které tyto běžné konvence formátování použít na všechny projekty: LLVM, Google, chromu, Mozilla nebo WebKit. Můžete také vytvořit vlastní definice .clang formátu nebo formátu _clang soubor ve formátu. Pokud takový soubor se nachází ve složce projektu, Visual Studio se používá k formátování všechny soubory zdrojového kódu v této složce a jejích podsložkách. 

Ve výchozím nastavení v sadě Visual Studio clangformat.exe běží na pozadí použije formátování během psaní. Můžete také zadat pouze pro spuštění ručně vyvolá formátování příkazy **formátovat dokument (Ctrl + K, Ctrl + D)** nebo **formátovat výběr (Ctrl + K, Ctrl + F)**.


## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Odsazení, nové řádky, mezery zabalení stránky

Tyto stránek umožňují provádět přizpůsobení různé formátování, ale jsou ignorovány, pokud je povoleno ClangFormat.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)