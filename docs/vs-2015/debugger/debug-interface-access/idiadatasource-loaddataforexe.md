---
title: Idiadatasource::loaddataforexe – | Dokumentace Microsoftu
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
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0c66a9f8859889e85d3f8edbdfedb702d168fb6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728526"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře a připraví data ladění přidružené k souboru.exe/.dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 spustitelný soubor  
 [in] Cesta k souboru .exe nebo .dll.  
  
 searchPath  
 [in] Alternativní cesty pro vyhledávání dat ladění.  
  
 pCallback  
 [in] `IUnknown` Rozhraní pro objekt, který podporuje ladění rozhraní zpětného volání, například [idialoadcallback –](../../debugger/debug-interface-access/idialoadcallback.md), [idialoadcallback2 –](../../debugger/debug-interface-access/idialoadcallback2.md), [idiareadexeatoffsetcallback –](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), nebo [idiareadexeatrvacallback –](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby. V následující tabulce jsou uvedeny některé možné chybové kódy pro tuto metodu.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Nepovedlo se otevřít soubor nebo soubor má neplatný formát.|  
|E_PDB_FORMAT|Došlo k pokusu o přístup k souboru se zastaralý formát.|  
|E_PDB_INVALID_SIG|Podpis neodpovídá.|  
|E_PDB_INVALID_AGE|Stáří neodpovídá.|  
|E_INVALIDARG|Neplatný parametr.|  
|E_UNEXPECTED, JE-|Zdroj dat je už připraven.|  
  
## <a name="remarks"></a>Poznámky  
 Ladění záhlaví souboru.exe/.dll názvy umístění dat přidružená ladění.  
  
 Tato metoda načte záhlaví ladění a pak vyhledá a připraví data ladění. Probíhá hledání může volitelně hlášené a řídit pomocí zpětných volání. Například [idialoadcallback::notifydebugdir –](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) při vyvolání `IDiaDataSource::loadDataForExe` metoda vyhledá a zpracuje adresář ladění.  
  
 [Idiareadexeatoffsetcallback –](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) a [idiareadexeatrvacallback –](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) rozhraní umožňují klientské aplikaci poskytují alternativní metody pro čtení dat ze spustitelného souboru souboru, když soubor Nelze přistupovat přímo pomocí standardních souborových vstupně-výstupních operací.  
  
 Chcete-li načíst soubor PDB bez ověřování, použijte [idiadatasource::loaddatafrompdb –](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metody.  
  
 Chcete-li ověřit soubor typu .pdb podle konkrétních kritérií, použijte [idiadatasource::loadandvalidatedatafrompdb –](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metody.  
  
 Chcete-li načíst soubor PDB přímo z paměti, použijte [idiadatasource::loaddatafromistream –](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metody.  
  
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
 [Idiadatasource –](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idialoadcallback –](../../debugger/debug-interface-access/idialoadcallback.md)   
 [Idialoadcallback2 –](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [Idialoadcallback::notifydebugdir –](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [Idiareadexeatoffsetcallback –](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [Idiareadexeatrvacallback –](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [Idiadatasource::loaddatafrompdb –](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [Idiadatasource::loadandvalidatedatafrompdb –](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)



