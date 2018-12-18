---
title: 'Postupy: Vytvoření základního Lambertova shaderu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d71a59e0173be60779675f838fad20943eabc85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913251"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Postupy: vytvoření základního Lambertova shaderu

Tento článek popisuje způsob použití návrháře shaderu a orientovaného grafu shaderu jazyka (DGSL) k vytvoření, který implementuje klasického modelu osvětlení Lambert osvětlení shaderu.

## <a name="the-lambert-lighting-model"></a>Lambertova modelu osvětlení

Model osvětlení Lambert zahrnuje okolí a směrové světlo na odstín objekty ve 3D scéně. Ambientní komponenty poskytují základní úroveň osvětlení ve 3D scéně. Směrové komponenty nabízejí další osvětlení z směrové zdroje (vzdálené) světla. Ambientní osvětlení má vliv na všechny plochy ve scéně stejně, bez ohledu na jejich orientace. Pro daný plochu je produkt okolní barvy na povrchu a barvy a intenzitu zrcadlových osvětlením okolí ve scéně. Směrové světlo ovlivňuje všechny oblasti ve scéně odlišně, na základě orientace povrchu s ohledem na směru světla. Je produkt barvy rozptýlení a orientaci ovládacího prvku na plochu a barvu, intenzity a směr světla zdrojů. Zařízení Surface směřujících přímo ke zdroji světla získat maximální příspěvek a povrchy směřujících přímo okamžitě obdržet žádná příspěvek. V části Lambertova modelu osvětlení okolí komponenty a jednu nebo více komponent směrové kombinovat určit příspěvek celkový rozptýlení barvy pro každý bod na objekt.

Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.

1. Vytvořte shader DGSL se kterým chcete pracovat. Informace o tom, jak přidat do projektu DGSL shader naleznete v části Začínáme v [návrháře shaderu](../designers/shader-designer.md).

2. Odpojte **barva bodu** uzlu z **konečnou barvu** uzlu. Zvolte **RGB** z terminálu **barva bodu** uzel a klikněte na tlačítko **přerušit odkazy**. Nechte **alfa** terminálu připojen.

3. Přidat **Lambertova** uzel do grafu. V **nástrojů**v části **nástroj**vyberte **Lambertova** a přesuňte jej na návrhovou plochu. Uzel lambertova vypočítá podíl celkové rozptýlení barvy pixelu na základě parametrů osvětlením okolí a difúzním.

4. Připojení **barva bodu** uzlu **Lambertova** uzlu. V **vyberte** režimu, přesunout **RGB** z terminálu **barva bodu** uzlu **rozptýlit barvu** z terminálu **Lambertova**  uzlu. Toto připojení obsahuje uzel lambertova s interpolovanými barvy rozptýlení pixelu.

5. Hodnota počítaného barvy se připojte k konečnou barvu. Přesunout **výstup** z terminálu **Lambertova** uzlu **RGB** z terminálu **konečnou barvu** uzlu.

   Následující obrázek znázorňuje dokončené shader graf a náhled shaderu použité pro model čajové konvice.

> [!NOTE]
> K předvedení lépe efekt shaderu na tomto obrázku, byl zadán oranžové barvy s použitím **MaterialDiffuse** parametr shaderu. Hry nebo aplikace můžete použít tento parametr slouží k poskytování hodnotu barvy jedinečný pro každý objekt. Informace o parametrech materiálu, naleznete v části Náhled shadery v [návrháře shaderu](../designers/shader-designer.md).

 ![Graf shaderu a jeho účinkem ve verzi preview.](../designers/media/digit-lambert-effect-graph.png)

 Určité tvary můžou poskytovat lepší verze Preview pro některé shadery. Další informace o tom, jak shadery v Návrháři shaderu ve verzi preview, najdete v části Náhled shadery v [návrháře shaderu](../designers/shader-designer.md).

 Následující obrázek znázorňuje shaderu, který je popsaný v tomto dokumentu použité pro 3D model.

 ![Osvětlení Lambert k modelu.](../designers/media/digit-lambert-effect-result.png)

 Další informace o tom, jak použití shaderu na 3D model, najdete v části [postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také:

- [Postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Exportování shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: Vytvoření základního Phongova shaderu](../designers/how-to-create-a-basic-phong-shader.md)
- [Návrhář shaderů](../designers/shader-designer.md)
- [Uzly návrháře shaderů](../designers/shader-designer-nodes.md)