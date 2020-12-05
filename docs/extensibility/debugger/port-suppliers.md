---
title: Dodavatelé portů | Microsoft Docs
description: Tento článek popisuje definice a roli dodavatele portu v architektuře ladicího programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b3226053a23a45c42a45de038e44829d4a150af6
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606577"
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
