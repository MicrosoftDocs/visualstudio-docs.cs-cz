---
title: Funkce nemá platný objekt prototypu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574606"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Metoda nemá platný prototyp objektu.
Pokusili jste se použít **instanceof** k určení, zda byl objekt odvozen z konkrétní třídy Function, ale předefinovali jste vlastnost `prototype` objektu jako buď `null`, nebo externí objekt typu (nejsou platné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objekty). Externí objekt může být objekt z objektového modelu hostitele (například dokument nebo objekt okna aplikace Internet Explorer) nebo externí objekt COM.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zajistěte, aby vlastnost `prototype` funkce odkazovala na platný objekt [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Viz také:  
 [Objekt funkce](../../javascript/reference/function-object-javascript.md)    
 [prototype – vlastnost (Object)](../../javascript/reference/prototype-property-object-javascript.md)