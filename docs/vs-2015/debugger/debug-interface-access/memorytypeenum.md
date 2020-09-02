---
title: Memorytypeenum – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ded136da4d601fd7c11a10c21aac0c90864bc0bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158133"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje typ paměti, pro který má být přístup.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `MemTypeCode`  
 Přistupuje pouze k paměti kódu.  
  
 `MemTypeData`  
 Přistupuje k datům nebo zásobníku paměti.  
  
 `MemTypeStack`  
 Přistupuje pouze do zásobníku paměti.  
  
 `MemTypeAny`  
 Přistupuje k jakémukoli typu paměti.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty v tomto výčtu jsou předány metodě [IDiaStackWalkHelper:: readMemory –](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) pro omezení přístupu k různým typům paměti.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst. h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
