---
title: 'Postupy: Vytvoření základního shaderu textury | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59a926ab35e04aa120bc57250c3e5b2712858aa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664490"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Postupy: Vytvoření shaderu základní textury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak pomocí Návrháře shaderu a jazyka DGSL (Direct Graph shader) vytvořit shader s jednou texturou. Tento shader nastaví konečnou barvu přímo na hodnoty RGB a alfa, které jsou odebírány z textury.

 Tento dokument znázorňuje tyto aktivity:

- Odebrání uzlů z grafu shaderu

- Přidání uzlů do grafu

- Nastavení parametrů shaderu

- Nastavení viditelnosti parametrů

- Připojování uzlů

## <a name="creating-a-basic-texture-shader"></a>Vytvoření základního shaderu textury
 Můžete implementovat základní shader s jednou texturou tak, že napíšete barvy a alfa hodnoty vzorku textury přímo do konečné výstupní barvy.

 Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

#### <a name="to-create-a-basic-texture-shader"></a>Vytvoření základního shaderu textury

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

2. Odstraňte uzel **Barva bodu** . V režimu **výběru** vyberte uzel **Barva bodu** a pak na panelu nabídek zvolte možnost **Upravit**, **Odstranit**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu uzel s **ukázkovým texturou** . V **panelu nástrojů**v části **Textura**vyberte **Ukázka textury** a přesuňte ji na návrhovou plochu.

4. Přidejte uzel **souřadnice textury** do grafu. V **panelu nástrojů**v části **Textura**vyberte možnost **souřadnice textury** a přesuňte ji na plochu návrhu.

5. Vyberte texturu, která se má použít. V režimu **výběru** vyberte uzel **Ukázka textury** a potom v okně **vlastnosti** zadejte texturu, kterou chcete použít, pomocí vlastnosti **filename** .

6. Zpřístupněte texturu jako veřejně přístupný. Vyberte uzel **Ukázka textury** a potom v okně **vlastnosti** nastavte vlastnost **přístup** na **veřejné**. Nyní můžete nastavit texturu z jiného nástroje, jako je například **Editor modelů**.

7. Připojte souřadnice textury k ukázce textury. V režimu **výběru** přesuňte **výstupní** terminál uzlu **souřadnice textury** do **UV** terminálu uzlu **ukázky textury** . Toto připojení vzorkuje texturu na zadaných souřadnicích.

8. Připojte ukázku textury k konečné barvě. Přesuňte terminál **RGB** uzlu **vzorku textury** do terminálu **RGB** **konečného uzlu barvy** a poté přesuňte terminál **alfa** uzlu **ukázky textury** do terminálu **alfa** koncového uzlu **barvy** .

   Následující ilustrace znázorňuje dokončený graf shaderu a náhled shaderu, který se použije pro datovou krychli.

> [!NOTE]
> Na tomto obrázku je jako obrazec náhledu použita rovina a je určena textura, aby lépe ukázala účinek shaderu.

 ![Graf shaderu a náhled jeho efektu](../designers/media/digit-texture-effect.png "Číslice – efekt textury")

 Některé tvary mohou pro některé shadery poskytnout lepší náhled. Další informace o tom, jak zobrazit shadery v Návrháři shaderu, najdete v tématu [Shader Designer](../designers/shader-designer.md) .

## <a name="see-also"></a>Viz také
 [Postupy: použití shaderu na](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [uzly návrháře](../designers/shader-designer-nodes.md) shaderu návrháře [shaderu](../designers/shader-designer.md) v [editoru obrazu](../designers/image-editor.md) na 3D modelu
