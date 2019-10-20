---
title: 'Postupy: Vytvoření základního Phongova shaderu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5141df9f7504229733a269c2f7b0f94903064d8f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635945"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Postupy: Vytvoření základního Phongova shaderu

Tento článek ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit světelný shader, který implementuje model osvětlení Classic Phongova.

## <a name="the-phong-lighting-model"></a>Model osvětlení Phongova

Model osvětlení Phongova rozšiřuje model osvětlení Lambert, aby zahrnoval odlesky, což simuluje reflektující vlastnosti povrchu. Odlesková komponenta poskytuje další osvětlení ze stejných směrových zdrojů, které se používají v modelu osvětlení Lambert, ale jeho příspěvek na konečnou barvu se zpracovává jinak. Zrcadlové zvýrazňování má vliv na všechny povrchy scény odlišně na základě vztahu mezi směrem zobrazení, směrem zdrojů světla a orientací povrchu. Je to součin zrcadlové barvy, odlesku a orientace povrchu a barva, intenzita a směr zdrojů světla. Plochy, které odrážejí zdroj světla přímo v prohlížeči, obdrží maximální podíl na odlesku a povrchy, které odrážejí zdroj světla od tohoto prohlížeče, neobdrží žádný příspěvek. V rámci modelu osvětlení Phongova jsou kombinovány jedné nebo více odlesků komponent pro určení barvy a intenzity zrcadlového zvýraznění pro každý bod objektu a poté jsou přidány do výsledku modelu osvětlení Lambert, aby vznikla konečná barva pixelu. .

Další informace o modelu osvětlení Lambert naleznete v tématu [How to: Create a Basic Lambert Shader](../designers/how-to-create-a-basic-lambert-shader.md).

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Vytvořte Lambert Shader, jak je popsáno v tématu [How to: Create a Basic Lambert Shader](../designers/how-to-create-a-basic-lambert-shader.md).

2. Odpojte uzel **Lambert** z **posledního uzlu Color** . Zvolte terminál **RGB** uzlu **Lambert** a pak zvolte možnost **přerušení propojení**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu uzel **Přidat** . V **sadě nástrojů**v oblasti **matematika**vyberte možnost **Přidat** a přesunout ji na návrhovou plochu.

4. Přidejte do grafu **Odleskový** uzel. V **panelu nástrojů**v části **Nástroj**vyberte možnost **odlesky** a přesunout ji na návrhovou plochu.

5. Přidejte odleskový příspěvek. Přesuňte **výstupní** terminál **odlesku** uzlu do terminálu **X** uzlu **Přidat** a pak přesuňte **výstupní** terminál uzlu **Lambert** do terminálu **Y** uzlu **Přidat** . Tato připojení spojují celkové rozptýlené a odlesky barev v pixelech.

6. Připojí vypočítanou hodnotu barvy k konečné barvě. Přesuňte **výstupní** terminál uzlu **Přidat** do terminálu **RGB** **konečného uzlu barvy** .

   Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro model konvice.

> [!NOTE]
> Pro lepší demonstraci účinku shaderu na tomto obrázku je oranžová barva určena pomocí parametru **MaterialDiffuse** shaderu a v případě, že byl dokončen kovový vzhled, byl zadán pomocí **MaterialSpecular** a Parametry **MaterialSpecularPower** Informace o parametrech materiálu naleznete v části shadery Preview v [Návrháři shaderu](../designers/shader-designer.md).

![Graf shaderu a náhled jeho efektu](../designers/media/digit-lighting-graph.png)

Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o tom, jak náhled shaderů v Návrháři shaderu zobrazit, naleznete v části shadery Preview v [Návrháři shaderu](../designers/shader-designer.md) .

Následující ilustrace znázorňuje shader, který je popsaný v tomto dokumentu, aplikovaný na 3D model. Vlastnost **MaterialSpecular** je nastavená na (1,00, 0,50, 0,20, 0,00) a jeho vlastnost **MaterialSpecularPower** je nastavená na 16.

> [!NOTE]
> Vlastnost **MaterialSpecular** určuje zjevné dokončení materiálu povrchu. Vysoce lesklý povrch, jako je sklo nebo plast, má na sebe odlesky, které jsou jasným barevným nádechem bílé. Metalická plocha má za následek odlesky barev, která je blízko své barvy difúze. Povrch saténového dokončení má za následek zrcadlovou barvu, která je tmavě šedá.
>
> Vlastnost **MaterialSpecularPower** určuje, jak velký má odlesky. Vysokými odlesky jsou simulovat matné a lépe lokalizované světla. Velmi nízké zrcadlové a rozlesky simulují náročné a nepatrné zvýraznění, které může přesytost a skrytí barvy celého povrchu.

![Phongova osvětlení použité pro model](../designers/media/digit-lighting-model.png)

Další informace o tom, jak použít shader na 3D model, naleznete v tématu [How to: Apply shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: Vytvoření základního Lambertova shaderu](../designers/how-to-create-a-basic-lambert-shader.md)
- [Návrhář shaderů](../designers/shader-designer.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)