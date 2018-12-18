---
title: 'Postupy: vytvoření základního 3D modelu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 83d4069135adf37156457321b8ce15a254c9c27b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825488"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Postupy: Vytvoření základního 3D modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje způsob použití Editoru modelů pro vytvoření základního 3D modelu.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Přidání objektů do scény  
  
-   Výběrem tváří a okraje  
  
-   Možnosti překladu  
  
-   Použití **rozdělit plochu** a **vyloučit plochu** nástroje  
  
-   Použití **Triangulovat** příkazu  
  
## <a name="creating-a-basic-3-d-model"></a>Vytvoření základního 3D modelu  
 Editor modelů můžete použít k vytvoření a úprava 3D modely a pozadí pro vaše hry nebo aplikace. Následující kroky ukazují, jak použít k vytvoření 3D modelu zjednodušené domu editoru modelů. Zjednodušený model může sloužit jako stand-in pro konečné prostředků, které jsou stále probíhá vytváření, jako síť pro detekci kolizí, nebo jako model s nízkou podrobností se použije, když je objekt, který představuje příliš daleko těžit z podrobnější vykreslování.  
  
 Jakmile budete hotovi, model by měl vypadat nějak takto:  
  
 ![Dokončené modelu zjednodušené house](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>K vytvoření 3D modelu zjednodušené domu  
  
1. Vytvoření 3D modelu chcete pracovat. Informace o tom, jak přidat modelu do projektu naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).  
  
2. Přidáte datové krychle do scény. V **nástrojů** okně v části **tvary**vyberte **datové krychle** a přesuňte jej na návrhovou plochu.  
  
3. Přepnout výběr pro rozpoznávání tváře. Na panelu nástrojů editoru modelů **tváří vybrat**.  
  
4. Rozdělit horní části datové krychle. V režimu výběru ploch zvolte krychli jednou aktivovat pro výběr a klikněte na tlačítko horní část datové krychle a vyberte hlavní rozpoznávání tváře. Na panelu nástrojů editoru modelů **rozdělit plochu**. Tento postup přidá nové vrcholy k hornímu okraji datové krychle, která ho rozdělit do čtyř oddílů stejně velké.  
  
    ![Má dělí horní části datové krychle](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")  
  
5. Vyloučit sociálními sousední datové krychle – například front-end a pravé straně datové krychle. V režimu výběru ploch zvolte datovou krychli jednou aktivovat pro výběr a klikněte na tlačítko straně datové krychle. Stiskněte a podržte klávesu CTRL, zvolte jinou stranu krychle sousedícího se na straně nejprve vyberete a pak zvolte na panelu nástrojů editoru modelů **vyloučit plochu**.  
  
    ![Strany krychle mít vyňaty.](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")  
  
6. Rozšiřte jednu extrusions. Vyberte jednu z plochy, které jste právě vyňaty a zvolte na panelu nástrojů editoru modelů **přeložit** nástroj a ve stejném směru jako vytlačení přesunout manipulátor překladu.  
  
    ![Straně krychle má další vyňaty. ](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")  
  
7. Triangulovat modelu. Na panelu nástrojů editoru modelů **Upřesnit**, **nástroje**, **Triangulovat**.  
  
8. Vytvoření stříška dům. Přepnout do režimu výběru okrajů výběrem **vyberte Edge** na panelu nástrojů editoru modelů a datové krychle aktivovat, klikněte na tlačítko. Stiskněte a podržte klávesu CTRL při výběru hran, která jsou zobrazena zde:  
  
    ![Hrany, které budou tvořit ve špičce stropu](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")  
  
    Když vyberete okrajů, na panelu nástrojů editoru modelů, zvolte **přeložit** nástroje a poté přesuňte směrem nahoru k vytvoření stříška dům manipulátor překladu.  
  
   Zjednodušené house modelu je dokončeno. Tady je znovu finálního modelu s plochým stínováním použít:  
  
   ![Dokončené modelu zjednodušené house](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
   V dalším kroku můžete tento 3D model použití shaderu. Informace najdete v tématu [postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: modelování 3D terénu](../designers/how-to-model-3-d-terrain.md)   
 [Editor modelů](../designers/model-editor.md)   
 [Návrhář shaderů](../designers/shader-designer.md)



