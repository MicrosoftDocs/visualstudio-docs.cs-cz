---
title: Idiainjectedsource – | Dokumentace Microsoftu
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
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8c8014d91f020bec5c9ab29c427fa78f7092b0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756638"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přístupy vloženy zdrojového kódu, které jsou uložené ve zdroji dat DIA.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDiaInjectedSource`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Načte kontrolu cyklické redundance (CRC) počítají na základě bajtů zdrojového kódu.|  
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Získá počet bajtů kódu.|  
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Načte název souboru zdroje.|  
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Načte název souboru objektů, ke kterému byl zkompilován zdroji.|  
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Načte název použitý pro kód nesouborového zdroje; To znamená, že kód, který se vloží.|  
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Načte ukazatel zdroj komprese používá.|  
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Získá počet bajtů zdrojového kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Vložené zdroje je text, který se vloží během kompilace. To neznamená, že preprocesor `#include` použít v jazyce C++.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Získat voláním toto rozhraní [idiaenuminjectedsources::Item –](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) nebo [idiaenuminjectedsources::Next –](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) metody. Zobrazit [idiaenuminjectedsources –](../../debugger/debug-interface-access/idiaenuminjectedsources.md) rozhraní příklad se dá získat `IDiaInjectedSource` rozhraní.  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje data k dispozici `IDiaInjectedSource` rozhraní. Alternativní způsob použití [idiapropertystorage –](../../debugger/debug-interface-access/idiapropertystorage.md) rozhraní, podívejte se na příklad v [idiaenuminjectedsources –](../../debugger/debug-interface-access/idiaenuminjectedsources.md) rozhraní.  
  
```cpp#  
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
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenuminjectedsources::Item –](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [Idiaenuminjectedsources::Next –](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



