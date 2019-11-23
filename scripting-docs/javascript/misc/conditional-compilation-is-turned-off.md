---
title: Podmíněná kompilace je vypnutá | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572939"
---
# <a name="conditional-compilation-is-turned-off"></a>Podmíněná kompilace je vypnutá
Pokusili jste se použít proměnnou podmíněné kompilace bez prvotního zapnutí podmíněné kompilace. Zapnutí podmíněné kompilace instruuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kompilátor, aby interpretoval identifikátory začínající znakem @ jako s proměnnými podmíněné kompilace. Provedete to tak, že spustíte podmíněný kód pomocí příkazu:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte následující příkaz na začátek podmíněného kódu:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Viz také:  
   [podmíněné kompilace](../../javascript/advanced/conditional-compilation-javascript.md)  
   [proměnných podmíněné kompilace](../../javascript/advanced/conditional-compilation-variables-javascript.md)  
 [příkaz@cc_on](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [příkaz@if](../../javascript/reference/at-if-statement-javascript.md)   
 [@set – příkaz](../../javascript/reference/at-set-statement-javascript.md)