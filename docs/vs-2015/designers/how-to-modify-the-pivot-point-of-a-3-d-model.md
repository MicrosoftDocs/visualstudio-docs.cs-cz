---
title: 'Postupy: Změna bodu otáčení 3D modelu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: beba04bab85b3fd09aafb195039ad6e34106e293
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850526"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Postupy: Změna bodu otáčení 3D modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje způsob použití Editoru modelů změnit *bodu otáčení* 3D modelu. Bod otáčení je bod v prostoru, který definuje střed matematické objektu pro rotace a změnu měřítka.  
  
 Tento dokument ukazuje, tato aktivita:  
  
-   Změna bodu otáčení objektu  
  
## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Změna bodu otáčení 3D modelu  
 Původ na 3D model můžete upravit tak, že upravíte jejich bodem otáčení.  
  
 Ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.  
  
#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>Chcete-li změna bodu otáčení 3D modelu  
  
1. Začátek s existující 3D modelu, jako je ten, který je popsaný v [postupy: vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md).  
  
2. Zadejte režim pivotu. Na **režim editoru modelů** nástrojů, zvolte **režim Pivotu** tlačítko aktivovat režim pivotu. Pole se zobrazí kolem **režim Pivotu** tlačítko k označení, že Editor modelů je nyní v režim pivotu. V režim pivotu ovlivňují operace, jako jsou překladu bodu otáčení objektu namísto strukturu objektů v prostoru světa.  
  
3. Změna bodu otáčení objektu. V **vyberte** režimu, vyberte objekt a pak na **prohlížeč modelu** nástrojů, zvolte **přeložit** nástroj. Na návrhové ploše se objeví pole, které představuje bodu otáčení. Přesuňte pole a změna bodu otáčení objektu.  
  
    Díky přesunu do pole, můžete přesunout bodu otáčení v všechny tři dimenze. K překladu bodu otáčení jednu osu přemístěte tuto šipku, která odpovídá na této osy. Pole a šipky změní na žlutou barvou pro označení toho osy, která jsou ovlivněná překlad.  
  
    Bod otáčení můžete také zadat pomocí **posunutí pozice Pivotu** vlastnost **vlastnosti** okna.  
  
   > [!TIP]
   >  Otočení objektu, můžete zobrazit vliv nového bodu otáčení. Otočení, použijte **otočit** nástroje nebo změnit **otočení** vlastnost.  
  
   Tady je model, který má bod upravené pivot:  
  
   ![Model, který má bod upravené otáčení domu](../designers/media/digit-modified-model.png "číslice upravit Model")  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření základního 3D modelu](../designers/how-to-create-a-basic-3-d-model.md)   
 [Editor modelů](../designers/model-editor.md)



