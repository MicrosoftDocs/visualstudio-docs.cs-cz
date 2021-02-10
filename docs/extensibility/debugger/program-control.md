---
title: Řízení programu | Microsoft Docs
description: Seznamte se s rutinami v ladění sady Visual Studio, ke kterým dochází na úrovni programu, jako je spouštění, krokování, pokračování a pozastavení a obnovení vláken.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9378dd2aa1ed52408e3aa4d0e9027a34d833dab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948449"
---
# <a name="program-control"></a>Řízení programu
V ladění sady Visual Studio se na úrovni programu vyskytují všechny následující kroky krokování a pokračujících rutin:

- Nastavení dalšího příkazu, to znamená, že nastavení počítače na další instrukci, která se má spustit v konkrétním prostředí rámce

- Provádění, to znamená, že se pokračuje v opuštění režimu krokování

- Krokování s další instrukcí

- Pokračuje se v aktuálním režimu krokování.

- Pozastavení vláken obsažených v programu

- Obnovování vláken obsažených v programu

> [!NOTE]
> Zobrazení zásobníku volání je implementováno na úrovni vlákna. Chcete-li vytvořit výčet informací o snímku při zobrazení zásobníku volání pro vlákno, je nutné implementovat všechny metody rozhraní [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .

## <a name="methods-of-program-control"></a>Metody řízení programu
 V následující tabulce jsou uvedeny metody [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , které musí být implementovány pro minimální funkční modul ladění (de) a řízení spouštění.

|Metoda|Popis|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Pokračuje ve spouštění všech vláken obsažených v programu ze stavu Zastaveno. Vyžadováno pro řízení spouštění.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Pokračuje ve spouštění všech vláken obsažených v programu ze stavu Zastaveno. Vyžadováno pro řízení spouštění.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Provede krok na daném vlákně. Pokračuje v spouštění všech ostatních vláken obsažených v programu. Vyžadováno pro řízení spouštění.|

 Pro programy s více vlákny je také nutné implementovat metodu [IDebugProgram2:: EnumThreads –](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) a všechny metody rozhraní [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
