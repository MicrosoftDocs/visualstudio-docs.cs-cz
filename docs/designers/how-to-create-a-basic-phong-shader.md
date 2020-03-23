---
title: 'Postupy: Vytvoření základního Phongova shaderu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3059048f44524b9a838a8dfefc948ec4018dd05
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589484"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Postupy: Vytvoření základního Phongova shaderu

Tento článek ukazuje, jak používat Shader Designer a directed graph shader jazyk (DGSL) k vytvoření osvětlení shader, který implementuje klasický model osvětlení Phong.

## <a name="the-phong-lighting-model"></a>Model osvětlení Phong

Model osvětlení Phong rozšiřuje model osvětlení Lambert tak, aby zahrnoval zrcadlové zvýraznění, které simuluje reflexní vlastnosti povrchu. Zrcadlová komponenta poskytuje dodatečné osvětlení ze stejných směrových světelných zdrojů, které se používají v modelu osvětlení Lambert, ale jeho příspěvek k konečné barvě je zpracován odlišně. Zrcadlové zvýraznění ovlivňuje každý povrch ve scéně odlišně na základě vztahu mezi směrem pohledu, směrem světelných zdrojů a orientací povrchu. Je to produkt zrcadlové barvy, zrcadlové síly a orientace povrchu a barvy, intenzity a směru světelných zdrojů. Povrchy, které odrážejí světelný zdroj přímo u diváka, obdrží maximální odleskový příspěvek a povrchy, které odrážejí světelný zdroj mimo diváka, neobdrží žádný příspěvek. Pod modelem osvětlení Phong jsou jedna nebo více zrcadlových součástí kombinovány, aby se určila barva a intenzita zrcadlového zvýraznění pro každý bod na objektu a poté jsou přidány do výsledku modelu osvětlení Lambert, aby se vytvořila konečná barva pixelu .

Další informace o modelu osvětlení Lambert naleznete v [tématu How to: Create a basic Lambert shader](../designers/how-to-create-a-basic-lambert-shader.md).

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

1. Vytvořte Lambertův shader, jak je popsáno v [části Jak: Vytvoření základního shaderu Lambert](../designers/how-to-create-a-basic-lambert-shader.md).

2. Odpojte **uzel Lambert** od uzlu Konečné **barva.** Zvolte **terminál RGB** uzlu **Lambert** a pak zvolte **Přerušit odkazy**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte **Add** do grafu uzel Přidat. V **panelu nástrojů**v části **Matematika**vyberte **Přidat** a přesuňte ho na návrhovou plochu.

4. Přidejte do grafu **zrcadlový** uzel. V **panelu nástrojů**v části **Nástroj**vyberte **Odlesk a** přesuňte ho na návrhovou plochu.

5. Přidejte zrcadlový příspěvek. Přesuňte **výstupní** terminál **zrcadlového** uzlu do terminálu **X** uzlu **Add** a potom přesuňte **výstupní** terminál **uzlu Lambert** na svorku **Y** uzlu **Přidat.** Tato připojení kombinují celkové difúzní a zrcadlové barevné příspěvky pro obrazový bod.

6. Připojte vypočítanou hodnotu barvy ke konečné barvě. Přesuňte **výstupní** terminál uzlu **Přidat** uzel do terminálu **RGB** uzlu **Final Color.**

   Následující obrázek znázorňuje dokončený graf shaderu a náhled shaderu aplikovaného na model čajové konvice.

> [!NOTE]
> Chcete-li lépe demonstrovat účinek shaderu na tomto obrázku, byla určena oranžová barva pomocí parametru **MaterialDiffuse** shaderu a metalický povrch byl určen pomocí parametrů **MaterialSpecular** a **MaterialSpecularPower.** Informace o parametrech materiálu naleznete v části Náhled shaderů v [Návrháři shaderů](../designers/shader-designer.md).

![Shader graf a náhled jeho účinku](../designers/media/digit-lighting-graph.png)

Některé obrazce mohou některým shaderům poskytovat lepší náhledy. Další informace o tom, jak zobrazit náhled shaderů v návrháři shaderů, najdete v části Náhled shaderů v [návrháři shaderu.](../designers/shader-designer.md)

Následující obrázek znázorňuje shader popsaný v tomto dokumentu aplikovaný na 3D model. **Vlastnost MaterialSpecular** je nastavena na (1.00, 0.50, 0.20, 0.00) a její vlastnost **MaterialSpecularPower** je nastavena na 16.

> [!NOTE]
> Vlastnost **MaterialSpecular** určuje zdánlivou povrchovou úpravu povrchového materiálu. Vysoce lesklý povrch, jako je sklo nebo plast, má tendenci mít zrcadlovou barvu, která je jasným odstínem bílé. Kovový povrch má tendenci mít odleskovou barvu, která se blíží jeho rozptýlené barvě. Povrch se saténovou úpravou má tendenci mít odleskovou barvu, která je tmavým odstínem šedé.
>
> Vlastnost **MaterialSpecularPower** určuje, jak intenzivní jsou odlesky. Vysoké zrcadlové síly simulují tupější, více lokalizované světla. Velmi nízké odleskové síly simulují intenzivní, zametání zdůrazňuje, že může přesytit a zakrýt barvu celého povrchu.

![Phong osvětlení aplikované na model](../designers/media/digit-lighting-model.png)

Další informace o použití shaderu na 3D model najdete v tématu [Postup: Aplikování shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: Vytvoření základního Lambertova shaderu](../designers/how-to-create-a-basic-lambert-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly Návrhářshaderu](../designers/shader-designer-nodes.md)
