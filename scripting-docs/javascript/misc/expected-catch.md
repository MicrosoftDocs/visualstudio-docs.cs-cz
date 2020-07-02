---
title: Byl očekáván typ catch | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9950573e7bbeefe3594d77df2ae41c12f77ed3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816681"
---
# <a name="expected-catch"></a>Byl očekáván příkaz 'catch'
Použili jste blok **Try** zpracování výjimek, ale nezapsali jste přidružený příkaz **catch** . Mechanismus zpracování výjimek vyžaduje, aby kód, který může selhat, a kód, který by neměl být proveden, pokud dojde k výjimce, je zabalen do bloku **Try** . Výjimky jsou vyvolány v rámci bloku **Try** pomocí příkazu **throw** a zachyceny mimo blok **Try** s jedním nebo více příkazy **catch** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte přidružený blok **catch** .  
  
- Zkuste místo bloku **catch** použít blok **finally** .  
  
## <a name="see-also"></a>Viz také:  
 [zkusit... zachytit... Finally – příkaz](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error – objekt](../../javascript/reference/error-object-javascript.md)