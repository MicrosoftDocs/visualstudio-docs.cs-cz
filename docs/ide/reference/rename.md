---
title: Přejmenování refaktoru
description: Naučte se používat funkci refaktor rename k přejmenování identifikátorů pro symboly kódu, jako jsou pole, místní proměnné, metody, obory názvů, vlastnosti a typy.
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 43a6e93815732c4f9d2ec7f29d6d6bef4c1f3451
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616717"
---
# <a name="rename-a-code-symbol-refactoring"></a>Přejmenování refaktoringu symbolů kódu

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje přejmenovat identifikátory pro symboly kódu, jako jsou pole, lokální proměnné, metody, obory názvů, vlastnosti a typy.

**Když:** Chcete bezpečně přejmenovat bez nutnosti najít všechny instance a pak tento nový název zkopírovat a vložit.

**Proč:** Kopírování a vkládání nového názvu v celém projektu by nejspíš vedlo k chybám. Tento nástroj refaktoringu provede přesně akci přejmenování.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor do položky, která má být přejmenována:

   - C#:

       ![Zvýrazněný kód-C #](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/rename-highlight-vb.png)

2. Pak použijte svou klávesnici nebo myš následujícím způsobem:

   - **Klávesnice**
      - Stiskněte klávesy **Ctrl + r** a pak **kombinaci kláves Ctrl + r**. (Všimněte si, že se vaše klávesová zkratka může lišit v závislosti na vybraném profilu.)
   - **Myš**
      - Vyberte možnost **upravit > refaktoring > přejmenovat**.
      - Klikněte pravým tlačítkem na kód a vyberte **Přejmenovat**.

3. Přejmenujte položku jednoduše zadáním nového názvu.

   - C#:

      ![Přejmenovat animaci – C #](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Přejmenování – VB](media/rename-rename-vb.png)

   > [!TIP]
   > Pomocí zaškrtávacích políček v poli **Přejmenovat** , které se zobrazí v pravém horním rohu editoru, můžete také aktualizovat komentáře a další řetězce a použít tento nový název a [Zobrazit náhled změn](../../ide/preview-changes.md) .

4. Až budete s změnou spokojeni, zvolte tlačítko **použít** nebo stiskněte klávesu **ENTER** . změny budou potvrzeny.

## <a name="remarks"></a>Poznámky

- Počínaje verzí Visual Studio 2019 verze 16,3 při přejmenování typu, který odpovídá názvu souboru, ve kterém se nachází, se zobrazí zaškrtávací políčko, které umožňuje přejmenovat soubor současně. Tato možnost se zobrazí při přejmenování třídy, rozhraní nebo výčtu. Tato možnost není podporována pro částečné typy s více definicemi.

   ![Přejmenovat animaci pomocí souboru-C #](media/rename-with-file-animated-cs.gif)

- Pokud použijete název, který již existuje, což by způsobilo konflikt, zobrazí se v poli pro **přejmenování** upozornění.

   ![Konflikt přejmenování](media/rename-conflict-cs.png)

- Dalším způsobem, jak přejmenovat symbol, je změnit jeho název v editoru. Pak stiskněte klávesu CTRL v názvu symbolu a potom stiskněte **klávesu CTRL** + **.** nebo jednoduše rozbalte nabídku ikony žárovky, která se zobrazí, a vyberte možnost **Přejmenovat \<old name> na \<new name>**.

   ![Přejmenování v editoru](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
