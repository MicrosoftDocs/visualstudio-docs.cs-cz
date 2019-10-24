---
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7a573eb92d7c51079b0a7e97067abd155ae4fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738702"
---
# <a name="idiatable"></a>IDiaTable
Vytvoří výčet tabulky zdroje dat DIA.

## <a name="syntax"></a>Syntaxe

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
Následující tabulka ukazuje metody `IDiaTable`.

|Metoda|Popis|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Načte verzi [rozhraní IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) tohoto enumerátoru.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Načte název tabulky.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Načte počet položek v tabulce.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Načte odkaz na konkrétní index záznamu.|

## <a name="remarks"></a>Poznámky
Toto rozhraní implementuje metody výčtu `IEnumUnknown` v oboru názvů Microsoft. VisualStudio. OLE. Interop. Rozhraní výčtu `IEnumUnknown` je mnohem efektivnější pro iteraci nad obsahem tabulky, než metody [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) a [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) .

Výklad rozhraní `IUnknown` vráceného metodou `IDiaTable::Item` nebo metodou `Next` (v oboru názvů Microsoft. VisualStudio. OLE. Interop) závisí na typu tabulky. Například pokud rozhraní `IDiaTable` představuje seznam vložených zdrojů, pro rozhraní [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) by se mělo zadat dotaz `IUnknown` rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
Získejte toto rozhraní voláním metody [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) nebo [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .

Následující rozhraní jsou implementována s rozhraním `IDiaTable` (to znamená, že můžete zadat dotaz na `IDiaTable` rozhraní pro jedno z následujících rozhraní):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Příklad
První funkce, `ShowTableNames`, zobrazí názvy všech tabulek v relaci. Druhá funkce, `GetTable`, vyhledá všechny tabulky pro tabulku, která implementuje zadané rozhraní. Třetí funkce `UseTable` ukazuje, jak používat funkci `GetTable`.

> [!NOTE]
> `CDiaBSTR` je třída, která obaluje `BSTR` a automaticky zpracovává uvolnění řetězce v případě, že instance přechází z rozsahu.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

Knihovna DLL: Msdia80. dll

## <a name="see-also"></a>Viz také:
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
