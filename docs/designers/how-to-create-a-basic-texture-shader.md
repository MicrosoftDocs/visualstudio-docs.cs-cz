---
title: 'Postupy: Vytvoření shaderu základní textury'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 211da971bc7e4e275ef43b88531fe46a7fc0b4eb
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924063"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Postupy: vytvoření shaderu základní textury

Tento článek popisuje způsob použití návrháře shaderu a orientovaného grafu shaderu jazyka (DGSL) k vytvoření shaderu textury jednou. Tento shader nastaví konečnou barvu přímo na RGB a alfa hodnot, které jsou odebírána data z textury.

## <a name="create-a-basic-texture-shader"></a>Vytvoření shaderu základní textury

Basic, jeden textury shaderu můžete implementovat pomocí zápisu hodnoty barev a alfa vzorek textury přímo do konečné výstupní barva.

Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.

1.  Vytvořte shader DGSL pracovat. Informace o tom, jak přidat do projektu DGSL shader naleznete v části Začínáme v [návrháře shaderu](../designers/shader-designer.md).

2.  Odstranit **barva bodu** uzlu. V **vyberte** režimu, vyberte **barva bodu** uzel a pak na panelu nabídek zvolte **upravit** > **odstranit**. Díky tomu místo pro uzel, který je přidán v dalším kroku.

3.  Přidat **vzorek textury** uzel do grafu. V **nástrojů**v části **textury**vyberte **vzorek textury** a přesuňte jej na návrhovou plochu.

4.  Přidat **textury koordinovat** uzel do grafu. V **nástrojů**v části **textury**vyberte **textury koordinovat** a přesuňte jej na návrhovou plochu.

5.  Zvolte textury, který chcete použít. V **vyberte** režimu, vyberte **vzorek textury** uzel a pak v **vlastnosti** okno, určete texturu, kterou chcete použít s použitím **název souboru**  vlastnost.

6.  Ujistěte se, textury veřejně přístupná. Vyberte **vzorek textury** uzel a pak v **vlastnosti** okno, nastavte **přístup** vlastnost **veřejné**. Nyní textury můžete nastavit od jiného nástroje, jako **editoru modelů**.

7.  Souřadnice textury se připojte k vzorek textury. V **vyberte** režimu, přesunout **výstup** z terminálu **koordinovat textury** uzlu **UV** z terminálu **textury Ukázka** uzlu. Toto připojení navzorkuje texturu na zadaných souřadnicích.

8.  Vzorek textury se připojte k konečnou barvu. Přesunout **RGB** z terminálu **vzorek textury** uzlu **RGB** z terminálu **konečnou barvu** uzel a potom ho přesuňte **Alfa** z terminálu **vzorek textury** uzlu **alfa** z terminálu **konečnou barvu** uzlu.

Následující obrázek znázorňuje dokončené shader graf a náhled shaderu použitý pro datovou krychli.

> [!NOTE]
> Na tomto obrázku rovině slouží jako tvar náhled a byl zadán lépe demonstruje účinek shader textury.

![Graf shaderu a jeho účinkem ve verzi preview](../designers/media/digit-texture-effect.png)

Určité tvary můžou poskytovat lepší verze Preview pro některé shadery. Další informace o tom, jak shadery v Návrháři shaderu ve verzi preview, najdete v části [návrháře shaderu](../designers/shader-designer.md)

## <a name="see-also"></a>Viz také:

- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Editor obrázků](../designers/image-editor.md)
- [Návrhář shaderů](../designers/shader-designer.md)
- [Uzly návrháře shaderů](../designers/shader-designer-nodes.md)