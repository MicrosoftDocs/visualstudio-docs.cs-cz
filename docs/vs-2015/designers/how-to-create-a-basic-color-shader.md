---
title: 'Postupy: vytvoření shaderu základní barvy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bcbbb8ede9f30ed1c0340098ffb358cf5715487
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813208"
---
# <a name="how-to-create-a-basic-color-shader"></a>Postupy: Vytvoření shaderu základní barvy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje způsob použití návrháře shaderu a orientovaného grafu shaderu jazyka (DGSL) k vytvoření shaderu plochý barvy. Tento shader nastaví konečnou barvu na konstantní hodnotu barvy RGB.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Odebrání uzlů z grafu  
  
-   Přidání uzlů do grafu  
  
-   Nastavení vlastnosti uzlu  
  
-   Spojující uzly  
  
## <a name="creating-a-flat-color-shader"></a>Vytváření shaderu plochý barvy  
 Můžete implementovat shaderu plochý barvy napsáním hodnota barvy RGB konstanty barvu na barvu závěrečný výstup.  
  
 Než začnete, ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.  
  
#### <a name="to-create-a-flat-color-shader"></a>K vytvoření shaderu plochý barvy  
  
1. Vytvořte shader DGSL pracovat. Informace o tom, jak přidat do projektu DGSL shader naleznete v části Začínáme v [návrháře shaderu](../designers/shader-designer.md).  
  
2. Odstranit **barva bodu** uzlu. Použití **vyberte** nástroj pro výběr **barva bodu** uzel a pak na panelu nabídek zvolte **upravit**, **odstranit**.  
  
3. Přidat **barva konstantní** uzel do grafu. V **nástrojů**v části **konstanty**vyberte **barva konstantní** a přesuňte jej na návrhovou plochu.  
  
4. Zadejte hodnotu barvy pro **barva konstantní** uzlu. Použití **vyberte** nástroj pro výběr **barva konstantní** uzel a pak na **vlastnosti** okno v **výstup** vlastnost, zadejte Hodnota barvy. Oranžová zadejte hodnotu (1.0, 0,5, 0.2, 1.0).  
  
5. Připojte se k konečnou barvu barevnou konstantu. Chcete-li vytvořit připojení, přesuňte **RGB** z terminálu **barva konstantní** uzlu **RGB** z terminálu **konečnou barvu** uzel, a Přesuňte **alfa** z terminálu **barva konstantní** uzlu **alfa** z terminálu **konečnou barvu** uzlu. Tato připojení nastavte konečnou barvu na barvu konstanta definovaná v předchozím kroku.  
  
   Následující obrázek znázorňuje dokončené shader graf a náhled shaderu použitý pro datovou krychli.  
  
> [!NOTE]
>  Na obrázku byl zadán oranžovou barvou lépe demonstruje účinek shaderu.  
  
 ![Graf shaderu a výsledek na 3&#45;D modelu](../designers/media/digit-flat-color-effect.png "číslice paušální barva efekt")  
  
 Určité tvary můžou poskytovat lepší verze Preview pro některé shadery. Další informace o tom, jak shadery v Návrháři shaderu ve verzi preview, najdete v části [návrháře shaderu](../designers/shader-designer.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Postupy: exportování shaderu](../designers/how-to-export-a-shader.md)   
 [Návrhář shaderů](../designers/shader-designer.md)   
 [Uzly návrháře shaderů](../designers/shader-designer-nodes.md)



