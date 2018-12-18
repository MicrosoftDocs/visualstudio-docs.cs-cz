---
title: Metody související se zarážkou | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1767afec32b2b90250a841317e0929fcdd7732c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794995"
---
# <a name="breakpoint-related-methods"></a>Metody související se zarážkou
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladicí stroj (DE) musí podporovat nastavení zarážky. Ladění aplikace Visual Studio podporuje následující typy zarážky:  
  
-   vázaný  
  
     Požadovaný přes uživatelské rozhraní a úspěšně svázaná s umístěním zadaný kód  
  
-   Čekající na vyřízení  
  
     Požadovaný prostřednictvím uživatelského rozhraní, ale není dosud vázaná na skutečné pokyny  
  
## <a name="discussion"></a>Diskuse  
 Například čekající zarážkou nastane, pokud ještě nejsou načtené pokynů. Při načítání kódu, čekajících zarážek zkuste vytvořit vazbu na kód určeného umístění, to znamená, chcete-li vložit pokyny přerušení v kódu. Události se posílají správce ladění relace (SDM) k označení úspěšného vazby nebo upozornit, že došlo k chybám vazby.  
  
 Čekající zarážkou také spravuje svou vlastní interní seznam odpovídající vazby zarážky. Jedno čekající zarážka může způsobit vložení mnoha zarážek v kódu. Ladění uživatelského rozhraní sady Visual Studio zobrazuje stromovou strukturu čekajících zarážek a jejich odpovídající vázaný zarážky.  
  
 Vytváření a používání čekajících zarážek vyžadují provádění [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metody, stejně jako tyto metody [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) rozhraní.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Určuje, zda zadané čekajících zarážek lze svázat místa v kódu.|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Váže zadanou čekajících zarážek na jeden nebo více umístění kódu.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Získá stav čekající zarážkou.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Získá požadavek zarážku použitý k vytvoření čekající zarážkou.|  
|[Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Přepíná povoleného stavu čekající zarážkou.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Zobrazí všechny zarážky, od čekající zarážka vázána.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Zobrazí všechny zarážky chyb, které jsou výsledkem čekající zarážkou.|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Odstraní čekající zarážkou a všechny zarážky, které jsou vázány z něj.|  
  
 Výčet vazby zarážky a Chyba zarážky, musí implementovat všechny metody [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) a [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Čekajících zarážek, kteří jsou navázáni na kód umístění vyžadují provádění následujících [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Získá čekající zarážka, který obsahuje zarážku.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Získá stav vázaná zarážka.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Získá řešení zarážek, které popisují zarážku.|  
|[Enable](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Povolí nebo zakáže zarážku.|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Odstraní vázaná zarážka.|  
  
 Překlad IP adres a žádost o informace vyžadují provádění následujících [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Získá typ zarážky reprezentována řešení.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Získá informace o řešení zarážek, popisující zarážku.|  
  
 Řešení chyb, které mohou nastat během vazby vyžaduje implementace následujících [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Získá čekající zarážka, která obsahuje zarážku k chybě.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Získá chyba řešení zarážek, popisující zarážku k chybě.|  
  
 Řešení chyb, které mohou nastat během vazby také vyžaduje následující metody [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Získá typ zarážky.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Získá informace o řešení zarážku.|  
  
 Zobrazení zdrojového kódu na zarážce je potřeba implementovat metody [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) a/nebo metody [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)

