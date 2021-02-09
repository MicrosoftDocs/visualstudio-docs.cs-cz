---
title: Zpracování výjimek (Visual Studio SDK) | Microsoft Docs
description: Přečtěte si o procesu, ke kterému dochází, když jsou výjimky vyvolány. Tento článek popisuje všechny kroky, které jsou k diskrokům.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ed8db28a7196551e2f1c8236d71e0f2291fce934
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921509"
---
# <a name="exception-handling-visual-studio-sdk"></a>Zpracování výjimek (Visual Studio SDK)
Následující článek popisuje proces, ke kterému dochází, když jsou vyvolány výjimky.

## <a name="exception-handling-process"></a>Proces zpracování výjimek

1. Při prvním vyvolání výjimky, ale předtím, než je zpracována obslužnou rutinou výjimky v laděném programu, ladicí stroj (DE) pošle [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) do Správce ladění relace (SDM) jako událost zastavení. `IDebugExceptionEvent2`Je odesláno, pokud pouze nastavení pro výjimku (určené v dialogovém okně výjimky v balíčku pro ladění) určuje, že uživatel chce zastavit při oznámení o první odpovídající výjimce.

2. Volání SDM [IDebugExceptionEvent2:: gets výjimkou](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) pro získání vlastnosti výjimky.

3. Balíček ladění volá [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) a určí, jaké možnosti má uživatel prezentovat.

4. Ladicí balíček požádá uživatele o zpracování výjimky otevřením dialogového okna s prvními možnostmi výjimky.

5. Pokud se uživatel rozhodne pokračovat, volání SDM zavolá [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Pokud metoda vrátí S_OK, volá [IDebugExceptionEvent2::P asstodebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -nebo-

         Pokud metoda vrátí S_FALSE, program, který se právě ladí, přestanou druhou pravděpodobností zpracovat výjimku.

6. Pokud program, který se právě ladí, nemá obslužnou rutinu pro výjimku s druhou pravděpodobností, příkaz DE pošle `IDebugExceptionEvent2` do SDM jako **EVENT_SYNC_STOP**.

7. Ladicí balíček požádá uživatele o zpracování výjimky otevřením dialogového okna s prvními možnostmi výjimky.

8. Balíček ladění volá [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) a určí, jaké možnosti má uživatel prezentovat.

9. Ladicí balíček vyzve uživatele, jak zpracovat výjimku, otevřením dialogového okna s výjimkou druhé možnosti.

10. Pokud metoda vrátí S_OK, volání `IDebugExceptionEvent2::PassToDebuggee` .

## <a name="see-also"></a>Viz také
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
