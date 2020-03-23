---
title: 'Postupy: Vytvoření shaderu textury stupňů šedé'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b74e956a74ff4c04dbc5a1c990fab708937d8f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112627"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Postupy: Vytvoření shaderu textury stupňů šedé

Tento článek ukazuje, jak pomocí Návrhář shaderu a směrovaný graf shader jazyk (DGSL) k vytvoření šedi textury shader. Tento shader upraví hodnotu barvy RGB vzorku textury a pak ji použije společně s nezměněnou hodnotou alfa k nastavení konečné barvy.

## <a name="create-a-grayscale-texture-shader"></a>Vytvoření shaderu textury stupňů šedé

Shader textury ve stupních šedi můžete implementovat úpravou hodnoty barvy vzorku textury před zápisem do konečné výstupní barvy.

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

1. Vytvořte základní shader textury, jak je popsáno v [části Postup: Vytvoření základního shaderu textury](../designers/how-to-create-a-basic-texture-shader.md).

2. Odpojte **terminál RGB** uzlu **Ukázkový textury** od terminálu **RGB** uzlu **Final Color.** V režimu **výběru** zvolte **terminál RGB** uzlu **Ukázkový textura** a pak zvolte **Přerušit odkazy**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu uzel **Odsycení.** V **panelu nástrojů**včásti **Filtry**vyberte **Odsycení** a přesuňte ho na návrhovou plochu.

4. Vypočítejte hodnotu stupně šedi pomocí uzlu **Odsycení.** V režimu **Select** přesuňte terminál **RGB** uzlu **Vzorkování textury** do terminálu **RGB** uzlu **Odsycení.**

    > [!NOTE]
    > Ve výchozím nastavení uzel **Odsytování** zcela odsytí vstupní barvu a používá standardní hmotnosti jasu pro převod stupňů šedi. Způsob chování uzlu **Odsycení** můžete změnit změnou hodnoty vlastnosti **Světlost** nebo pouze částečným desatucí vstupní barvy. Chcete-li částečně odbarvit vstupní barvu, zadejte skalární hodnotu v rozsahu [0,1) terminálu **Procento** uzlu **Odsycení.**

5. Připojte hodnotu barvy ve stupních šedi ke konečné barvě. Přesuňte **výstupní** terminál uzlu **Odsycení** do **terminálu RGB** uzlu **Final Color.**

Následující obrázek znázorňuje dokončený graf shaderu a náhled shaderu aplikovaného na krychli.

> [!NOTE]
> Na tomto obrázku se jako obrazec náhledu použije rovina a byla zadána textura, která lépe demonstruje účinek shaderu.

![Shader graf a náhled jeho účinku](../designers/media/digit-grayscale-effect.png)

Některé obrazce mohou některým shaderům poskytovat lepší náhledy. Další informace o náhledu shaderů v návrháři shaderu naleznete v [tématu Shader Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Editor obrázků](../designers/image-editor.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly Návrhářshaderu](../designers/shader-designer-nodes.md)
