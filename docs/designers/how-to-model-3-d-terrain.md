---
title: 'Postup: Model 3D terénu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a863834790683b229c17ad55b9930a2b382c027b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589419"
---
# <a name="how-to-model-3d-terrain"></a>Postup: Model3D terénu

Tento článek ukazuje, jak pomocí Editoru modelů vytvořit 3D model terénu.

## <a name="create-a-3d-terrain-model"></a>Vytvoření 3D modelu terénu

3D terén můžete vytvořit rozdělením roviny tak, aby vznikly další plochy, a manipulací s jejich vrcholy a vytvořením zajímavých prvků terénu.

Po dokončení by měl model vypadat takto:

![3&#45;D scéna, která zobrazuje model terénu](../designers/media/digit-terrain-model.png)

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** **a panel nástrojů.**

1. Vytvořte 3D model, se kterým chcete pracovat. Informace o tom, jak přidat model do projektu, naleznete v části Začínáme v [Editoru modelů](../designers/model-editor.md).

2. Přidejte na scénu letadlo. V **panelu nástrojů**v části **Tvary**vyberte **Rovina** a přesuňte ji na návrhovou plochu.

    > [!TIP]
    > Chcete-li usnadnit práci s rovinným objektem, můžete jej zarámovat v návrhové ploše. V režimu **Výběr** vyberte rovinný objekt a pak na panelu nástrojů Editor modelů zvolte tlačítko **Objekt rámce.**

3. Vstupte do režimu výběru plochy. Na panelu nástrojů Editor modelů zvolte **Vybrat plochu**.

4. Rozdělte letadlo. V režimu výběru plochy zvolte rovinu jednou, abyste ji aktivovali pro výběr, a pak ji zvolte znovu, abyste vybrali její jedinou plochu. Na panelu nástrojů Editor modelů zvolte **Rozdělit plochu**. Tím přidáte nové vrcholy do roviny, které ji rozdělí na čtyři oddíly stejné velikosti.

5. Vytvořte další pododdíly. Pokud jsou nové plochy stále vybrané, zvolte **Rozdělit plochu** ještě dvakrát. Tím se vytvoří celkem 64 ploch. Vytvořením více subdivisions, můžete dát terén ještě více detailů.

6. Zadejte režim výběru bodů. Na panelu nástrojů Editor modelů zvolte **Vybrat bod**.

7. Upravte bod a vytvořte prvek terénu. V režimu výběru bodů vyberte jeden z bodů a potom na panelu nástrojů Editor modelů zvolte nástroj **překlad.** Na návrhové ploše se zobrazí rámeček, který představuje bod. Pomocí zelené šipky přesuňte rámeček a tím upravte výšku bodu. Tento krok opakujte pro různé body a vytvořte zajímavé prvky terénu.

    > [!TIP]
    > Můžete vybrat několik bodů najednou a upravit je jednotným způsobem.

Model terénu je kompletní. Zde je konečný model znovu, s Phong stínování použít:

![3&#45;D scéna, která zobrazuje model terénu](../designers/media/digit-terrain-model.png)

Tento model terénu můžete použít k předvedení efektu shaderu přechodu popsaného v [části Postup: Vytvoření shaderu přechodu založeného na geometrii](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Viz také

- [Editor modelů](../designers/model-editor.md)
