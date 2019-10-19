---
title: 'IJsDebugProcess:: Createstackwalker – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70f5d4885abba3d891526723d3ca1f174549c348
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573829"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker – metoda
Metoda factory pro prohlížeč zásobníku  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 pro ID vlákna.  
  
 `ppStackWalker`  
 mimo Nový objekt stack prohlížeč.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí E_JsDEBUG_UNKNOWN_THREAD, pokud vlákno neobsahuje JavaScript. Tato metoda může být volána pouze v případě, že cílový proces je zastaven.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugProcess – rozhraní](../../winscript/reference/ijsdebugprocess-interface.md)