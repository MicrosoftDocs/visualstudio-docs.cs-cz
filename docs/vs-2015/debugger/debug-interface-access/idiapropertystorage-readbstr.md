---
title: 'IDiaPropertyStorage:: Readbstr – | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0c7a796a57d5c96d870850bb02051d745fd8473
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538826"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přečte `BSTR` hodnoty v sadě vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 pro Identifikátor vlastnosti, která má být načtena ( `PROPID` je definována v WTypes. h jako `ULONG` ).  
  
 `pValue`  
 mimo Vrátí hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Vrátí, `E_INVALIDARG` zda vlastnost není typu `BSTR` .  
  
## <a name="remarks"></a>Poznámky  
 Objekt `BSTR` je definován systémem Windows jako řetězec s velkým počtem znaků zakončený nulou.  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
