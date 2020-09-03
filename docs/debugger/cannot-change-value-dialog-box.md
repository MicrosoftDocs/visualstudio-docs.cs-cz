---
title: Nelze změnit hodnotu dialogového okna | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97f057edefefd590c37b49d709ecf8a6e029b905
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745745"
---
# <a name="cannot-change-value-dialog-box"></a>Dialogové okno Nelze změnit hodnotu
## <a name="error"></a>Chyba
 `The value of this variable cannot be changed``The name` *Název* &#124; `does not exist in the current context` &#124; *různých dalších zprávách*

 Toto okno se zprávou se zobrazí při pokusu o změnu obsahu proměnné na neplatnou hodnotu v okně ladicího programu (automatické, kukátko nebo v oknech Místní hodnoty) nebo v dialogovém okně QuickWatch. Například pokud se pokusíte nastavit hodnotu celočíselné proměnné na řetězec znaků, zobrazí se toto okno se zprávou.

## <a name="solution"></a>Řešení
 Ujistěte se, že vstup zadaný do okna ladicího programu nebo do dialogového okna QuickWatch představuje platnou hodnotu pro proměnnou, kterou chcete nastavit.

## <a name="see-also"></a>Viz také

- [Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md)