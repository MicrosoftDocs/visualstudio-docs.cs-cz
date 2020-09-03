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
ms.openlocfilehash: 44f207d2e32a7ca79ee0d5851a80261c5da9743d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814587"
---
# <a name="exception-thrown-and-not-caught"></a>Byla vyvolána výjimka, která nebyla zachycena
Do kódu jste zahrnuli `throw` příkaz, který ale není uzavřený v rámci bloku **Try** , nebo k ní nebyl přidružen žádný blok **catch** k zachycení této chyby. Výjimky jsou vyvolány v rámci bloku **Try** pomocí příkazu **throw** a zachyceny mimo blok **Try** pomocí příkazu **catch** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Uzavřete kód, který může vyvolat výjimku v bloku **Try** , a zajistěte, aby byl k dispozici odpovídající blok **catch** .  
  
- Ujistěte se, že váš příkaz catch očekává správný tvar výjimky.  
  
- Pokud je výjimka znovu vyvolána, ujistěte se, že existuje další odpovídající příkaz catch.  
  
## <a name="see-also"></a>Viz také  
 [Error – objekt](../../javascript/reference/error-object-javascript.md)   
 [throw – příkaz](../../javascript/reference/throw-statement-javascript.md)   
 [zkusit... zachytit... Finally – příkaz](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)