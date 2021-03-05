---
description: Přistupuje k vloženému zdrojovému kódu uloženému ve zdroji dat DIA.
title: IDiaInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7ea02d5312aea0bdf5e38d5a1f54de546860edfd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148330"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
Přistupuje k vloženému zdrojovému kódu uloženému ve zdroji dat DIA.

## <a name="syntax"></a>Syntax

```
IDiaInjectedSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDiaInjectedSource` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Načte cyklickou kontrolu redundance (CRC) vypočítanou z bajtů zdrojového kódu.|
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Načte počet bajtů kódu.|
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Načte název souboru pro zdroj.|
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Načte název souboru objektu, na který byl zdroj zkompilován.|
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Načte název předaný zdrojovému kódu, který není soubor; To znamená, že kód, který byl vložen.|
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Načte indikátor použité zdrojové komprese.|
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Načte bajty zdrojového kódu.|

## <a name="remarks"></a>Poznámky
Vložený zdroj je text vložený během kompilace. To neznamená, že preprocesor `#include` použitý v jazyce C++.

## <a name="notes-for-callers"></a>Poznámky pro volající
Získejte toto rozhraní voláním metody [IDiaEnumInjectedSources:: Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) nebo [IDiaEnumInjectedSources:: Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) . Příklad získání rozhraní naleznete v rozhraní [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) `IDiaInjectedSource` .

## <a name="example"></a>Příklad
Tento příklad zobrazuje data dostupná z `IDiaInjectedSource` rozhraní. Alternativní přístup pomocí rozhraní [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) naleznete v příkladu v rozhraní [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

```C++
void PrintInjectedSource(IDiaInjectedSource* pSource)
{
    ULONGLONG codeLength      = 0;
    DWORD     crc             = 0;
    DWORD     compressionType = 0;
    BSTR      sourceFilename  = NULL;
    BSTR      objectFilename  = NULL;
    BSTR      virtualFilename = NULL;

    std::cout << "Injected Source:" << std::endl;
    if (pSource != NULL)
    {
        if (pSource->get_crc(&crc) == S_OK &&
            pSource->get_sourceCompression(&compressionType) == S_OK &&
            pSource->get_length(&codeLength) == S_OK)
        {
            wprintf(L"  crc = %lu\n", crc);
            wprintf(L"  code length = %I64u\n",codeLength);
            wprintf(L"  compression type code = %lu\n", compressionType);
        }

        wprintf(L"  source filename: ");
        if (pSource->get_filename(&sourceFilename) == S_OK)
        {
            wprintf(L"%s", sourceFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  object filename: ");
        if (pSource->get_filename(&objectFilename) == S_OK)
        {
            wprintf(L"%s", objectFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  virtual filename: ");
        if (pSource->get_filename(&virtualFilename) == S_OK)
        {
            wprintf(L"%s", virtualFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        SysFreeString(sourceFilename);
        SysFreeString(objectFilename);
        SysFreeString(virtualFilename);
    }
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)
- [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
