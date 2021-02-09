---
title: 'Postupy: použití shaderu na 3D model'
description: Naučte se používat Editor modelů k použití shaderu orientovaného jazykového shaderu na 3D model k tomu, aby získal zajímavý vzhled.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdaf4b86bfc773df678c03875a9ec260cd72084f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917075"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Postupy: Použití shaderu na 3D model

Tento článek ukazuje, jak použít Editor modelů k použití shaderu DGSL (Direct Graph shader Language) na 3D model.

## <a name="apply-a-shader-to-a-3d-model"></a>Použití shaderu na 3D model

Můžete použít efekt shaderu na 3D model a dát mu tak zajímavý vzhled.

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** .

1. Začněte s 3D scénou, která obsahuje jeden nebo více modelů. Pokud nemáte vhodnou 3D scénu, vytvořte ji tak, jak je popsáno v tématu [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md). Musíte mít také DGSL shader, který můžete použít na model. Pokud nemáte vhodný shader, vytvořte ho tak, jak je popsáno v tématu [How to: Create a Basic Color shader](../designers/how-to-create-a-basic-color-shader.md) , a ujistěte se, že jste ho uložili do souboru, než budete pokračovat.

2. V režimu **výběru** vyberte model, pro který chcete shader použít, a poté v okně **vlastnosti** ve vlastnosti **filename** skupiny vlastností **efekt** určete DGSL shader, který chcete použít pro model.

Zde je model, který má použit základní barevný efekt:

![3&#45;D scény, která zobrazuje základní barevný efekt](../designers/media/digit-3d-model-effect.png)

Po použití shaderu na model jej můžete otevřít v Návrháři shaderu, a to tak, že vyberete model a potom v okně **vlastnosti** ve vlastnosti **(rozšířené)** skupiny vlastností **efekt** zvolíte tlačítko se třemi tečkami (**...**).

## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md)
- [Postupy: Vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md)
- [Editor modelů](../designers/model-editor.md)
- [Návrhář shaderů](../designers/shader-designer.md)
