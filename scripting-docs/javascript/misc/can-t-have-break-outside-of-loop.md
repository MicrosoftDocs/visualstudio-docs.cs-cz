---
title: Můžete&#39;nemá &#39;přerušení&#39; uveden mimo smyčku | Dokumentace společnosti Microsoft
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928552"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Můžete&#39;nemá &#39;přerušení&#39; uveden mimo smyčku
Pokusili jste se použít **přerušení** – klíčové slovo mimo smyčku. **Přerušení** – klíčové slovo se používá k ukončení smyčky nebo `switch` příkazu. Musí být vložen do těla smyčky nebo `switch` příkazu. Nicméně **popisek** můžete postupovat podle break – klíčové slovo.  
  
```  
break labelname;  
```  
  
 Potřebujete jenom s popiskem formu **přerušení** – klíčové slovo při použití vnořených smyčky nebo `switch` příkazy a nutnosti přerušit ze smyčky, která není té nejvíce uvnitř.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, **přerušení** – klíčové slovo se zobrazí uvnitř příkazu nadřazené smyčky nebo přepínače.  
  
## <a name="see-also"></a>Viz také  
 [BREAK – příkaz](../../javascript/reference/break-statement-javascript.md)   
 [Řízení toku programu](../../javascript/controlling-program-flow-javascript.md)   
 [Řešení potíží se skripty](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)