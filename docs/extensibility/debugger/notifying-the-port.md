---
title: Oznámení přístavu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738328"
---
# <a name="notify-the-port"></a>Upozornit port
Po spuštění programu musí být port oznámen takto:

1. Když port obdrží nový uzel programu, odešle událost vytvoření programu zpět do relace ladění. Událost s sebou nese rozhraní, které představuje program.

2. Relace ladění se dotazuje programu na identifikátor ladicího stroje (DE), ke kterému se lze připojit.

3. Ladicí relace zkontroluje, zda DE je na seznamu povolených DEs pro tento program. Relace ladění získá tento seznam z nastavení aktivního programu řešení, původně předána ladicí balíček.

    De musí být na seznamu povolených, jinak DE nebude připojen k programu.

   Programově, když port poprvé obdrží nový uzel programu, vytvoří rozhraní [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) představující program.

> [!NOTE]
> To by nemělo `IDebugProgram2` být zaměňováno s rozhraním vytvořeným později ladicím motorem (DE).

 Port odešle událost vytvoření programu [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zpět do správce ladění relace (SDM) pomocí rozhraní COM. `IConnectionPoint`

> [!NOTE]
> To by nemělo `IDebugProgramCreateEvent2` být zaměňováno s rozhraním, které je odesláno později DE.

 Spolu se samotným rozhraním události port odesílá rozhraní [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)a [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) které představují port, proces a program. SDM volá [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) získat identifikátor GUID DE, který může ladit program. Identifikátor GUID byl původně získán z rozhraní [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 SDM zkontroluje, zda DE je na seznamu povolených DEs. SDM získá tento seznam z nastavení aktivního programu řešení, původně předán y ladicí balíček. De musí být na seznamu povolených, jinak nebude připojen k programu.

 Jakmile je známa identita DE, SDM je připraven k připojení k programu.

## <a name="see-also"></a>Viz také
- [Spuštění programu](../../extensibility/debugger/launching-a-program.md)
- [Připojení po startu](../../extensibility/debugger/attaching-after-a-launch.md)
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
