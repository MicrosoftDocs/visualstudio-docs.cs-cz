---
title: 'IDebugExpression –:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576433"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Zahájí vyhodnocení výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdecb`  
 pro Zpětné volání pro indikaci, kdy bylo dokončeno vyhodnocení výrazu. Pokud je tento parametr `NULL`, nejsou vyvolány žádné události a klient musí dotazovat stav výrazu pomocí `QueryIsComplete`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zahájí vyhodnocení výrazu.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugExpression –:: Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression – rozhraní](../../winscript/reference/idebugexpression-interface.md)