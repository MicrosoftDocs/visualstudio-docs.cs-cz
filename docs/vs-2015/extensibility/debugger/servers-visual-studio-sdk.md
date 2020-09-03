---
title: Servery (Visual Studio SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ed2ce924b22827a82a67664e3e473f0930a87e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199406"
---
# <a name="servers-visual-studio-sdk"></a>Servery (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V rámci architektury ladicího programu **Server**:  
  
- Je kontejner portů a dodavatelů portů a slouží ke komunikaci portů a dodavatelů portů se správcem ladění relace (SDM) a moduly ladění.  
  
- Může identifikovat podle názvu a vytvořit výčet portů a dodavatelů portů.  
  
- Je reprezentován rozhraním [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , které je implementováno pouze sadou Visual Studio (jedna instance serveru pro každou instanci sady Visual Studio se spuštěnou).  
  
## <a name="see-also"></a>Viz také  
 [Přístavu](../../extensibility/debugger/ports.md)   
 [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
