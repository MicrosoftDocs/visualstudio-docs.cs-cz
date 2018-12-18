---
title: IDebugMessageEvent2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ac168e24de6cf444ac8fcd4215e4ee978fae925
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799805"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní používá ladicí stroj (DE) k odeslání zprávy do sady Visual Studio, který vyžaduje odpověď od uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní pro odeslání zprávy do sady Visual Studio, která vyžaduje odpověď uživatele. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) na stejný objekt jako toto rozhraní musí implementovat rozhraní. Používá SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) přístup `IDebugEvent2` rozhraní.  
  
 Implementace tohoto rozhraní musí komunikovat volání sady Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) na DE. Například to můžete udělat a zobrazí se zpráva pošle zprávu je DE zpracování vláken, nebo objekt implementující toto rozhraní může obsahovat odkaz na DE a zpětné volání DE s odpovědí předaná do `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 DE vytvoří a odešle tento objekt události pro zobrazení zprávy pro uživatele, který vyžaduje odpověď. Událost je odeslána pomocí [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkce zpětného volání, který je poskytnut pomocí SDM, když je připojen k laděnému programu.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugMessageEvent2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Získá zprávu, která se zobrazí.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Nastaví odpověď, a pokud některý z okna se zprávou.|  
  
## <a name="remarks"></a>Poznámky  
 DE bude používat toto rozhraní, pokud vyžaduje konkrétní odpověď od uživatele pro konkrétní zprávu. Například pokud DE dostane zprávu "Přístup byl odepřen" po pokus o vzdálené připojení k programu, DE odešle tuto konkrétní zprávu do sady Visual Studio v `IDebugMessageEvent2` událost s poli styl zprávy `MB_RETRYCANCEL`. To mu umožní opakovat nebo ukončit operaci připojení.  
  
 DE Určuje, jak tuto zprávu zpracovat konvencemi funkce Win32 `MessageBox` (viz [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) podrobnosti).  
  
 Použití [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) rozhraní pro odesílání zpráv do Visual Studio, které nevyžadují odpověď od uživatele.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)

