---
title: 'IJsDebugDataTarget:: Createstackframeenumerator – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation:
- jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 59d58f0256a326d3922e280818176a43ef4aa5ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577634"
---
# <a name="ijsdebugdatatargetcreatestackframeenumerator-method"></a>IJsDebugDataTarget::CreateStackFrameEnumerator – metoda
Vytvoří enumerátor pro rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 pro Vlákno spuštěné v cílovém procesu.  
  
 `ppEnumerator`  
 mimo Enumerátor pro rámce zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)