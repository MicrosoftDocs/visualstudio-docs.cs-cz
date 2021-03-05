---
description: Představuje zdrojový soubor.
title: IDiaSourceFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2695fdb267d328b596673ed08f5dc0be63cfaeaa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147581"
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Představuje zdrojový soubor.

## <a name="syntax"></a>Syntax

```
IDiaSourceFile : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDiaSourceFile` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Načte jednoduchou celočíselnou hodnotu klíče, která je pro tento obrázek jedinečná.|
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Načte název zdrojového souboru.|
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Načte typ kontrolního součtu.|
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Načte enumerátor compilands s čísly řádků odkazujícími na tento soubor.|
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Načte bajty kontrolního součtu.|

## <a name="remarks"></a>Poznámky

## <a name="notes-for-callers"></a>Poznámky pro volající
Získejte toto rozhraní voláním metody [IDiaEnumSourceFiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) nebo [IDiaEnumSourceFiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) . Podrobnosti najdete v příkladu.

## <a name="example"></a>Příklad
Tato funkce zobrazí názvy všech zdrojových souborů, které přispívají k zadané tabulce.

```C++
void ShowSourceFiles(IDiaTable *pTable)
{
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSourceFiles ),
                               (void**)&pSourceFiles )
                  )
       )
    {
        CComPtr<IDiaSourceFile> pSourceFile;
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR fileName;
            if ( pSourceFile->get_fileName( &fileName) == S_OK )
            {
                printf( "file name: %ws\n", fileName );
            }
            pSourceFile = NULL;
        }
    }
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)
- [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)
- [IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)
- [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
