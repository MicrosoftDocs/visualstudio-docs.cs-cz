---
title: Funkce nemá platný objekt prototypu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca6f13620bb486cf1663bd5bef9a9a93b2c8a480
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817356"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Metoda nemá platný prototyp objektu.
Pokusili jste se použít **instanceof** k určení, zda byl objekt odvozen z konkrétní třídy Function, ale předefinovali jste `prototype` vlastnost objektu buď buď `null` , nebo externí typ objektu (nejsou platné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objekty). Externí objekt může být objekt z objektového modelu hostitele (například dokument nebo objekt okna aplikace Internet Explorer) nebo externí objekt COM.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zajistěte, aby `prototype` vlastnost funkce odkazovala na platný [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objekt.  
  
## <a name="see-also"></a>Viz také:  
 [Function – objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype – vlastnost (Object)](../../javascript/reference/prototype-property-object-javascript.md)