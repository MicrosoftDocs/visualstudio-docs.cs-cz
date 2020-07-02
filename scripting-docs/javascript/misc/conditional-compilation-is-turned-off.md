---
title: Podmíněná kompilace je vypnutá | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da272529768f3227ce6e0ee3e0ebbf086140dd15
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816121"
---
# <a name="conditional-compilation-is-turned-off"></a>Podmíněná kompilace je vypnutá
Pokusili jste se použít proměnnou podmíněné kompilace bez prvotního zapnutí podmíněné kompilace. Zapnutí podmíněné kompilace instruuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kompilátor, aby interpretoval identifikátory začínající na @ jako proměnné podmíněné kompilace. Provedete to tak, že spustíte podmíněný kód pomocí příkazu:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte následující příkaz na začátek podmíněného kódu:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Viz také:  
 [Podmíněná kompilace](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Proměnné podmíněné kompilace](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onVydá](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@ifVydá](../../javascript/reference/at-if-statement-javascript.md)   
 [@setVydá](../../javascript/reference/at-set-statement-javascript.md)