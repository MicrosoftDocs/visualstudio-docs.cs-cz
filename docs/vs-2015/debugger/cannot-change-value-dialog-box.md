---
title: Nelze změnit hodnotu dialogového okna | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfe275411346e499312ba51c50a3a2ac3f4ed7d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161651"
---
# <a name="cannot-change-value-dialog-box"></a>Dialogové okno Nelze změnit hodnotu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chyba  
 `The value of this variable cannot be changed``The name` *Název* &#124; `does not exist in the current context` &#124; *různých dalších zprávách*  
  
 Toto okno se zprávou se zobrazí při pokusu o změnu obsahu proměnné na neplatnou hodnotu v okně ladicího programu (automatické, kukátko nebo v oknech Místní hodnoty) nebo v dialogovém okně QuickWatch. Například pokud se pokusíte nastavit hodnotu celočíselné proměnné na řetězec znaků, zobrazí se toto okno se zprávou.  
  
## <a name="solution"></a>Řešení  
 Ujistěte se, že vstup zadaný do okna ladicího programu nebo do dialogového okna QuickWatch představuje platnou hodnotu pro proměnnou, kterou chcete nastavit.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md)
