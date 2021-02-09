---
title: 'Postupy: Vytvoření přechodu shaderu založeného na geometrii'
description: Naučte se používat Designer shaderu a jazyk orientovaného grafu shaderu k vytvoření barevného shaderu založeného na geometrii, který škáluje konstantní hodnotu barvy RGB.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f3814eabb38e205acedd6bd2b00fd98901568c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931029"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Postupy: Vytvoření přechodu shaderu založeného na geometrii

Tento článek ukazuje, jak pomocí Návrháře shaderu a jazyka orientovaného shaderu grafu vytvořit přechodový shader založený na geometrii. Tento shader škáluje konstantní hodnotu barvy RGB výškou každého místa objektu v celém světě.

## <a name="create-a-geometry-based-gradient-shader"></a>Vytvoření přechodu shaderu založeného na geometrii

Shader založený na geometrii můžete implementovat zahrnutím pozice obrazového bodu do shaderu. V jazycích stínování obsahuje pixel více informací, než je pouze jeho barva a umístění na 2D obrazovce. Pixel (označovaný jako *fragment* v některých systémech) je kolekce hodnot, které popisují plochu, která odpovídá obrazovému bodu. Shader, který je popsaný v tomto dokumentu, používá výšku každého pixelu 3D objektu v prostoru světa, aby ovlivnil konečnou výstupní barvu fragmentu.

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Vytvořte DGSL shader, který bude fungovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

2. Odpojí uzel **Barva bodu** od **finálního uzlu barvy** . Zvolte terminál **RGB** pro uzel **Barva bodu** a pak zvolte možnost **přerušení propojení**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu uzel **násobení** . V **sadě nástrojů** v části **Math** vyberte možnost **násobit** a přesunout na návrhovou plochu.

4. Přidejte do grafu **vektorový uzel masky** . V **panelu nástrojů** v části **Nástroj** vyberte možnost **Vektor masky** a přesuňte ji na návrhovou plochu.

5. Zadejte hodnoty masky pro uzel **Vector masky** . V **režimu výběru** vyberte uzel **Vektor masky** a potom v okně **vlastnosti** nastavte vlastnost **zelená/Y** na **hodnotu true** a nastavte vlastnosti **Red/X**, **Blue/Z** a **alfa/W** na **hodnotu false**. V tomto příkladu vlastnosti **Red/X**, **zelená/Y** a **Blue/Z** odpovídají komponentám X, Y a z uzlu **pozice světa** a **alfa/W** se nepoužívá. Protože pouze **zelená/Y** je nastavena na **hodnotu true**, po maskování zůstane pouze komponenta Y vstupního vektoru.

6. Přidejte do grafu uzel **pozice na světě** . V **sadě nástrojů** v části **konstanty** vyberte **umístění světa** a přesuňte jej na plochu návrhu.

7. Maskovat pozici fragmentu místa na světě. V režimu **výběru** přesuňte **výstupní** terminál uzlu **pozice světa** do **vektorového** terminálu pro uzel **Mask Vector** . Toto připojení maskuje umístění fragmentu pro ignorování komponent x a z.

8. Vynásobit barevnou konstantu RGB maskou pozice WWPN (World World Space). Přesuňte terminál **RGB** uzlu **barevného bodu** do terminálu **Y** uzlu **násobek** a poté přesuňte **výstupní** terminál uzlu **Mask Vector** do terminálu **X** v uzlu **násobení** . Toto připojení škáluje hodnotu barvy podle výšky pixelu v prostoru světa.

9. Připojte hodnotu barvy škálované do konečné barvy. Přesuňte **výstupní** terminál uzlu **násobení** do terminálu **RGB** **konečného uzlu barvy** .

Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro objekt sphere.

> [!NOTE]
> Na tomto obrázku je určena oranžová barva, aby lépe ukázala účinek shaderu, ale vzhledem k tomu, že obrazec náhledu nemá žádnou polohu v celém prostoru, shader nemůže být plně zobrazen v Návrháři shaderu. Aby bylo možné předvést úplný efekt, musí být shader zobrazen v reálné scéně.

![Graf shaderu a náhled jeho efektu](../designers/media/digit-gradient-effect-graph.png)

Některé tvary mohou pro některé shadery poskytnout lepší náhled. Informace o tom, jak zobrazit náhled shaderů v Návrháři shaderu, naleznete v tématu Náhled **shaderů** v [Návrháři shaderu](../designers/shader-designer.md).

Následující ilustrace znázorňuje shader, který je popsán v tomto dokumentu, aplikovaný na 3D scénu, která je znázorněna v tématu [How to: model 3D terénu](../designers/how-to-model-3-d-terrain.md). Intenzita barvy se zvyšuje se výškou bodu na světě.

![Efekt přechodu aplikovaný na 3&#45;D model terénu](../designers/media/digit-gradient-effect-result.png)

Další informace o tom, jak použít shader na 3D model, naleznete v tématu [How to: Apply shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: modelování 3D terénu](../designers/how-to-model-3-d-terrain.md)
- [Postupy: Vytvoření shaderu textury stupňů šedé](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)
