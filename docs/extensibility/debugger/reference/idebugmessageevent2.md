---
title: IDebugMessageEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d0cb1f270d3d3ae77c43ea89fba5b7483e80412
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116165"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Toto rozhraní používá stroj ladění (DE) k odeslání zprávy do Visual Studia, která vyžaduje odpověď od uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní k odeslání zprávy do Visual Studia, která vyžaduje odpověď uživatele. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) rozhraní musí být implementována pro stejný objekt jako toto rozhraní. Používá SDM [QueryInterface](/cpp/atl/queryinterface) k přístupu `IDebugEvent2` rozhraní.  
  
 Implementace tohoto rozhraní musí komunikovat Visual Studio volání [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) k DE. Například to můžete provést zprávou odesílat zprávy je DE zpracování vláken, nebo objekt implementace tohoto rozhraní by mohla obsahovat odkaz na DE a zpětné volání je DE s odpovědí předaný do `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 DE vytvoří a odešle tento objekt událostí k zobrazení zprávy pro uživatele, který vyžaduje odpověď. Událost je odeslána pomocí [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkce zpětného volání, který poskytl SDM při připojení k programu laděné.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugMessageEvent2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Získá zprávu, která se má zobrazit.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Nastaví odpověď, pokud existuje, v rozevíracím seznamu zpráv.|  
  
## <a name="remarks"></a>Poznámky  
 DE bude používat toto rozhraní, pokud to vyžaduje konkrétní odpověď od uživatele pro danou zprávu. Například pokud je DE získá zprávu "Přístup byl odepřen" po pokusu o vzdáleně připojit k programu, DE odešle tato konkrétní zpráva k sadě Visual Studio v `IDebugMessageEvent2` událost s styl box zpráva `MB_RETRYCANCEL`. To umožňuje uživateli opakovat nebo ukončit v operaci připojení.  
  
 DE Určuje, jak se tato zpráva je zpracovávat souladu s konvencemi prostředí Win32 funkce `MessageBox` (viz [AfxMessageBox –](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) podrobnosti).  
  
 Použití [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) rozhraní pro odesílání zpráv pro Visual Studio, které nevyžadují odpověď od uživatele.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)