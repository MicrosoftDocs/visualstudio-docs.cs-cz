---
title: Vyvolaná výjimka a nebyla zachycena | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572852"
---
# <a name="exception-thrown-and-not-caught"></a>Byla vyvolána výjimka, která nebyla zachycena
Do kódu jste zahrnuli příkaz `throw`, který však nebyl uzavřený v rámci bloku **Try** , nebo nebyl k zachycení chyby přidružen žádný blok **catch** . Výjimky jsou vyvolány v rámci bloku **Try** pomocí příkazu **throw** a zachyceny mimo blok **Try** pomocí příkazu **catch** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Uzavřete kód, který může vyvolat výjimku v bloku **Try** , a zajistěte, aby byl k dispozici odpovídající blok **catch** .  
  
- Ujistěte se, že váš příkaz catch očekává správný tvar výjimky.  
  
- Pokud je výjimka znovu vyvolána, ujistěte se, že existuje další odpovídající příkaz catch.  
  
## <a name="see-also"></a>Viz také:  
 [Objekt Error](../../javascript/reference/error-object-javascript.md)   
   [příkazu throw](../../javascript/reference/throw-statement-javascript.md)  
 [try...catch...finally – příkaz](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)