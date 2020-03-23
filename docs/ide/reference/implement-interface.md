---
title: Implementace rozhraní
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d420bd0d42e89476696966f7eda94a19893fc23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595550"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementace rozhraní v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě vygenerovat kód potřebný k implementaci rozhraní.

**Kdy:** Chcete dědit z rozhraní.

**Proč:** Můžete ručně implementovat všechny rozhraní jeden po druhém, ale tato funkce bude generovat všechny podpisy metody automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek, kde je červená vlnovka, která označuje, že jste odkazovali na rozhraní, ale nebyly implementovány všechny požadované členy.

   - C#:

       ![Zvýrazněný kód C #](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/interface-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Najeďte přes červenou vlnovku a klikněte na ![chybová žárovka](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![chybová žárovka](media/error-bulb.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s červenou vlnovkou.

3. V rozevírací nabídce vyberte **Implementovat rozhraní.**

   ![Implementace náhledu rozhraní](media/interface-preview-cs.png)

   > [!TIP]
   > - Pomocí odkazu **Náhled změn** v dolní části okna náhledu [zobrazíte všechny změny,](../../ide/preview-changes.md) které budou provedeny před provedením výběru.
   > - Pomocí odkazů **Dokument**, **Projekt**a **Řešení** v dolní části okna náhledu vytvořte správné podpisy metod napříč více třídami, které implementují rozhraní.

   Podpisy metody rozhraní je vytvořen a je připraven k implementaci.

   - C#:

       ![Výsledek implementace rozhraní C #](media/interface-result-cs.png)

   - Visual Basic:

       ![Implementovat výsledek rozhraní VB](media/interface-result-vb.png)

   > [!TIP]
   > (pouze C#) Pomocí **možnosti Implement interface explicit** můžete předběžně předpojit každou generovanou metodu s názvem rozhraní, abyste se vyhnuli kolizím názvů.
   >
   > ![Implementovat explicitně výsledek rozhraní](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
