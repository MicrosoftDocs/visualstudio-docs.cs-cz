---
title: 'Postupy: Vytvoření shaderu základní textury'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac74155b8de4669d959d9b14e9be20ada2ec51d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589471"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Postupy: Vytvoření shaderu základní textury

Tento článek ukazuje, jak pomocí Návrhář shaderu a směrovaný graf shader jazyk (DGSL) k vytvoření shader s jednou texturou. Tento shader nastaví konečnou barvu přímo na hodnoty RGB a alfa, které jsou vzorkovány z textury.

## <a name="create-a-basic-texture-shader"></a>Vytvoření shaderu základní textury

Základní shader s jednou texturou můžete implementovat zápisem hodnot barev a alfa vzorku textury přímo do konečné výstupní barvy.

Než začnete, ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

1. Vytvořte shader DGSL pro práci. Informace o tom, jak přidat shader SChL do projektu, naleznete v části Začínáme v [návrháři shaderu](../designers/shader-designer.md).

2. Odstraňte uzel **Barva bodu.** V režimu **výběru** vyberte uzel **Barva bodu** a potom na řádku nabídek zvolte **Upravit** > **odstranění**. Tím se vytvoří místo pro uzel, který je přidán v dalším kroku.

3. Přidejte do grafu uzel **Ukázkový** vzorek textury. V **panelu nástrojů**v části **Textura**vyberte **Vzorek textury** a přesuňte ho na návrhovou plochu.

4. Přidejte do grafu uzel **Souřadnice textury.** V **panelu nástrojů**v části **Textura**vyberte **Souřadnice textury** a přesuňte ji na návrhovou plochu.

5. Vyberte texturu, která se má použít. V režimu **Výběr** vyberte uzel **Ukázkový texturu** a pak v okně **Vlastnosti** určete texturu, kterou chcete použít, pomocí vlastnosti **Název_souboru.**

6. Zpřístupňte texturu veřejně přístupnou. Vyberte uzel **Ukázkový** textura a potom v okně **Vlastnosti** nastavte vlastnost **Access** na **hodnotu Public**. Nyní můžete nastavit texturu z jiného nástroje, například **editoru modelů**.

7. Připojte souřadnice textury ke vzorku textury. V režimu **Select** přesuňte **výstupní** terminál uzlu **Souřadnice textury** na terminál **UV** uzlu **Vzorku textury.** Toto připojení vzorku textury na zadané souřadnice.

8. Připojte vzorek textury ke konečné barvě. Přesuňte terminál **RGB** uzlu **Ukázkový textury** do terminálu **RGB** uzlu **Konečné barvy** a potom přesuňte **terminál alfa** uzlu **Vzorku textury** do **terminálu Alfa** uzlu Konečné **barva.**

Následující obrázek znázorňuje dokončený graf shaderu a náhled shaderu aplikovaného na krychli.

> [!NOTE]
> Na tomto obrázku se jako obrazec náhledu použije rovina a byla zadána textura, která lépe demonstruje účinek shaderu.

![Shader graf a náhled jeho účinku](../designers/media/digit-texture-effect.png)

Některé obrazce mohou některým shaderům poskytovat lepší náhledy. Další informace o zobrazení náhledu shaderů v návrháři shaderů najdete v [tématu Shader Designer](../designers/shader-designer.md)

## <a name="see-also"></a>Viz také

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Editor obrázků](../designers/image-editor.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Uzly Návrhářshaderu](../designers/shader-designer-nodes.md)
