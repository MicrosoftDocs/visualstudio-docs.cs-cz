---
title: Řízení programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8102bc488d5c74f751fb93584016aa6904fbe2d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858634"
---
# <a name="program-control"></a>Řízení programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
