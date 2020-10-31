---
title: 'Postupy: Vytvoření základního Lambertova shaderu'
description: Naučte se používat Designer shaderu a jazyk orientovaného grafu shaderu k vytvoření světelného shaderu, který implementuje klasický model osvětlení Lambert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1677de15006dcf3bbe2f7a6b925be247518f752
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134521"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Postupy: Vytvoření základního Lambertova shaderu

Tento článek ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit světelný shader, který implementuje model osvětlení Classic Lambert.

## <a name="the-lambert-lighting-model"></a>Model osvětlení Lambert

Model osvětlení Lambert zahrnuje okolí a směrové osvětlení k vystínování objektů ve 3D scéně. Okolní komponenty poskytují základní úroveň osvětlení 3D scény. Směrové komponenty poskytují další osvětlení ze směrných (nečinných) světelných zdrojů. Okolní osvětlení ovlivňuje všechny povrchy scény stejně, bez ohledu na jejich orientaci. Pro danou plochu je to součin okolní barvy povrchu a barvy a intenzita okolního osvětlení na scéně. Směrové světlo má vliv na všechny povrchy scény odlišně na základě orientace povrchu v závislosti na směru zdroje světla. Jde o součin barev a orientace povrchu a barvu, intenzitu a směr zdrojů světla. Plochy, které čelí přímo ke zdroji světla, obdrží maximální podíl a plochy, které čelí přímo, nezískají žádný příspěvek. V rámci modelu osvětlení Lambert se kombinovaná komponenta a jedna nebo více směrových komponent spojí s cílem určit celkový podíl barev difúzí pro každý bod objektu.

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Vytvořte DGSL shader, který bude fungovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

2. Odpojí uzel **Barva bodu** od **finálního uzlu barvy** . Zvolte terminál **RGB** pro uzel **Barva bodu** a pak zvolte možnost **přerušení propojení** . Nechejte terminál **Alpha** připojený.

3. Přidejte uzel **Lambert** do grafu. V **panelu nástrojů** vyberte v části **Nástroj** možnost **Lambert** a přesuňte ji na návrhovou plochu. Uzel Lambert vypočítá celkový podíl barvy difúze v pixelech na základě parametrů okolí a rozptýlené osvětlení.

4. Připojte uzel **Barva bodu** k **Lambert** uzlu. V režimu **výběru** přesuňte terminál **RGB** uzlu **barvy bodu** do terminálu **rozdifúze barvy** uzlu **Lambert** . Toto připojení poskytuje uzel Lambert s interpolací barvou difúze na pixelu.

5. Připojí vypočítanou hodnotu barvy k konečné barvě. Přesuňte **výstupní** terminál uzlu **Lambert** do terminálu **RGB** **konečného uzlu barvy** .

   Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro model konvice.

> [!NOTE]
> Pro lepší ukázku účinku shaderu na tomto obrázku je oranžová barva určena pomocí parametru **MaterialDiffuse** shaderu. Hra nebo aplikace může pomocí tohoto parametru zadat jedinečnou hodnotu barvy pro každý objekt. Informace o parametrech materiálu naleznete v části shadery Preview v [Návrháři shaderu](../designers/shader-designer.md).

![Graf shaderu a náhled jeho efektu.](../designers/media/digit-lambert-effect-graph.png)

Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o tom, jak zobrazit náhled shaderů v Návrháři shaderu, naleznete v části shadery Preview v [Návrháři shaderu](../designers/shader-designer.md).

Následující ilustrace znázorňuje shader, který je popsaný v tomto dokumentu, aplikovaný na 3D model.

![Lambert osvětlení použité pro model.](../designers/media/digit-lambert-effect-result.png)

Další informace o tom, jak použít shader na 3D model, naleznete v tématu [How to: Apply shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také

- [Postupy: použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: Vytvoření základního Phongova shaderu](../designers/how-to-create-a-basic-phong-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)
