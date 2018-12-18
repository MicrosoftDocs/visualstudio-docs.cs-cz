---
title: Nelze změnit hodnotu – dialogové | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23a6eb8059d9780e3b7343c6a7864896a0c529c6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31456686"
---
# <a name="cannot-change-value-dialog-box"></a>Dialogové okno Nelze změnit hodnotu
## <a name="error"></a>Chyba  
 `The value of this variable cannot be changed` &#124;`The name` *název* `does not exist in the current context` &#124; *různé další zprávy*  
  
 Při pokusu o změnu obsahu proměnné na neplatnou hodnotu v okně ladicí program (automobily, sledovat nebo místní hodnoty – windows) nebo v dialogovém okně QuickWatch, zobrazí se toto okno se zprávou. Například pokud se pokusíte nastavit hodnotu na celé číslo proměnnou na řetězec znaků, zobrazí se toto okno se zprávou.  
  
## <a name="solution"></a>Řešení  
 Zajistěte, aby vstupní zadáte do okna ladicího programu nebo QuickWatch – dialogové představuje platnou hodnotu pro proměnnou, kterou se pokoušíte nastavit.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md)