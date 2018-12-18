---
title: Vyvolána výjimka která nebyla zachycena | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788766"
---
# <a name="exception-thrown-and-not-caught"></a>Byla vyvolána výjimka, která nebyla zachycena
Můžete zahrnout `throw` příkaz v kódu, ale nebyla uzavřena v rámci **zkuste** bloku, nebo se žádné související **catch** blok k zachycení chyby. Jsou výjimky vyvolány v rámci **zkuste** blokovat, s využitím **throw** příkaz a zachycení mimo **zkuste** blokovat s **catch** příkaz.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Uzavřete kód, který může vyvolat výjimku v **zkuste** blokovat a zajistěte odpovídající **catch** bloku.  
  
-   Ujistěte se, že váš příkaz catch očekává správném tvaru výjimky.  
  
-   Pokud výjimka je znovu vyvolány, ujistěte se, že existuje jiný odpovídající příkaz catch.  
  
## <a name="see-also"></a>Viz také  
 [Error – objekt](../../javascript/reference/error-object-javascript.md)   
 [throw – příkaz](../../javascript/reference/throw-statement-javascript.md)   
 [Try... catch... finally – příkaz](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)