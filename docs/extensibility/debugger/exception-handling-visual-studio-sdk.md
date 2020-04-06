---
title: Zpracování výjimek (Visual Studio SDK) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738758"
---
# <a name="exception-handling-visual-studio-sdk"></a>Zpracování výjimek (Visual Studio SDK)
Následující popisuje proces, ke kterému dochází při vyvolání výjimky.

## <a name="exception-handling-process"></a>Proces zpracování výjimek

1. Při prvním vyvolání výjimky, ale před tím, než je zpracována obslužnou rutinou výjimky v ladicím programu, ladicí modul (DE) odešle [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) správci ladění relace (SDM) jako událost zastavení. Je `IDebugExceptionEvent2` odeslána, pokud pouze nastavení výjimky (zadané v dialogovém okně Výjimky v balíčku ladění) určuje, že uživatel chce zastavit na oznámení o výjimce první šance.

2. SDM volá [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) získat vlastnost exception.

3. Ladicí balíček volá [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) k určení, jaké možnosti předložit uživateli.

4. Ladicí balíček se uživatele zeptá, jak zpracovat výjimku otevřením dialogového okna výjimky první šance.

5. Pokud se uživatel rozhodne pokračovat, SDM volá [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Pokud metoda vrátí S_OK, volá [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -nebo-

         Pokud metoda vrátí S_FALSE, program, který je laděn je dána druhá možnost zpracovat výjimku.

6. Pokud program, který je laděn nemá žádnou obslužnou rutinu pro druhou šanci výjimku, DE odešle a `IDebugExceptionEvent2` sDM jako **EVENT_SYNC_STOP**.

7. Ladicí balíček se uživatele zeptá, jak zpracovat výjimku otevřením dialogového okna výjimky první šance.

8. Ladicí balíček volá [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) k určení, jaké možnosti předložit uživateli.

9. Ladicí balíček se uživatele zeptá, jak zpracovat výjimku otevřením dialogového okna výjimky druhé šance.

10. Pokud metoda vrátí S_OK, volání `IDebugExceptionEvent2::PassToDebuggee`.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
