---
title: 'IDiaSession:: findLinesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByLinenum method
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2486d3cbbecad1dee6b171f105d155d95a4e231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855128"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
Určuje čísla řádků kompilantu, že zadané číslo řádku ve zdrojovém souboru leží uvnitř nebo blízko.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLinesByLinenum ( 
    IDiaSymbol*           compiland,
    IDiaSourceFile*       file,
    DWORD                 linenum,
    DWORD                 column,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
`compiland`

pro Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje kompilantu, ve kterém chcete vyhledat čísla řádků. Tento parametr nemůže být `NULL` .

`file`

pro Objekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , který představuje zdrojový soubor pro hledání. Tento parametr nemůže být `NULL` .

`linenum`

pro Určuje číslo řádku založené na jednom čísle.

> [!NOTE]
> Hodnotu nula nelze použít k určení všech řádků (k vyhledání všech řádků použijte metodu [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) ).

`column`

pro Určuje číslo sloupce. K určení všech sloupců použijte nulu. Sloupec je posun bajtů na řádek.

`ppResult`

mimo Vrátí [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objta, který obsahuje seznam čísel řádků, které se načetly.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak otevřít zdrojový soubor, vytvořit výčet compilands, který tento soubor přispěl, a vyhledat čísla řádků ve zdrojovém souboru, kde se spouští jednotlivé kompilantu.

```C++
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)
{
    IDiaEnumSourceFiles* pEnum;
    IDiaSourceFile*      pFile;
    DWORD                celt;

    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file
    {
        IDiaEnumSymbols* pEnumCompilands;
        IDiaSymbol* pCompiland;

        pFile->get_compilands ( &pEnumCompilands );
        // for each compiland
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )
        {
            IDiaEnumLineNumbers* pEnum;
            // Find first compiland closest to line 1 of the file.
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)
            {
                IDiaLineNumber *pLineNumber;
                DWORD lineCount;
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)
                {
                    DWORD lineNum;
                    if (pLineNumber->get_line(&lineNum) == S_OK)
                    {
                        printf("compiland starts in source at line number = %lu\n",lineNum);
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Viz také
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
