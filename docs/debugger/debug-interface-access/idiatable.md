---
title: Idiatable – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b9b792876e281f73f4df0246734403812a72aea
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056407"
---
# <a name="idiatable"></a>IDiaTable
Vytvoří výčet DIA data zdrojová tabulka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDiaTable`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Načte [IEnumVARIANT rozhraní](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) verzi této enumerátor.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Načte název tabulky.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Načte počet položek v tabulce.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Získá odkaz na konkrétní položku indexu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní implementuje `IEnumUnknown` výčet metod v oboru názvů sestavení Microsoft.VisualStudio.OLE.Interop. `IEnumUnknown` Výčtu rozhraní je mnohem efektivnější pro iterování přes obsahu tabulky než [idiatable::get_count –](../../debugger/debug-interface-access/idiatable-get-count.md) a [idiatable::Item –](../../debugger/debug-interface-access/idiatable-item.md) metody.  
  
 Výklad `IUnknown` rozhraní vrácená z buď `IDiaTable::Item` metoda nebo `Next` – metoda (v oboru názvů sestavení Microsoft.VisualStudio.OLE.Interop) je závislá na typu tabulky. Například pokud `IDiaTable` rozhraní představuje seznam vloženého zdroje `IUnknown` rozhraní mají být získána pro [idiainjectedsource –](../../debugger/debug-interface-access/idiainjectedsource.md) rozhraní.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Získat voláním toto rozhraní [idiaenumtables::Item –](../../debugger/debug-interface-access/idiaenumtables-item.md) nebo [idiaenumtables::Next –](../../debugger/debug-interface-access/idiaenumtables-next.md) metody.  
  
 Následující rozhraní je implementováno s `IDiaTable` rozhraní (to znamená, můžete zadat dotaz `IDiaTable` rozhraní pro jednu z následujících rozhraní):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Příklad  
 První funkce `ShowTableNames`, zobrazuje názvy všechny tabulky v relaci. Funkce second `GetTable`, vyhledá všechny tabulky pro tabulku, která implementuje rozhraní je zadaný. Třetí funkce `UseTable`, ukazuje způsob použití `GetTable` funkce.  
  
> [!NOTE]
>  `CDiaBSTR` je třída, která zabalí `BSTR` a automaticky zpracovává uvolnění řetězec při vytváření instance ocitne mimo rozsah.  
  
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
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (přístup k rozhraní SDK ladění)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumtables –](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables::Item –](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)