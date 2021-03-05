---
description: Vytvoří výčet tabulky zdroje dat DIA.
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3b93dad0baef701a7d417993080d6511373454a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161653"
---
# <a name="idiatable"></a>IDiaTable
Vytvoří výčet tabulky zdroje dat DIA.

## <a name="syntax"></a>Syntax

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDiaTable` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Načte verzi [rozhraní IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) tohoto enumerátoru.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Načte název tabulky.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Načte počet položek v tabulce.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Načte odkaz na konkrétní index záznamu.|

## <a name="remarks"></a>Poznámky
Toto rozhraní implementuje `IEnumUnknown` metody výčtu v oboru názvů Microsoft. VisualStudio. OLE. Interop. `IEnumUnknown`Rozhraní výčtu je mnohem efektivnější pro iteraci nad obsahem tabulky, než metody [IDiaTable:: Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) a [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) .

Interpretace `IUnknown` rozhraní vráceného buď `IDiaTable::Item` metodou nebo `Next` metodou (v oboru názvů Microsoft. VisualStudio. OLE. Interop) závisí na typu tabulky. Například pokud `IDiaTable` rozhraní představuje seznam vložených zdrojů, `IUnknown` pro rozhraní [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) by se mělo zadat dotaz na rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
Získejte toto rozhraní voláním metody [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) nebo [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .

Následující rozhraní jsou implementována s `IDiaTable` rozhraním (to znamená, že můžete zadat dotaz na `IDiaTable` rozhraní pro jedno z následujících rozhraní):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Příklad
První funkce `ShowTableNames` zobrazí názvy všech tabulek v relaci. Druhá funkce, `GetTable` , vyhledá všechny tabulky pro tabulku, která implementuje zadané rozhraní. Třetí funkce, `UseTable` , ukazuje, jak používat `GetTable` funkci.

> [!NOTE]
> `CDiaBSTR` je třída, která obaluje `BSTR` a automaticky zpracovává uvolnění řetězce, když se instance vychází z rozsahu.

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

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
