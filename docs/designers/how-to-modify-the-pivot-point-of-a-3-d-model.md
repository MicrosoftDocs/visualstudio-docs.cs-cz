---
title: 'Postupy: Změna bodu otáčení 3D modelu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 352685e6b31aa688ff51f9564f141fa800c348d8
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977809"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Postupy: Změna bodu otáčení 3D modelu

Tento článek ukazuje, jak upravit pomocí Editoru modelů *bodu otáčení* 3D modelu. Bod otáčení je bod v prostoru, který definuje střed matematické objektu pro rotace a změnu měřítka.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Změna bodu otáčení 3D modelu

Původ na 3D model můžete upravit tak, že upravíte jejich bodem otáčení.

Ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.

1.  Začátek s existující 3D model, jako je ten, který je popsaný v [postupy: vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md).

2.  Zadejte režim pivotu. Na **režim editoru modelů** nástrojů, zvolte **režim Pivotu** tlačítko aktivovat režim pivotu. Pole se zobrazí kolem **režim Pivotu** tlačítko k označení, že Editor modelů je nyní v režim pivotu. V režim pivotu ovlivňují operace, jako jsou překladu bodu otáčení objektu namísto strukturu objektů v prostoru světa.

3.  Změna bodu otáčení objektu. V **vyberte** režimu, vyberte objekt a pak na **prohlížeč modelu** nástrojů, zvolte **přeložit** nástroj. Na návrhové ploše se objeví pole, které představuje bodu otáčení. Přesuňte pole a změna bodu otáčení objektu.

     Díky přesunu do pole, můžete přesunout bodu otáčení v všechny tři dimenze. K překladu bodu otáčení jednu osu přemístěte tuto šipku, která odpovídá na této osy. Pole a šipky změní na žlutou barvou pro označení toho osy, která jsou ovlivněná překlad.

     Bod otáčení můžete také zadat pomocí **posunutí pozice Pivotu** vlastnost **vlastnosti** okna.

    > [!TIP]
    > Otočení objektu, můžete zobrazit vliv nového bodu otáčení. Otočení, použijte **otočit** nástroje nebo změnit **otočení** vlastnost.

Tady je model, který má bod upravené pivot:

![Model, který má bod upravené otáčení domu](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md)
- [Editor modelů](../designers/model-editor.md)