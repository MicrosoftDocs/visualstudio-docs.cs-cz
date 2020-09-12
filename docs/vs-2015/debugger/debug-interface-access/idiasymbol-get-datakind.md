---
title: 'IDiaSymbol:: get_dataKind | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataKind method
ms.assetid: 45005ad0-8b29-4cde-9d33-6bef72f6e463
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5a67a55ee5c25dc002d107815fb136420641159d
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "64825920"
---
# <a name="idiasymbolget_datakind"></a>IDiaSymbol::get_dataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte klasifikaci proměnných pro datový symbol.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_dataKind (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrací hodnotu z výčtu [výčtu datakind](../../debugger/debug-interface-access/datakind.md) určující druh dat, jako je například globální, statická nebo konstanta.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="requirements"></a>Požadavky  
  
|Požadavek|Popis|  
|-----------------|-----------------|  
|Hlaviček|Dia2. h|  
|Verze:|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [DataKind – výčet](../../debugger/debug-interface-access/datakind.md)
