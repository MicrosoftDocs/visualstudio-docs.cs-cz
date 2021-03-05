---
description: Vytvoří výčet různých segmentů obsažených ve zdroji dat.
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab7d5129ac1f2a6cf256bf7cbbeb0ea78d26e506
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148827"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Vytvoří výčet různých segmentů obsažených ve zdroji dat.

## <a name="syntax"></a>Syntax

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDiaEnumSegments` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Načte verzi [rozhraní IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) tohoto enumerátoru.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Načte počet segmentů.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Načte segment prostřednictvím indexu.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Načte zadaný počet segmentů v sekvenci výčtu.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Přeskočí zadaný počet segmentů v sekvenci výčtu.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|

## <a name="remarks"></a>Poznámky

## <a name="notes-for-callers"></a>Poznámky pro volající
Získejte toto rozhraní voláním `QueryInterface` metody pro objekt [IDiaTable](../../debugger/debug-interface-access/idiatable.md) . Podrobnosti najdete v příkladu.

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak získat `IDiaEnumSections` rozhraní z tabulky. Úplnější příklad použití segmentů naleznete v rozhraní [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) .

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
