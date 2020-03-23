---
title: 'Postup: Použití shaderu na 3D model'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ae04f4cc0afb1c24f391d140081040efe9db50e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112752"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Postupy: Použití shaderu na 3D model

Tento článek ukazuje, jak použít Editor modelu použít shader jazyka shaderu s rozhraním Směrný graf (DGSL) na 3D model.

## <a name="apply-a-shader-to-a-3d-model"></a>Použití shaderu na 3D model

Efekt shaderu můžete použít na 3D model, abyste mu dali zajímavý vzhled.

Než začnete, ujistěte se, že se zobrazí okno **Vlastnosti.**

1. Začněte s 3D scénou, která obsahuje jeden nebo více modelů. Pokud nemáte vhodnou 3D scénu, vytvořte ji, jak je popsáno v [části Postup: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md). Musíte mít také shader DGSL, který můžete použít pro model. Pokud nemáte vhodný shader, vytvořte ho, jak je popsáno v [části Postup: Vytvořte základní barevný shader](../designers/how-to-create-a-basic-color-shader.md) a ujistěte se, že jste ho uložili do souboru, než budete pokračovat.

2. V režimu **Výběr** vyberte model, na který chcete použít shader, a pak v okně **Vlastnosti** ve vlastnosti **Název_souboru** skupiny vlastností **Efekt** určete shader DGSL, který chcete použít na model.

Zde je model, který má základní barevný efekt použít na to:

![3&#45;D scéna, která zobrazuje základní barevný efekt](../designers/media/digit-3d-model-effect.png)

Po aplikování shaderu na model jej můžete otevřít v návrháři shaderu výběrem modelu a potom v okně **Vlastnosti** ve **vlastnosti (Upřesnit)** skupiny vlastností **Efekt,** výběrem tlačítka tři tečky (**...**).

## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md)
- [Postupy: Vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md)
- [Editor modelů](../designers/model-editor.md)
- [Návrhář shaderů](../designers/shader-designer.md)
