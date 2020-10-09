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
ms.openlocfilehash: 15b00087cd66b873044b7bafb1bfecf4fc91f8d9
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862392"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Metoda nemá platný prototyp objektu.
Pokusili jste se použít **instanceof** k určení, zda byl objekt odvozen z konkrétní třídy Function, ale předefinovali jste `prototype` vlastnost objektu buď buď `null` , nebo externí typ objektu (nejsou platné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objekty). Externí objekt může být objekt z objektového modelu hostitele (například dokument nebo objekt okna aplikace Internet Explorer) nebo externí objekt COM.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zajistěte, aby `prototype` vlastnost funkce odkazovala na platný [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objekt.  
  
## <a name="see-also"></a>Viz také  
 [Function – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype – vlastnost (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)