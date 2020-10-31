---
title: 'Postupy: Vytvoření shaderu základní textury'
description: Pomocí Návrháře shaderu a jazyka orientovaného shaderu v grafu můžete vytvořit shader s jednou texturou, který nastaví konečnou barvu na hodnoty RGB a alfa z textury.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93696dfe9fbf3b8db1d4be137ced6798b3a60aae
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134495"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Postupy: Vytvoření shaderu základní textury

Tento článek ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit shader s jednou texturou. Tento shader nastaví konečnou barvu přímo na hodnoty RGB a alfa, které jsou odebírány z textury.

## <a name="create-a-basic-texture-shader"></a>Vytvoření shaderu základní textury

Můžete implementovat základní shader s jednou texturou tak, že napíšete barvy a alfa hodnoty vzorku textury přímo do konečné výstupní barvy.

Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

2. Odstraňte uzel **Barva bodu** . V režimu **výběru** vyberte uzel **Barva bodu** a pak na panelu nabídek zvolte **Upravit**  >  **Odstranit** . Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu uzel s **ukázkovým texturou** . V **panelu nástrojů** v části **Textura** vyberte **Ukázka textury** a přesuňte ji na návrhovou plochu.

4. Přidejte uzel **souřadnice textury** do grafu. V **panelu nástrojů** v části **Textura** vyberte možnost **souřadnice textury** a přesuňte ji na plochu návrhu.

5. Vyberte texturu, která se má použít. V režimu **výběru** vyberte uzel **Ukázka textury** a potom v okně **vlastnosti** zadejte texturu, kterou chcete použít, pomocí vlastnosti **filename** .

6. Zpřístupněte texturu jako veřejně přístupný. Vyberte uzel **Ukázka textury** a potom v okně **vlastnosti** nastavte vlastnost **přístup** na **veřejné** . Nyní můžete nastavit texturu z jiného nástroje, jako je například **Editor modelů** .

7. Připojte souřadnice textury k ukázce textury. V režimu **výběru** přesuňte **výstupní** terminál uzlu **souřadnice textury** do **UV** terminálu uzlu **ukázky textury** . Toto připojení vzorkuje texturu na zadaných souřadnicích.

8. Připojte ukázku textury k konečné barvě. Přesuňte terminál **RGB** uzlu **vzorku textury** do terminálu **RGB** **konečného uzlu barvy** a poté přesuňte terminál **alfa** uzlu **ukázky textury** do terminálu **alfa** koncového uzlu **barvy** .

Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro datovou krychli.

> [!NOTE]
> Na tomto obrázku je jako obrazec náhledu použita rovina a je určena textura, aby lépe ukázala účinek shaderu.

![Graf shaderu a náhled jeho efektu](../designers/media/digit-texture-effect.png)

Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o tom, jak zobrazit shadery v Návrháři shaderu, najdete v tématu [Shader Designer](../designers/shader-designer.md) .

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Editor obrázků](../designers/image-editor.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)
