---
title: Idiaimagedata – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fae8401d7702351e4d51d8b8d485ece87a9478b9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31463010"
---
# <a name="idiaimagedata"></a>IDiaImageData
Zpřístupní podrobnosti o základní umístění a paměť posunutí modulu nebo image.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaImageData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDiaImageData`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Načte umístění ve virtuální paměti modulu vzhledem k aplikaci.|  
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Načte umístění ve virtuální paměti bitové kopie.|  
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Načte paměti umístění, kde by měla být založena bitovou kopii.|  
  
## <a name="remarks"></a>Poznámky  
 Některé datové proudy debug (XDATA, PDATA) obsahovat kopií dat, které jsou také uloženy v bitové kopii. Tyto Streamovat data objektů může být dotázán na `IDiaImageData` rozhraní. Najdete v části "Poznámky pro volající" v tomto tématu podrobnosti.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Získat toto rozhraní vyvoláním `QueryInterface` na [idiaenumdebugstreamdata –](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) objektu. Všimněte si, že ne všechny ladění datové proudy podpory `IDiaImageData` rozhraní. Například aktuálně podporují pouze XDATA a PDATA datové proudy `IDiaImageData` rozhraní.  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá všechny datové proudy debug pro jakýkoli proud, který podporuje `IDiaImageData` rozhraní. Pokud je nalezen datový proud, se zobrazí některé informace o tohoto datového proudu.  
  
```C++  
void ShowImageData(IDiaSession *pSession)  
{  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumDebugStreams> pStreamsList;  
        HRESULT hr;  
  
        hr = pSession->getEnumDebugStreams(&pStreamsList);  
        if (SUCCEEDED(hr))  
        {  
            LONG numStreams = 0;  
            hr = pStreamsList->get_Count(&numStreams);  
            if (SUCCEEDED(hr))  
            {  
                ULONG fetched = 0;  
                for (LONG i = 0; i < numStreams; i++)  
                {  
                    CComPtr<IDiaEnumDebugStreamData> pStream;  
                    hr = pStreamsList->Next(1,&pStream,&fetched);  
                    if (fetched == 1)  
                    {  
                        CComPtr<IDiaImageData> pImageData;  
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),  
                                                     (void **)&pImageData);  
                        if (SUCCEEDED(hr))  
                        {  
                            CComBSTR name;  
                            hr = pStream->get_name(&name);  
                            if (SUCCEEDED(hr))  
                            {  
                                wprintf(L"Stream %s:\n",(BSTR)name);  
                            }  
                            else  
                            {  
                                wprintf(L"Failed to get name of stream\n");  
                            }  
  
                            ULONGLONG imageBase = 0;  
                            if (pImageData->get_imageBase(&imageBase) == S_OK)  
                            {  
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);  
                            }  
  
                            DWORD relVA = 0;  
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)  
                            {  
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);  
                            }  
  
                            ULONGLONG va = 0;  
                            if (pImageData->get_virtualAddress(&va) == S_OK)  
                            {  
                                wprintf(L"  virtual address = 0x%0I64x\n", va);  
                            }  
                        }  
                    }  
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
 [Rozhraní (přístup k rozhraní SDK ladění)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)