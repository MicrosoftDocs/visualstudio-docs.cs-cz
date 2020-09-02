---
title: Basictype – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580834"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje základní typ symbolu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementy  
 btNoType  
 Není zadán žádný základní typ.  
  
 btVoid  
 Základní typ je `void` .  
  
 btChar  
 Základní typ je `char` typ (C/C++).  
  
 btWChar  
 Základní typ je roztažitelné znak (Unicode) ( `WCHAR` ).  
  
 btInt  
 Základní typ je `signed int` (typ C/C++).  
  
 btUInt  
 Základní typ je `unsigned int` (typ C/C++).  
  
 btFloat  
 Základní typ je číslo s plovoucí desetinnou čárkou ( `FLOAT` ).  
  
 btBCD  
 Základní typ je binární kódované číslo ( `BCD` ).  
  
 btBool  
 Základní typ je logická hodnota ( `BOOL` ).  
  
 btLong  
 Základní typ je `long int` typ (C/C++).  
  
 btULong  
 Základní typ je `unsigned long int` typ (C/C++).  
  
 btCurrency  
 Základní typ je měna.  
  
 btDate  
 Základní typ je datum a čas ( `DATE` ).  
  
 btVariant  
 Základní typ je struktura typu proměnné ( `VARIANT` ).  
  
 btComplex  
 Základní typ je komplexní číslo.  
  
 btBit  
 Základní typ je bit.  
  
 btBSTR  
 Základní typ je základní nebo binární řetězec ( `BSTR` ).  
  
 btHresult  
 Základní typ je `HRESULT` .  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty v tomto výčtu jsou vráceny metodou [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst. h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
