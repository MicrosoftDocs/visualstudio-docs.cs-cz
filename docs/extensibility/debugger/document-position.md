---
title: Umístění dokumentu | Microsoft Docs
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
ms.openlocfilehash: 19b88ead19e4578adb7c151a681583120cf2ec17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738912"
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
