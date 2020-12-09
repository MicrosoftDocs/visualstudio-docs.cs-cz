---
title: Kontext kódu | Microsoft Docs
description: Přečtěte si o kontextu kódu v ladění sady Visual Studio, které popisuje pozici v kódu, který existuje, když se program zastaví na zarážce.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 60eabaca8d39d40649e20e022b25ce1b02bd8faf
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914306"
---
# <a name="code-context"></a>Kontext kódu
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění, **kontext kódu**:

- Poskytuje abstrakci pozice v kódu, který je známý ladicímu stroji (DE). Pro většinu architektur za běhu v současné době lze kontext kódu představit jako adresu v datovém proudu instrukcí programu. Pro netradiční jazyky, kde kód nemůže být reprezentován pokyny, kontext kódu může být reprezentován jiným způsobem.

- Popisuje aktuální pozici v datovém proudu spuštění programu, který ladíte.

- Existuje pouze v případě, že program byl zastaven na zarážce.

- Má přidružený kontext dokumentu.

- Je implementováno pomocí rozhraní [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .

## <a name="see-also"></a>Viz také
- [Kontext dokumentu](../../extensibility/debugger/document-context.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
