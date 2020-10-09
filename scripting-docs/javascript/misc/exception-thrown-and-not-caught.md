---
title: Vyvolaná výjimka a nebyla zachycena | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862761"
---
# <a name="exception-thrown-and-not-caught"></a>Byla vyvolána výjimka, která nebyla zachycena
Do kódu jste zahrnuli `throw` příkaz, který ale není uzavřený v rámci bloku **Try** , nebo k ní nebyl přidružen žádný blok **catch** k zachycení této chyby. Výjimky jsou vyvolány v rámci bloku **Try** pomocí příkazu **throw** a zachyceny mimo blok **Try** pomocí příkazu **catch** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Uzavřete kód, který může vyvolat výjimku v bloku **Try** , a zajistěte, aby byl k dispozici odpovídající blok **catch** .  
  
- Ujistěte se, že váš příkaz catch očekává správný tvar výjimky.  
  
- Pokud je výjimka znovu vyvolána, ujistěte se, že existuje další odpovídající příkaz catch.  
  
## <a name="see-also"></a>Viz také  
 [Error – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [zkusit... zachytit... Finally – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)