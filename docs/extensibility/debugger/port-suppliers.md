---
title: Dodavatelé portů | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738291"
---
# <a name="port-suppliers"></a>Dodavatelé portů
V architektuře ladicího programu je *Dodavatel portu*:

- Je součástí serveru a poskytuje porty na vyžádání daného serveru.

- Může přidat nebo odebrat porty z nadřazeného serveru.

- Může vytvořit výčet všech portů, které daný server dodal.

- Je reprezentován rozhraním [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , které je zaregistrováno v aplikaci Visual Studio prostřednictvím registru. Toto rozhraní lze získat voláním [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje výchozího dodavatele portu a výchozí port. Pokud je nutné implementovat vlastní port, musí být také implementován vlastní dodavatel portu, aby tyto vlastní porty poskytoval.

## <a name="see-also"></a>Viz také
- [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Porty](../../extensibility/debugger/ports.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
