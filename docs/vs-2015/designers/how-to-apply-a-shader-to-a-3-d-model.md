---
title: 'Postupy: použití shaderu na 3D model | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15d88f52b3af3a3e4502c618280107a882761259
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664605"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Postupy: Použití shaderu na 3D model
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak použít Editor modelů k použití shaderu DGSL (Direct Graph shader Language) na 3D model.

 Tento dokument ukazuje tuto aktivitu:

- Použití shaderu na 3D model

## <a name="applying-a-shader-to-a-3-d-model"></a>Použití shaderu na 3D model
 Můžete použít efekt shaderu na 3D model a dát mu tak zajímavý vzhled.

 Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** .

#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Použití shaderu na 3D model

1. Začněte 3D scénou, která obsahuje jeden nebo více modelů. Pokud nemáte vhodnou 3D scénu, vytvořte ji tak, jak je popsáno v tématu [How to: Create a Basic 3D model](../designers/how-to-create-a-basic-3-d-model.md). Také musíte mít DGSL shader, který můžete použít na model. Pokud nemáte vhodný shader, vytvořte ho tak, jak je popsáno v tématu [How to: Create a Basic Color shader](../designers/how-to-create-a-basic-color-shader.md) , a ujistěte se, že jste ho uložili do souboru, než budete pokračovat.

2. V režimu **výběru** vyberte model, na který chcete shader použít, a poté v okně **vlastnosti** v poli vlastnost **filename** skupiny vlastností **efekt** zadejte DGSL shader, který chcete použít pro model.

   Zde je model, který má použit základní barevný efekt:

   ![3D&#45;scéna, která zobrazuje základní barevný efekt](../designers/media/digit-3d-model-effect.png "Číslice – prostorový model – efekt")

   Po použití shaderu na model jej můžete otevřít v Návrháři shaderu, a to tak, že vyberete model a potom v okně **vlastnosti** ve vlastnosti **(rozšířené)** skupiny vlastností **efekt** zvolíte tlačítko se třemi tečkami ( **...** ).

## <a name="see-also"></a>Viz také
 [Postupy: Vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md) [Postupy: Vytvoření základního](../designers/how-to-create-a-basic-color-shader.md) [modelu shader Editor](../designers/model-editor.md) [shader designeru](../designers/shader-designer.md)
