---
title: 'IDiaSymbol:: get_thisAdjust | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thisAdjust method
ms.assetid: 56b9a147-e8c0-4d4b-a42a-398214dd5f86
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 979f79658834f9bdcf50f0af51597515eaab2991
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814063"
---
# <a name="idiasymbolget_thisadjust"></a>IDiaSymbol::get_thisAdjust
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte logický `this` seřizovací modul pro metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_thisAdjust (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí logický `this` seřizovací metodu pro metodu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 V některých případech vícenásobné dědičnosti může metoda sám vypočítat hodnotu true přidáním `this` posunu k `this` .  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
