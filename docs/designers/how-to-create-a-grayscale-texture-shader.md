---
title: 'Postupy: Vytvoření shaderu textury stupňů šedé'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a311456fd3f8eab12c24e26c32349f208e0a723
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769063"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Postupy: Vytvoření shaderu textury stupňů šedé

Tento článek ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit shader textury ve stupních šedi. Tento shader upraví hodnotu barvy RGB ukázky textury a pak ji použije společně s neupravenou hodnotou Alpha k nastavení konečné barvy.

## <a name="create-a-grayscale-texture-shader"></a>Vytvoření shaderu textury stupňů šedé

Můžete implementovat shader textury ve stupních šedi úpravou hodnoty barvy vzorku textury před jeho zápisem do konečné výstupní barvy.

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Vytvořte základní shader textury, jak je popsáno v tématu [How to: Create a Basic textur shader](../designers/how-to-create-a-basic-texture-shader.md).

2. Odpojte terminál **RGB** uzlu **ukázkové textury** z terminálu **RGB** konečného uzlu **barvy** . V režimu **výběru** zvolte terminál **RGB** pro uzel **Ukázka textury** a pak zvolte možnost **přerušení propojení**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu **rozsytost** uzlu. V **sadě nástrojů**v části **filtry**vyberte možnost **desytost** a přesuňte ji na návrhovou plochu.

4. Vypočítá hodnotu ve stupních šedi pomocí uzlu **desytost** . V režimu **výběru** přesuňte terminál **RGB** uzlu **vzorku textury** do terminálu **RGB** uzlu **desytost** .

    > [!NOTE]
    > Ve výchozím nastavení rozodstínů šedi **uzel plně rozsytost vstupní** barvy a používá ke konverzi standardní tloušťky světelnosti. Můžete změnit způsob, jakým se rozumělý **uzel chová** , změnou hodnoty vlastnosti **světelnosti** nebo pouze částečně rozuměle vstupní barvou. Chcete-li částečně desytost vstupní barvy, zadejte skalární hodnotu v rozsahu [0, 1) až k **procentu** terminálu **rozsyceného** uzlu.

5. Propojte hodnotu barvy ve stupních šedi s konečnou barvou. Přesuňte **výstupní** terminál uzlu **desytost** do terminálu **RGB** **konečného uzlu barvy** .

Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro datovou krychli.

> [!NOTE]
> Na tomto obrázku je jako obrazec náhledu použita rovina a je určena textura, aby lépe ukázala účinek shaderu.

![Graf shaderu a náhled jeho efektu](../designers/media/digit-grayscale-effect.png)

Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o náhledu shaderů v Návrháři shaderu naleznete v tématu [Shader Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Editor obrázků](../designers/image-editor.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)
