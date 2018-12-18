---
title: Struktura DebugStackFrameDescriptor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791850"
---
# <a name="debugstackframedescriptor-structure"></a>Struktura DebugStackFrameDescriptor
Vytváří výčet rámců zásobníku a slučuje výstup z několika enumerátorů ve stejném vláknu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Členové  
 `pdsf`  
 Objekt rámce zásobníku.  
  
 `dwMin`  
 Reprezentace závislé na počítači nižší rozsah fyzické adresy přidružené k této rámce zásobníku.  
  
 `dwLim`  
 Reprezentace závislé na počítač horní hranice fyzické adresy přidružené k této rámce zásobníku.  
  
 `fFinal`  
 Příznak, který indikuje, že rámečku je zpracovávána.  
  
 `punkFinal`  
 Pokud není tento parametr `NULL`novou má být spuštěn, a aktuální enumerátor slučování by se měla zastavit. Objekt určuje, jak spustit nový výčet.  
  
## <a name="remarks"></a>Poznámky  
 Správce ladění proces používá tato struktura seřadit rámce zásobníku z více skriptovací stroje. Podle konvence zásobníky růst dolů. V důsledku toho na architektury, kde zásobníky růst nahoru, adresy musí být doplněny dvou.  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)