---
title: Byl očekáván typ catch | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573425"
---
# <a name="expected-catch"></a>Byl očekáván příkaz 'catch'
Použili jste blok **Try** zpracování výjimek, ale nezapsali jste přidružený příkaz **catch** . Mechanismus zpracování výjimek vyžaduje, aby kód, který může selhat, a kód, který by neměl být proveden, pokud dojde k výjimce, je zabalen do bloku **Try** . Výjimky jsou vyvolány v rámci bloku **Try** pomocí příkazu **throw** a zachyceny mimo blok **Try** s jedním nebo více příkazy **catch** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte přidružený blok **catch** .  
  
- Zkuste místo bloku **catch** použít blok **finally** .  
  
## <a name="see-also"></a>Viz také:  
 [zkusit... zachytit... Příkaz finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error – objekt](../../javascript/reference/error-object-javascript.md)