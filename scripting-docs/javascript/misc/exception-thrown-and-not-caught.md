---
description: Do kódu jste zahrnuli příkaz throw, který však nebyl uzavřen do bloku try, nebo nebyl k zachycení chyby přidružen žádný blok catch.
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
ms.openlocfilehash: b8abcfced6dfe78dc18f4e31d2bd90d5e5a45a4a
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570632"
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
