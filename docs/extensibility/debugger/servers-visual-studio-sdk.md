---
title: Servery (Visual Studio SDK) | Microsoft Docs
description: Tento článek popisuje definice a roli serveru v architektuře ladicího programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d60c214fce57f5958d8b30ca231c3e8a2bc05194
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960803"
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
