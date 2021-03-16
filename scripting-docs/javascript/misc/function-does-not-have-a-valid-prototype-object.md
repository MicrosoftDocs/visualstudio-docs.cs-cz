---
description: Pokusili jste se použít instanceof k určení, zda byl objekt odvozen z konkrétní třídy Function, ale předefinovali jste vlastnost prototypu objektu buď null, nebo externí objekt typu (nejsou platné objekty JavaScriptu).
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
ms.openlocfilehash: 0356ac9ef7c63c77c0cc0dfca623ff24d3de24af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571412"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Metoda nemá platný prototyp objektu.
Pokusili jste se použít **instanceof** k určení, zda byl objekt odvozen z konkrétní třídy Function, ale předefinovali jste `prototype` vlastnost objektu buď buď `null` , nebo externí typ objektu (nejsou platné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objekty). Externí objekt může být objekt z objektového modelu hostitele (například dokument nebo objekt okna aplikace Internet Explorer) nebo externí objekt COM.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zajistěte, aby `prototype` vlastnost funkce odkazovala na platný [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objekt.  
  
## <a name="see-also"></a>Viz také  
 [Function – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype – vlastnost (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
