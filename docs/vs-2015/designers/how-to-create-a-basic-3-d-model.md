---
title: 'Postupy: Vytvoření základního 3D modelu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b4db5b54f39a0be6de184b609e672b1f0173890
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664595"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Postupy: Vytvoření základního 3D modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak použít Editor modelů k vytvoření základního 3D modelu.

 Tento dokument znázorňuje tyto aktivity:

- Přidání objektů do scény

- Výběr plošek a hran

- Překládání výběrů

- Použití **rozdělte obličej** a **přetlačení obličeje** nástrojů

- Použití příkazu **triangulovat**

## <a name="creating-a-basic-3-d-model"></a>Vytvoření základního 3D modelu
 Editor modelů můžete použít k vytvoření a úpravě 3D modelů a scén pro vaši hru nebo aplikaci. Následující kroky ukazují, jak použít Editor modelů k vytvoření zjednodušeného 3D modelu domu. Zjednodušený model lze použít jako samostatný pro finální materiály, které jsou stále vytvářeny, jako síť pro detekci kolizí nebo jako model s nízkými podrobnostmi, který má být použit, pokud je objekt, který představuje příliš daleko, nevýhodou podrobnějšího vykreslování.

 Až budete hotovi, model by měl vypadat takto:

 ![Dokončený model zjednodušené domu](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

 Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Vytvoření zjednodušeného 3D modelu domu

1. Vytvořte 3D model pro práci s. Informace o tom, jak přidat model do projektu, naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).

2. Přidejte do scény datovou krychli. V okně **sady nástrojů** v části **tvary**vyberte **krychle** a potom ji přesuňte na návrhovou plochu.

3. Přepněte na výběr obličeje. Na panelu nástrojů editoru modelů zvolte **možnost vybrat obličej**.

4. Rozdělte horní část datové krychle. V režimu výběru plochy Zvolte datovou krychli jednou, abyste ji aktivovali pro výběr, a pak zvolte horní stranu datové krychle a vyberte horní plochu. Na panelu nástrojů editoru modelů vyberte **rozdělit plochu**. Tím se do horní části datové krychle přidá nové vrcholy, které se rozdělí do čtyř oddílů se stejnou velikostí.

    ![Horní část datové krychle byla rozdělena](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")

5. Vytlačení dvou sousedních stran krychle, například přední a pravé strany datové krychle. V režimu výběru plochy vyberte datovou krychli jednou, abyste ji aktivovali pro výběr, a pak zvolte jednu stranu datové krychle. Stiskněte a podržte řídicí klávesu, vyberte jinou stranu datové krychle, která sousedí se stranou, kterou jste vybrali jako první, a pak na panelu nástrojů editoru modelů zvolte možnost **tlačení obličeje**.

    ![Strany krychle byly vytlačeny.](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")

6. Rozšíří jeden z vytlačení. Zvolte jednu z ploch, kterou jste právě vytlačeni, a potom na panelu nástrojů editoru modelů **Zvolte nástroj pro překlad a** přesuňte manipulátor překladu ve stejném směru jako vytlačení.

    ![Jedna strana datové krychle byla dále vytlačena.](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")

7. Triangulovat model. Na panelu nástrojů editoru modelů vyberte **Možnosti Upřesnit**, **nástroje**, **triangulovat**.

8. Vytvořte střechu domu. Přepněte do režimu výběru okrajů tak, že na panelu nástrojů editoru modelů kliknete na **Vybrat Edge** a potom ho aktivujete kliknutím na datovou krychli. Stisknutím a podržením řídicí klávesy při výběru hran, které jsou zde zobrazeny:

    ![Okraje, které budou tvořit špičku střechy](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")

    Když jsou vybrané okraje, na panelu nástrojů editoru modelů **Zvolte nástroj pro** překládání a pak posunutím manipulátor směrem nahoru vytvořte střechu domu.

   Model zjednodušené domovní konstrukce je dokončen. Zde je konečný model znovu s použitým plochým stínováním:

   ![Dokončený model zjednodušené domu](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

   V dalším kroku můžete použít shader na tento 3D model. Informace naleznete v tématu [How to: Apply shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také
 [Postupy: model trojrozměrného modelu pro](../designers/how-to-model-3-d-terrain.md) [Editor modelů](../designers/model-editor.md) [](../designers/shader-designer.md) terénu
