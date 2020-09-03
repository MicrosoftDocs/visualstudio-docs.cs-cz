---
title: Zpracování výjimek (Visual Studio SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e646f032a12de48bbfb55b089462c7f8a4dd26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152797"
---
# <a name="exception-handling-visual-studio-sdk"></a>Zpracování výjimek (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
