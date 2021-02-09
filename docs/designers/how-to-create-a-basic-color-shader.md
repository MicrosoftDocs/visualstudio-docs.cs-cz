---
title: 'Postupy: Vytvoření shaderu základní barvy'
description: Naučte se používat návrháře shaderů a jazyk orientovaného grafu shaderu k vytvoření plochého barevného shaderu, který nastaví konečnou barvu na konstantní hodnotu barvy RGB.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b3c90496050754cc79c8bd774c0faa246e21512
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917044"
---
# <a name="how-to-create-a-basic-color-shader"></a>Postupy: Vytvoření shaderu základní barvy

Tento článek ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit plochý barevný shader. Tento shader nastaví konečnou barvu na konstantní hodnotu barvy RGB.

## <a name="create-a-flat-color-shader"></a>Vytvořit plochý barevný shader

Můžete implementovat plochý barevný shader napsáním hodnoty barvy barevné konstanty RGB do konečné výstupní barvy.

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

2. Odstraňte uzel **Barva bodu** . Pomocí nástroje pro **Výběr** vyberte uzel **Barva bodu** a pak na panelu nabídek zvolte možnost **Upravit**  >  **odstranění**.

3. Přidejte do grafu uzel **barevné konstanty** . V **sadě nástrojů** v části **konstanty** vyberte **barevný konstanta** a přesuňte ji na plochu návrhu.

4. Zadejte hodnotu barvy pro uzel **Color Constant** . Pomocí nástroje pro **Výběr** vyberte uzel **Barevná konstanta** a poté v okně **vlastnosti** ve vlastnosti **výstup** zadejte hodnotu barvy. V případě oranžová zadejte hodnotu (1,0, 0,5, 0,2, 1,0).

5. Připojte barevnou konstantu k konečné barvě. Chcete-li vytvořit připojení, přesuňte terminál **RGB** uzlu **Color Constant** do terminálu **RGB** **koncového uzlu barvy** a poté přesuňte terminál **alfa** uzlu **Color Constant** do terminálu **alfa** koncového uzlu **barvy** . Tato připojení nastavily konečnou barvu na barevnou konstantu definovanou v předchozím kroku.

Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro datovou krychli.

> [!NOTE]
> Na ilustraci byla určena oranžová barva pro lepší ukázku účinku shaderu.

![Graf shaderu a jeho výsledek na 3&#45;D modelu](../designers/media/digit-flat-color-effect.png)

Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o tom, jak zobrazit shadery v Návrháři shaderu, najdete v tématu [Shader Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)
