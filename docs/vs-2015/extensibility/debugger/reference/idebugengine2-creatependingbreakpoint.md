---
title: 'IDebugEngine2:: CreatePendingBreakpoint | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84c36d08c7ad907006eb9f41d2f6e2c9cd77e7bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196035"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří nevyřízenou zarážku v ladicím modulu (DE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBPRequest`  
 pro Objekt [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , který popisuje probíhající zarážku, která má být vytvořena.  
  
 `ppPendingBP`  
 mimo Vrátí objekt [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , který představuje nevyřízenou zarážku.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Obvykle vrátí `E_FAIL` , pokud `pBPRequest` parametr neodpovídá žádnému jazyku podporovanému de z, pokud `pBPRequest` je parametr neplatný nebo neúplný.  
  
## <a name="remarks"></a>Poznámky  
 Nevyřízená zarážka je v podstatě kolekcí všech informací potřebných k navázání zarážky na kód. Nevyřízená zarážka vrácená z této metody není vázána na kód, dokud není volána metoda [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) .  
  
 Pro každou nevyřízenou zarážku, kterou nastaví uživatel, volá Správce ladění relace (SDM) tuto metodu u každého připojeného příkazu DE. Aby bylo možné ověřit, zda je zarážka platná pro programy běžící v této DE, je až do DE.  
  
 Když uživatel nastaví zarážku na řádek kódu, je DE-Free k navázání zarážky na nejbližší řádek v dokumentu, který odpovídá tomuto kódu. Díky tomu může uživatel nastavit zarážku na prvním řádku víceřádkového příkazu, ale vytvoří jej na posledním řádku (kde je veškerý kód uveden v ladicích informacích).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CProgram` objekt. Implementace DE `IDebugEngine2::CreatePendingBreakpoint` by pak mohla přesměrovat všechna volání do této implementace metody v každém programu.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Zapisovat](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
