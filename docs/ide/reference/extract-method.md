---
title: Extrahovat metodu
description: Přepněte fragment kódu na vlastní metodu výběrem kódu a zadáním Ctrl+R, Ctrl+M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 50f14cc2a7eafe5d65e0c6a6af54bafa2ebb5a1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569696"
---
# <a name="extract-a-method-refactoring"></a>Extrahovat metodu refaktoringu

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje převést fragment kódu do vlastní metody.

**Kdy:** Máte fragment existujícího kódu v některé metodě, která musí být volána z jiné metody.

**Proč:** Můžete tento kód zkopírovat nebo vložit, ale to by vedlo k duplikaci. Lepším řešením je refaktorovat tento fragment do své vlastní metody, kterou lze volně volat jinou metodou.

## <a name="how-to"></a>Postupy

1. Zvýrazněte kód, který má být extrahován:

   - C#:

       ![Zvýrazněný kód- C #](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/extractmethod-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **kombinaci kláves Ctrl+R**a potom **kombinaci kláves Ctrl+M**. (Všimněte si, že klávesová zkratka se může lišit podle vybraného profilu.)
      - Stiskněte **klávesu Ctrl**+**.** aktivujte nabídku **Rychlé akce a Refaktoringy** a z místního okna Náhled vyberte **Možnost Extrahovat metodu.**
   - **Myš**
      - Vyberte **možnost Upravit > refaktorovat > metoda extrakce**.
      - Klepněte pravým tlačítkem myši na kód a vyberte **příkaz Refactor > Extract > Metoda extrakce**.
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Možnost Extrahovat metodu.**

   Metoda bude okamžitě vytvořena. Odtud můžete metodu jednoduše přejmenovat zadáním nového názvu.

   > [!TIP]
   > Můžete také aktualizovat komentáře a další řetězce pro použití tohoto nového názvu, stejně jako [náhled změn](../../ide/preview-changes.md) před uložením pomocí zaškrtávacích políček v poli **Přejmenovat,** které se zobrazí v pravém horním rohu vašeho ide.

   - C#:

      ![Přejmenovat metodu - C #](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Metoda přejmenování – Visual Basic](media/extractmethod-rename-vb.png)

3. Až budete se změnou spokojeni, zvolte tlačítko **Použít** nebo stiskněte **Enter** a změny budou potvrzeny.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
