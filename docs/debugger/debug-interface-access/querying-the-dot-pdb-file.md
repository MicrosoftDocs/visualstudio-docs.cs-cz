---
title: Dotazování na. Soubor PDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68efbd59abe1b0aff717a55383f3ac330586164a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738584"
---
# <a name="querying-the-pdb-file"></a>Dotazování na soubor .Pdb
Soubor databáze programu (s příponou. pdb) je binární soubor, který obsahuje informace o typech a symbolickém ladění shromážděné v průběhu kompilování a propojení projektu. Soubor PDBC++ se vytvoří při kompilaci C/programu pomocí **/Zi** nebo **/Zi** nebo [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] programu s možností **/Debug** . Soubory objektů obsahují odkazy na soubor. PDB pro informace o ladění. Další informace o souborech PDB naleznete v tématu [soubory PDB](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Aplikace DIA může pomocí následujících obecných kroků získat podrobnosti o různých symbolech, objektech a datových prvcích v rámci spustitelné bitové kopie.

### <a name="to-query-the-pdb-file"></a>Dotazování na soubor. pdb

1. Získání zdroje dat vytvořením rozhraní [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) .

    ```C++
    CComPtr<IDiaDataSource> pSource;
    hr = CoCreateInstance( CLSID_DiaSource,
                           NULL,
                           CLSCTX_INPROC_SERVER,
                           __uuidof( IDiaDataSource ),
                          (void **) &pSource);

    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    ```

2. Pro načtení informací o ladění zavolejte [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) nebo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

    ```C++
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    ```

3. Voláním [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) otevřete [IDiaSession](../../debugger/debug-interface-access/idiasession.md) pro získání přístupu k ladicím informacím.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Použijte metody v `IDiaSession` k dotazování na symboly ve zdroji dat.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Rozhraní `IDiaEnum*` můžete použít k vytvoření výčtu a prohledání symbolů nebo jiných prvků informací o ladění.

    ```C++
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )
    {
        // Do something with each IDiaTable.
    }
    ```

## <a name="see-also"></a>Viz také:
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
