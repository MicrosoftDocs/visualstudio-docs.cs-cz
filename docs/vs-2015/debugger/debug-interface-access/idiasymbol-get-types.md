---
title: Idiasymbol::get_types – | Dokumentace Microsoftu
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
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d22c6c973fbbd57694849e5ca7d7c7d46f79eb0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766244"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte pole typů kompilátoru specifické pro tento symbol.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cTypes`  
 [in] Velikost vyrovnávací paměti pro data.  
  
 `pcTypes`  
 [out] Vrátí počet typů napsaných, nebo pokud `types` parametr je `NULL`, pak celkový počet typů, které jsou k dispozici.  
  
 `types[]`  
 [out] Pole, které je v tankujeme [idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md) objekty, které představují všechny typy pro tento symbol.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
>  Vrácená hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



