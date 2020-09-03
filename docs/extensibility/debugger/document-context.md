---
title: Kontext dokumentu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738918"
---
# <a name="document-context"></a>Kontext dokumentu
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění, *kontext dokumentu*:

- Představuje pozici ve zdrojovém souboru. V případě jazyků, kde zdrojový soubor nemusí být k dispozici, určuje kontext dokumentu pozici v dokumentu obvykle generované běhovým prostředím. Skriptovací stroj může například vygenerovat dokument ze skriptu. Další informace najdete v tématu [pozice dokumentu](../../extensibility/debugger/document-position.md).

- Popisuje pozici ve zdrojovém dokumentu, která odpovídá kontextu kódu. Obslužná rutina symbolu mapuje kontext kódu k dokumentaci v kontextu pomocí informací generovaných kompilátorem nebo překladačem.

- Je implementováno pomocí rozhraní [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="see-also"></a>Viz také
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [Zprostředkovatel symbolů](../../extensibility/debugger/symbol-provider.md)
- [Rozhraní poskytovatele symbolů](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
