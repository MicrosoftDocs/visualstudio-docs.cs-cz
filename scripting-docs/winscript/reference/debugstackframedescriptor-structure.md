---
title: Struktura Debugstackframedescriptor – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576556"
---
# <a name="debugstackframedescriptor-structure"></a>Struktura DebugStackFrameDescriptor
Vytváří výčet rámců zásobníku a slučuje výstup z několika enumerátorů ve stejném vláknu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 Reprezentace závislá na počítači s nižším rozsahem fyzických adres spojených s tímto rámcem zásobníku.  
  
 `dwLim`  
 Reprezentace závislého počítače na horním rozsahu fyzických adres přidružených k tomuto bloku zásobníku.  
  
 `fFinal`  
 Příznak, který označuje, že je snímek zpracováván.  
  
 `punkFinal`  
 Pokud tento parametr není `NULL`, je nutné zastavit aktuální sloučení enumerátoru a spustit nový. Objekt označuje, jak spustit nový výčet.  
  
## <a name="remarks"></a>Poznámky  
 Správce procesu ladění používá tuto strukturu k řazení rámců zásobníku z více skriptovacích strojů. Podle konvence roste velikost zásobníků. V důsledku toho se v architekturách, ve kterých se rozšiřují hromádky, musí tyto adresy přidvojkovéhoně doplnit.  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)