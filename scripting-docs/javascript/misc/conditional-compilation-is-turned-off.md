---
description: Pokusili jste se použít proměnnou podmíněné kompilace bez prvotního zapnutí podmíněné kompilace.
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
ms.openlocfilehash: ccda9769597d6a981a9277d2b1e1f54b73d6ae18
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571425"
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
  
## <a name="see-also"></a>Viz také  
 [Podmíněná kompilace](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Proměnné podmíněné kompilace](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on Vydá](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if Vydá](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set Vydá](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)
