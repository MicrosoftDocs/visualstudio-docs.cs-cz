---
title: 'Postupy: změna bodu otáčení 3D modelu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2c49e42009c81f6932f76128f12fb37399a789b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635468"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Postupy: změna bodu otáčení 3D model

Tento článek ukazuje, jak použít Editor modelů pro úpravu *bodu otáčení* 3D model. Bod otáčení je bod v prostoru, který definuje matematické centrum objektu pro rotaci a škálování.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Změna bodu otáčení 3D modelu

Počátek 3D model můžete předefinovat změnou jeho bodu otáčení.

Ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Začněte s existujícím 3D model, jako je ta, která je popsána v tématu [How to: Create a basic 3D model](../designers/how-to-create-a-basic-3-d-model.md).

2. Zadejte režim Pivot. Na panelu nástrojů **režim editoru modelů** aktivujte režim pivotu kliknutím na tlačítko **režim pivotu** . Zobrazí se okno kolem tlačítka **režim pivotu** , které indikuje, že Editor modelů je nyní v režimu Pivot. V režimu pivotu jsou operace, jako je například převod, ovlivněné bodem otáčení objektu místo struktury objektu v celém prostoru.

3. Upravte bod otáčení objektu. V režimu **výběru** vyberte objekt a pak na panelu nástrojů **prohlížeče modelů** zvolte nástroj pro **Překlad** . Rámeček, který představuje bod otáčení, se zobrazí na návrhové ploše. Přesuňte pole pro úpravu bodu otáčení objektu.

     Přesunutím pole můžete přesunout bod otáčení ve všech třech rozměrech. Chcete-li přeložit bod otáčení podél jedné osy, přesuňte šipku, která odpovídá dané ose. Pole a šipky se změní na žlutou barvu, aby označovala osu, která je ovlivněna překladem.

     Můžete také zadat bod otáčení pomocí vlastnosti pro **posunutí pivotu** v okně **vlastnosti** .

    > [!TIP]
    > Můžete zobrazit efekt nového bodu otáčení otočením objektu. Chcete-li jej otočit, použijte nástroj pro **otočení** nebo upravte vlastnost **otočení** .

Zde je model, který má upravený bod otáčení:

![Model domu, který má upravený bod otáčení](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md)
- [Editor modelů](../designers/model-editor.md)