---
title: 'Postupy: vytvoření shaderu přechodu na základě geometrie | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61dd80bb8d8ba4c272beff018d3ab65ffce41dc6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911873"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Postupy: Vytvoření přechodu shaderu založeného na geometrii
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje způsob použití návrháře shaderu a Directed Graph Shader Language vytvoření přechodu shader geometrie založené. Tento shader škáluje konstantní hodnota barvy RGB výška jednotlivých bodů objektu v prostoru světa.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Přidání uzlů do grafu shaderu  
  
-   Nastavení vlastnosti uzlu  
  
-   Odpojuje se uzly  
  
-   Spojující uzly  
  
## <a name="creating-a-geometry-based-gradient-shader"></a>Vytvoření přechodu shader geometrie podle  
 Začleňte do vašeho shaderu pozice pixelu můžete implementovat na základě geometry shader. V jazycích stínování pixel obsahuje více informace než jenom její barvu a umístění na obrazovce 2D. Pixel – označované jako *fragment* u některých systémů – je kolekce hodnot, které popisují, která odpovídá povrchu pixelu. Shader, který je popsaný v tomto dokumentu využívá výška každý pixel 3D objekt v prostoru světa ovlivní barvu závěrečný výstup fragmentu.  
  
 Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.  
  
#### <a name="to-create-a-geometry-based-gradient-shader"></a>Chcete-li vytvořit shader přechodu na základě geometrie  
  
1. Vytvořte shader DGSL pracovat. Informace o tom, jak přidat do projektu DGSL shader naleznete v části Začínáme v [návrháře shaderu](../designers/shader-designer.md).  
  
2. Odpojte **barva bodu** uzlu z **konečnou barvu** uzlu. Zvolte **RGB** z terminálu **barva bodu** uzel a klikněte na tlačítko **přerušit odkazy**. Díky tomu místo pro uzel, který je přidán v dalším kroku.  
  
3. Přidat **vynásobit** uzel do grafu. V **nástrojů**v části **matematické**vyberte **vynásobit** a přesuňte jej na návrhovou plochu.  
  
4. Přidat **maskovat vektor** uzel do grafu. V **nástrojů**v části **nástroj**vyberte **maskovat vektor** a přesuňte jej na návrhovou plochu.  
  
5. Zadejte hodnoty masky **maskovat vektor** uzlu. V **vyberte** režimu, vyberte **maskovat vektor** uzel a pak v **vlastnosti** okno, nastavte **zelená / Y** vlastnost **True**a pak nastavte **Červená / X**, **modrá / Z** a **alfa / W** vlastnosti, které chcete **False**. V tomto příkladu **Červená / X**, **zelená / Y**, a **modrá / Z** vlastnosti odpovídají x, y a z komponenty **pozice světa** uzel, a **alfa / W** se nepoužívá. Protože pouze **zelená / Y** je nastavena na **True**, jenom součásti y vstupní vektoru zůstává poté, co je zakryté hvězdičkami.  
  
6. Přidat **pozice světa** uzel do grafu. V **nástrojů**v části **konstanty**vyberte **pozice světa** a přesuňte jej na návrhovou plochu.  
  
7. Maskovat pozice místa na světě fragmentu. V **vyberte** režimu, přesunout **výstup** z terminálu **pozice světa** uzlu **vektoru** z terminálu **maska Vektor** uzlu. Toto připojení zakrývá pozice fragment ignorovat x a z komponenty.  
  
8. Vynásobte barevnou konstantu RGB umístěním maskované světě prostor. Přesunout **RGB** z terminálu **barva bodu** uzlu **Y** z terminálu **vynásobit** uzel a potom ho přesuňte  **Výstup** z terminálu **maskovat vektor** uzlu **X** z terminálu **vynásobit** uzlu. Toto připojení se škáluje hodnota barvy podle výšky pixelu v prostoru světa.  
  
9. Hodnota barvy dokončeno škálování se připojte k konečnou barvu. Přesunout **výstup** z terminálu **vynásobit** uzlu **RGB** z terminálu **konečnou barvu** uzlu.  
  
   Následující obrázek znázorňuje dokončené shader graf a náhled shaderu u koule.  
  
> [!NOTE]
>  Na tomto obrázku je zadána oranžovou barvou lépe demonstruje účinek shaderu, ale protože tvar náhled nemá žádné pozice v prostoru světa, shader, nepůjde zobrazit náhled plně v Návrháři shaderu. Shader musí být zobrazen ve skutečných scéně k předvedení plný vliv.  
  
 ![Graf shaderu a náhled vlivu](../designers/media/digit-gradient-effect-graph.png "číslice přechodu efekt grafu")  
  
 Určité tvary můžou poskytovat lepší verze Preview pro některé shadery. Informace o tom, jak shadery v Návrháři shaderu ve verzi preview najdete v tématu **náhled shadery** v [návrháře shaderu](../designers/shader-designer.md)  
  
 Následující obrázek znázorňuje shaderu, který je popsaný v tomto dokumentu použitý pro 3D scény, což je znázorněno v [postupy: modelování 3D terénu](../designers/how-to-model-3-d-terrain.md). Intenzita barvy se zvyšuje s výšky bodu na světě.  
  
 ![Efekt přechodu použít na 3&#45;D terénu modelu](../designers/media/digit-gradient-effect-result.png "číslice přechodu efekt výsledků")  
  
 Další informace o tom, jak použití shaderu na 3D model, najdete v části [postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Postupy: exportování shaderu](../designers/how-to-export-a-shader.md)   
 [Postupy: modelování 3D terénu](../designers/how-to-model-3-d-terrain.md)   
 [Postupy: vytvoření shaderu textury stupňů šedé](../designers/how-to-create-a-grayscale-texture-shader.md)   
 [Návrhář shaderů](../designers/shader-designer.md)   
 [Uzly návrháře shaderů](../designers/shader-designer-nodes.md)



