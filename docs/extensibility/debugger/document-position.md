---
title: Umístění dokumentu | Microsoft Docs
description: Zjistěte, jak pozice dokumentu v ladění sady Visual Studio poskytuje abstrakci pozice ve zdrojovém souboru, jak je známo rozhraní IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fef3debcbce3a178c4321114d69c87c627611a07
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915320"
---
# <a name="document-position"></a>Pozice dokumentu
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění, *umístění dokumentu*:

- Poskytuje abstrakci pozice ve zdrojovém souboru, jak je známo pro rozhraní IDE. Pro většinu jazyků dnes lze umístění dokumentu představit jako pozici ve zdrojovém souboru.

- Popisuje pozici ve zdrojovém dokumentu pro ladicí stroj.

- Je implementováno pomocí rozhraní [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>Viz také
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [Kontext dokumentu](../../extensibility/debugger/document-context.md)
- [Zprostředkovatel symbolů](../../extensibility/debugger/symbol-provider.md)
- [Rozhraní poskytovatele symbolů](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
