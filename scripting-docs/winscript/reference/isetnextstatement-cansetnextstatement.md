---
title: 'ISetNextStatement –:: CanSetNextStatement | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56cf0b2e4afd7a86a087b37be4b23758a5b59720
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571840"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Tato metoda určuje, zda bod provádění, který určuje další příkaz kódu, který má být spuštěn, lze nastavit na zadané umístění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 pro Ukazatel na objekt rámce zásobníku.  
  
 `pCodeContext`  
 pro Ukazatel na objekt kontextu kódu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Následující příkaz lze aktualizovat na zadaný kontext kódu.|  
|`S_FALSE`|Následující příkaz nelze aktualizovat na zadaný kontext kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 [ISetNextStatement – rozhraní](../../winscript/reference/isetnextstatement-interface.md)