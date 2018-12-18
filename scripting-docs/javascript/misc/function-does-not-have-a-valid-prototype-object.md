---
title: Funkce nemá platný prototyp objektu. | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788730"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Metoda nemá platný prototyp objektu.
Jste se pokusili použít **instanceof** k určení, pokud byl objekt odvozování od třídy určitou funkci, ale předefinovat objektu `prototype` vlastnost jako buď `null`, nebo typ externího objektu (obě není platný [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objektů). Externí objekt může být objekt v objektovém modelu hostitele (například dokument aplikace Internet Explorer nebo objektu okna) nebo externího objektu COM.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, funkce `prototype` vlastnost odkazuje na platný [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objektu.  
  
## <a name="see-also"></a>Viz také  
 [Function – objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype – vlastnost (Object)](../../javascript/reference/prototype-property-object-javascript.md)