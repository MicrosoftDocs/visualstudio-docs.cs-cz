---
title: Byl očekáván objekt VBArray | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844143"
---
# <a name="vbarray-expected"></a>Byl očekáván objekt VBArray
Můžete zadat objekt, který nebyl safeArray jazyka Visual Basic, když byl očekáván jeden.  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays jsou jen pro čtení a nelze vytvořit přímo. Argument pole safeArray je hodnota VBArray a musíte již mít vyřízené VBArray hodnotu před předáním `VBArray` konstruktoru. To lze provést pouze načtením hodnoty z existující ActiveX nebo jiného objektu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte předání pouze **VBArray** objektů **VBArray** konstruktoru.  
  
## <a name="see-also"></a>Viz také  
 [VBArray – objekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Používání polí](../../javascript/advanced/using-arrays-javascript.md)