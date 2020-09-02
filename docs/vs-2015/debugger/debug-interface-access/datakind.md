---
title: Datakind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197638"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Označuje konkrétní rozsah hodnoty dat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elementy  
 DataIsUnknown  
 Nelze určit datový symbol.  
  
 DataIsLocal  
 Datová položka je místní proměnná.  
  
 DataIsStaticLocal  
 Datová položka je statická lokální proměnná.  
  
 DataIsParam  
 Položka dat je formální parametr.  
  
 DataIsObjectPtr  
 Datová položka je ukazatel na objekt ( `this` ).  
  
 DataIsFileStatic  
 Datová položka je proměnná s rozsahem souboru.  
  
 DataIsGlobal  
 Datová položka je globální proměnná.  
  
 DataIsMember  
 Datová položka je proměnná člena objektu.  
  
 DataIsStaticMember  
 Datová položka je statická proměnná třídy.  
  
 DataIsConstant  
 Datová položka je konstantní hodnota.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty v tomto výčtu jsou vráceny metodou [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst. h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
