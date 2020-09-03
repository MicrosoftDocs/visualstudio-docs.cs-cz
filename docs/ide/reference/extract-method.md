---
title: Extrakce metody
description: Zapněte fragment kódu do své vlastní metody, a to tak, že vyberete kód a zadáte CTRL + R, CTRL + M.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569696"
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

       ![Zvýrazněný kód-C #](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/extractmethod-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte **kombinaci kláves CTRL + R**a potom **CTRL + M**. (Všimněte si, že se vaše klávesová zkratka může lišit v závislosti na vybraném profilu.)
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a vybrat možnost **Extrahovat metodu** z místní nabídky okna náhledu.
   - **Myš**
      - Vyberte **upravit > refaktorovat > metoda extrahování**.
      - Klikněte pravým tlačítkem na kód a vyberte **refaktoring > extrahovat > extrahovat metodu**.
      - Klikněte pravým tlačítkem na kód, vyberte nabídku **rychlé akce a refaktoring** a v okně Náhled **rozbalte položku extrahovat metodu** .

   Metoda se vytvoří okamžitě. Odsud teď můžete metodu přejmenovat jednoduše zadáním nového názvu.

   > [!TIP]
   > Pomocí zaškrtávacích políček v poli **Přejmenovat** , které se zobrazí v pravém horním rohu integrovaného vývojového prostředí (IDE), můžete také aktualizovat komentáře a další řetězce, aby používaly tento nový název i [Náhled změn](../../ide/preview-changes.md) .

   - C#:

      ![Přejmenovat metodu-C #](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Přejmenovat metodu – Visual Basic](media/extractmethod-rename-vb.png)

3. Až budete s změnou spokojeni, zvolte tlačítko **použít** nebo stiskněte klávesu **ENTER** . změny budou potvrzeny.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
