---
title: IDebugCanStopEvent2 | Dokumentace Microsoftu
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
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 564fb7103e82d5d4a82447a3e24a032671890557
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741673"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní umožňuje požádat správce ladění relace (SDM), jestli se má zastavit na aktuální umístění v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní pro podporu procházení zdrojového kódu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí implementovat rozhraní na stejný objekt jako toto rozhraní (SDM používá [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) přístup `IDebugEvent2` rozhraní).  
  
 Implementace tohoto rozhraní musí komunikovat SDM volání [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) k ladicímu stroji. Například to lze provést pomocí zprávy odeslané na zpracování vlákna zprávy ladicímu stroji nebo objekt implementující toto rozhraní může obsahovat odkaz na ladicí stroj a zpětné volání do ladicího stroje s příznakem předaná do `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 DE odeslat, že tato metoda pokaždé, když je DE se zobrazí výzva, chcete-li pokračovat v provádění a DE je krokování kódu. Tato událost je odeslána pomocí [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) poskytnutých SDM při připojení k laděnému programu funkce zpětného volání.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugCanStopEvent2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Získá důvod pro tuto událost.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Určuje, zda by měl laděnému programu zastavit v umístění této události (a odeslat událost, která popisuje důvody, proč zastavení) nebo pouze pokračování v provádění.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Získá kontext dokumentu, který popisuje umístění této události.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Získá kontext kódu, který popisuje umístění této události.|  
  
## <a name="remarks"></a>Poznámky  
 DE odešle toto rozhraní, pokud uživatel kroky do funkce a DE najde žádné ladicí informace nebo informace o ladění existuje, ale DE neví, pokud pro toto umístění můžete zobrazit zdrojový kód.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

