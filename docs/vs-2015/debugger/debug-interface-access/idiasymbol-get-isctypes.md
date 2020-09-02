---
title: 'IDiaSymbol:: get_isCTypes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2 interface
ms.assetid: 00c73cf9-2933-472e-bc1d-d041f4d7e412
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2a4ebe70d8cf26907446494009838e9ba2f795e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819143"
---
# <a name="idiasymbolget_isctypes"></a>IDiaSymbol::get_isCTypes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte příznak označující, zda soubor symbolů obsahuje typy jazyka C.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_isCTypes(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 mimo Vrátí, `TRUE` zda soubor symbolů obsahuje typy jazyka C. v opačném případě vrátí `FALSE` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 Tato vlastnost je k dispozici z `SymTagExe` typu symbolu (viz [exe](../../debugger/debug-interface-access/exe.md)).  
  
## <a name="requirements"></a>Požadavky  
  
|Požadavek|Popis|  
|-----------------|-----------------|  
|Hlaviček|Dia2. h|  
|Verze:|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)
