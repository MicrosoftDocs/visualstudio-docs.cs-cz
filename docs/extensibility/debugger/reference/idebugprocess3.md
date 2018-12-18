---
title: IDebugProcess3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21c4dfffe02d2550bccf5b23f264ab8283524aa2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121089"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Toto rozhraní představuje spuštěných procesů a jeho programy. Toto rozhraní existuje jako náhrada k několika metod ve [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) rozhraní. Umožňuje kontrolu nad všechny programy v procesu.  
  
> [!NOTE]
>  [Pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), a [krok](../../../extensibility/debugger/reference/idebugprogram2-step.md) metody jsou zastaralé a by měl být dále používán. Použijte odpovídající metodu na `IDebugProcess3` místo toho rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno modulem vlastní port dodavatele pro správu programy jako skupina. Při správě programy jako skupina, můžete řídit jejich spuštění a vytvořit jazyk pro vyhodnocovací filtr výrazů. Toto rozhraní musí být implementované dodavatel portu.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní je volána především správce ladicí relace (SDM) Chcete-li pracovat s skupinu programů identifikovat v tomto procesu.  
  
 Volání [QueryInterface](/cpp/atl/queryinterface) na [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) rozhraní k získání tohoto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Kromě metod zděděno z [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementuje následujících metod.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Pokračuje v provádění nebo procházení proces.|  
|[Spuštění](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Zahájí spuštění procesu.|  
|[Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Kroky předat jeden pokyn nebo příkaz v procesu.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Získá z důvodu, že proces byl spuštěn pro ladění.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Nastaví hostitelský jazyk tak, aby vyhodnocovací filtr výrazů odpovídající můžete načíst modul ladění.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Získá jazyk nastaveno pro tento proces.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Zakáže upravit a pokračovat (ŠIF) pro tento proces.<br /><br /> Vlastní port dodavatele neimplementuje tuto metodu (vždy by měla vrátit `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Zjištění stavu KODÉRU pro tento proces.<br /><br /> Vlastní port dodavatele neimplementuje tuto metodu (vždy by měla vrátit `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Načte pole jedinečné identifikátory pro ladění k dispozici moduly.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)