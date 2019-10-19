---
title: 'IJsDebugBreakPoint:: deaktived – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25d66b7f8691a74eac77e9a90ec610fa21ec688e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577674"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled – metoda
Určuje, zda je povolena zarážka.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIsEnabled`  
 mimo Vrátí hodnotu true, pokud je zarážka povolena; v opačném případě vrátí hodnotu false.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí E_UNEXPECTED, pokud se volá na odstraněnou zarážku.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugBreakPoint – rozhraní](../../winscript/reference/ijsdebugbreakpoint-interface.md)