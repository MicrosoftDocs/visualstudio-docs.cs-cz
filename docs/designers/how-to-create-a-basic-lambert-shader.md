---
title: 'Postupy: Vytvoření základního Lambertova shaderu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78bc6e1b384f339d80e09fec81d42c1ab8ed103
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589497"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Postupy: Vytvoření základního Lambertova shaderu

Tento článek ukazuje, jak pomocí Návrhář shaderu a směrovaný graf shader jazyk (DGSL) k vytvoření osvětlení shader, který implementuje klasický model osvětlení Lambert.

## <a name="the-lambert-lighting-model"></a>Model osvětlení Lambert

Model osvětlení Lambert zahrnuje okolní a směrové osvětlení pro stínování objektů ve 3D scéně. Okolní komponenty poskytují základní úroveň osvětlení ve 3D scéně. Směrové komponenty poskytují dodatečné osvětlení ze směrových (vzdálených) světelných zdrojů. Okolní osvětlení ovlivňuje všechny povrchy ve scéně stejně, bez ohledu na jejich orientaci. Pro daný povrch je to produkt okolní barvy povrchu a barvy a intenzity okolního osvětlení ve scéně. Směrové osvětlení ovlivňuje každý povrch ve scéně odlišně, na základě orientace povrchu vzhledem ke směru světelného zdroje. Je to produkt rozptýlené barvy a orientace povrchu a barvy, intenzity a směru světelných zdrojů. Povrchy, které směřují přímo ke zdroji světla, obdrží maximální příspěvek a povrchy, které směřují přímo pryč, neobdrží žádný příspěvek. V rámci modelu osvětlení Lambert jsou okolní součásti a jedna nebo více směrových součástí kombinovány, aby se určil celkový příspěvek rozptýlené barvy pro každý bod na objektu.

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat shader SChL do projektu, naleznete v části Začínáme v [návrháři shaderu](../designers/shader-designer.md).

2. Odpojte uzel **Barva bodu** od uzlu **Konečné barva.** Zvolte **terminál RGB** uzlu **Barva bodu** a pak zvolte Přerušit **odkazy**. Nechte terminál **Alfa** připojený.

3. Přidejte do grafu uzel **Lambert.** V **panelu nástrojů**vyberte v části **Nástroj** **možnost Lambert** a přesuňte jej na návrhovou plochu. Uzel lambert vypočítá celkový příspěvek difuzní barvy obrazového bodu na základě parametrů okolního a rozptýleného osvětlení.

4. Připojte uzel **Barva bodu** k **uzlu Lambert.** V režimu **Select** přesuňte terminál **RGB** uzlu **Barva bodu** do terminálu **Difuzní barvy** uzlu **Lambert.** Toto připojení poskytuje lambert uzlu interpolovolupou rozptýlenou barvu pixelu.

5. Připojte vypočítanou hodnotu barvy ke konečné barvě. Přesuňte **výstupní** terminál uzlu **Lambert** do **terminálu RGB** uzlu **Final Color.**

   Následující obrázek znázorňuje dokončený graf shaderu a náhled shaderu aplikovaného na model čajové konvice.

> [!NOTE]
> Chcete-li lépe demonstrovat účinek shaderu na tomto obrázku, byla určena oranžová barva pomocí parametru **MaterialDiffuse** shaderu. Hra nebo aplikace může tento parametr použít k zadání jedinečné hodnoty barvy pro každý objekt. Informace o parametrech materiálu naleznete v části Náhled shaderů v [Návrháři shaderů](../designers/shader-designer.md).

![Shader graf a náhled jeho efekt.](../designers/media/digit-lambert-effect-graph.png)

Některé obrazce mohou některým shaderům poskytovat lepší náhledy. Další informace o tom, jak zobrazit náhled shaderů v návrháři shaderů, najdete v části Náhledy shadrů v [návrháři shaderu](../designers/shader-designer.md).

Následující obrázek znázorňuje shader popsaný v tomto dokumentu aplikovaný na 3D model.

![Lambert osvětlení aplikován na model.](../designers/media/digit-lambert-effect-result.png)

Další informace o použití shaderu na 3D model najdete v tématu [Postup: Aplikování shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také

- [Postup: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postup: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postup: Vytvoření základního shaderu Phong](../designers/how-to-create-a-basic-phong-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)
