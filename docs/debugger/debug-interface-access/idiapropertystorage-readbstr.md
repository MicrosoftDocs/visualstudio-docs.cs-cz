---
title: IDiaPropertyStorage::ReadBSTR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47272cbfc572d85af631edb6d33cf6a0c6f4b20d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909065"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Přečte `BSTR` hodnoty v sadu vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identifikátor vlastnosti pro čtení (`PROPID` je definována v WTypes.h jako `ULONG`).  
  
 `pValue`  
 [out] Vrátí hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby. Vrátí `E_INVALIDARG` Pokud vlastnost není typu `BSTR`.  
  
## <a name="remarks"></a>Poznámky  
 A `BSTR` je definován Windows jako řetězec širokých znaků ukončit nulou.  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)