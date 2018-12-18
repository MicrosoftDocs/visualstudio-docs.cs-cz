---
title: 'Postupy: použití shaderu na 3D Model'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12fc18532888dbf688c3fcc0e5695edfaf47d953
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924132"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Postupy: použití shaderu na 3D model

Tento článek popisuje způsob použití Editoru modelů pro použití orientovaného grafu Shader Language (DGSL) shaderu na 3D model.

## <a name="apply-a-shader-to-a-3d-model"></a>Použití shaderu na 3D model

Použít efekt shaderu na 3D model nabízí zajímavé vzhled.

Než začnete, ujistěte se, že **vlastnosti** se zobrazí okno.

1. Začněte s 3D scéně, který obsahuje jeden nebo více modelů. Pokud nemáte k dispozici vhodný 3D scény, vytvořit jak je popsáno v [postupy: vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md). Musíte mít také DGSL shader, který můžete použít pro model. Pokud nemáte k dispozici vhodný shaderu, vytvořit jak je popsáno v [postupy: vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md) a ujistěte se, že jste uložili ji do souboru předtím, než budete pokračovat.

2. V **vyberte** režimu, vyberte model, na který chcete použít shaderu a pak v **vlastnosti** okno v **Filename** vlastnost **efekt**  skupiny vlastností zadejte DGSL shader, který má být použita k modelu.

Tady je model, který je použit efekt základní barvy:

![3&#45;scény D, která demonstruje účinek základní barvy](../designers/media/digit-3d-model-effect.png)

Po použití shaderu na model, lze jej otevřít v Návrháři shaderu tak, že vyberete model a pak v **vlastnosti** okno v **(rozšířené)** vlastnost **efekt**skupiny vlastností, vyberete symbol tří teček (**...** ) tlačítko.

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md)
- [Postupy: Vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md)
- [Editor modelů](../designers/model-editor.md)
- [Návrhář shaderů](../designers/shader-designer.md)