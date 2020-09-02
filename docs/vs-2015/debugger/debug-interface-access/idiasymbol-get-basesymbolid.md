---
title: 'IDiaSymbol:: get_baseSymbolId | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f8642c8585aa1964068e1f66082a1da5ea878c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149827"
---
# <a name="idiasymbolget_basesymbolid"></a>IDiaSymbol::get_baseSymbolId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte ID symbolu, ze kterého je založen ukazatel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_baseSymbolId(   
   DWORD *pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Ukazatel na `DWORD` , který obsahuje ID symbolu, ze kterého je ukazatel založen.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)
