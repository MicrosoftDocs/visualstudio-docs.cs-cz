---
title: Servery (Visual Studio SDK) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 871eeb59832c640ede32e0fcd188941605c4afcb
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276650"
---
# <a name="servers-visual-studio-sdk"></a>Servery (Visual Studio SDK)
V architektuře ladicího programu *server*:  
  
-   Je kontejner, portů a dodavatelé portů a komunikuje porty a dodavatelé portů Správce ladění relace (SDM) a ladicí stroj.  
  
-   Můžete identifikovat podle názvu a vypsat jeho porty a dodavatelé portů.  
  
-   Je reprezentován [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) rozhraní, které je implementováno pouze Visual Studio (jednu instanci serveru pro každou instanci sady Visual Studio spuštěná).  
  
## <a name="see-also"></a>Viz také:  
 [Porty](../../extensibility/debugger/ports.md)   
 [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)