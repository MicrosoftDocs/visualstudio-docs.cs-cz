---
title: Očekává se VBArray | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 467a6ec6ca45f2ea0411e0266163ca23a9e3d594
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572505"
---
# <a name="vbarray-expected"></a>Byl očekáván objekt VBArray
Zadali jste objekt, který nebyl Visual Basic safeArray, pokud byla očekávána jedna.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays jsou jen pro čtení a nelze je vytvořit přímo. Argument safeArray je hodnota VBArray a před předáním konstruktoru `VBArray` musí získat hodnotu VBArray. To lze provést pouze načtením hodnoty z existujícího prvku ActiveX nebo jiného objektu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že předáte pouze objekty **VBArray** do konstruktoru **VBArray** .  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [objektu VBArray](../../javascript/reference/vbarray-object-javascript.md)  
 [Používání polí](../../javascript/advanced/using-arrays-javascript.md)