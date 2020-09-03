---
title: Servery (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712900"
---
# <a name="servers-visual-studio-sdk"></a>Servery (Visual Studio SDK)
V architektuře ladicího programu *Server*:

- Je kontejner portů a dodavatelů portů a komunikuje porty a dodavatelé portů se správcem ladění relace (SDM) a moduly ladění.

- Může identifikovat podle názvu a vytvořit výčet portů a dodavatelů portů.

- Je reprezentován rozhraním [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , které je implementováno pouze sadou Visual Studio (jedna instance serveru pro každou instanci sady Visual Studio se spuštěnou).

## <a name="see-also"></a>Viz také
- [Porty](../../extensibility/debugger/ports.md)
- [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
