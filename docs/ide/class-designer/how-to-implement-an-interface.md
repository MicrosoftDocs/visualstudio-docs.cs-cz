---
title: 'Postupy: Implementace rozhraní (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81b6815dd96894acd574de59c5616371220d2999
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770107"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Postupy: implementace rozhraní v Návrhář tříd

V **Návrhář tříd**můžete implementovat rozhraní v diagramu tříd tím, že ho propojíte s třídou, která poskytuje kód pro metody rozhraní. **Návrhář tříd** generuje implementaci rozhraní a zobrazuje vztah mezi rozhraním a třídou jako vztah dědičnosti. Rozhraní lze implementovat kreslením čáry dědičnosti mezi rozhraním a třídou nebo přetažením rozhraní z Zobrazení tříd.

> [!TIP]
> Rozhraní můžete vytvořit stejným způsobem jako jiné typy. Pokud rozhraní existuje, ale není zobrazeno v diagramu tříd, pak jej nejprve zobrazte. Další informace naleznete v tématu [Postupy: vytváření typů pomocí Návrhář tříd](how-to-create-types.md) a [Postupy: zobrazení existujících typů](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Implementace rozhraní kreslením čáry dědičnosti

1. V diagramu tříd Zobrazte rozhraní a třídu, která bude implementovat rozhraní.

2. Nakreslete čáru dědičnosti z třídy a rozhraní.

     Zobrazí se Lupa připojená ke třídě a popisek s názvem rozhraní identifikuje vztah dědičnosti. Visual Studio generuje zástupné procedury pro všechny členy rozhraní.

Další informace naleznete v tématu [How to: Create dědičnost mezi typy](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Implementace rozhraní z okna Zobrazení tříd

1. V diagramu tříd Zobrazte třídu, kterou chcete implementovat rozhraní.

2. Otevřete **zobrazení tříd** a vyhledejte rozhraní.

    > [!TIP]
    > Pokud **zobrazení tříd** není otevřený, otevřete **zobrazení tříd** v nabídce **zobrazení** nebo stiskněte klávesovou **zkratku** + **SHIFT +** + **C**.

3. Přetáhněte uzel rozhraní do obrazce Třída v diagramu.

     Zobrazí se Lupa připojená ke třídě a popisek s názvem rozhraní identifikuje vztah dědičnosti. Visual Studio generuje zástupné procedury pro všechny členy rozhraní; v tomto okamžiku je rozhraní implementováno.

## <a name="see-also"></a>Viz také

- [Postupy: Vytváření typů pomocí Návrháře tříd](how-to-create-types.md)
- [Postupy: zobrazení existujících typů](how-to-view-existing-types.md)
- [Postupy: vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Refaktoring tříd a typů](refactoring-classes-and-types.md)
