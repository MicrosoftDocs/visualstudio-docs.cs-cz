---
title: Byl očekáván &#39;)&#39; v regulárním výrazu (JavaScript) | Dokumentace Microsoftu
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
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d1075a41d2b97d10166b1372e8df3a93dd9d8e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279125"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Byl očekáván &#39;)&#39; v regulárním výrazu (JavaScript)
Proběhl pokus o vytvoření zachycení regulárních výrazů, kontrolní výraz nebo skupiny, ale neobsahuje pravou závorku. Závorky mají několik účely v regulárních výrazech. Především se používají k zachycení dílčí výrazy, zadejte kontrolních výrazů nebo seskupení vzory tak, aby položky lze považovat za jednu jednotku podle *, +,?, a tak dále.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidáte úplně vpravo pravými závorkami.  
  
    > [!NOTE]
    >  Pokud chcete najít jeden závorky, před něj zpětné lomítko - \\(– tak, aby nebyl interpretován jako znak zvláštní podle [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)