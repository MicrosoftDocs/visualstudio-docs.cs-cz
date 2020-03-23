---
title: 'Postupy: Vytvoření přechodu shaderu založeného na geometrii'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96326910a04294e30c410cc96bf9c600bfb3f17c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589448"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Postupy: Vytvoření přechodu shaderu založeného na geometrii

Tento článek ukazuje, jak pomocí Návrháře shaderů a jazyka shaderu s řízeným grafem vytvořit shader přechodu založený na geometrii. Tento shader změní konstantní hodnotu barvy RGB podle výšky každého bodu objektu v prostoru světa.

## <a name="create-a-geometry-based-gradient-shader"></a>Vytvoření přechodu shaderu založeného na geometrii

Shader založený na geometrii můžete implementovat začleněním polohy obrazového bodu do shaderu. V jazycích stínování obsahuje pixel více informací než jen jeho barvu a umístění na 2D obrazovce. Pixel – v některých systémech označovaný jako *fragment* – je kolekce hodnot, které popisují povrch, který odpovídá obrazovému bodu. Shader, který je popsán v tomto dokumentu využívá výšku každého obrazového bodu 3D objektu ve světovém prostoru k ovlivnění konečné výstupní barvy fragmentu.

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat shader SChL do projektu, naleznete v části Začínáme v [návrháři shaderu](../designers/shader-designer.md).

2. Odpojte uzel **Barva bodu** od uzlu **Konečné barva.** Zvolte **terminál RGB** uzlu **Barva bodu** a pak zvolte Přerušit **odkazy**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu uzel **Násobení.** V **panelu nástrojů**včásti **Matematika**vyberte **Násobit** a přesuňte ji na návrhovou plochu.

4. Přidejte do grafu uzel **Vektor masky.** V **panelu nástrojů**vyberte v části **Nástroj** **vektor masky** a přesuňte ho na návrhovou plochu.

5. Určete hodnoty masky pro uzel **Vektor masky.** V režimu **Výběr** vyberte uzel **Vektor masky** a potom v okně **Vlastnosti** nastavte vlastnost **Zelená / Y** na **hodnotu True**a potom nastavte vlastnosti Červená / **X**, Modrá **/ Z** a Alfa / **W** na **False**. V tomto příkladu **red / X**, Green / **Y**a Blue **/ Z** vlastnosti odpovídají x, y a z komponenty uzlu **Světová pozice** a Alfa / **W** je nevyužitý. Protože pouze **Zelená / Y** je nastavena na **True**, zůstane pouze y komponenta vstupního vektoru po maskované.

6. Přidejte do grafu uzel **Světová pozice.** V **panelu nástrojů**v části **Konstanty**vyberte **Světová pozice** a přesuňte ji na návrhovou plochu.

7. Maskovat světovou vesmírnou pozici fragmentu. V režimu **Select** přesuňte **výstupní** svorku uzlu **Světová pozice** na **vektorovou** svorku uzlu **Vektormaska.** Toto připojení maskuje pozici fragmentu ignorovat komponenty x a z.

8. Vynásobte barevnou konstantu RGB maskovanou světovou pozicí. Přesuňte terminál **RGB** uzlu **Barva bodu** do terminálu **Y** uzlu **Násobení** a potom přesuňte **výstupní** terminál uzlu **Vektor masky** do terminálu **X** uzlu **Násobení.** Toto připojení změní barvu podle výšky obrazového bodu v prostoru světa.

9. Připojte hodnotu barvy s měřítkem ke konečné barvě. Přesuňte **výstupní** terminál uzlu **Násobit** do terminálu **RGB** uzlu **Konečné barvy.**

Následující obrázek znázorňuje dokončený graf shaderu a náhled shaderu aplikovaného na kouli.

> [!NOTE]
> Na tomto obrázku je určena oranžová barva, aby se lépe demonstroval účinek shaderu, ale protože obrazec náhledu nemá žádnou pozici ve světovém prostoru, nelze shader plně zobrazit v návrháři shaderu. Shader musí být zobrazen v reálném prostředí, aby se prokázal plný efekt.

![Shader graf a náhled jeho účinku](../designers/media/digit-gradient-effect-graph.png)

Některé obrazce mohou některým shaderům poskytovat lepší náhledy. Informace o tom, jak zobrazit náhled shaderů v návrháři shaderů, naleznete v **tématu Náhled shaderů** v [návrháři shaderu](../designers/shader-designer.md).

Následující obrázek znázorňuje shader popsaný v tomto dokumentu aplikovaný na 3D scénu, která je znázorněna v [článku Jak: Modelovat 3D terén](../designers/how-to-model-3-d-terrain.md). Intenzita barvy se zvyšuje s výškou bodu na světě.

![Efekt přechodu aplikovaný na model terénu 3&#45;D](../designers/media/digit-gradient-effect-result.png)

Další informace o použití shaderu na 3D model najdete v tématu [Postup: Aplikování shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postup: Model3D terénu](../designers/how-to-model-3-d-terrain.md)
- [Postupy: Vytvoření shaderu textury stupňů šedé](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly Návrhářshaderu](../designers/shader-designer-nodes.md)
