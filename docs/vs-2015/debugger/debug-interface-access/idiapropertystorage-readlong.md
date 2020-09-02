---
title: 'IDiaPropertyStorage:: ReadLONG | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08661272bea779ff0789619d58bf6f2837a21917
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538312"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přečte `LONG` hodnoty v sadě vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 pro Identifikátor vlastnosti, která má být načtena ( `PROPID` je definována v WTypes. h jako `ULONG` ).  
  
 `pValue`  
 mimo Vrátí hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Vrátí, `E_INVALIDARG` zda vlastnost není typu `LONG` .  
  
## <a name="remarks"></a>Poznámky  
 Objekt `LONG` je definován systémem Windows jako 32 celé číslo se znaménkem.  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
