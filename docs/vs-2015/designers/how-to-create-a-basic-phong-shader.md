---
title: 'Postupy: vytvoření základního Phongova shaderu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ddb8f32cbf23184da140c3426e88c1f622dea1b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832677"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Postupy: Vytvoření základního Phongova shaderu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje způsob použití návrháře shaderu a orientovaného grafu shaderu jazyka (DGSL) vytvořit osvětlení shader, který implementuje Klasický model osvětlení Phong.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Přidání uzlů do grafu shaderu  
  
-   Odpojuje se uzly  
  
-   Spojující uzly  
  
## <a name="the-phong-lighting-model"></a>Model osvětlení Phong  
 Model osvětlení Phong rozšiřuje Lambertova modelu osvětlení zahrnout odlesků zvýraznění, který simuluje vlastnosti reflektivní povrchu. Reflexní součást poskytuje další osvětlení ze stejné směrové zdrojů světla, které se používají v Lambertova modelu osvětlení, ale jinak zpracování jeho příspěvku na konečnou barvu. Reflexní zvýraznění ovlivňuje všechny oblasti ve scéně odlišně, na základě vztahu mezi směr zobrazení, směr světla zdrojů a orientace povrchu. Je produkt reflexní barvy, síla odlesku a orientaci ovládacího prvku na plochu a barvu, intenzity a směr světla zdrojů. Zařízení Surface, které odráží světelný zdroj přímo v prohlížeči zobrazí maximální příspěvek lesku a površích, které odráží světelný zdroj mimo prohlížeč získat žádné příspěvek. V části model osvětlení Phong jednu nebo více komponent odlesky jsou zkombinované určíte barvu a intenzitu zrcadlových odlesků zvýraznění pro každý bod na objekt a se pak přidá do výsledku Lambertova modelu osvětlení vytvoří konečnou barvu pixelu .  
  
 Další informace o modelu osvětlení Lambert najdete v tématu [postupy: vytvoření základního Lambertova shaderu](../designers/how-to-create-a-basic-lambert-shader.md).  
  
 Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.  
  
#### <a name="to-create-a-phong-shader"></a>Chcete-li vytvořit Phongova shaderu  
  
1. Vytvoření Lambertova shaderu, jak je popsáno v [postupy: vytvoření základního Lambertova shaderu](../designers/how-to-create-a-basic-lambert-shader.md).  
  
2. Odpojte **Lambertova** uzlu z **konečnou barvu** uzlu. Zvolte **RGB** z terminálu **Lambertova** uzel a klikněte na tlačítko **přerušit odkazy**. Díky tomu místo pro uzel, který je přidán v dalším kroku.  
  
3. Přidat **přidat** uzel do grafu. V **nástrojů**v části **matematické**vyberte **přidat** a přesuňte jej na návrhovou plochu.  
  
4. Přidat **Specular** uzel do grafu. V **nástrojů**v části **nástroj**vyberte **Specular** a přesuňte jej na návrhovou plochu.  
  
5. Přidáte příspěvek lesku. Přesunout **výstup** z terminálu **Specular** uzlu **X** z terminálu **přidat** uzel a potom ho přesuňte **výstup**  z terminálu **Lambertova** uzlu **Y** z terminálu **přidat** uzlu. Tato připojení kombinovat příspěvky celkový barvy rozptýlení a množství odrazů pro obrazový bod.  
  
6. Hodnota počítaného barvy se připojte k konečnou barvu. Přesunout **výstup** z terminálu **přidat** uzlu **RGB** z terminálu **konečnou barvu** uzlu.  
  
   Následující obrázek znázorňuje dokončené shader graf a náhled shaderu použité pro model čajové konvice.  
  
> [!NOTE]
>  K předvedení lépe efekt shaderu na tomto obrázku, byl zadán oranžové barvy s použitím **MaterialDiffuse** byl zadán parametr shaderu a dokončení se kovové hledání s použitím **MaterialSpecular** a **MaterialSpecularPower** parametry. Informace o parametrech materiálu, naleznete v části Náhled shadery v [návrháře shaderu](../designers/shader-designer.md).  
  
 ![Graf shaderu a náhled vlivu](../designers/media/digit-lighting-graph.png "číslice. osvětlení grafu")  
  
 Určité tvary můžou poskytovat lepší verze Preview pro některé shadery. Další informace o tom, jak shadery v Návrháři shaderu ve verzi preview, najdete v části Náhled shadery v [návrháře shaderu](../designers/shader-designer.md)  
  
 Následující obrázek znázorňuje shaderu, který je popsaný v tomto dokumentu se použijí na 3D model. **MaterialSpecular** je nastavena na (1,00 0,50, 0.20 a novější, 0,00) a jeho **MaterialSpecularPower** je nastavena na 16.  
  
> [!NOTE]
>  **MaterialSpecular** vlastnost určuje zřejmý dokončit materiál povrchu. Vysoce lesklý povrch například lupy nebo plasty obvykle mají odlesky barva, která je jasně odstín prázdné. Kovové surface obvykle mají odlesky barva, která se blíží k jeho rozptýlení barvy. Povrch Satén dokončit obvykle mají odlesky barva, která je tmavé stínování šedé.  
>   
>  **MaterialSpecularPower** vlastnost určuje, jak velký odlesky jsou. Simulace vysoké množství odrazů využívá méně výrazné, lokalizované informace zvýrazní. Velmi nízké odlesků umožňuje simulovat velký, úklidem světla, které mohou oversaturate a skrýt barvu celého povrchu.  
  
 ![Použít pro model osvětlení Phong](../designers/media/digit-lighting-model.png "Model osvětlení číslice")  
  
 Další informace o tom, jak použití shaderu na 3D model, najdete v části [postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Postupy: exportování shaderu](../designers/how-to-export-a-shader.md)   
 [Postupy: vytvoření základního Lambertova shaderu](../designers/how-to-create-a-basic-lambert-shader.md)   
 [Návrhář shaderů](../designers/shader-designer.md)   
 [Uzly návrháře shaderů](../designers/shader-designer-nodes.md)



