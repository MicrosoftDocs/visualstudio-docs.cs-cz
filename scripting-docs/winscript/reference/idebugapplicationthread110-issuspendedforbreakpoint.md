---
title: 'Idebugapplicationthread110 –:: IsSuspendedForBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0e70993b95ccffcf6041bb04f37af90667fc4fd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574462"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
Určuje, zda byla v tomto vlákně volána metoda [idebugapplicationthreadevents110 –:: OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) a ještě nebyla dokončena.  
  
> [!IMPORTANT]
> [Rozhraní idebugapplicationthread110 –](../../winscript/reference/idebugapplicationthread110-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsSuspended`  
 [out] `true`, pokud je vlákno pozastaveno pro zarážku, jinak `false`.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationThread110 – rozhraní](../../winscript/reference/idebugapplicationthread110-interface.md)