---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bd68ae1996ce9ca70e2a8bf1dcb66822e1a8bb1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823278"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Technologie IntelliSense pro soubory kódu jazyka Visual Basic

Editor zdrojového kódu jazyka Visual Basic nabízí následující funkce IntelliSense:

## <a name="syntax-tips"></a>Syntaxe tipy

Syntaxe tipy zobrazení syntaxe příkazu, který píšete. To je užitečné pro příkazy, jako [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Automatické dokončování

- Dokončení různých klíčových slov

     Pokud zadáte například `goto` a mezeru, technologie IntelliSense zobrazí seznam popisků definované v rozevírací nabídce. Zahrnout další podporované klíčová slova `Exit`, `Implements`, `Option`, a `Declare`.

- Dokončení `Enum` a `Boolean`

    Pokud příkaz bude odkazovat na člena výčtu, IntelliSense zobrazí seznam členů `Enum`. Pokud příkaz bude odkazovat `Boolean`, technologie IntelliSense zobrazí rozevírací nabídku true na false.

Dokončení může být ve výchozím nastavení vypnuta odznačením **automatický seznam členů** z **Obecné** stránku vlastností v **jazyka Visual Basic** složky.

Dokončení lze vyvolat ručně vyvoláním seznam členů, úplné slovo nebo **Alt**+**šipka vpravo**. Další informace najdete v tématu [použití IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>Technologie IntelliSense v zóně

Technologie IntelliSense v zóně pomáhá vývojáře jazyka Visual Basic, kteří potřebují nasazovat aplikace prostřednictvím [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a jsou omezeny na nastavení částečným vztahem důvěryhodnosti. Tuto funkci:

- Umožní vám vybrat oprávnění, která bude aplikace spuštěna s.

- Rozhraní API zobrazení ve vybrané jako dostupné v seznamu členů zóny a zobrazit rozhraní API, která vyžadují další oprávnění jako nedostupné.

Další informace najdete v tématu [zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Filtrované seznamy dokončení

Seznamy dokončení technologie IntelliSense v jazyce Visual Basic mají dva ovládací prvky karet v dolní části seznamu. **Běžné** kartu, která je standardně vybraná, zobrazuje položky, které se nejčastěji používají k dokončení příkazu, který píšete. **Všechny** karta zobrazuje všechny položky, které jsou k dispozici pro automatické dokončování, včetně těch, které jsou k dispozici také v **běžné** kartu.

## <a name="see-also"></a>Viz také:

- [Používání technologie IntelliSense](../ide/using-intellisense.md)