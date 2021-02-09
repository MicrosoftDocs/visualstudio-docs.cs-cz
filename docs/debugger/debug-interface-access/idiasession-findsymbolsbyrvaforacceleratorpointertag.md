---
title: 'IDiaSession:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdc8d94abf02b1e090dd9d4c78bdded88fda7bab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864108"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
S ohledem na odpovídající hodnotu značky vrátí tato metoda výčet symbolů, které jsou obsaženy v zadané relativní virtuální adrese v zadané nadřazené funkci akcelerátoru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

pro Ta `IDiaSymbol` , která odpovídá funkci pro vyhledávání zástupné procedury akcelerátoru.

 `tagValue`

pro Hodnota značky ukazatele.

 `rva`

pro Relativní virtuální adresa.

 `ppResult`

mimo Ukazatel na `IDiaEnumSymbols` ukazatel rozhraní, který je inicializován s výsledkem.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tuto metodu volejte pouze na `IDiaSymbol` rozhraní, které odpovídá funkci akcelerátoru zástupné procedury.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)