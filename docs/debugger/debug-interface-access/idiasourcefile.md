---
title: Idiasourcefile – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a810d43df678d79a57a755681907b8c472fdd82d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464846"
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Představuje zdrojového souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDiaSourceFile`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Načte jednoduché celočíselnou hodnotu klíče, které jsou jedinečné pro tuto bitovou kopii.|  
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Načte název zdrojového souboru.|  
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Načte typ kontrolního součtu.|  
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Získá enumerátor souborech určených ke kompilaci s odkazy na tento soubor čísla řádků.|  
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Načte kontrolní součet bajtů.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Získat voláním toto rozhraní [idiaenumsourcefiles::Item –](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) nebo [idiaenumsourcefiles::Next –](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) metody. Podívejte se na příklad podrobnosti.  
  
## <a name="example"></a>Příklad  
 Tato funkce zobrazí názvy všechny zdrojové soubory, které přispívají k zadané tabulky.  
  
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
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (přístup k rozhraní SDK ladění)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumsourcefiles::Item –](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [Idiaenumsourcefiles::Next –](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [Idialinenumber::get_sourcefile –](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)   
 [Idiasession::findfilebyid –](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [Idiasession::findlines –](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)