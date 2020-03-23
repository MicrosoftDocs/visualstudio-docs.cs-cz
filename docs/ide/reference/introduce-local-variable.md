---
title: Zavedení místní proměnné
description: Vygenerujte místní proměnnou, která nahradí existující výraz. Vyberte výraz, klikněte pravým tlačítkem myši a vyberte nabídku Rychlé akce a Refaktoringy, vyberte Zavést místní pro (všechny výskyty) výrazu.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0fbd5ed752b28cc3f8c0dd734ed2b3ce09e80b78
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568812"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Zavedení místní proměnné v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě vygenerovat místní proměnnou, která nahradí existující výraz.

**Kdy:** Máte kód, který by mohl být snadno znovu použít později, pokud byly v místní proměnné.

**Proč:** Můžete zkopírovat a vložit kód vícekrát použít v různých umístěních, ale bylo by lepší provést operaci jednou, ukládat výsledek v místní proměnné a používat místní proměnné v celém textu.

## <a name="how-to"></a>Postupy

1. Zvýrazněte výraz, který chcete přiřadit nové místní proměnné.

   - C#:

       ![Zvýrazněný kód C #](media/local-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/local-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Klikněte na ![Šroubovák](media/screwdriver.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku se zvýrazněným výrazem.

   ![Zavedení místního náhledu](media/local-preview-cs.png)

3. V rozevírací nabídce vyberte možnost **Zavést místní pro (všechny výskyty) výrazu.**

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna náhledu [zobrazíte všechny změny,](../../ide/preview-changes.md) které budou provedeny před provedením výběru.

   Místní proměnná je vytvořena, s typem odvozeným z jeho použití. Pojmenujte novou místní proměnnou novým názvem.

   - C#:

       ![Výsledek implementace rozhraní C #](media/local-result-cs.png)

   - Visual Basic:

       ![Implementovat výsledek rozhraní VB](media/local-result-vb.png)

   > [!NOTE]
   > Můžete použít **... všechny výskyty...** možnost nabídky, která nahradí každou instanci vybraného výrazu, nikoli pouze tu, kterou jste konkrétně zvýraznili.

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
