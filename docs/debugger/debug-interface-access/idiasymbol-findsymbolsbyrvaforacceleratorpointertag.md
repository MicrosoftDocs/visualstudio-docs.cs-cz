---
title: 'IDiaSymbol:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5f4fc54ee9192877c7c59f32a4f8fe41ff063c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854624"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
S ohledem na odpovídající hodnotu značky vrátí tato metoda výčet symbolů, které jsou obsaženy v této zástupné funkci v zadané relativní virtuální adrese.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametry
 `tagValue`

pro Hodnota značky ukazatele, pro kterou jsou nalezeny záznamy symbolů pointee.

 `rva`

pro Adresa RVA, která slouží k filtrování symbolů odpovídajících proměnné pointee se zadanou hodnotou značky.

 `ppResult`

mimo Ukazatel na `IDiaEnumSymbols` ukazatel rozhraní, který je inicializován s výsledkem.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="remarks"></a>Poznámky
 Tuto metodu volejte pouze na `IDiaSymbol` rozhraní, které odpovídá funkci akcelerátoru zástupné procedury.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)