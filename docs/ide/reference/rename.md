---
title: Přejmenování přepojení
ms.date: 01/26/2018
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
ms.openlocfilehash: 4dbccd4732f56d671fd74f59916885ea338136f8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565458"
---
# <a name="rename-a-code-symbol-refactoring"></a>Přejmenování refaktoringu symbolu kódu

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje přejmenovat identifikátory symbolů kódu, jako jsou pole, místní proměnné, metody, obory názvů, vlastnosti a typy.

**Kdy:** Chcete bezpečně přejmenovat něco, aniž byste museli najít všechny instance a zkopírovat/vložit nový název.

**Proč:** Kopírování a vkládání nového názvu v celém projektu by pravděpodobně mělo za následek chyby. Tento refaktoring nástroj bude přesně provádět akci přejmenování.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor do položky, která má být přejmenována:

   - C#:

       ![Zvýrazněný kód - C #](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/rename-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **kombinaci kláves Ctrl+R**a potom **kombinaci kláves Ctrl+R**. (Všimněte si, že klávesová zkratka se může lišit podle vybraného profilu.)
   - **Myš**
      - Vyberte **možnost Upravit > Refaktorovat > přejmenovat**.
      - Klepněte pravým tlačítkem myši na kód a vyberte **příkaz Přejmenovat**.

3. Položku přejmenujte jednoduše zadáním nového názvu.

   - C#:

      ![Přejmenovat animaci - C #](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Přejmenování - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Můžete také aktualizovat komentáře a další řetězce, abyste mohli použít tento nový název, a [také zobrazit náhled změn](../../ide/preview-changes.md) před uložením pomocí zaškrtávacích políček v poli **Přejmenovat,** které se zobrazí v pravém horním rohu editoru.

4. Až budete se změnou spokojeni, zvolte tlačítko **Použít** nebo stiskněte **Enter** a změny budou potvrzeny.

## <a name="remarks"></a>Poznámky

- Počínaje Visual Studio 2019 verze 16.3, když přejmenujete typ, který odpovídá názvu souboru, ve které se nachází, zobrazí se zaškrtávací políčko, které vám umožní přejmenovat soubor současně. Tato možnost se zobrazí při přejmenování třídy, rozhraní nebo výčtu. Tato možnost není podporována pro částečné typy s více definicemi.

   ![Přejmenování animace se souborem - C #](media/rename-with-file-animated-cs.gif)

- Pokud použijete název, který již existuje, což by způsobilo konflikt, pole **Přejmenovat** vás upozorní.

   ![Přejmenovat konflikt](media/rename-conflict-cs.png)

- Dalším způsobem, jak přejmenovat symbol, je změnit jeho název v editoru. Potom s kurzorem v názvu symbolu stiskněte **klávesu Ctrl**+**.** nebo stačí rozbalit nabídku ikon žárovky, která se zobrazí, a zvolte **Přejmenovat \<starý název> na \<nový název>**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
