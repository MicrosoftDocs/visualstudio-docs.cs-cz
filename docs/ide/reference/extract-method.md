---
title: Extrakce metody
description: Zapněte fragment kódu do své vlastní metody, a to tak, že vyberete kód a zadáte CTRL + R, CTRL + M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6ee11ec012ae0f104f5fefff7302d3982e43721a
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083652"
---
# <a name="extract-a-method-refactoring"></a>Extrakce refaktoringu metody

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje přepínat fragment kódu na svou vlastní metodu.

**Když:** Máte fragment stávajícího kódu v některé metodě, který je třeba volat z jiné metody.

**Proč:** Tento kód můžete zkopírovat nebo vložit, ale to by vedlo k duplikaci. Lepším řešením je refaktoring, který by se měl fragmentovat na vlastní metodu, kterou může volat libovolná jiná metoda.

## <a name="how-to"></a>Postupy

1. Zvýrazněte kód, který se má extrahovat:

   - C#:

       ![Snímek obrazovky zobrazující kód C# pro třídu programu V hlavní funkci této třídy byl zvýrazněn řádek kódu.](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Snímek obrazovky zobrazující kód Visual Basic pro hlavní sub V tomto sub je zvýrazněna řádka kódu.](media/extractmethod-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte **kombinaci kláves CTRL + R** a potom **CTRL + M**. (Všimněte si, že se vaše klávesová zkratka může lišit v závislosti na vybraném profilu.)
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a vybrat možnost **Extrahovat metodu** z místní nabídky okna náhledu.
   - **Myš**
      - Vyberte **upravit > refaktorovat > metoda extrahování**.
      - Klikněte pravým tlačítkem na kód a vyberte **refaktoring > extrahovat > extrahovat metodu**.
      - Klikněte pravým tlačítkem na kód, vyberte nabídku **rychlé akce a refaktoring** a v okně Náhled **rozbalte položku extrahovat metodu** .

   Metoda se vytvoří okamžitě. Odsud teď můžete metodu přejmenovat jednoduše zadáním nového názvu.

   > [!TIP]
   > Pomocí zaškrtávacích políček v poli **Přejmenovat** , které se zobrazí v pravém horním rohu integrovaného vývojového prostředí (IDE), můžete také aktualizovat komentáře a další řetězce, aby používaly tento nový název i [Náhled změn](../../ide/preview-changes.md) .

   - C#:

      ![Snímek obrazovky zobrazující kód C# pro třídu programu Název metody je zvýrazněn a automaticky otevírané okno pro přejmenování je otevřené.](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Snímek obrazovky zobrazující kód Visual Basic pro hlavní sub Název metody je zvýrazněn a automaticky otevírané okno pro přejmenování je otevřené.](media/extractmethod-rename-vb.png)

3. Až budete s změnou spokojeni, zvolte tlačítko **použít** nebo stiskněte klávesu **ENTER** . změny budou potvrzeny.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
