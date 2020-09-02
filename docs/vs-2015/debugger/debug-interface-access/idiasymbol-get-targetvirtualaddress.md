---
title: 'IDiaSymbol:: get_targetVirtualAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetVirtualAddress method
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 911295730548e905e55a61fa16fc3adc792a1bbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793143"
---
# <a name="idiasymbolget_targetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte virtuální adresu (VA) cíle s převoláním.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_targetVirtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí hodnotu VA cíle s převoláním.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 Tato vlastnost je platná pouze v případě, že symbol jako hodnota [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk` .  
  
 "Převádějící" je část kódu, která se převádí mezi 32 adresního prostoru (označovaného také jako plochý adresní prostor) a 16bitového adresního prostoru (označovaného jako segmentované adresní místo).  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
