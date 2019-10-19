---
title: 'Idebugapplicationthread110 –:: IsThreadCallable | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ff81190247454a4471a4150843d3fb0aaed5999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574470"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Určuje, zda je toto vlákno ve stavu, který bude zpracovávat volání prováděná pomocí mechanismů přepínání vláken PDM, jako je například SynchronousCallInThread.  
  
> [!IMPORTANT]
> [Rozhraní idebugapplicationthread110 –](../../winscript/reference/idebugapplicationthread110-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsCallable`  
 [out] `true`, pokud vlákno je volat, jinak `false`.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationThread110 – rozhraní](../../winscript/reference/idebugapplicationthread110-interface.md)