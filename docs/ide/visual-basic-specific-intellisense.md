---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 118de9ec05bcd5c56376376619bea0c5148d36ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594185"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Technologie IntelliSense pro soubory kódu jazyka Visual Basic

Editor zdrojového kódu jazyka Visual Basic nabízí následující funkce technologie IntelliSense:

## <a name="syntax-tips"></a>Tipy pro syntaxi

Popisy syntaxe zobrazují syntaxi příkazu, který zadáváte. To je užitečné pro příkazy, jako je [například Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Automatické dokončování

- Dokončení na různých klíčových slov

     Pokud například zadáte `goto` a zadáte mezeru, technologie IntelliSense zobrazí seznam definovaných popisků v rozevírací nabídce. Mezi další podporovaná `Option`klíčová `Declare`slova patří `Exit`, `Implements`, a .

- Dokončení `Enum` dne a`Boolean`

    Pokud příkaz bude odkazovat na člena výčtu, IntelliSense zobrazí seznam `Enum`členů . Pokud bude příkaz odkazovat na `Boolean`, intelliSense zobrazí true-false rozevírací nabídku.

Dokončení lze ve výchozím nastavení vypnout zrušením výběru **výběru členů seznamu Automaticky** ze stránky vlastností **Obecné** ve složce **Visual Basic.**

Dokončení můžete vyvolat ručně vyvoláním zobrazení členů seznamu, úplného wordu nebo **alt**+**pravé šipky**. Další informace naleznete [v tématu Use IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>Technologie IntelliSense v zóně

Technologie IntelliSense v zóně pomáhá vývojářům [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jazyka Visual Basic, kteří potřebují nasadit aplikace prostřednictvím a jsou omezeny na nastavení částečné důvěryhodnosti. Tato funkce:

- Umožňuje zvolit oprávnění, se kterými bude aplikace spuštěna.

- Zobrazte rozhraní API ve zvolené zóně jako dostupná v seznamu Členové a zobrazíte rozhraní API, která vyžadují další oprávnění jako nedostupná.

Další informace naleznete v [tématu Zabezpečení přístupu kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Filtrované seznamy dokončení

V jazyce Visual Basic mají seznamy dokončení technologie IntelliSense dva ovládací prvky karet umístěné v dolní části seznamů. Karta **Společné,** která je ve výchozím nastavení vybraná, zobrazuje položky, které se nejčastěji používají k dokončení příkazu, který píšete. Na kartě **Vše** se zobrazí všechny položky, které jsou k dispozici pro automatické dokončení, včetně těch, které jsou také na kartě **Společné.**

## <a name="see-also"></a>Viz také

- [Používání technologie IntelliSense](../ide/using-intellisense.md)
