---
title: 'Postup: Vytvoření základního 3D modelu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce16e436172a7d369f2df8342f6b027b574056ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589523"
---
# <a name="how-to-create-a-basic-3d-model"></a>Postupy: Vytvoření základního 3D modelu

Tento článek ukazuje, jak pomocí Editoru modelů vytvořit základní 3D model. Zahrnuty jsou tyto činnosti:

- Přidání objektů do scény

- Výběr ploch a hran

- Překlad výběrů

- Použití nástrojů **Rozdělit plochu** a **Vysunutí plochy**

- Použití **příkazu Triangulate**

## <a name="create-a-basic-3d-model"></a>Vytvoření základního 3D modelu
Editor modelů můžete použít k vytváření a úpravám 3D modelů a scén pro vaši hru nebo aplikaci. Následující kroky ukazují, jak pomocí Editoru modelů vytvořit zjednodušený 3D model domu. Zjednodušený model lze použít jako záslužka pro prostředky konečné umění, které jsou stále vytvářeny, jako síť pro detekci kolizí nebo jako model s nízkými podrobnostmi, který se má použít, když je objekt, který představuje, příliš daleko, aby bylo možné využívat podrobnější vykreslování.

Po dokončení by měl model vypadat takto:

![Dokončený model zjednodušeného domu](../designers/media/gfx_model_demo_house_final.png)

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** **a panel nástrojů.**

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Vytvoření zjednodušeného 3D modelu domu

1. Vytvořte 3D model, se kterým chcete pracovat. Informace o tom, jak přidat model do projektu, naleznete v části Začínáme v [Editoru modelů](../designers/model-editor.md).

2. Přidejte do scény kostku. V okně **Panelu nástrojů** včásti **Obrazce**vyberte **Kostka** a pak ji přesuňte na návrhovou plochu.

3. Přepněte na výběr obličeje. Na panelu nástrojů Editor modelů zvolte **Vybrat plochu**.

4. Rozdělte horní část krychle. V režimu výběru plochy zvolte kostku jednou, abyste ji aktivovali pro výběr, a pak zvolte horní část krychle a vyberte horní plochu. Na panelu nástrojů Editor modelů zvolte **Rozdělit plochu**. Tím přidáte nové vrcholy do horní části krychle, které je rozdělí na čtyři oddíly stejné velikosti.

    ![Horní část krychle byla rozdělena](../designers/media/gfx_model_demo_house_subdiv.png)

5. Vysuněte dvě přilehlé strany krychle – například přední a pravé strany krychle. V režimu výběru obličeje zvolte kostku jednou, abyste ji aktivovali pro výběr, a pak zvolte jednu stranu krychle. Stiskněte a podržte klávesu **Ctrl,** zvolte jinou stranu krychle, která sousedí s vybranou stranou, a pak na panelu nástrojů Editor u modelu zvolte **Vysunutí plochy**.

    ![Strany krychle byly vysunuty](../designers/media/gfx_model_demo_house_extrude.png)

6. Rozšiřte jeden z vysunutí. Vyberte jednu z ploch, které jste právě vysunuli, a potom na panelu nástrojů Editor u modelu zvolte nástroj **přeložit** a přesuňte manipulátor překladu stejným směrem jako vysunutí.

    ![Jedna strana krychle byla dále vytlačována.](../designers/media/gfx_model_demo_house_extend.png)

7. Triangulujte model. Na panelu nástrojů Editor modelů zvolte **Upřesnit** > **triangulovat****nástroje** > .

8. Vytvořte střechu domu. Přepněte do režimu výběru hran, když na panelu nástrojů Editor modelů **zvolíte Vybrat hranu** a pak zvolte krychle, kterou chcete aktivovat. Při výběru okrajů, které jsou zde zobrazeny, stiskněte a podržte klávesu **Ctrl:**

    ![Hrany, které budou tvořit vrchol střechy](../designers/media/gfx_model_demo_house_edges.png)

    Když jsou vybrány hrany, na panelu nástrojů Editor modelů zvolte nástroj **přeložit** a pak přesuňte manipulátor překladu nahoru, abyste vytvořili střechu domu.

   Zjednodušený model domu je kompletní. Zde je konečný model znovu, s plochým stínováním použít:

   ![Dokončený model zjednodušeného domu](../designers/media/gfx_model_demo_house_final.png)

   Jako další krok můžete použít shader pro tento 3D model. Další informace naleznete v [tématu Jak: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také

- [Postup: Model3D terénu](../designers/how-to-model-3-d-terrain.md)
- [Editor modelů](../designers/model-editor.md)
- [Návrhář shaderů](../designers/shader-designer.md)
