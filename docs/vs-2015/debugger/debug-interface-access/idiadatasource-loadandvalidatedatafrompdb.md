---
title: 'IDiaDataSource:: loadAndValidateDataFromPdb | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f19a910af45ed70ae74c72441890ecae6c81d2a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198621"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře a ověří, že soubor databáze programu (PDB) odpovídá poskytnutým informacím o podpisu a připraví soubor. pdb jako zdroj dat pro ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdbPath`  
 pro Cesta k souboru. pdb.  
  
 `pcsig70`  
 pro Signatura identifikátoru GUID, který se má ověřit proti podpisu souboru. pdb. Signatury GUID mají jenom soubory. pdb v [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] a novější.  
  
 `sig`  
 pro 32 signatura, která se má ověřit proti podpisu souboru. pdb.  
  
 `age`  
 pro Věková hodnota, která se má ověřit Věk nutně neodpovídá žádné známé časové hodnotě, používá se k určení, jestli soubor. pdb není synchronizovaný s odpovídajícím souborem. exe.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny možné návratové hodnoty pro tuto metodu.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Soubor se nepovedlo otevřít, nebo má neplatný formát.|  
|E_PDB_FORMAT|Došlo k pokusu o přístup k souboru s zastaralým formátem.|  
|E_PDB_INVALID_SIG|Podpis neodpovídá.|  
|E_PDB_INVALID_AGE|Stáří neodpovídá.|  
|E_INVALIDARG|Neplatný parametr|  
|E_UNEXPECTED|Zdroj dat již byl připraven.|  
  
## <a name="remarks"></a>Poznámky  
 Soubor. pdb obsahuje hodnoty signature i Age. Tyto hodnoty jsou replikovány v souboru. exe nebo. dll, který odpovídá souboru. pdb. Před přípravou zdroje dat tato metoda ověřuje, že název pojmenovaného souboru. pdb a stáří odpovídají zadaným hodnotám.  
  
 Chcete-li načíst soubor. pdb bez ověření, použijte metodu [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Chcete-li získat přístup k procesu načítání dat (pomocí mechanismu zpětného volání), použijte metodu [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Chcete-li načíst soubor. pdb přímo z paměti, použijte metodu [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## <a name="example"></a>Příklad  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>Viz také  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
