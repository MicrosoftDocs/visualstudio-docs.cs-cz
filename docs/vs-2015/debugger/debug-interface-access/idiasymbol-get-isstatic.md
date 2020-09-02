---
title: 'IDiaSymbol:: get_isStatic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStatic method
ms.assetid: 3be5fe1b-46e8-4b07-90d8-4929dbbe7ff7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d8a3ecf54730c16248ba5fdb8ac6db92e488947
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64809608"
---
# <a name="idiasymbolget_isstatic"></a>IDiaSymbol::get_isStatic
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte příznak, který určuje, zda byla funkce nebo přeznaková vrstva označena jako statická.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_isStatic(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 mimo Vrátí, `TRUE` zda je funkce nebo vrstva s převoláním označena jako statická; v opačném případě vrátí `FALSE` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="requirements"></a>Požadavky  
  
|Požadavek|Popis|  
|-----------------|-----------------|  
|Hlaviček|Dia2. h|  
|Verze:|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
