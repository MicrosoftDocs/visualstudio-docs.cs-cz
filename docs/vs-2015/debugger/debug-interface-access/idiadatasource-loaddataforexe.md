---
title: 'IDiaDataSource:: loadDataForExe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 623cdd74b086a46bc52c0f0534953ae6e11168ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547374"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře a připraví ladicí data přidružená k souboru. exe/. dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 spouštěcí  
 pro Cesta k souboru. exe nebo. dll.  
  
 searchPath  
 pro Alternativní cesta pro hledání dat ladění  
  
 pCallback  
 pro `IUnknown` Rozhraní pro objekt, který podporuje rozhraní zpětného volání ladění, jako je například [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)nebo rozhraní [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Následující tabulka uvádí některé z možných kódů chyb pro tuto metodu.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Soubor se nepovedlo otevřít, nebo má neplatný formát.|  
|E_PDB_FORMAT|Došlo k pokusu o přístup k souboru s zastaralým formátem.|  
|E_PDB_INVALID_SIG|Podpis neodpovídá.|  
|E_PDB_INVALID_AGE|Stáří neodpovídá.|  
|E_INVALIDARG|Neplatný parametr|  
|E_UNEXPECTED|Zdroj dat už je připravený.|  
  
## <a name="remarks"></a>Poznámky  
 Hlavička ladění souboru. exe/. dll pojmenovává umístění přidružených dat pro ladění.  
  
 Tato metoda přečte hlavičku ladění a pak vyhledá a připraví ladicí data. Průběh hledání může být volitelně hlášen a ovládán pomocí zpětných volání. Například [IDiaLoadCallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) je vyvolána, když `IDiaDataSource::loadDataForExe` Metoda najde a zpracuje ladicí adresář.  
  
 Rozhraní [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) a [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) umožňují, aby klientská aplikace poskytovala alternativní metody pro čtení dat ze spustitelného souboru, když k souboru nelze získat přímý vstup/výstup souboru.  
  
 Chcete-li načíst soubor. pdb bez ověření, použijte metodu [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Chcete-li ověřit soubor. pdb proti konkrétním kritériím, použijte metodu [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Chcete-li načíst soubor. pdb přímo z paměti, použijte metodu [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## <a name="example"></a>Příklad  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
