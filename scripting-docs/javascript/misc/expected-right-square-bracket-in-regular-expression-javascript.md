---
title: Byl očekáván &#39;]&#39; v regulárním výrazu (JavaScript) | Dokumentace Microsoftu
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ef929ba309f0b496e72f3cf740daf6970d08fb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283714"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Byl očekáván &#39;]&#39; v regulárním výrazu (JavaScript)
Se pokusil vytvořit třídu znaků shody regulárního výrazu, ale neobsahuje pravou závorku. Jednotlivý znak literálu kombinace lze sestavit do třídy znaků tak, že je umístíte do hranatých závorek. Třída znaků odpovídá jeden libovolný znak, který ji obsahuje. Například / [abc] / odpovídá jakémukoli znaku z písmen "a", "b" nebo "c".  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidejte pravou závorku regulárnímu výrazu.  
  
    > [!NOTE]
    >  Pokud chcete odpovídat jedné závorky, před něj zpětné lomítko - \\[– aby nebyl interpretován jako znak zvláštní podle [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)