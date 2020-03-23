---
title: 'Postupy: Implementace rozhraní (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe8db6c6bd7df5285880f7f860df5bb26db736a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590108"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Postup: Implementace rozhraní v Návrháři tříd

V **Návrháři tříd**, můžete implementovat rozhraní v diagramu třídy připojením ke třídě, která poskytuje kód pro metody rozhraní. **Návrhář třídy** generuje implementaci rozhraní a zobrazuje vztah mezi rozhraním a třídou jako vztah dědičnosti. Rozhraní můžete implementovat nakreslením čáry dědičnosti mezi rozhraním a třídou nebo přetažením rozhraní ze zobrazení třídy.

> [!TIP]
> Rozhraní můžete vytvářet stejným způsobem jako jiné typy. Pokud rozhraní existuje, ale nezobrazí se v diagramu třídy, nejprve jej zobrazte. Další informace naleznete v [tématu How to: Create types by using Class Designer](how-to-create-types.md) and How [to: View existing types](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Implementace rozhraní nakreslením čáry dědičnosti

1. V diagramu třídy zobrazte rozhraní a třídu, která bude implementovat rozhraní.

2. Nakreslete čáru dědičnosti z třídy a rozhraní.

     K třídě se zobrazí lízátko a popisek s názvem rozhraní identifikuje vztah dědičnosti. Visual Studio generuje zástupné procedury pro všechny členy rozhraní.

Další informace naleznete v [tématu How to: Create inheritance between types](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Implementace rozhraní z okna Zobrazení třídy

1. V diagramu třídy zobrazte třídu, kterou chcete implementovat rozhraní.

2. Otevřete **zobrazení tříd a** vyhledejte rozhraní.

    > [!TIP]
    > Pokud **zobrazení třídy** není otevřené, **otevřete zobrazení třídy** z nabídky **Zobrazení** nebo stiskněte **kombinaci kláves Ctrl**+**Shift**+**C**.

3. Přetáhněte uzel rozhraní do obrazce třídy v diagramu.

     K třídě se zobrazí lízátko a popisek s názvem rozhraní identifikuje vztah dědičnosti. Visual Studio generuje zástupné procedury pro všechny členy rozhraní; v tomto okamžiku je implementováno rozhraní.

## <a name="see-also"></a>Viz také

- [Postupy: Vytváření typů pomocí Návrháře tříd](how-to-create-types.md)
- [Postup: Zobrazení existujících typů](how-to-view-existing-types.md)
- [Postup: Vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Refaktoring tříd a typů](refactoring-classes-and-types.md)
