---
title: 'Iremotedebugapplicationthread –:: SetNextStatement | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575511"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Vynutí, aby provádění pokračovalo co nejblíže danému kontextu kódu v kontextu daného rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 pro Objekt rámce zásobníku. Tento argument může mít hodnotu NULL, což znamená, že by měl být použit aktuální rámec zásobníku.  
  
 `pCodeContext`  
 pro Kontext kódu. Tento argument může mít hodnotu NULL, což znamená, že by měl být použit aktuální kontext kódu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vynutí, aby provádění pokračovalo co nejblíže kontextu kódu určeném pomocí `pCodeContext` v kontextu rámce určeného parametrem `pStackFrame`. Jeden z těchto argumentů může být `NULL`, představující aktuální rámec nebo kontext.  
  
## <a name="see-also"></a>Viz také:  
 [IRemoteDebugApplicationThread – rozhraní](../../winscript/reference/iremotedebugapplicationthread-interface.md)