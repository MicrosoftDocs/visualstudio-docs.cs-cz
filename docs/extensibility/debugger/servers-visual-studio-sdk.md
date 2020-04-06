---
title: Servery (Visual Studio SDK) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712900"
---
# <a name="servers-visual-studio-sdk"></a>Servery (Visual Studio SDK)
V architektuře ladicího programu *server*:

- Je kontejner portů a dodavatelů portů a komunikuje porty a porty dodavatelů na relace ladicí správce (SDM) a ladění motorů.

- Dokáže se identifikovat podle názvu a vytvořit výčet portů a dodavatelů portů.

- Je reprezentován [rozhraním IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) které je implementováno pouze visual studio (jedna instance serveru pro každou instanci Visual Studio běží).

## <a name="see-also"></a>Viz také
- [Porty](../../extensibility/debugger/ports.md)
- [Dodavatelé přístavů](../../extensibility/debugger/port-suppliers.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
