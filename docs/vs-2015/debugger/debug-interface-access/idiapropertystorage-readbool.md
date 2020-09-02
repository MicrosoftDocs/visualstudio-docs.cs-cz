---
title: 'IDiaPropertyStorage:: ReadBOOL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538873"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přečte `BOOL` hodnoty v sadě vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 pro Identifikátor vlastnosti, která má být načtena ( `PROPID` je definována v WTypes. h jako `ULONG` ).  
  
 `pValue`  
 mimo Vrátí hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Vrátí, `E_INVALIDARG` zda vlastnost není typu `BOOL` .  
  
## <a name="remarks"></a>Poznámky  
 Pro konzistentní výsledky interpretujte `BOOL` hodnotu tak, aby nenulové hodnoty byly `TRUE` a nula `FALSE` .  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
