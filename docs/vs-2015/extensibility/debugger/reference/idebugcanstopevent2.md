---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4ac1f3a8d9b470fbb3734f822601a7dce08a44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696671"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní se používá k vyžádání Správce ladění relace (SDM), zda se má zastavit v aktuálním umístění kódu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní pro podporu krokování prostřednictvím zdrojového kódu. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se musí implementovat na stejný objekt jako toto rozhraní (SDM používá pro přístup k rozhraní [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugEvent2` .).  
  
 Implementace tohoto rozhraní musí komunikovat s voláním metody SDM [po spuštění](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) do ladicího stroje. To lze provést například pomocí zprávy odeslané do vlákna zpracování zpráv modulu ladění nebo objektu, který implementuje toto rozhraní, může obsahovat odkaz na ladicí modul a zpětné volání zpět do ladicího stroje s příznakem předaným do `IDebugCanStopEvent2::CanStop` .  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Metoda DE může odeslat tuto metodu pokaždé, když se žádost DE pokusí pokračovat v provádění a DE krokování pomocí kódu. Tato událost se posílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , kterou poskytuje služba SDM, když je připojená k laděnému programu.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugCanStopEvent2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Získá důvod pro tuto událost.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Určuje, zda se má ladicí program zastavit v umístění této události (a pošle událost, která popisuje důvod zastavení), nebo jen pokračovat v provádění.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Získá kontext dokumentu, který popisuje umístění této události.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Získá kontext kódu, který popisuje umístění této události.|  
  
## <a name="remarks"></a>Poznámky  
 DE pošle toto rozhraní, pokud uživatel kroky do funkce a nenajde žádné informace o ladění, nebo existují informace o ladění, ale DE neví, zda lze pro dané umístění zobrazit zdrojový kód.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
