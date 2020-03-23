---
title: 'Postupy: Vytvoření shaderu základní barvy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 162632f0043d23fb111a9e455c1100f9506924a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589510"
---
# <a name="how-to-create-a-basic-color-shader"></a>Postupy: Vytvoření shaderu základní barvy

Tento článek ukazuje, jak pomocí Návrhář shaderu a směrovaný graf shader jazyk (DGSL) k vytvoření shader plochých barev. Tento shader nastaví konečnou barvu na konstantní hodnotu barvy RGB.

## <a name="create-a-flat-color-shader"></a>Vytvoření shaderu plochých barev

Shader s plochými barvami můžete implementovat zápisem barevné hodnoty barevné konstanty RGB do konečné výstupní barvy.

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

1. Vytvořte shader DGSL pro práci. Informace o tom, jak přidat shader SChL do projektu, naleznete v části Začínáme v [návrháři shaderu](../designers/shader-designer.md).

2. Odstraňte uzel **Barva bodu.** Pomocí nástroje **pro výběr** vyberte uzel **Barva bodu** a potom na řádku nabídek zvolte **Upravit** > **odstranění**.

3. Přidejte do grafu uzel **Konstanta barev.** V **panelu nástrojů**včásti **Konstanty**vyberte **Konstanta barvy** a přesuňte ji na návrhovou plochu.

4. Určete hodnotu barvy pro uzel **Konstanta barvy.** Nástrojem **pro výběr** vyberte uzel **Konstanta barvy** a pak v okně **Vlastnosti** ve vlastnosti **Output** určete hodnotu barvy. Pro oranžovou zadejte hodnotu (1,0, 0,5, 0,2, 1,0).

5. Připojte barevnou konstantu ke konečné barvě. Chcete-li vytvořit připojení, přesuňte terminál **RGB** uzlu **Konstanta barev** do terminálu **RGB** uzlu **Konečné barvy** a potom přesuňte terminál **alfa** uzlu **Konstanta barev** do **terminálu Alfa** uzlu Konečné **barvy.** Tato připojení nastaví konečnou barvu na konstantu barvy definovanou v předchozím kroku.

Následující obrázek znázorňuje dokončený graf shaderu a náhled shaderu aplikovaného na krychli.

> [!NOTE]
> Na obrázku byla zadána oranžová barva, aby se lépe demonstroval účinek shaderu.

![Shader graf a jeho výsledek na 3&#45;D modelu](../designers/media/digit-flat-color-effect.png)

Některé obrazce mohou některým shaderům poskytovat lepší náhledy. Další informace o zobrazení náhledu shaderů v návrháři shaderu naleznete v [tématu Shader Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly Návrhářshaderu](../designers/shader-designer-nodes.md)
