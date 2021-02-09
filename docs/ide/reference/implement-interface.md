---
title: Implementace rozhraní
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoring hned vygenerovat kód potřebný k implementaci rozhraní.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 37adee082f5356180b4e1d58007db48a7f9bb60e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852489"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementace rozhraní v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje hned vygenerovat kód potřebný k implementaci rozhraní.

**Když:** Chcete dědit z rozhraní.

**Proč:** Všechna rozhraní můžete ručně implementovat jednou, ale tato funkce vygeneruje všechny signatury metod automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek, kde je červená vlnovka, která indikuje, že jste odkazovali na rozhraní, ale neimplementovali všechny požadované členy.

   - C#:

       ![Zvýrazněný kód C #](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/interface-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Myš**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

3. V rozevírací nabídce vyberte **implementovat rozhraní** .

   ![Implementovat rozhraní Preview](media/interface-preview-cs.png)

   > [!TIP]
   > - Pomocí odkazu **Náhled změn** v dolní části okna Preview [zobrazíte všechny změny](../../ide/preview-changes.md) , které budou provedeny před provedením výběru.
   > - Použijte odkazy **dokumentu**, **projektu** a **řešení** v dolní části okna Preview k vytvoření správných podpisů metody napříč více třídami, které implementují rozhraní.

   Signatury metody rozhraní jsou vytvořeny a jsou připraveny k implementaci.

   - C#:

       ![Implementovat výsledek rozhraní C #](media/interface-result-cs.png)

   - Visual Basic:

       ![Implementovat výsledek rozhraní VB](media/interface-result-vb.png)

   > [!TIP]
   > (Pouze C#) Použijte možnost **implementovat rozhraní explicitně k předvedení** každé vygenerované metody s názvem rozhraní, abyste se vyhnuli kolizím názvů.
   >
   > ![Výsledek implementace explicitního rozhraní](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
