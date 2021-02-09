---
title: 'IDiaStackWalkHelper:: symbolForVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6944e2736fb418581306fa25b4541471335488f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854708"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Načte symbol, který obsahuje zadanou virtuální adresu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symbolForVA( 
   ULONGLONG     va,
   IDiaSymbol**  ppSymbol
);
```

#### <a name="parameters"></a>Parametry
 `va`

pro Virtuální adresa, která je obsažena v požadovaném symbolu. Symbol musí být `SymTagFunctionType` (hodnota z výčtu [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).

 `ppSymbol`

mimo Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje symbol na zadané adrese.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)