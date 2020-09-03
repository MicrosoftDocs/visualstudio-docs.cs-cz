---
title: 'Postupy: Vytvoření základní funkce Color shader | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90f27e2359954e56a5b3d86bfc31883d4f29c44d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664590"
---
# <a name="how-to-create-a-basic-color-shader"></a>Postupy: Vytvoření shaderu základní barvy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit plochý barevný shader. Tento shader nastaví konečnou barvu na konstantní hodnotu barvy RGB.

 Tento dokument znázorňuje tyto aktivity:

- Odebírání uzlů z grafu

- Přidání uzlů do grafu

- Nastavení vlastností uzlu

- Připojování uzlů

## <a name="creating-a-flat-color-shader"></a>Vytvoření plochého barevného shaderu
 Můžete implementovat plochý barevný shader napsáním hodnoty barvy barevné konstanty RGB do konečné výstupní barvy.

 Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

#### <a name="to-create-a-flat-color-shader"></a>Vytvoření plochého barevného shaderu

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

2. Odstraňte uzel **Barva bodu** . Pomocí nástroje pro **Výběr** vyberte uzel **Barva bodu** a pak na panelu nabídek zvolte možnost **Upravit**, **Odstranit**.

3. Přidejte do grafu uzel **barevné konstanty** . V **sadě nástrojů**v části **konstanty**vyberte **barevný konstanta** a přesuňte ji na plochu návrhu.

4. Zadejte hodnotu barvy pro uzel **Color Constant** . Pomocí nástroje pro **Výběr** vyberte uzel **Barevná konstanta** a poté v okně **vlastnosti** ve vlastnosti **výstup** zadejte hodnotu barvy. V případě oranžová zadejte hodnotu (1,0, 0,5, 0,2, 1,0).

5. Připojte barevnou konstantu k konečné barvě. Chcete-li vytvořit připojení, přesuňte terminál **RGB** uzlu **Color Constant** do terminálu **RGB** **koncového uzlu barvy** a poté přesuňte terminál **alfa** uzlu **Color Constant** do terminálu **alfa** koncového uzlu **barvy** . Tato připojení nastavily konečnou barvu na barevnou konstantu definovanou v předchozím kroku.

   Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro datovou krychli.

> [!NOTE]
> Na ilustraci byla určena oranžová barva pro lepší ukázku účinku shaderu.

 ![Graf shaderu a jeho výsledek na 3&#45;D modelu](../designers/media/digit-flat-color-effect.png "Číslice – plochá barva – efekt")

 Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o tom, jak zobrazit shadery v Návrháři shaderu, najdete v tématu [Shader Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Viz také
 [Postupy: použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [Postupy: Export](../designers/how-to-export-a-shader.md) [uzlů Návrháře](../designers/shader-designer-nodes.md) shader shader shader [designeru](../designers/shader-designer.md)
