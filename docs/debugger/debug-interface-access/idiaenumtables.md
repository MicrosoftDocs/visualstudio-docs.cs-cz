---
description: Vytvoří výčet různých tabulek obsažených ve zdroji dat.
title: IDiaEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 022ab4db45355db86965582c951e67ee41d53bde
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157866"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Vytvoří výčet různých tabulek obsažených ve zdroji dat.

## <a name="syntax"></a>Syntax

```
IDiaEnumTables : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDiaEnumTables` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Načte verzi [rozhraní IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) tohoto enumerátoru.|
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Načte počet tabulek.|
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Načte tabulku prostřednictvím indexu nebo názvu.|
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Načte zadaný počet tabulek v sekvenci výčtu.|
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Přeskočí zadaný počet tabulek ve výčtové sekvenci.|
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|

## <a name="remarks"></a>Poznámky

## <a name="notes-for-callers"></a>Poznámky pro volající
Získejte toto rozhraní voláním metody [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) .

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak získat `IDiaEnumTables` rozhraní z relace. Úplnější příklad použití tabulek naleznete v rozhraní [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    // Do something with table
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
