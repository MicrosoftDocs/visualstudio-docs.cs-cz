---
title: V regulárním výrazu byl očekáván znak '] ' (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 9af38a5fa754a811416f1a998b90946345f3e4a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576483"
---
# <a name="expected--in-regular-expression-javascript"></a>V regulárním výrazu byl očekáván znak ']' (JavaScript)
Pokusili jste se vytvořit třídu znaků pro porovnávání regulárního výrazu, ale neobsahovala pravou hranatou závorku. Jednotlivé znakové kombinace literálů lze sestavit do tříd znaků jejich umístěním do závorek. Třída znaků odpovídá jakémukoli libovolnému znaku, který obsahuje. Například/[abc]/odpovídá libovolnému z písmen "a", "b" nebo "c".  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Do regulárního výrazu přidejte pravou hranatou závorku.  
  
    > [!NOTE]
    > Pokud chcete, aby se shodovala s jednou závorkou, zastavte ji s zpětným lomítkem-\\ [-proto není interpretována jako speciální znak [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [objektu regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)  
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)