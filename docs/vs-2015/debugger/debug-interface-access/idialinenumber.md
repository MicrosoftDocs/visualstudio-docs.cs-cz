---
title: Idialinenumber – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber interface
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08ab059a5489a648927677bc95a37bdbabc92440
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777796"
---
# <a name="idialinenumber"></a>IDiaLineNumber
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přístupy informace, které popisují proces mapování z bloku bajty bitové kopie textu na číslo řádku zdrojového souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaLineNumber : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDiaLineNumber`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaLineNumber::get_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Získá odkaz na symbol kompilace, které přispěly bajtů text obrázku.|  
|[IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|Získá odkaz na objekt zdrojového souboru.|  
|[IDiaLineNumber::get_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|Získá číslo řádku ve zdrojovém souboru.|  
|[IDiaLineNumber::get_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Získá číslo řádku založen na jedničce zdroj, kde končí příkazem nebo výrazem.|  
|[IDiaLineNumber::get_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Získá číslo sloupce, kde začíná výraz nebo příkaz.|  
|[IDiaLineNumber::get_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Získá číslo sloupce, kde končí výraz nebo příkaz.|  
|[IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Načte části součástí adresa paměti, kde začíná bloku.|  
|[IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Načte posunu součástí adresa paměti, kde začíná bloku.|  
|[IDiaLineNumber::get_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Načte obrázek relativní virtuální adresu (RVA) bloku.|  
|[IDiaLineNumber::get_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Načte virtuální adresy (VA) bloku.|  
|[IDiaLineNumber::get_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|Získá počet bajtů v bloku.|  
|[IDiaLineNumber::get_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Načte identifikátor jedinečný zdrojového souboru pro zdrojový soubor, který uživatel tento řádek.|  
|[IDiaLineNumber::get_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|Získá příznak označující, že informace o tomto řádku popisuje počátku příkazu ve zdrojovém programu.|  
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Získá jedinečný identifikátor souboru pro kompilaci, která uživatel tento řádek.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Získat voláním toto rozhraní [idiaenumlinenumbers::Item –](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) nebo [idiaenumlinenumbers::Next –](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) metody.  
  
## <a name="example"></a>Příklad  
 Následující funkce zobrazuje čísla řádků ve funkci použít (představované `pSymbol`).  
  
```cpp#  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD     isect  = 0;  
    DWORD     offset = 0;  
  
    pSymbol->get_addressSection( &isect );  
    pSymbol->get_addressOffset( &offset );  
    pSymbol->get_length( &length );  
    if ( isect != 0 && length > 0 )  
    {  
        CComPtr< IDiaEnumLineNumbers > pLines;  
        if ( SUCCEEDED( pSession->findLinesByAddr(  
                                      isect,  
                                      offset,  
                                      static_cast<DWORD>( length ),  
                                      &pLines)  
                      )  
           )  
        {  
            CComPtr< IDiaLineNumber > pLine;  
            DWORD celt      = 0;  
            bool  firstLine = true;  
  
            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&  
                    celt == 1 )  
            {  
                DWORD offset;  
                DWORD seg;  
                DWORD linenum;  
                CComPtr< IDiaSymbol >     pComp;  
                CComPtr< IDiaSourceFile > pSrc;  
  
                pLine->get_compiland( &pComp );  
                pLine->get_sourceFile( &pSrc );  
                pLine->get_addressSection( &seg );  
                pLine->get_addressOffset( &offset );  
                pLine->get_lineNumber( &linenum );  
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );  
                pLine = NULL;  
                if ( firstLine )  
                {  
                    // sanity check  
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;  
                    if ( SUCCEEDED( pSession->findLinesByLinenum(  
                                                  pComp,  
                                                  pSrc,  
                                                  linenum,  
                                                  0,  
                                                  &pLinesByLineNum)  
                                  )  
                       )  
                    {  
                        CComPtr< IDiaLineNumber > pLine;  
                        DWORD celt;  
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&  
                                celt == 1 )  
                        {  
                            DWORD offset;  
                            DWORD seg;  
                            DWORD linenum;  
  
                            pLine->get_addressSection( &seg );  
                            pLine->get_addressOffset( &offset );  
                            pLine->get_lineNumber( &linenum );  
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );  
                            pLine = NULL;  
                       }  
                    }  
                    firstLine = false;  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumlinenumbers –](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [Idiaenumlinenumbers::Item –](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)   
 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)



