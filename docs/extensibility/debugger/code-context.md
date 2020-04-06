---
title: Kontext kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739148"
---
# <a name="code-context"></a>Kontext kódu
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění **kontext kódu**:

- Poskytuje abstrakci pozice v kódu, jak je známo, že ladicí modul (DE). Pro většinu architektur za běhu dnes kontextu kódu lze považovat za adresu v instrukčním proudu programu. Pro netradiční jazyky, kde kód nemusí být reprezentován pokyny, kontext kódu může být reprezentován jiným způsobem.

- Popisuje aktuální pozici v proudu spuštění programu, který ladíte.

- Existuje pouze v případě, že program byl zastaven na zarážku.

- Má přidružený kontext dokumentu.

- Je implementována rozhraním [IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>Viz také
- [Kontext dokumentu](../../extensibility/debugger/document-context.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
