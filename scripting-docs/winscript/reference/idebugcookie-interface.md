---
title: Rozhraní Idebugcookie – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47b48b917ee3376c417beffd9972d76a444513ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573190"
---
# <a name="idebugcookie-interface"></a>IDebugCookie – rozhraní
Povoluje nastavení souboru cookie pro ladění pro použití s rozhraním `IMachineDebugManagerCookie`. Další informace najdete v tématu [rozhraní imachinedebugmanagercookie –](../../winscript/reference/imachinedebugmanagercookie-interface.md). Toto rozhraní je implementováno pomocí Správce ladění procesu (PDM) a spotřebovaného ladicími programy skriptu.  
  
## <a name="methods"></a>Metody  
 Kromě metod zděděných z `IUnknown` rozhraní `IDebugCookie` zpřístupňuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Nastaví soubor cookie ladění aplikace.|  
  
## <a name="see-also"></a>Viz také:  
 [IMachineDebugManagerCookie – rozhraní](../../winscript/reference/imachinedebugmanagercookie-interface.md)