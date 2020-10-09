---
title: V regulárním výrazu byl očekáván znak '] ' (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31d1ebd30ba5e793a1c52c00d8b58603bdaa9a75
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862328"
---
# <a name="expected--in-regular-expression-javascript"></a>V regulárním výrazu byl očekáván znak ']' (JavaScript)
Pokusili jste se vytvořit třídu znaků pro porovnávání regulárního výrazu, ale neobsahovala pravou hranatou závorku. Jednotlivé znakové kombinace literálů lze sestavit do tříd znaků jejich umístěním do závorek. Třída znaků odpovídá jakémukoli libovolnému znaku, který obsahuje. Například/[abc]/odpovídá libovolnému z písmen "a", "b" nebo "c".  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Do regulárního výrazu přidejte pravou hranatou závorku.  
  
    > [!NOTE]
    > Pokud chcete, aby se shodovala s jednou hranatou závorkou, vystavte ji zpětným lomítkem- \\ [-proto není interpretována jako speciální znak [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntaxe regulárního výrazu (JavaScript)](/previous-versions/1400241x(v=vs.100))