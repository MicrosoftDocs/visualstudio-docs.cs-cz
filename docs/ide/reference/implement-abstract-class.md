---
title: Implementace abstraktní třídy
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoring hned vygenerovat kód potřebný k implementaci abstraktní třídy.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 05527e8ab1414b3f372f6db22c258d51fcd119a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852502"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementace abstraktní třídy v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje hned vygenerovat kód potřebný k implementaci abstraktní třídy.

**Když:** Chcete dědit z abstraktní třídy.

**Proč:** Můžete ručně implementovat všechny abstraktní členy jednou po jedné, ale tato funkce automaticky vygeneruje všechny signatury metod.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek, kde je červená vlnovka, která indikuje, že jste zdědili od abstraktní třídy, ale neimplementovali všechny požadované členy.

   - C#:

       ![Zvýrazněný kód C #](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/abstract-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Myš**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

   ![Implementovat třídu Preview](media/abstract-preview-cs.png)

3. V rozevírací nabídce vyberte **implementovat abstraktní třídu** .

   > [!TIP]
   > - Pomocí odkazu **Náhled změn** v dolní části okna Preview [zobrazíte všechny změny](../../ide/preview-changes.md) , které budou provedeny před provedením výběru.
   > - Použijte odkazy **dokumentu**, **projektu** a **řešení** v dolní části okna Preview k vytvoření správných signatur metod napříč více třídami, které dědí z abstraktní třídy.

   Signatury abstraktní metody jsou vytvořeny a jsou připraveny k implementaci.

   - C#:

       ![Implementovat výsledek třídy C #](media/abstract-result-cs.png)

   - Visual Basic:

       ![Implementovat výsledek třídy VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
