---
title: IDiaPropertyStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2de57f0d3bd44e4d46f19ee74484380bf0e6f2ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742847"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
Umožňuje číst trvalé vlastnosti sady vlastností DIA.

## <a name="syntax"></a>Syntaxe

```
IDiaPropertyStorage : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
Následující tabulka ukazuje metody `IDiaPropertyStorage`.

|Metoda|Popis|
|------------|-----------------|
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Získá ukazatel na enumerátor pro vlastnosti v rámci této sady.|
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Přečte `BOOL` hodnoty v sadě vlastností.|
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Přečte `BSTR` hodnoty v sadě vlastností.|
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Přečte `DWORD` hodnoty v sadě vlastností.|
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Přečte `LONG` hodnoty v sadě vlastností.|
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Přečte hodnoty vlastností v sadě vlastností.|
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Získá odpovídající názvy řetězců pro dané identifikátory vlastností.|
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Přečte `ULONGLONG` hodnoty v sadě vlastností.|

## <a name="remarks"></a>Poznámky
Každá vlastnost v rámci sady vlastností je identifikována identifikátorem vlastnosti (ID), čtyřmi `ULONG` hodnotou jedinečnou pro tuto sadu. Vlastnosti vystavené prostřednictvím rozhraní `IDiaPropertyStorage` odpovídají vlastnostem, které jsou k dispozici v nadřazeném rozhraní. Například vlastnosti rozhraní [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) lze přistupovat pomocí názvu prostřednictvím rozhraní `IDiaPropertyStorage` (Všimněte si ale, že i když vlastnost může být přístupná, neznamená to, že je vlastnost platná pro určitý objekt `IDiaSymbol`).

## <a name="notes-for-callers"></a>Poznámky pro volající
Získejte toto rozhraní voláním metody `QueryInterface` v jiném rozhraní. Pro rozhraní `IDiaPropertyStorage` lze zadat dotaz na následující rozhraní:

- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

## <a name="example"></a>Příklad
Tento příklad ukazuje funkci, která zobrazí všechny vlastnosti vystavené objektem `IDiaPropertyStorage`. V rozhraní [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) najdete příklad toho, jak se rozhraní `IDiaPropertyStorage` získává z rozhraní [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .

```C++
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)
{
    IEnumSTATPROPSTG* pEnumProps;
    STATPROPSTG       prop;
    DWORD             celt = 1;

    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)
    {
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)
        {
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };
            PROPVARIANT vt = { VT_EMPTY };

            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)
            {
                switch( vt.vt ){
                    case VT_BOOL:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );
                        break;
                    case VT_I2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );
                        break;
                    case VT_UI2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );
                        break;
                    case VT_I4:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );
                        break;
                    case VT_UI4:
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );
                        break;
                    case VT_UI8:
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );
                        break;
                    case VT_BSTR:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );
                        break;
                    case VT_UNKNOWN:
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );
                        break;
                    case VT_SAFEARRAY:
                        break;
                    default:
                       break;
                }
                VariantClear((VARIANTARG*) &vt);
            }
        }
        pEnumProps->Release();
    }
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

Knihovna DLL: Msdia80. dll

## <a name="see-also"></a>Viz také:
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
