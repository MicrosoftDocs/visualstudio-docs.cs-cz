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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42f85d0d15c46cfdfc2b76130649976d15035d7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840714"
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
