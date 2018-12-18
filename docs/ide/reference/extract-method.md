---
title: Extrahovat metodu
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b80b5053022b9e42bb6cfd30e3c76a72bef70746
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064611"
---
# <a name="extract-a-method-refactoring"></a>Extrahovat metodu refaktoring

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** umožňuje zapnout fragment kódu do své vlastní metody.

**Kdy:** máte fragment stávající kód v některé metody, která musí být volána z jiné metody.

**Důvod, proč:** vám může kopírovat/vložit tento kód, ale které by mohlo dojít k duplikaci. Lepším řešením je refaktorovat tohoto fragmentu do své vlastní metody, které je možné vyvolat volně jiným způsobem.

## <a name="how-to"></a>Postupy

1. Zvýraznění kódu extrahovaným:

   - C#:

       ![Zvýrazněný kód –C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/extractmethod-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl + R**, pak **Ctrl + M**. (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **extrahovat metodu** z automaticky otevíraného okna okno náhledu.
   - **Myši**
      - Vyberte **Upravit > Refaktorovat > extrahovat metodu**.
      - Klikněte pravým tlačítkem na kód a vybrat **Refaktorovat > extrahovat > extrahovat metodu**.
      - Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **extrahovat metodu** z automaticky otevíraného okna okno náhledu.

   Metoda se okamžitě vytvoří. Z tohoto místa můžete nyní přejmenovat metodu jednoduše tak, že zadáte nový název.

   > [!TIP]
   > Můžete také aktualizovat komentáře a jiných řetězců použít tento nový název, stejně jako [náhled změn](../../ide/preview-changes.md) před uložením používání zaškrtávacích políček v **přejmenovat** pole, které se zobrazí v horní části napravo od prostředí (IDE).

   - C#:

      ![Přejmenovat metodu-C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Přejmenovat metodu - jazyka Visual Basic](media/extractmethod-rename-vb.png)

3. Až budete spokojení s změny, zvolte **použít** tlačítko nebo stisknutím klávesy **Enter** a změny budou potvrzeny.

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)