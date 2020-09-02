---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576405"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje typy převodů.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elementy  
 THUNK_ORDINAL_NOTYPE  
 Standardní převolání.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Převod pomocí `this` kódu pro úpravy  
  
 THUNK_ORDINAL_VCALL  
 Virtuální volání je převoláno.  
  
 THUNK_ORDINAL_PCODE  
 P-code převod.  
  
 THUNK_ORDINAL_LOAD  
 Zpožděné načtení převodu do kódu  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Přírůstkové Trampoline převodu (Trampoline převodu se používá pro odskok volání z jednoho paměťového prostoru na jiný).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Trampoline převodu na bod větve.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty v tomto výčtu jsou vráceny ze volání metody [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst. h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
