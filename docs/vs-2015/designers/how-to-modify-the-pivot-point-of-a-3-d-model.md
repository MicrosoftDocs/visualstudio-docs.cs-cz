---
title: 'Postupy: změna bodu otáčení 3D modelu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: baeae2af825edc6a0032445288de7311b1ab1ae1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664407"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Postupy: Změna bodu otáčení 3D modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak použít Editor modelů pro úpravu *bodu otáčení* 3D modelu. Bod otáčení je bod v prostoru, který definuje matematické centrum objektu pro rotaci a škálování.

 Tento dokument ukazuje tuto aktivitu:

- Změna bodu otáčení objektu

## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Změna bodu otáčení 3D modelu
 Můžete znovu definovat počátek 3D modelu úpravou jeho bodu otáčení.

 Ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>Změna bodu otáčení 3D modelu

1. Začněte s existujícím 3D modelem, jako je ten, který je popsaný v tématu [How to: Create a Basic 3D model](../designers/how-to-create-a-basic-3-d-model.md).

2. Zadejte režim Pivot. Na panelu nástrojů **režim editoru modelů** aktivujte režim pivotu kliknutím na tlačítko **režim pivotu** . Zobrazí se okno kolem tlačítka **režim pivotu** , které indikuje, že Editor modelů je nyní v režimu Pivot. V režimu pivotu jsou operace, jako je například převod, ovlivněné bodem otáčení objektu místo struktury objektu v celém prostoru.

3. Upravte bod otáčení objektu. V režimu **výběru** vyberte objekt a pak na panelu nástrojů **prohlížeče modelů** zvolte nástroj pro **Překlad** . Rámeček, který představuje bod otáčení, se zobrazí na návrhové ploše. Přesuňte pole pro úpravu bodu otáčení objektu.

    Přesunutím pole můžete přesunout bod otáčení ve všech třech rozměrech. Chcete-li přeložit bod otáčení podél jedné osy, přesuňte šipku, která odpovídá dané ose. Pole a šipky se změní na žlutou barvu, aby označovala osu, která je ovlivněna překladem.

    Můžete také zadat bod otáčení pomocí vlastnosti pro **posunutí pivotu** v okně **vlastnosti** .

   > [!TIP]
   > Můžete zobrazit efekt nového bodu otáčení otočením objektu. Chcete-li jej otočit, použijte nástroj pro **otočení** nebo upravte vlastnost **otočení** .

   Zde je model, který má upravený bod otáčení:

   ![Model domu, který má upravený bod otáčení](../designers/media/digit-modified-model.png "Upravený číselný model")

## <a name="see-also"></a>Viz také
 [Postupy: Vytvoření základního 3D](../designers/how-to-create-a-basic-3-d-model.md) [editoru modelů](../designers/model-editor.md) modelů
