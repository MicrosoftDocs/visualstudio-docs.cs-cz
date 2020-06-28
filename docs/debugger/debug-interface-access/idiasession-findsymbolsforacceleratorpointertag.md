---
title: 'IDiaSession:: findSymbolsForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a58795531d2537fc299e6e15554561129f0da0e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465501"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Vrátí výčet symbolů pro proměnnou, na kterou je zadaná hodnota značky odpovídat ve funkci zástupného kódu nadřazeného akcelerátoru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

pro IDiaSymbol, který odpovídá funkci pro vyhledávání zástupné procedury akcelerátoru.

 `tagValue`

pro Hodnota značky ukazatele.

 `ppResult`

mimo Ukazatel na `IDiaEnumSymbols` ukazatel rozhraní, který je inicializován s výsledkem.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)