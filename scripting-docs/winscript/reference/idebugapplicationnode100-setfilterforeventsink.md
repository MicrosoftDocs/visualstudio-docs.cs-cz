---
title: 'Idebugapplicationnode100 –:: SetFilterForEventSink | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574727"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Nastaví filtr na konkrétní implementaci [rozhraní idebugapplicationnodeevents –](../../winscript/reference/idebugapplicationnodeevents-interface.md) . Umožňuje ladicím programům skriptů vyfiltrovat uzly podřízených aplikací generovaných kompilátorem tak, aby PDM už po vytvoření nebo odebrání neodesílaly události. Ve výchozím nastavení se odešlou všechny uzly.  
  
> [!IMPORTANT]
> [Rozhraní idebugapplicationnode100 –](../../winscript/reference/idebugapplicationnode100-interface.md) je implementováno pomocí PDM v 10.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Soubor cookie filtru.  
  
 `filter`  
 Filtr.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationNode100 – rozhraní](../../winscript/reference/idebugapplicationnode100-interface.md)