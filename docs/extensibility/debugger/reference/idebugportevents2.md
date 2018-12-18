---
title: IDebugPortEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af2652bd18ff5d371389e8d3a7d3ab4c477eaa34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120033"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Toto rozhraní upozorní naslouchací proces (obvykle relace ladění správce [SDM] nebo modul ladění) proces a program vytváření a odstraňování na konkrétním portu. Tyto informace slouží k dispozici v reálném čase zobrazení procesy a programy spuštěné na portu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Visual Studio obvykle implementuje toto rozhraní k přijímání oznámení o programu vytváření a likvidace. Modul ladění můžete taky implementovat toto rozhraní tak, aby naslouchala událostem takové port.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Všechny [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) rozhraní může být dotazován pro <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní. Pak se <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metodu pro `IDebugPortEvents2` je volána <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní získat <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní. Nakonec <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metoda v <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní nazývá odesílat události prostřednictvím [událostí](../../../extensibility/debugger/reference/idebugportevents2-event.md) metoda.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metodě `IDebugPortEvents2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Události](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Odesílá události, které popisují vytváření a likvidace procesy a programů na portu.|  
  
## <a name="remarks"></a>Poznámky  
 `IDebugPortEvents2` používá také SDM k ladění programů, které běží v procesu, který je již ladit.  
  
 Port události je předán SDM pomocí tohoto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)