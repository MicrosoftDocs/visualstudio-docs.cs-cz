---
title: Implementace abstraktní třídy
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6fcfdc06a055df28159f9d1ddc440aaf113f3264
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568903"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementace abstraktní třídy v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě vygenerovat kód potřebný k implementaci abstraktní třídy.

**Kdy:** Chcete dědit z abstraktní třídy.

**Proč:** Můžete ručně implementovat všechny abstraktní členy jeden po druhém, ale tato funkce automaticky vygeneruje všechny podpisy metod.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek, kde je červená vlnovka, která označuje, že jste zdědili z abstraktní třídy, ale nebyly implementovány všechny požadované členy.

   - C#:

       ![Zvýrazněný kód C #](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/abstract-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Najeďte přes červenou vlnovku a klikněte na ![chybová žárovka](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![chybová žárovka](media/error-bulb.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s červenou vlnovkou.

   ![Implementace náhledu třídy](media/abstract-preview-cs.png)

3. V rozevírací nabídce vyberte **Implementovat abstraktní třídu.**

   > [!TIP]
   > - Pomocí odkazu **Náhled změn** v dolní části okna náhledu [zobrazíte všechny změny,](../../ide/preview-changes.md) které budou provedeny před provedením výběru.
   > - Pomocí odkazů **Dokument**, **Projekt**a **Řešení** v dolní části okna náhledu vytvořte správné podpisy metod napříč více třídami, které dědí z abstraktní třídy.

   Podpisy abstraktní metody jsou vytvořeny a jsou připraveny k implementaci.

   - C#:

       ![Výsledek implementace třídy C #](media/abstract-result-cs.png)

   - Visual Basic:

       ![Výsledek implementace třídy VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
