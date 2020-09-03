---
title: Očekává se VBArray | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09ab257e6c473e2747a24559200e7b1f432d5687
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815276"
---
# <a name="vbarray-expected"></a>Byl očekáván objekt VBArray
Zadali jste objekt, který nebyl Visual Basic safeArray, pokud byla očekávána jedna.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays jsou jen pro čtení a nelze je vytvořit přímo. Argument safeArray je hodnota VBArray a před předáním konstruktoru musí být získána hodnota VBArray `VBArray` . To lze provést pouze načtením hodnoty z existujícího prvku ActiveX nebo jiného objektu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že předáte pouze objekty **VBArray** do konstruktoru **VBArray** .  
  
## <a name="see-also"></a>Viz také  
 [Objekt VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Používání polí](../../javascript/advanced/using-arrays-javascript.md)