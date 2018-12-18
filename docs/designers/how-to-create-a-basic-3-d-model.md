---
title: 'Postupy: vytvoření základního 3D modelu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6242b80c1dcefe0e1a3a35561337a75e6098d25d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913446"
---
# <a name="how-to-create-a-basic-3d-model"></a>Postupy: vytvoření základního 3D modelu

Tento článek popisuje způsob použití Editoru modelů pro vytvoření základního 3D modelu. Zahrnuje následující činnosti:

-   Přidání objektů do scény

-   Výběrem tváří a okraje

-   Možnosti překladu

-   Použití **rozdělit plochu** a **vyloučit plochu** nástroje

-   Použití **Triangulovat** příkazu

## <a name="create-a-basic-3d-model"></a>Vytvoření základního 3D modelu
 Editor modelů můžete použít k vytvoření a úprava 3D modely a pozadí pro vaše hry nebo aplikace. Následující kroky ukazují, jak vytvořit jednoduchý model 3D domu pomocí Editoru modelů. Zjednodušený model může sloužit jako stand-in pro konečné prostředků, které jsou stále probíhá vytváření, jako síť pro detekci kolizí, nebo jako model s nízkou podrobností se použije, když je objekt, který představuje příliš daleko těžit z podrobnější vykreslování.

 Jakmile budete hotovi, model by měl vypadat nějak takto:

 ![Dokončené modelu zjednodušené house](../designers/media/gfx_model_demo_house_final.png)

 Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>K vytvoření 3D modelu zjednodušené domu

1. Vytvoření 3D modelu, se kterým chcete pracovat. Informace o tom, jak přidat modelu do projektu naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).

2. Přidáte datové krychle do scény. V **nástrojů** okně v části **tvary**vyberte **datové krychle** a přesuňte jej na návrhovou plochu.

3. Přepnout výběr pro rozpoznávání tváře. Na panelu nástrojů editoru modelů **tváří vybrat**.

4. Rozdělit horní části datové krychle. V režimu výběru ploch zvolte krychli jednou aktivovat pro výběr a klikněte na tlačítko horní část datové krychle a vyberte hlavní rozpoznávání tváře. Na panelu nástrojů editoru modelů **rozdělit plochu**. Tento postup přidá nové vrcholy k hornímu okraji datové krychle, která ho rozdělit do čtyř oddílů stejně velké.

    ![Má dělí horní části datové krychle](../designers/media/gfx_model_demo_house_subdiv.png)

5. Vyloučit sociálními sousední datové krychle – například front-end a pravé straně datové krychle. V režimu výběru ploch zvolte datovou krychli jednou aktivovat pro výběr a klikněte na tlačítko straně datové krychle. Stiskněte a podržte **Ctrl** klíče, zvolte jinou stranu krychle sousedícího se na straně nejprve vyberete a pak zvolte na panelu nástrojů editoru modelů **vyloučit plochu**.

    ![Strany krychle mít vyňaty.](../designers/media/gfx_model_demo_house_extrude.png)

6. Rozšiřte jednu extrusions. Vyberte jednu z plochy, které jste právě vyňaty a zvolte na panelu nástrojů editoru modelů **přeložit** nástroj a ve stejném směru jako vytlačení přesunout manipulátor překladu.

    ![Straně krychle má další vyňaty.](../designers/media/gfx_model_demo_house_extend.png)

7. Triangulovat modelu. Na panelu nástrojů editoru modelů **Upřesnit** > **nástroje** > **Triangulovat**.

8. Vytvoření stříška dům. Přepnout do režimu výběru okrajů výběrem **vyberte Edge** na panelu nástrojů editoru modelů a datové krychle aktivovat, klikněte na tlačítko. Stiskněte a podržte **Ctrl** klíče při výběru hran, která jsou zobrazena zde:

    ![Hrany, které budou tvořit ve špičce stropu](../designers/media/gfx_model_demo_house_edges.png)

    Když vyberete okrajů, na panelu nástrojů editoru modelů, zvolte **přeložit** nástroje a poté přesuňte směrem nahoru k vytvoření stříška dům manipulátor překladu.

   Zjednodušené house modelu je dokončeno. Tady je znovu finálního modelu s plochým stínováním použít:

   ![Dokončené modelu zjednodušené house](../designers/media/gfx_model_demo_house_final.png)

   V dalším kroku můžete tento 3D model použití shaderu. Informace najdete v tématu [postupy: použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Modelování 3D terénu](../designers/how-to-model-3-d-terrain.md)
- [Editor modelů](../designers/model-editor.md)
- [Návrhář shaderů](../designers/shader-designer.md)
