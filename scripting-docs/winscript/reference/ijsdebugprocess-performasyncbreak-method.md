---
title: Ijsdebugprocess::performasyncbreak – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.PerformAsyncBreak
apilocation:
- jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e2d3ad50c1be5da0f4e93748227933d5f1ffd92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794580"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>IJsDebugProcess::PerformAsyncBreak – metoda
Skriptovací stroj převádí v režimu pozastavení způsobuje ho na přerušení na další skript instrukcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [v] ID vlákna.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugprocess – rozhraní](../../winscript/reference/ijsdebugprocess-interface.md)