---
title: Volání událostí ladicího programu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3deef418620ab17297b4ef7e824a0d95c25e439e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904323"
---
# <a name="call-debugger-events"></a>Události ladicího programu volání
Události v relacích ladění se vyskytují v určitém pořadí.

## <a name="discussion"></a>Diskuse
 Pro pochopení vzorce volání mezi ladicím modulem (DE) a správcem ladění relace (SDM) představuje následující pořadí volání událostí, ke kterým dochází v typické relaci ladění:

1. [Připojení k programu a jeho odpojení](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Spuštění ladicího programu](../../extensibility/debugger/launching-the-debugger.md)

3. [Ukončení programu](../../extensibility/debugger/terminating-a-program.md)

4. [Vytvoření zarážky](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Když se zarážka váže nebo se stane nevázanou](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Chyby zarážky](../../extensibility/debugger/breakpoint-errors.md)

7. [Zasáhne zarážku](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Odstranění zarážky](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Vstup do režimu přerušení](../../extensibility/debugger/entering-break-mode.md)

10. [Krokování v režimu pozastavení](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Vyhodnocení výrazu v režimu přerušení](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Zpracování výjimek](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Viz také
- [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)
