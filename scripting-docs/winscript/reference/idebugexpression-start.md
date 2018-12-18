---
title: IDebugExpression::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 14d293649e3a6a87c7f594e244378dc2a7e15ac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794433"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Zahájí vyhodnocování výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdecb`  
 [v] Zpětné volání pro označující po dokončení vyhodnocení výrazu. Pokud tento parametr je `NULL`, při vyvolání žádné události a klient se musí dotazovat stav výrazu pomocí `QueryIsComplete`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda začne vyhodnocování výrazu.  
  
## <a name="see-also"></a>Viz také  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Idebugexpression – rozhraní](../../winscript/reference/idebugexpression-interface.md)