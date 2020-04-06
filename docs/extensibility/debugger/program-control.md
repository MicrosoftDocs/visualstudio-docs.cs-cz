---
title: Řízení programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738229"
---
# <a name="program-control"></a>Řízení programu
V ladění sady Visual Studio dochází všechny následující krokování a pokračování rutiny dojít na úrovni programu:

- Nastavení dalšího příkazu, to znamená nastavení počítače na další instrukce, které mají být provedeny v určitém prostředí rámce

- Provádění, to znamená, že i nadále ukončovat z režimu krokování

- Krokování k dalšímu pokynu

- Pokračování v aktuálním režimu krokování

- Pozastavení vláken obsažených v programu

- Obnovení vláken obsažených v programu

> [!NOTE]
> Zobrazení zásobníku volání je implementováno na úrovni vlákna. Chcete-li vytvořit výčet informací o rámci při zobrazení zásobníku volání pro vlákno, je nutné implementovat všechny metody rozhraní [IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Metody řízení programu
 V následující tabulce jsou uvedeny metody [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) které musí být implementovány pro minimálně funkční ladicí modul (DE) a řízení provádění.

|Metoda|Popis|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Pokračuje ve spuštění všech vláken obsažených v programu ze zastaveného stavu. Vyžadováno pro řízení provádění.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Pokračuje ve spuštění všech vláken obsažených v programu ze zastaveného stavu. Vyžadováno pro řízení provádění.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Provede krok v daném vlákně. Pokračuje ve spuštění všech ostatních vláken obsažených v programu. Vyžadováno pro řízení provádění.|

 Pro vícevláknové programy je nutné také implementovat metodu [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) a všechny metody rozhraní [IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
