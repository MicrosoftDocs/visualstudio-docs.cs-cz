---
title: Dotazování. Soubor PDB | Dokumentace Microsoftu
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
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f82180427155a364ad4240eeede0503e99857f80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793253"
---
# <a name="querying-the-pdb-file"></a>Dotazování na soubor .Pdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Soubor databáze programu (příponou PDB) je binární soubor, který obsahuje typ a symbolické ladicí informace shromážděné v průběhu kompilace a propojování projektu. Soubor PDB je vytvořen při kompilaci programu jazyka C/C++ pomocí **/zi** nebo **/zi** nebo [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], nebo [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] programovat s **/debug** možnost. Objektové soubory obsahují odkazy do souboru PDB pro informace o ladění. Další informace o souborech pdb, naleznete v tématu [soubory PDB](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). DIA aplikace můžete použít následující obecné kroky k získání podrobností o různých symboly, objektů a dat elementů v rámci spustitelnou bitovou kopii.  
  
### <a name="to-query-the-pdb-file"></a>K dotazování na soubor .pdb  
  
1.  Získání zdroje dat tak, že vytvoříte [idiadatasource –](../../debugger/debug-interface-access/idiadatasource.md) rozhraní.  
  
    ```cpp#  
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
  
2.  Volání [idiadatasource::loaddatafrompdb –](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) nebo [idiadatasource::loaddataforexe –](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) načíst informace o ladění.  
  
    ```cpp#  
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
  
3.  Volání [idiadatasource::opensession –](../../debugger/debug-interface-access/idiadatasource-opensession.md) otevřete [idiasession –](../../debugger/debug-interface-access/idiasession.md) se a získat informace o ladění.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Použijte metody v `IDiaSession` dotazu pro symboly ve zdroji dat.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Použití `IDiaEnum*` rozhraní možné vytvořit výčet a procházet symboly nebo další prvky ladicí informace.  
  
    ```cpp#  
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
  
## <a name="see-also"></a>Viz také  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)



