---
title: Dodavatelé přístavů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738291"
---
# <a name="port-suppliers"></a>Dodavatelé přístavů
V architektuře ladicího programu *dodavatel portu*:

- Je obsažen serverem a poskytuje porty na vyžádání k tomuto serveru.

- Můžete přidat a odebrat porty z obsahujícího serveru.

- Můžete vytvořit výčet všech portů, které dodal serveru.

- Je reprezentován [rozhraníM IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) které je registrováno v sadě Visual Studio prostřednictvím registru. Toto rozhraní lze získat voláním [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]poskytuje výchozího dodavatele portu a výchozí port. Pokud je třeba implementovat vlastní port, musí být implementován také dodavatel vlastního portu, který tyto vlastní porty dodává.

## <a name="see-also"></a>Viz také
- [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Porty](../../extensibility/debugger/ports.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
