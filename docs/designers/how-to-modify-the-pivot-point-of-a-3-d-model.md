---
title: 'Postup: Úprava kontingenčního bodu 3D modelu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 114beda700359eb5cdbfd4db12c18e442b8894f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589939"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Postupy: Změna bodu otáčení 3D modelu

Tento článek ukazuje, jak pomocí Editoru modelů upravit *pivotní bod* 3D modelu. Pivot point je bod v prostoru, který definuje matematický střed objektu pro otočení a změnu měřítka.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Změna bodu otáčení 3D modelu

Počátek 3D modelu můžete předefinovat úpravou jeho otočného bodu.

Ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

1. Začněte s existujícím 3D modelem, například s tím, který je popsán v [části Postup: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md).

2. Předejte režim otáčení. Na panelu nástrojů **Režim editoru modelů** zvolte tlačítko **Kontingenční režim,** abyste aktivovali režim otáčení. Kolem tlačítka **kontingenčního režimu** se zobrazí rámeček označující, že Editor modelů je nyní v režimu otáčení. V režimu otáčení operace, jako je například překlad, ovlivňují otočný bod objektu namísto struktury objektu ve světovém prostoru.

3. Upravte otočný bod objektu. V režimu **výběru** vyberte objekt a pak na panelu nástrojů **Prohlížeč modelů** zvolte nástroj **přeložit.** Na návrhové ploše se zobrazí rámeček, který představuje otočný bod. Přesunutím pole upravte otočný bod objektu.

     Přesunutím rámečku můžete přesunout otočný bod ve všech třech rozměrech. Chcete-li převést otočný bod podél jedné osy, přesuňte šipku, která této ose odpovídá. Pole a šipky se změní na žlutou barvu a označují osu, která je ovlivněna překladem.

     Bod otáčení můžete také určit pomocí vlastnosti **Kontingenční překlad** v okně **Vlastnosti.**

    > [!TIP]
    > Efekt nového otočného bodu můžete zobrazit otočením objektu. Chcete-li jej otočit, použijte nástroj **otočit** nebo upravte vlastnost **Otočení.**

Zde je model, který má upravený pivot bod:

![Model domu, který má upravený otočný bod](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md)
- [Editor modelů](../designers/model-editor.md)
