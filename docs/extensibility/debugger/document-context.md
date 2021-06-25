---
title: Kontextová | dokumentu Microsoft Docs
description: Seznamte se s kontextem Visual Studio ladění, které představuje pozici ve zdrojovém souboru nebo pozici ve zdrojovém dokumentu pro kontext kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4b7554e274977f23474f6cf3e8e1af30d9e73b3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898185"
---
# <a name="document-context"></a>Kontext dokumentu
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění kontext *dokumentu*:

- Představuje pozici ve zdrojovém souboru. Pro jazyky, ve kterých zdrojový soubor nemusí být k dispozici, kontext dokumentu identifikuje pozici v dokumentu, který obvykle generuje běhové prostředí. Skriptovací modul může například vygenerovat dokument ze skriptu. Další informace najdete v tématu [Umístění dokumentu.](../../extensibility/debugger/document-position.md)

- Popisuje pozici ve zdrojovém dokumentu, která odpovídá kontextu kódu. Obslužná rutina symbolů mapuje kontext kódu na kontext dokumentace pomocí informací generovaných kompilátorem nebo interpretem.

- Je implementováno [rozhraním IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Viz také
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [Zprostředkovatel symbolů](../../extensibility/debugger/symbol-provider.md)
- [Rozhraní zprostředkovatele symbolů](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
