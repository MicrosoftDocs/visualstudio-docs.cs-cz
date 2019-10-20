---
title: 'Postupy: Vytvoření základního Lambert shaderu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 038b3e7db7f1e3b79ee3e41b6e256216a39b91bd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664560"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Postupy: Vytvoření základního Lambertova shaderu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit shader osvětlení, který implementuje model osvětlení Classic Lambert.

 Tento dokument znázorňuje tyto aktivity:

- Přidání uzlů do grafu shaderu

- Odpojování uzlů

- Připojování uzlů

## <a name="the-lambert-lighting-model"></a>Model osvětlení Lambert
 Model osvětlení Lambert zahrnuje okolí a směrové osvětlení k vystínování objektů v 3D scéně. Okolní komponenty poskytují základní úroveň osvětlení v 3D scéně. Směrové komponenty poskytují další osvětlení ze směrných (nečinných) světelných zdrojů. Okolní osvětlení ovlivňuje všechny povrchy scény stejně, bez ohledu na jejich orientaci. Pro danou plochu je to součin okolní barvy povrchu a barvy a intenzita okolního osvětlení na scéně. Směrové světlo má vliv na všechny povrchy scény odlišně na základě orientace povrchu v závislosti na směru zdroje světla. Jde o součin barev a orientace povrchu a barvu, intenzitu a směr zdrojů světla. Plochy, které čelí přímo ke zdroji světla, obdrží maximální podíl a plochy, které čelí přímo, nezískají žádný příspěvek. V rámci modelu osvětlení Lambert se kombinovaná komponenta a jedna nebo více směrových komponent spojí s cílem určit celkový podíl barev difúzí pro každý bod objektu.

 Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

#### <a name="to-create-a-lambert-shader"></a>Vytvoření shaderu Lambert

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

2. Odpojí uzel **Barva bodu** od **finálního uzlu barvy** . Zvolte terminál **RGB** pro uzel **Barva bodu** a pak zvolte možnost **přerušení propojení**. Nechejte terminál **Alpha** připojený.

3. Přidejte uzel **Lambert** do grafu. V **panelu nástrojů**vyberte v části **Nástroj**možnost **Lambert** a přesuňte ji na návrhovou plochu. Uzel Lambert vypočítá celkový podíl barvy difúze v pixelech na základě parametrů okolí a rozptýlené osvětlení.

4. Připojte uzel **Barva bodu** k **Lambert** uzlu. V režimu **výběru** přesuňte terminál **RGB** uzlu **barvy bodu** do terminálu **rozdifúze barvy** uzlu **Lambert** . Toto připojení poskytuje uzel Lambert s interpolací barvou difúze na pixelu.

5. Připojí vypočítanou hodnotu barvy k konečné barvě. Přesuňte **výstupní** terminál uzlu **Lambert** do terminálu **RGB** **konečného uzlu barvy** .

   Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro model konvice.

> [!NOTE]
> Pro lepší ukázku účinku shaderu na tomto obrázku je oranžová barva určena pomocí parametru **MaterialDiffuse** shaderu. Hra nebo aplikace může pomocí tohoto parametru zadat jedinečnou hodnotu barvy pro každý objekt. Informace o parametrech materiálu naleznete v části shadery Preview v [Návrháři shaderu](../designers/shader-designer.md).

 ![Graf shaderu a náhled jeho efektu.](../designers/media/digit-lambert-effect-graph.png "Číslice – Lambert – efekt – graf")

 Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o tom, jak zobrazit náhled shaderů v Návrháři shaderu, naleznete v části shadery Preview v [Návrháři shaderu](../designers/shader-designer.md).

 Následující ilustrace znázorňuje shader, který je popsaný v tomto dokumentu, aplikovaný na 3D model.

 ![Lambert osvětlení použité pro model.](../designers/media/digit-lambert-effect-result.png "Číslice – Lambert – výsledek efektu")

 Další informace o tom, jak použít shader na 3D model, naleznete v tématu [How to: Apply shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Viz také
 [Postupy: použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [Postupy: Export shaderu](../designers/how-to-export-a-shader.md) [Postupy: vytvoření základních](../designers/how-to-create-a-basic-phong-shader.md) [uzlů Návrháře](../designers/shader-designer-nodes.md) shaderu shaderu Phongova shader [designeru](../designers/shader-designer.md)
