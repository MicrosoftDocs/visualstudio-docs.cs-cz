---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b036bd68aca126675f26b9823d2c786a0ae652
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675332"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní umožňuje správci ladění relace (SDM) oznamovat proces, ke kterému se připojuje nebo odpojuje od tohoto procesu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Vlastní dodavatel portu implementuje toto rozhraní na stejném objektu jako rozhraní [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , aby:  
  
- Podpora sledování relací připojených k procesu  
  
- Podpora automatického připojení mezi několika ladicími moduly  
  
  Vlastní dodavatel portu může implementovat toto rozhraní, pokud se rozhodne.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
  
- SDM zavolá metodu [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugProcess2` rozhraní, aby získala toto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugProcessEx2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Připojit](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje o procesu, že relace právě ladí proces.|  
|[Odpojit](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje o procesu, že relace již neprovádí ladění procesu.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Přidá uzly programu pro seznam ladicích modulů.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je privátní mezi modelem SDM a procesem.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Portpriv. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
