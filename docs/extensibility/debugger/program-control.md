---
title: Program Control | Microsoft Docs
description: Seznamte se s rutinami Visual Studio ladění, ke kterým dochází na úrovni programu, například spouštění, krokování, pokračování a pozastavení/obnovení vláken.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900707"
---
# <a name="program-control"></a>Řízení programu
V Visual Studio ladění se na úrovni programu vyskytují všechny následující rutiny krokování a pokračování:

- Nastavení dalšího příkazu, to znamená nastavení počítače na další instrukci, která se má provést v konkrétním prostředí rámce

- Provádění, to znamená, že pokračujeme v ukončení krokového režimu

- Krokování na další instrukci

- Pokračování s aktuálním režimem krokování

- Pozastavení vláken obsažených v programu

- Obnovení vláken obsažených v programu

> [!NOTE]
> Zobrazení zásobníku volání je implementováno na úrovni vlákna. Chcete-li zobrazit výčet informací o snímku při zobrazení zásobníku volání pro vlákno, je nutné implementovat všechny metody rozhraní [IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Metody řízení programů
 Následující tabulka ukazuje metody [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) které musí být implementovány pro minimální funkční ladicí modul (DE) a řízení provádění.

|Metoda|Popis|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Pokračuje ve spouštění všech vláken obsažených v programu ze stavu ukončeno. Vyžaduje se pro řízení spouštění.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Pokračuje ve spouštění všech vláken obsažených v programu ze stavu ukončeno. Vyžaduje se pro řízení spouštění.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Provede krok na daném vlákně. Pokračuje ve spouštění všech ostatních vláken obsažených v programu. Vyžaduje se pro řízení spouštění.|

 U programů s více vlákny je také nutné implementovat [metodu IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) a všechny metody rozhraní [IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Viz také
- [Řízení spouštění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
