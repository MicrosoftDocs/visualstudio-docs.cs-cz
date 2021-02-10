---
title: Změna podpisu metody
description: Přidat, odebrat nebo změnit pořadí parametrů metody. Klikněte pravým tlačítkem na metodu, vyberte rychlé akce a refaktoring a vyberte změnit signaturu.
ms.date: 07/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 01acbab7725effff5b2edbf8a80ab4f115fd2eff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935843"
---
# <a name="change-a-method-signature-refactoring"></a>Změna refaktoringu signatury metody

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje odebrat nebo změnit pořadí parametrů metody.

**Když:** Chcete přesunout nebo odebrat parametr metody, který je aktuálně používán v různých umístěních.

**Proč:** Můžete ručně odebrat a změnit pořadí parametrů a pak vyhledat všechna volání této metody a změnit je po jednom, ale to může vést k chybám.  Tento nástroj refaktoringu úlohu provede automaticky.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor do názvu metody, kterou chcete změnit, nebo jedno z jeho použití:

   - C#:

       ![Zvýrazněný kód C #](media/changesignature-highlight-cs.png)

   - JAZYK

       ![Zvýrazněný Visual Basic kódu](media/changesignature-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesy **CTRL + R** a potom **CTRL + V**.  (Všimněte si, že se vaše klávesová zkratka může lišit v závislosti na vybraném profilu.)
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoringu** a v okně náhledu vyberte možnost **změnit podpis** .
   - **Myš**
      - Vyberte možnost **upravit > refaktoring > odebrat parametry**.
      - Vyberte možnost **upravit > refaktoring > změnit pořadí parametrů**.
      - Klikněte pravým tlačítkem na kód, vyberte nabídku **rychlé akce a refaktoring** a v okně Náhled vyberte **změnit podpis** .

3. V dialogu **změnit podpis** , který se zobrazí, můžete pomocí tlačítek na pravé straně změnit signaturu metody:

   ![Dialogové okno změnit podpis](media/change-signature.png)

   | Tlačítko | Description
   | ------ | ---
   | **Nahoru/dolů** | Přesunout vybraný parametr nahoru a dolů v seznamu
   | **Přidat** | Přidat do seznamu nový parametr
   | **Odebrat** | Odebere vybraný parametr ze seznamu.
   | **Obnovení** | Obnoví vybraný, překřížený parametr na seznam.

   > [!TIP]
   > Pomocí zaškrtávacího políčka **Náhled změn odkazu** můžete [Zobrazit, co bude výsledek](../../ide/preview-changes.md) před potvrzením.

4. Když v dialogovém okně **změnit podpis** vyberete **Přidat** , otevře se dialogové okno **Přidat parametr** . V okně **Přidat parametr** můžete zadat název typu a název parametru. Parametr lze nastavit jako povinný, nebo volitelný s výchozí hodnotou. Potom můžete přidat hodnotu pro lokalitu volání a vybrat pro ni pojmenovaný argument, anebo použít proměnnou TODO. Proměnná TODO vloží do kódu znak TODO, abyste mohli postupně zkontrolovat jednotlivé chyby a projít si lokality volání, a tak se rozhodnout, co se má předat. V případě volitelných parametrů máte možnost lokalitu volání úplně vynechat.

    ![Dialogové okno Přidat parametr-C #](media/add-parameter-dialog.png)

5. Až dokončíte přidávání parametru, klikněte na **OK** , aby se změny zobrazily.

    ![Dialogové okno změnit podpis](media/change-signature.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)