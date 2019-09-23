---
title: Refaktorovat a přejmenovat
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d1b4ff448f04ff6f683fac06cbc0b31797edf587
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186599"
---
# <a name="rename-a-code-symbol-refactoring"></a>Symbol kód refaktoring pro přejmenování

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje přejmenovat identifikátory pro symboly kódu, jako jsou pole, lokální proměnné, metody, obory názvů, vlastnosti a typy.

**Kdy:** Chcete bezpečně přejmenovat bez nutnosti najít všechny instance a pak tento nový název zkopírovat a vložit.

**Proč:** Kopírování a vkládání nového názvu v celém projektu by nejspíš vedlo k chybám. Tento nástroj refaktoringu přesně provede akci přejmenování.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte kurzor textu uvnitř položky, která má být přejmenována:

   - C#:

       ![Zvýrazněný kód:C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/rename-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl + R**, pak **Ctrl + R**. (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
   - **Myši**
      - Vyberte **Upravit > Refaktorovat > přejmenujte**.
      - Klikněte pravým tlačítkem na kód a vybrat **přejmenovat**.

3. Přejmenujte položku jednoduše tak, že zadáte nový název.

   - C#:

      ![Animace – přejmenovatC#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Rename - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Můžete také aktualizovat komentáře a jiných řetězců použít tento nový název, stejně jako [zobrazit náhled změn](../../ide/preview-changes.md) před uložením používání zaškrtávacích políček v **přejmenovat** pole, které se zobrazí v horní části přímo z editoru.

4. Až budete spokojení s změny, zvolte **použít** tlačítko nebo stisknutím klávesy **Enter** a změny budou potvrzeny.

## <a name="remarks"></a>Poznámky

- Počínaje verzí Visual Studio 2019 verze 16,3 při přejmenování typu, který odpovídá názvu souboru, ve kterém se nachází, se zobrazí zaškrtávací políčko, které umožňuje přejmenovat soubor současně. Tato možnost se zobrazí při přejmenování třídy, rozhraní nebo výčtu. Tato možnost není podporována pro částečné typy s více definicemi.

   ![Přejmenovat animaci souborem –C#](media/rename-with-file-animated-cs.gif)
   
- Pokud použijete název, který již existuje, která by způsobila konflikt, který **přejmenovat** vás upozorní pole.

   ![Přejmenovat konflikt](media/rename-conflict-cs.png)

- Dalším způsobem, jak přejmenovat symbol, je změnit jeho název v editoru. Pak stiskněte klávesu CTRL v názvu symbolu a potom stiskněte **klávesu CTRL**+ **.** nebo jednoduše rozbalte nabídku ikony žárovky, která se zobrazí, a vyberte  **\<přejmenovat starý název \<> na nový název >** .

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
