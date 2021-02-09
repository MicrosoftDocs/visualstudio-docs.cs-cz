---
title: 'Postupy: modelování 3D terénu'
description: Naučte se pomocí editoru modelů vytvořit model 3D terénu tak, že rozdělíte rovinu, aby se vytvořily další obličeje a manipulují se vrcholy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 969dd229d8d6cd6bdbe9d53eaabd63f1eedd6570
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930847"
---
# <a name="how-to-model-3d-terrain"></a>Postupy: modelování 3D terénu

Tento článek ukazuje, jak pomocí editoru modelů vytvořit model 3D terénu.

## <a name="create-a-3d-terrain-model"></a>Vytvoření modelu 3D terénu

Prostorovou terén můžete vytvořit rozrozdělením roviny tak, aby se vytvořily další plošky, a potom manipulovat s jejich vrcholy a vytvářet zajímavé funkce terénu.

Až budete hotovi, model by měl vypadat takto:

![3&#45;D scény zobrazující model terénu](../designers/media/digit-terrain-model.png)

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Vytvořte 3D model, se kterou chcete pracovat. Informace o tom, jak přidat model do projektu, naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).

2. Přidejte rovinu do scény. V **sadě nástrojů** v části **tvary** vyberte **rovina** a přesuňte ji na návrhovou plochu.

    > [!TIP]
    > Chcete-li nastavit objekt roviny tak, aby lépe fungoval, můžete ho orámovat na návrhové ploše. V režimu **výběru** vyberte objekt rovina a pak na panelu nástrojů editoru modelů zvolte tlačítko **objekt rámce** .

3. Zadejte režim výběru obličeje. Na panelu nástrojů editoru modelů zvolte **možnost vybrat obličej**.

4. Rozdělit rovinu V režimu výběru plochy vyberte rovinu, která se má aktivovat pro výběr, a pak ji znovu vyberte, abyste vybrali jenom svoji plošku. Na panelu nástrojů editoru modelů vyberte **rozdělit plochu**. Tím přidáte nové vrcholy do roviny, které ji rozdělí do čtyř oddílů s rovnoměrné velikosti.

5. Vytvořte další dílčí dělení. Když je vybraná možnost nové plošky, klikněte na **rozdělit obličej** ještě dvakrát. Tím se vytvoří celkem 64 ploch. Vytvořením dalších dílčích dělení můžete přidělit terénu ještě více podrobností.

6. Zadejte režim výběru bodu. Na panelu nástrojů editoru modelů zvolte **možnost vybrat bod**.

7. Úpravou bodu vytvořte funkci terénu. V režimu výběru bodu vyberte jeden z bodů a pak na panelu nástrojů editoru modelů zvolte nástroj pro **Překlad** . Pole, které představuje bod, se zobrazí na návrhové ploše. Pomocí zelené šipky můžete přesunout pole a tím upravit výšku bodu. Opakujte tento krok pro různé body pro vytváření zajímavých funkcí terénu.

    > [!TIP]
    > Můžete vybrat několik bodů najednou a upravit je jednotným způsobem.

Model terénu je dokončený. Zde je konečný model znovu s aplikovaným Phongova stínováním:

![3&#45;D scény zobrazující model terénu](../designers/media/digit-terrain-model.png)

Tento model terénu lze použít k předvedení efektu přechodu, který je popsán v tématu [Postupy: vytvoření shaderu přechodu na základě geometrie](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Viz také

- [Editor modelů](../designers/model-editor.md)
