---
title: 'IDiaPropertyStorage:: ReadDWORD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e92b74fc1165adf359614e354ab60f3fc118e34b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538821"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přečte `DWORD` hodnoty v sadě vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 pro Identifikátor vlastnosti, která má být načtena ( `PROPID` je definována v WTypes. h jako `ULONG` ).  
  
 `pValue`  
 mimo Vrátí hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Vrátí, `E_INVALIDARG` zda vlastnost není typu `DWORD` .  
  
## <a name="remarks"></a>Poznámky  
 Objekt `DWORD` je definován systémem Windows jako 32-bit unsigned integer.  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
