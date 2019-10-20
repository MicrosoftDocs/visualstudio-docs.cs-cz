---
title: 'Postupy: Vytvoření základního 3D modelu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604847e5f9bf6111d548b9d3bbdc0a0e10301784
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72636737"
---
# <a name="how-to-create-a-basic-3d-model"></a>Postupy: Vytvoření základní 3D model

Tento článek ukazuje, jak pomocí editoru modelů vytvořit základní 3D model. Jsou pokryty následující aktivity:

- Přidání objektů do scény

- Výběr plošek a hran

- Překládání výběrů

- Použití **rozdělte obličej** a **přetlačení obličeje** nástrojů

- Použití příkazu **triangulovat**

## <a name="create-a-basic-3d-model"></a>Vytvoření základního 3D modelu
Editor modelů můžete použít k vytvoření a úpravě 3D modelů a scén pro vaši hru nebo aplikaci. Následující kroky ukazují, jak pomocí editoru modelů vytvořit zjednodušenou 3D model domu. Zjednodušený model lze použít jako samostatný pro finální materiály, které jsou stále vytvářeny, jako síť pro detekci kolizí nebo jako model s nízkými podrobnostmi, který má být použit, pokud je objekt, který představuje příliš daleko, nevýhodou podrobnějšího vykreslování.

Až budete hotovi, model by měl vypadat takto:

![Dokončený model zjednodušené domu](../designers/media/gfx_model_demo_house_final.png)

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Vytvoření zjednodušené 3D model domu

1. Vytvořte 3D model, se kterou chcete pracovat. Informace o tom, jak přidat model do projektu, naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).

2. Přidejte do scény datovou krychli. V okně **sady nástrojů** v části **tvary**vyberte **krychle** a potom ji přesuňte na návrhovou plochu.

3. Přepněte na výběr obličeje. Na panelu nástrojů editoru modelů zvolte **možnost vybrat obličej**.

4. Rozdělte horní část datové krychle. V režimu výběru plochy Zvolte datovou krychli jednou, abyste ji aktivovali pro výběr, a pak zvolte horní stranu datové krychle a vyberte horní plochu. Na panelu nástrojů editoru modelů vyberte **rozdělit plochu**. Tím se do horní části datové krychle přidá nové vrcholy, které se rozdělí do čtyř oddílů se stejnou velikostí.

    ![Horní část datové krychle byla rozdělena](../designers/media/gfx_model_demo_house_subdiv.png)

5. Vytlačení dvou sousedních stran krychle, například přední a pravé strany datové krychle. V režimu výběru plochy vyberte datovou krychli jednou, abyste ji aktivovali pro výběr, a pak zvolte jednu stranu datové krychle. Stiskněte a podržte klávesu **CTRL** , zvolte jinou stranu datové krychle, která sousedí se stranou, kterou jste vybrali jako první, a pak na panelu nástrojů editoru modelů zvolte možnost **tlačení obličeje**.

    ![Strany krychle byly vytlačeny.](../designers/media/gfx_model_demo_house_extrude.png)

6. Rozšíří jeden z vytlačení. Zvolte jednu z ploch, kterou jste právě vytlačeni, a potom na panelu nástrojů editoru modelů **Zvolte nástroj pro překlad a** přesuňte manipulátor překladu ve stejném směru jako vytlačení.

    ![Jedna strana datové krychle byla dále vytlačena.](../designers/media/gfx_model_demo_house_extend.png)

7. Triangulovat model. Na panelu nástrojů editoru modelů vyberte možnost **rozšířené**  > **nástroje**  > **triangulovat**.

8. Vytvořte střechu domu. Přepněte do režimu výběru okrajů tak, že na panelu nástrojů editoru modelů kliknete na **Vybrat Edge** a potom ho aktivujete kliknutím na datovou krychli. Stisknutím a podržením klávesy **CTRL** můžete vybrat hrany, které jsou zde zobrazeny:

    ![Okraje, které budou tvořit špičku střechy](../designers/media/gfx_model_demo_house_edges.png)

    Když jsou vybrané okraje, na panelu nástrojů editoru modelů **Zvolte nástroj pro** překládání a pak posunutím manipulátor směrem nahoru vytvořte střechu domu.

   Model zjednodušené domovní konstrukce je dokončen. Zde je konečný model znovu s použitým plochým stínováním:

   ![Dokončený model zjednodušené domu](../designers/media/gfx_model_demo_house_final.png)

   V dalším kroku můžete použít shader na tento 3D model. Informace naleznete v tématu [How to: Apply a shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Modelování 3D terénu](../designers/how-to-model-3-d-terrain.md)
- [Editor modelů](../designers/model-editor.md)
- [Návrhář shaderů](../designers/shader-designer.md)
