---
title: Umístění dokumentu | Microsoft Docs
description: Zjistěte, jak pozice dokumentu v ladění sady Visual Studio poskytuje abstrakci pozice ve zdrojovém souboru, jak je známo rozhraní IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d14f9619059735aaecabf72adef248c69ed247e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097250"
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
