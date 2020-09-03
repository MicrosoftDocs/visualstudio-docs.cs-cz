---
title: 'Postupy: implementace rozhraní (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b750830e8263d0016f52a71ad4eac8c6950eda8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651854"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Postupy: Implementace rozhraní (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrhář tříd můžete implementovat rozhraní v diagramu tříd tím, že ho propojíte s třídou, která poskytuje kód pro metody rozhraní. Návrhář tříd generuje implementaci rozhraní a zobrazuje vztah mezi rozhraním a třídou jako vztah dědičnosti. Rozhraní lze implementovat kreslením čáry dědičnosti mezi rozhraním a třídou nebo přetažením rozhraní z Zobrazení tříd.

> [!TIP]
> Rozhraní můžete vytvořit stejným způsobem jako jiné typy. Pokud rozhraní existuje, ale není zobrazeno v diagramu tříd, pak jej nejprve zobrazte. Další informace naleznete v tématu [Postupy: vytváření typů pomocí Návrhář tříd](../ide/how-to-create-types-by-using-class-designer.md) a [Postupy: zobrazení existujících typů (návrhář tříd)](../ide/how-to-view-existing-types-class-designer.md).

### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Implementace rozhraní kreslením čáry dědičnosti

1. V diagramu tříd Zobrazte rozhraní a třídu, která bude implementovat rozhraní.

2. Nakreslete čáru dědičnosti z třídy a rozhraní.

    Zobrazí se Lupa připojená ke třídě a popisek s názvem rozhraní identifikuje vztah dědičnosti. Visual Studio generuje zástupné procedury pro všechny členy rozhraní.

   Další informace naleznete v tématu [How to: Create dědičnost mezi typy (návrhář tříd)](../ide/how-to-create-inheritance-between-types-class-designer.md).

### <a name="to-implement-an-interface-from-the-class-view-window"></a>Implementace rozhraní z okna Zobrazení tříd

1. V diagramu tříd Zobrazte třídu, kterou chcete implementovat rozhraní.

2. Otevřete Zobrazení tříd a vyhledejte rozhraní.

    > [!TIP]
    > Pokud Zobrazení tříd není otevřený, otevřete Zobrazení tříd v nabídce **zobrazení** . Další informace o Zobrazení tříd naleznete v tématu [zobrazení tříd a jejich členů](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

3. Přetáhněte uzel rozhraní do obrazce Třída v diagramu.

     Zobrazí se Lupa připojená ke třídě a popisek s názvem rozhraní identifikuje vztah dědičnosti. Visual Studio generuje zástupné procedury pro všechny členy rozhraní; v tomto okamžiku je rozhraní implementováno.

## <a name="see-also"></a>Viz také
 [Postupy: vytváření typů pomocí Návrhář tříd](../ide/how-to-create-types-by-using-class-designer.md) [Postupy: zobrazení existujících typů (návrhář tříd)](../ide/how-to-view-existing-types-class-designer.md) [Postupy: vytvoření dědičnosti mezi typy (návrhář tříd)](../ide/how-to-create-inheritance-between-types-class-designer.md) [refaktoring tříd a typů (návrhář tříd)](../ide/refactoring-classes-and-types-class-designer.md)
