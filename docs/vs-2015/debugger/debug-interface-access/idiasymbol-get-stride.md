---
title: 'IDiaSymbol:: get_stride | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3eb93749a3190bf2468c8d12e1ca906dc40f0cbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428219"
---
# <a name="idiasymbolget_stride"></a>IDiaSymbol::get_stride
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte rozteč matice nebo pole s roztečí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_stride(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Ukazatel na `DWORD` , který má rozteč.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
