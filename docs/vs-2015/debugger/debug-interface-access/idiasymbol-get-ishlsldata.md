---
title: 'IDiaSymbol:: get_isHLSLData | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd67253ffeb266ba1d700b7271e95e9e40c736ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155886"
---
# <a name="idiasymbolget_ishlsldata"></a>IDiaSymbol::get_isHLSLData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje, zda tento symbol představuje data HLSL (High Level shader Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Ukazatel na `BOOL` , který určuje, zda tento symbol představuje HLSL data.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
