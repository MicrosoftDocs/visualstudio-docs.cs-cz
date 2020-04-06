---
title: Kontext dokumentu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738918"
---
# <a name="document-context"></a>Kontext dokumentu
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění kontext *dokumentu*:

- Představuje pozici ve zdrojovém souboru. Pro jazyky, kde zdrojový soubor nemusí být k dispozici, kontext dokumentu identifikuje pozici v dokumentu obvykle generované prostředí mů e být za běhu. Skriptovací stroj může například generovat dokument ze skriptu. Další informace naleznete v [tématu Pozice dokumentu](../../extensibility/debugger/document-position.md).

- Popisuje pozici ve zdrojovém dokumentu, která odpovídá kontextu kódu. Obslužná rutina symbolu mapuje kontext kódu na kontext dokumentace pomocí informací generovaných kompilátorem nebo interpretem.

- Je implementována rozhraním [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Viz také
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [Poskytovatel symbolů](../../extensibility/debugger/symbol-provider.md)
- [Rozhraní zprostředkovatele symbolů](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
