---
title: Idiasymbol::get_issplitted – | Dokumentace Microsoftu
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
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0d8b220c4df7a5381f2d436e23148724df058cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730269"
---
# <a name="idiasymbolgetissplitted"></a>IDiaSymbol::get_isSplitted
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Získá příznak, který určuje, zda byl datový symbol rozdělen do agregaci nebo kolekce jiných symbolů; Kompilátor považuje za samostatné entity, symboly, i když jsou ve skutečnosti součástí větší symbol.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Vrátí `TRUE` Pokud symbol má byl rozdělen do agregace symbolů; v opačném případě vrátí `FALSE`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
>  Vrácená hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 [Idiasymbol::get_isaggregated –](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) vrátí metoda `TRUE` pro všechny symboly, které jsou součástí rozdělit symbol.  
  
## <a name="requirements"></a>Požadavky  
  
|Požadavek|Popis|  
|-----------------|-----------------|  
|Záhlaví:|dia2.h|  
|Verze:|Ve verzi 8.0 DIA SDK|  
  
## <a name="see-also"></a>Viz také  
 [Idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)



